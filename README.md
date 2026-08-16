# Corvid OS

Własna dystrybucja Linuksa oparta na Arch Linux — ładny wygląd, gaming, deweloperka
i codzienny desktop w jednym. GNOME lub Hyprland do wyboru przy instalacji, własny
modularny instalator (Python + GTK4/libadwaita), Btrfs + snapper + grub-btrfs,
pacman + paru.

## Repozytoria organizacji [`corvid-os`](https://github.com/corvid-os)

Projekt jest podzielony na osobne repo per komponent — każde do pobrania/wersjonowania
niezależnie:

| Repo | Zawartość |
|---|---|
| **`corvid`** *(to repo)* | meta/dokumentacja, ewolucja promptu/designu |
| [`installer`](https://github.com/corvid-os/installer) | Corvid Installer — Python + GTK4/libadwaita |
| [`iso`](https://github.com/corvid-os/iso) | profil `archiso` do budowania Live/Install ISO |
| [`branding`](https://github.com/corvid-os/branding) | logo, ikony, motywy Plymouth/GRUB, tapety, paleta |
| [`pkgbuilds`](https://github.com/corvid-os/pkgbuilds) | PKGBUILDy / własne repo pakietów (`corvid-*`) |

## Struktura tego repo

- [`prompt-el/`](./prompt-el) — **folder roboczy z ewolucją promptu/designu.**
  Tu na bieżąco powstają notatki, decyzje projektowe, propozycje itd. Docelowo
  ten folder zostanie skompresowany do 3 plików (`prompt.md`, `design.md`, `code.md`)
  i przeniesiony do osobnego, prywatnego repo — to co tu widać to etap roboczy,
  publiczny tymczasowo.

Zobacz [`prompt-el/README.md`](./prompt-el/README.md) po szczegóły plików roboczych.

## Status

Wczesna faza projektowa — ustalamy design, branding i architekturę zanim
zabierzemy się za kod (instalator, profil archiso, custom repo pakietów).
