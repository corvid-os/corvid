# Aplikacje po instalacji

Finalizacja sekcji "Post-instalacja" z `apps.md`. Zestawy powiązane z krokiem
"Profil" (`installer-steps.md` #8) i metapaczkami z `package-management.md`.

## Core (zawsze, niezależnie od profilu)

| Aplikacja | Pakiet | Rola |
|---|---|---|
| Firefox | `firefox` | przeglądarka domyślna |
| Menedżer plików | `nautilus` (GNOME) / **`thunar`** (Hyprland) | ✅ różne per DE — Thunar zgodnie z realnym setupem w `desktop-hyprland.md` (lżejszy, bez zależności GNOME) |
| Terminal | patrz `dev-environment.md` (per DE) | — |
| Odtwarzacz multimediów | `mpv` | lekki, uniwersalny |
| Przeglądarka zdjęć | `loupe` (GNOME) / `imv` (Hyprland) | — |
| Archiwizator | `file-roller` (GNOME) / `xarchiver` (Hyprland, spójne z Thunar) | zip/tar/itd. |
| LibreOffice | ✅ `libreoffice-fresh` (pełny pakiet) | Writer, Calc, Impress, Draw, Base, Math — kompletny pakiet biurowy od razu, bez doinstalowywania modułów |

## Profil Gaming (dodatkowo)
Patrz `gaming.md` → pakiet `corvid-gaming` (Steam, gamemode, mangohud, Proton-GE
przez protonup-qt, sterowniki kontrolerów).

## Profil Dev (dodatkowo)
Patrz `dev-environment.md` → pakiet `corvid-dev` (fish+starship, Podman, git+delta+lazygit+gh,
VSCodium, neovim, mise).

## Profil "Oba" (Gaming + Dev)
Suma `corvid-gaming` + `corvid-dev` — bez konfliktów pakietowych (różne przestrzenie:
jeden gra, drugi koduje), więc łączenie jest bezpieczne.

## Profil Minimalny
Tylko `corvid-base` + wybrane DE (`corvid-gnome`/`corvid-hyprland`) + Core z tabeli
wyżej — bez Gaming/Dev. Dla użytkowników chcących lekkiego, czystego systemu i
doinstalowania wszystkiego ręcznie później.

## TBD
- Czy Core zawiera cokolwiek do komunikacji (Discord? — kontrowersyjne jako "domyślne",
  raczej NIE preinstalować, zostawić do doinstalowania)
- Klient poczty — raczej nie domyślnie (większość używa web/Firefoxa)
