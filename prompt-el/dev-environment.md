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
- ✅ **VSCodium** (pakiet `vscodium-bin` z AUR) — domyślny GUI edytor/IDE. Wybrany
  zamiast VS Code świadomie: ten sam kod źródłowy (Code-OSS, MIT), ale bez
  telemetrii Microsoftu wbudowanej w binarkę i bez własnościowej warstwy —
  spójne z resztą filozofii projektu (własny instalator zamiast Calamares,
  Podman zamiast Dockera). Domyślny rejestr rozszerzeń: **Open VSX**
  (ograniczenie: część oficjalnych rozszerzeń MS, np. C/C++, nie jest tam
  dostępna/wspierana — użytkownik może ręcznie dodać inny rejestr na własne ryzyko)
- **neovim** — zawsze obecny jako edytor terminalowy (fallback, szybkie edycje configów)

## NVIDIA / CUDA (gdy wykryto kartę NVIDIA)
Sterownik GPU (`nvidia-open-dkms`/`nvidia-dkms`) instaluje się zawsze na
poziomie sprzętu, niezależnie od profilu — patrz `gaming.md` → Sterowniki GPU.
Profil **Dev** dokłada do tego narzędzia pod pracę z GPU (ML/AI, obliczenia
równoległe), których Gaming/Minimalny nie potrzebują:

| Pakiet | Rola |
|---|---|
| `cuda` | CUDA Toolkit — kompilator `nvcc`, biblioteki do obliczeń na GPU (PyTorch/TensorFlow z akceleracją, itd.) |
| `cudnn` | biblioteka do sieci neuronowych na GPU (wymagana przez większość frameworków ML) |
| `nvidia-container-toolkit` | dostęp do GPU **z poziomu kontenerów Podman** (`--device nvidia.com/gpu=all`) — bez tego kontenery nie widzą karty |

Instalowane automatycznie w profilu Dev/Oba **tylko jeśli** instalator wykrył
GPU NVIDIA w kroku 13 (na AMD/Intel te pakiety nie mają zastosowania — ROCm
dla AMD to osobny, większy temat, poza zakresem pierwszego wydania).

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
- Czy dorzucamy `docker` alias na `podman`, czy zostawiamy jawny wybór usera
- Czy `corvid-dev` instaluje jakiekolwiek kompilatory/runtime domyślnie (np. `base-devel`
  już jest w `corvid-base` — patrz `package-management.md` — więc gcc/make już jest)
