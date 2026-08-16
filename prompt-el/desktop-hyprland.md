# Środowisko graficzne — Hyprland

✅ **Nie jest to nasz autorski config.** Bazą domyślnego Hyprlanda w Corvid OS
jest publiczny projekt **[Echilonvibin/minimaLinux](https://github.com/Echilonvibin/minimaLinux)**
(licencja **GPL-3.0**) — "minimalny starter dla Hyprland, świeży punkt wyjścia
do personalizacji, bez bloatu". Pełny kredyt dla autora, żadnych roszczeń do
tego configu — Corvid tylko go integruje i (ewentualnie) dostosowuje kolorystykę
pod branding. Rozpoznaliśmy ten stack, bo dotfiles usera są jego personalną
customizacją tego właśnie projektu — poniżej rozbiór tego co w nim jest.

**Ważne przez GPL-3.0**: jeśli Corvid pakuje/dystrybuuje ten config (nawet
zmodyfikowany), pakiet z nim musi zostać na GPL-3.0 i zawierać źródło + link
do oryginału — nie ma tu miejsca na relicencjonowanie.

## Komponenty stacka (z realnego configu)

| Rola | Wybór | Uwaga |
|---|---|---|
| Shell / bar / launcher / lock / OSD / tapeta | **[Noctalia Shell](https://github.com/noctalia-dev/noctalia-shell)** (QuickShell-based) | jeden spójny "shell" zamiast osobnych waybar+wofi+mako+hyprpaper+hyprlock+swayosd — sterowany przez `noctalia msg <cmd>` |
| Config Hyprlanda | pisany w **Lua** przez API `hl.*` (`hl.config()`, `hl.bind()`, `hl.monitor()`, `hl.dsp.*`) | zamiast klasycznego `hyprland.conf` — modularne pliki: `monitors.lua`, `inputs.lua`, `keybind.lua`, `windowrules.lua`, `animations.lua`, `startup.lua`, `themes/theme.lua` |
| Terminal | **kitty** | ✅ zgodne z tym co już ustaliliśmy w `dev-environment.md` |
| Menedżer plików | **Thunar** | ⚠️ zmiana względem wcześniejszego założenia — wcześniej zakładaliśmy Nautilus też pod Hyprland dla spójności z GNOME, ale realny setup usera używa Thunara (lżejszy, bez ciągnięcia zależności GNOME) — patrz TBD niżej |
| Zrzuty ekranu | `hyprshot` (szybki zrzut) + `satty` (adnotacje/edycja) | zamiast samego `grim`+`slurp` |
| Odtwarzacz muzyki | `quodlibet` | |
| Odtwarzacz wideo | `mpv` (`--player-operation-mode=pseudo-gui`) | |
| Edytor (keybind) | w wersji dystrybucyjnej: **`codium`** | osobiste dotfiles usera wskazują `code` — w Corvid dostosowane do decyzji o VSCodium (`dev-environment.md`) |
| Przeglądarka (skrypt) | fallback-chain: brave → firefox → zen-browser → vivaldi → librewolf (+ warianty Flatpak) | fajny wzorzec jako opcjonalny skrypt w configu; domyślny **Core** browser zostaje Firefox (`apps.md`) — nie zmieniamy domyślnej instalacji |

## Kolorystyka
Noctalia generuje motyw dynamicznie (`noctalia-colors.lua`) — aktualne wartości
w dotfiles usera to lawendowy zestaw w stylu Material You (`primary: #cacdff`,
`surface: #131318`, `secondary: #c2c4e7`, `error: #ffb4ab`) — ta sama rodzina
barw co `corvid-violet` z `branding-palette.md`, ale nie identyczna (jaśniejsza,
bardziej pastelowa). Decyzja koloru: patrz TBD.

## Keybindy (rzeczywisty schemat)

| Skrót | Akcja |
|---|---|
| `SUPER + RETURN` | terminal (kitty) |
| `SUPER + E` | menedżer plików (Thunar) |
| `SUPER + C` | edytor (codium) |
| `SUPER + B` | przeglądarka (skrypt fallback) |
| `SUPER + ALT + SPACE` | toggle launchera (Noctalia) |
| `SUPER + L` | zablokuj ekran |
| `SUPER + T` | toggle panelu ustawień (Noctalia) |
| `SUPER + H` / `SUPER + SHIFT + H` | cheatsheet skrótów / odśwież cheatsheet |
| `SUPER + K` | panel wszystkich skrótów Hyprlanda |
| `SUPER + S` | Steam |
| `SUPER + M` / `SUPER + V` | muzyka / wideo |
| `SUPER + W` | zamknij okno |
| `SUPER + F` | toggle floating |
| `SUPER + CTRL + F` | fullscreen |
| strzałki | focus w danym kierunku |
| `SUPER + SHIFT + CTRL + strzałki` | przenieś/zamień okno (inteligentnie: floating → przesuń, tiled → zamień) |
| `SUPER + [1-9,0]` / `+ SHIFT` | przejdź / przenieś okno na workspace |
| `SUPER + CTRL + strzałki` | następny/poprzedni workspace |
| `ALT + TAB` | cykl okien |
| `SUPER + A` / `ALT + PRINT` / `SHIFT + PRINT` | zrzut okna / monitora / regionu (hyprshot) |
| `SUPER + P` | zrzut z adnotacją (satty) |
| `SUPER + X` | tryb resize |
| `SUPER + scroll` | przełączanie workspace kółkiem |

Filozofia: `SUPER` jako jedyny główny modyfikator, nawigacja strzałkami (nie
vim-style hjkl — realny setup tego nie używa, więc nie narzucamy tego w
domyślnym configu Corvid).

## Instalacja / zależności
- minimaLinux jest napisany pod **świeży, czysty Arch** (z profilem Hyprland
  z `archinstall`) — dokładnie to co robi nasz instalator, więc integracja
  powinna być prosta (patrz `iso`/`installer`)
- Instaluje **Chaotic-AUR** jako zależność — jedyny pakiet stamtąd to sama
  **Noctalia** (AUR-only, nie ma jej w oficjalnych repo Arch)
- TBD: czy Corvid dociąga Chaotic-AUR na produkcyjnym systemie (dodatkowe,
  zewnętrzne, niezaufane-przez-nas repo), czy budujemy własny pakiet Noctalii
  we własnym `pkgbuilds` (patrz `custom-repo.md`) i unikamy zależności od
  zewnętrznego repo trzeciej strony

## Pierwsze uruchomienie
Przy pierwszym starcie Hyprlanda w świeżo zainstalowanym Corvid — patrz
**[`onboarding.md`](./onboarding.md)** (link do wideo z personalizacją +
repo źródłowego).

## TBD
- Stała paleta `corvid-violet` narzucona na Noctalię, czy zostawiamy dynamiczne
  generowanie motywu Noctalii (auto z tapety) jako domyślne zachowanie
- Zmienne środowiskowe NVIDIA z bloku `nvidia_optional` w `startup.lua` —
  kiedy dokładnie aplikowane (instalator powinien wstrzykiwać je warunkowo,
  tylko gdy wykryto GPU NVIDIA — patrz `gaming.md`)
- Panel "Użytkownicy" (zarządzanie kontem systemowym) pod Hyprland/Noctalia —
  `SUPER+T` (`settings-toggle`) to ustawienia **samego Noctalia Shell**
  (tapety, moduły paska), **nie** zarządzanie kontem systemowym — temat z
  `installer-steps.md` (equivalent GNOME Settings → Users) pozostaje otwarty
- Nautilus vs Thunar — potwierdzić ostatecznie Thunar jako domyślny dla ścieżki
  Hyprland (aktualizacja `post-install-apps.md`), i sprawdzić czy Thunar
  wymaga dodatkowych GVFS-backendów dla montowania dysków/MTP itd.
- Chaotic-AUR jako zależność vs własny pakiet Noctalii — patrz sekcja
  Instalacja/zależności wyżej
