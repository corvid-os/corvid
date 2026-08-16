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
| **`corvid`** *(to repo)* | meta/dokumentacja |
| [`installer`](https://github.com/corvid-os/installer) | Corvid Installer — Python + GTK4/libadwaita |
| [`iso`](https://github.com/corvid-os/iso) | profil `archiso` do budowania Live/Install ISO |
| [`branding`](https://github.com/corvid-os/branding) | logo, ikony, motywy Plymouth/GRUB, tapety, paleta |
| [`pkgbuilds`](https://github.com/corvid-os/pkgbuilds) | PKGBUILDy / własne repo pakietów (`corvid-*`) |
| `prompt-el` *(prywatne)* | pełna specyfikacja projektu (`prompt.md`/`design.md`/`code.md`) + historia decyzji |

## Design

Pełny design systemu żyje w prywatnym repo `corvid-os/prompt-el` (`design.md`) —
etap burzy mózgów z rozproszonymi plikami roboczymi (`prompt-el/` który był tu
wcześniej) został skompresowany i przeniesiony tam po zamknięciu fazy design (M0).

## Status

Design (M0) zamknięty. W trakcie: szkielet instalatora (M1) — patrz
`code.md` w `corvid-os/prompt-el` i roadmapę w `design.md`.
