# Corvid Installer — architektura kodu

Szczegóły implementacyjne dla repo [`installer`](https://github.com/corvid-os/installer).
Python + GTK4/libadwaita, modularny.

## Struktura katalogów (docelowa)

```
installer/
├── pyproject.toml
├── corvid_installer/
│   ├── __init__.py
│   ├── main.py              # entry point, tworzy Adw.Application
│   ├── state.py             # InstallState — centralny stan wyborów użytkownika
│   ├── window.py            # główne okno, Adw.NavigationView jako "wizard"
│   ├── steps/                # jeden moduł = jeden krok z installer-steps.md
│   │   ├── __init__.py
│   │   ├── base.py           # klasa bazowa InstallStep
│   │   ├── welcome.py
│   │   ├── keyboard.py
│   │   ├── network.py
│   │   ├── disk.py
│   │   ├── encryption.py
│   │   ├── locale.py
│   │   ├── desktop_choice.py
│   │   ├── profile_choice.py
│   │   ├── user_account.py
│   │   ├── bootloader.py
│   │   ├── snapshots.py
│   │   ├── summary.py
│   │   └── progress.py
│   ├── backend/               # logika bez GUI — testowalna osobno
│   │   ├── disk.py            # partycjonowanie, formatowanie (parted/sgdisk wrappers)
│   │   ├── btrfs.py           # subwolumeny, mount options
│   │   ├── pacstrap.py        # wywołania pacstrap/genfstab
│   │   ├── chroot.py          # konfiguracja w arch-chroot (locale, bootloader, użytkownik)
│   │   └── snapper.py         # inicjalizacja configu snapper
│   └── ui/
│       └── widgets/           # współdzielone widgety (np. password strength meter)
└── tests/
    └── ...                    # testy jednostkowe backendu (bez potrzeby realnego dysku — mock)
```

## Wzorzec kroku (`InstallStep`)

Każdy krok implementuje wspólny interfejs:

```python
class InstallStep:
    id: str
    title: str

    def build_widget(self, state: InstallState) -> Gtk.Widget: ...
    def validate(self, state: InstallState) -> ValidationResult: ...
    def apply(self, state: InstallState) -> None: ...   # zapisuje wybór do InstallState
    def is_visible(self, state: InstallState) -> bool: ... # np. krok "encryption" zawsze widoczny, ale profil może warunkować kolejne
```

Kroki rejestrowane w liście w `window.py` — dodanie nowego kroku instalatora
to: nowy plik w `steps/`, dopisanie go do listy. Zero zmian gdzie indziej.

## `InstallState`
Prosty, serializowalny obiekt (dataclass) trzymający wszystkie wybory —
jedno źródło prawdy, przekazywane do każdego kroku i do backendu wykonującego
faktyczną instalację. Dzięki temu podsumowanie (krok 12) to po prostu render
tego obiektu, a wykonanie (krok 13) to jedna funkcja `run_installation(state)`.

## GUI
- `Adw.ApplicationWindow` + `Adw.NavigationView` do przejść między krokami (animacje "wizard-style")
- `Adw.ToastOverlay` do nieblokujących komunikatów (np. "Połączono z Wi-Fi")
- Ciemny motyw wymuszony w live/instalatorze (spójność z brandingiem niezależnie od motywu systemowego)

## Logowanie i obsługa błędów
- Wszystkie komendy backendu logowane do `/var/log/corvid-installer.log` (dostępne
  też z live session przez terminal — patrz `apps.md`)
- Błąd w kroku 13 nie zamyka instalatora — pokazuje log + opcję "Spróbuj ponownie" / "Przerwij"

## Tryb testowy
- Backend uruchamialny w trybie `--dry-run` — loguje komendy zamiast je wykonywać,
  pozwala testować cały flow UI bez realnego dysku/VM

## TBD
- Konkretny wybór narzędzia do partycjonowania w backendzie (`parted` przez subprocess
  vs `python-parted`/`pyparted` bindings)
- Format pliku do zapisu/wczytania konfiguracji (np. eksport `InstallState` do YAML
  dla przyszłej instalacji nienadzorowanej / automatyzacji)
- CI: lint (ruff) + testy backendu na każdy PR
