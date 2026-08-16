# Design distro

Szkic dokumentu projektowego. Zawiera tylko to, co już ustalone — reszta to
sekcje `TBD` do uzupełnienia w kolejnych turach.

## Cel / target
Wszystko naraz, nie wąska nisza: ładny wygląd, gaming, deweloperka, codzienny desktop.

## Baza
Arch Linux (rolling release), budowa ISO przez `archiso`.

## Środowisko graficzne
- Live ISO / instalator: **GNOME**
- Do wyboru przy instalacji: **GNOME** albo **Hyprland**
- TBD: dokładny zestaw pakietów per DE (rozszerzenia GNOME, konfiguracja Hyprland/waybar/itd.)

## Instalator
- Własny, pisany w **Pythonie**, **modularny** — każdy krok instalacji to osobny moduł,
  żeby dało się łatwo dodać kolejny krok bez rozrastania się jednego pliku do
  kilku tysięcy linijek
- GUI: **GTK4 + libadwaita** (spójne z GNOME live ISO)
- Powód własnego instalatora zamiast Calamares: dokumentacja Calamares nie
  pasuje do tego jak chcemy to rozwijać
- TBD: dokładna lista kroków instalatora (partycjonowanie, użytkownik, lokalizacja,
  wybór DE, bootloader, itd.), struktura modułów

## Zarządzanie pakietami
- `pacman` jako podstawa
- `paru` jako AUR helper

## System plików / snapshoty
- **Btrfs** jako domyślny system plików
- **snapper** do automatycznych snapshotów
- Integracja z **GRUB** przez `grub-btrfs` (bootowanie snapshotów z menu GRUB)

## Branding
- **Nazwa: Corvid OS** (decyzja w [`naming.md`](./naming.md))
- Instalator: **Corvid Installer**, binarka/prefiks: `corvid`
- Prefiks pakietów własnego repo: `corvid-*`
- Kolorystyka: **fiolet/indygo** jako akcent (nawiązanie do iridescencji piór kruka), ciemny motyw domyślny (z jasnym wariantem opcjonalnym)
- Maskotka: kruk (motyw "corvid")
- TBD: logo/maskotka (konkretny design), motyw Plymouth, motyw GRUB, tapety, konkretna paleta (hex), ikony

## Infrastruktura / GitHub
- Organizacja: **[`corvid-os`](https://github.com/corvid-os)** (kontakt: `corvid-os@proton.me`)
- ✅ Decyzja: **multi-repo**, nie jeden monolit — każdy komponent osobno do pobrania/wersjonowania:

| Repo | Zawartość |
|---|---|
| [`corvid`](https://github.com/corvid-os/corvid) | meta/dokumentacja, ewolucja promptu (`prompt-el/`), docelowo `prompt.md`/`design.md`/`code.md` |
| [`installer`](https://github.com/corvid-os/installer) | **Corvid Installer** — Python + GTK4/libadwaita, modularny |
| [`iso`](https://github.com/corvid-os/iso) | profil `archiso` do budowania Live/Install ISO (spina installer, branding, listę apek live) |
| [`branding`](https://github.com/corvid-os/branding) | logo, ikony, motyw Plymouth/GRUB, tapety, paleta kolorów |
| [`pkgbuilds`](https://github.com/corvid-os/pkgbuilds) | PKGBUILDy / custom repo pakietów (`corvid-*`, patche gamingowe itd.) |

- TBD: CI/CD do automatycznego budowania ISO i publikowania paczek

## Aplikacje
- ✅ Zestaw dla **Live ISO** ustalony — patrz [`apps.md`](./apps.md)
- Zestaw **predefiniowanych aplikacji po instalacji** (przeglądarka, edytor/IDE,
  narzędzia gamingowe typu Steam/Proton/gamemode, narzędzia dev typu git/kontenery)
  — TBD, patrz [`apps.md`](./apps.md) (sekcja placeholder)

## Własne repozytorium pakietów
TBD — czy robimy własne repo (wzorem Chaotic-AUR/CachyOS), co by w nim siedziało
(np. prebuild AUR, patche do gamingu), jak je hostować.

## Struktura projektu (docelowa kompresja)
Etap roboczy: dużo plików w tym katalogu (ten plik, `naming.md`, `wiki.md`, `links.md`, itd.).
Cel końcowy: skompresować wszystko do 3 plików:
- `prompt.md` — finalny prompt/spec całego projektu
- `design.md` — ostateczny design systemu
- `code.md` — kod (instalator, konfiguracja archiso, itd.)
