# Środowisko graficzne — Hyprland

Szczegóły implementacyjne dla ścieżki Hyprland z `design.md` → Środowisko graficzne.
Wybór dla power-userów podczas instalacji (krok 7 w `installer-steps.md`).

## Komponenty stacka

| Rola | Wybór |
|---|---|
| Compositor | `hyprland` |
| Pasek/status bar | `waybar` |
| Launcher | `wofi` |
| Lockscreen | `hyprlock` |
| Idle/auto-lock | `hypridle` |
| Powiadomienia | `mako` |
| Tło pulpitu | `hyprpaper` |
| Portal (screen share, file picker) | `xdg-desktop-portal-hyprland` |
| Terminal | `kitty` |
| Pasek głośności/jasności (OSD) | `swayosd` |
| Zrzuty ekranu | `grim` + `slurp` |

## Filozofia keybindów
- `SUPER` jako główny modyfikator (spójnie z konwencją większości tiling WM)
- `SUPER + [1-9]` — przełączanie workspace, `SUPER + SHIFT + [1-9]` — przenieś okno
- `SUPER + Q` — zamknij okno, `SUPER + Return` — terminal, `SUPER + D` — launcher (wofi)
- Nawigacja fokusu strzałkami **i** `hjkl` (vim-style) — obie opcje działają, żeby nie
  zmuszać nikogo do jednego stylu

## Domyślny wygląd
- Gaps/rounding: umiarkowane (nie ultra-minimalistyczne "bare" ani przesadnie "eye-candy")
- Motyw kolorystyczny: ta sama paleta co reszta systemu (`branding-palette.md`) —
  `waybar` i `wofi` stylowane pod `corvid-violet`/`corvid-void`
- Blur i animacje włączone domyślnie, ale lekkie (priorytet: płynność na słabszym sprzęcie
  gamingowym/starszych laptopach)

## Dystrybucja configów
Domyślny config (`~/.config/hypr/`, `waybar/`, `wofi/`, `mako/`) pakowany jako
`corvid-hyprland-config` w repo `pkgbuilds` (patrz `custom-repo.md`) — instalowany
automatycznie gdy użytkownik wybierze Hyprland w kroku 7 instalatora.

## TBD
- Dokładny plik `hyprland.conf` (do napisania jako właściwa treść pakietu, nie tylko spec)
- Czy oferujemy alternatywny launcher (`rofi-wayland` zamiast `wofi`) jako opcję
- Wsparcie multi-monitor — domyślne zachowanie (mirror vs extend, per-monitor workspace)
- Osobne repo `dotfiles` czy trzymamy configi w `branding`/`pkgbuilds`? (do decyzji)
