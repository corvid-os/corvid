# prompt-el

Folder roboczy z ewolucją promptu/designu dla **Corvid OS**. Projekt robiony
wspólnie, na razie w formie roboczej — dużo małych plików, docelowo
skompresowane do 3 i przeniesione do osobnego, prywatnego repo:

- `prompt.md` — finalny prompt/spec projektu
- `design.md` — ostateczny design systemu
- `code.md` — kod (instalator, konfiguracja archiso)

## Pliki robocze (obecny etap)

**Zacznij od [`design.md`](./design.md)** — to jest indeks/spis treści z linkami
do wszystkich plików poniżej, pogrupowany tematycznie.

| Plik | Zawartość |
|---|---|
| [`design.md`](./design.md) | **indeks** — spis treści całego designu z linkami |
| [`naming.md`](./naming.md) | nazwa (decyzja: Corvid OS) + historia odrzuconych nazw i dlaczego |
| [`branding-palette.md`](./branding-palette.md) | paleta kolorów (hex), typografia, logo, ikony |
| [`desktop-gnome.md`](./desktop-gnome.md) | GNOME: rozszerzenia, motyw, dconf, domyślne apki |
| [`desktop-hyprland.md`](./desktop-hyprland.md) | Hyprland: stack, keybindy, dystrybucja configów |
| [`onboarding.md`](./onboarding.md) | ekran powitalny przy pierwszym uruchomieniu (GNOME/Hyprland) |
| [`installer-steps.md`](./installer-steps.md) | 14 kroków instalatora, krok po kroku |
| [`installer-architecture.md`](./installer-architecture.md) | struktura kodu, wzorzec kroku, backend |
| [`package-management.md`](./package-management.md) | pacman/paru config, mirrorlist, grupy metapaczek |
| [`custom-repo.md`](./custom-repo.md) | własne repo pakietów — hosting, podpisywanie, CI |
| [`filesystem-btrfs-snapper.md`](./filesystem-btrfs-snapper.md) | subwolumeny, snapper, grub-btrfs, rollback |
| [`apps.md`](./apps.md) | lista aplikacji Live ISO |
| [`post-install-apps.md`](./post-install-apps.md) | zestawy apek po instalacji (Core/Gaming/Dev/Minimalny) |
| [`gaming.md`](./gaming.md) | kernel, sterowniki GPU, Steam/Proton/gamemode |
| [`dev-environment.md`](./dev-environment.md) | shell, kontenery, git tooling, edytor, mise |
| [`security-users.md`](./security-users.md) | sudo, firewall, LUKS, konta użytkowników |
| [`hardware-support.md`](./hardware-support.md) | firmware, GPU, laptopy, audio, Bluetooth |
| [`roadmap.md`](./roadmap.md) | kamienie milowe M0 → M6 |
| [`wiki.md`](./wiki.md) | notatki/fragmenty z Arch Wiki i innej dokumentacji |
| [`links.md`](./links.md) | same linki referencyjne, bez komentarza |

## Workflow
Dorzucamy pliki i notatki na bieżąco, każdy swoje. Zasada podziału: **jeden
temat = jeden plik**, `design.md` zostaje czystym indeksem (nie rozrasta się
w nieskończoność). Treść wiki/dokumentacji — do `wiki.md`, same linki — do
`links.md`. Iterujemy, aż uznamy że design jest kompletny, potem kompresja
do 3 plików docelowych.
