# Deweloperka — szczegóły

Rozwinięcie profilu *Dev* z `installer-steps.md` (krok 8) i `package-management.md`.

## Shell
- **fish** jako domyślny shell dla nowo tworzonego użytkownika (przyjazny out-of-the-box:
  autouzupełnianie, podświetlanie składni bez konfiguracji)
- **starship** jako prompt — jeden spójny, szybki prompt niezależnie od shella
  (fish/bash/zsh), skonfigurowany pod paletę `branding-palette.md`
- `bash` zostaje dostępny (skrypty systemowe/kompatybilność), ale nie jest
  domyślnym shellem interaktywnym użytkownika

## Kontenery
- **Podman** jako domyślny silnik kontenerów (rootless z założenia — lepiej pasuje
  do desktopowego, jednoużytkownikowego systemu niż Docker z demonem jako root)
- `podman-compose` dla kompatybilności z `docker-compose.yml`
- Alias/wrapper `docker` → `podman` do rozważenia (dla narzędzi zakładających
  literalnie komendę `docker`) — TBD czy to nie myli bardziej niż pomaga
- Docker dostępny do doinstalowania dla kogoś kto naprawdę go potrzebuje (VM/CI lokalne itp.)

## Git i narzędzia CLI
- `git` + `git-lfs`
- `delta` — czytelniejszy `git diff` (skonfigurowany jako pager gita domyślnie)
- `lazygit` — TUI do gita dla osób które go lubią (nieobowiązkowy nawyk, ale w zestawie)
- `gh` (GitHub CLI) — biorąc pod uwagę że cały projekt Corvid żyje na GitHubie,
  sensowne żeby był pod ręką od razu

## Edytor / IDE
- **VS Code** (pakiet `code` z AUR/repo — NIE `code` z Microsoft marketplace-owym
  telemetry blobem bez namysłu; do ustalenia dokładnie która paczka: `visual-studio-code-bin`
  vs w pełni open-source `vscodium`) — domyślny GUI edytor/IDE
- **neovim** — zawsze obecny jako edytor terminalowy (fallback, szybkie edycje configów)

## Menedżer wersji językowych
- **mise** (dawniej rtx) — zamiast preinstalowania konkretnych wersji Python/Node/Go/itd.
  na sztywno, użytkownik dev-profile dostaje `mise` i sam dobiera wersje projektowo
  (zgodnie z filozofią "nie zaśmiecamy systemu założeniami o stackach")

## Terminal
- GNOME: `gnome-console` (spójne z `desktop-gnome.md`)
- Hyprland: `kitty` (spójne z `desktop-hyprland.md`)
- Oba skonfigurowane z tym samym fontem (`branding-palette.md` → JetBrains Mono)
  i paletą kolorów, żeby doświadczenie było spójne niezależnie od DE

## TBD
- VSCodium vs VS Code (kompromis: wygoda/rozszerzenia Marketplace vs pełna otwartość)
- Czy dorzucamy `docker` alias na `podman`, czy zostawiamy jawny wybór usera
- Czy `corvid-dev` instaluje jakiekolwiek kompilatory/runtime domyślnie (np. `base-devel`
  już jest w `corvid-base` — patrz `package-management.md` — więc gcc/make już jest)
