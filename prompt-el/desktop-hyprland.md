# Środowisko graficzne — Hyprland

✅ Bazujemy na realnych, prywatnych dotfiles: **[`Lion15official/dotfiles`](https://github.com/Lion15official/dotfiles)**
("Hyprland / Noctalia dotfiles") — przetestowany na co dzień setup, nie
wymyślamy configu od zera. Poniżej rozbiór tego co tam jest i jak to
przekłada się na domyślny Hyprland w Corvid.

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

## Pochodzenie configu / plan wdrożenia w Corvid
- Źródło: prywatne repo [`Lion15official/dotfiles`](https://github.com/Lion15official/dotfiles)
- Plan: zaadaptować jako pakiet dystrybucyjny (patrz TBD — które repo/paczka),
  z usunięciem elementów osobistych (zawartość `Pictures/`, cokolwiek
  specyficznego dla maszyny/danych usera), zachowując szkielet Lua configu
  jako bazę domyślną w Corvid

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
- Docelowe repo/pakiet: nowe osobne repo (`corvid-os/hyprland-dotfiles`) czy
  wchodzi do istniejącego `branding`/`pkgbuilds`
- Licencja adaptowanego configu (dotfiles usera są prywatne — do ustalenia
  pod jaką licencją trafiają do publicznego Corvid)
