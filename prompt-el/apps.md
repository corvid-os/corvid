# Aplikacje

## ✅ Live ISO — zestaw startowy

Środowisko live oparte o GNOME (patrz `design.md` → Środowisko graficzne).
Cel: użytkownik ma od razu narzędzia do (a) zainstalowania systemu, (b) awaryjnej
naprawy/ratowania danych, (c) sprawdzenia że sprzęt/sieć działa, zanim zdecyduje
się na instalację.

| Aplikacja | Pakiet (Arch) | Rola |
|---|---|---|
| **Corvid Installer** | `corvid-installer` (własny) | odpala się automatycznie po starcie live session (z opcją "Try / Install", jak Ubuntu), dostępny też jako ikona na pulpicie |
| GNOME Files | `nautilus` | przeglądanie plików, sprawdzenie dysków/partycji przed instalacją |
| GNOME Console | `gnome-console` | terminal — dostęp do `pacman`, `lsblk`, ręcznej diagnostyki |
| GNOME Text Editor | `gnome-text-editor` | szybka edycja configów (np. ręczna edycja `fstab`, `sshd_config` w trybie ratunkowym) |
| Firefox | `firefox` | internet — dokumentacja, forum, sprawdzenie że Wi-Fi/sieć działa przed instalacją |
| GParted | `gparted` | ręczny partycjoner dla zaawansowanych — alternatywa/uzupełnienie kroku partycjonowania w instalatorze |
| GNOME System Monitor | `gnome-system-monitor` | podgląd RAM/CPU/dysków — przydatne przy starszym sprzęcie |
| nm-applet / GNOME Wi-Fi | `network-manager-applet` (część GNOME Shell) | podłączenie do sieci przed instalacją |
| htop | `htop` | terminalowy monitor procesów, fallback gdy GUI nie odpala |
| TestDisk / PhotoRec | `testdisk` | ratowanie danych / odzyskiwanie partycji — tryb "rescue" |

### Zachowanie przy starcie
- Live session startuje w GNOME, na pulpicie/dashboardzie widoczna ikona/skrót **"Zainstaluj Corvid OS"**
- Opcjonalnie: okno powitalne przy starcie (styl GNOME Initial Setup / Ubuntu welcome) z wyborem: *Wypróbuj Live* / *Zainstaluj teraz*
- TBD: czy robimy własny "welcome dialog" czy odpalamy installer wprost

## Post-instalacja — zestaw domyślnych aplikacji

TBD — do ustalenia. Robocze kierunki do dyskusji w kolejnej turze:
- **Podstawa** (niezależnie od profilu): przeglądarka, menedżer plików, terminal, edytor tekstu, odtwarzacz multimediów
- **Gaming**: Steam, Proton (przez Steam), `gamemode`, `mangohud`, sterowniki GPU (TBD: automatyczna detekcja NVIDIA/AMD w instalatorze)
- **Dev**: git, edytor/IDE (VS Code? TBD który), Docker/Podman (TBD który), baza narzędzi CLI (TBD lista)
- TBD: czy to jeden wspólny zestaw dla wszystkich, czy instalator pyta o profil (gaming/dev/minimal) i dobiera pakiety
