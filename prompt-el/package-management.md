# Zarządzanie pakietami

Szczegóły implementacyjne dla sekcji "Zarządzanie pakietami" z `design.md`.

## pacman

Zmiany względem domyślnego `/etc/pacman.conf`:

```ini
[options]
Color
ILoveCandy
ParallelDownloads = 10
VerbosePkgLists
```

- **multilib włączone domyślnie** — wymagane pod gaming (Steam, biblioteki 32-bit),
  a że gaming jest jednym z głównych celów dystrybucji, nie ma sensu robić tego opcjonalnym

## Mirrorlist

- `reflector` uruchamiany raz podczas instalacji (wybór najszybszych mirrorów wg
  kraju/regionu wykrytego automatycznie lub wybranego w kroku lokalizacji)
- systemd timer `reflector.timer` — odświeżanie mirrorlisty co tydzień w tle

## paru (AUR helper)

Domyślna konfiguracja (`/etc/paru.conf` lub per-user):
- `BottomUp` — nowe wyniki wyszukiwania na dole (czytelniej)
- `SudoLoop` — nie pyta o hasło sudo wielokrotnie w trakcie długiego builda
- Podgląd PKGBUILD przed budową **włączony domyślnie** (bezpieczeństwo — użytkownik
  widzi co faktycznie się buduje z AUR)

## Grupy pakietów (bazowe, niezależne od profilu)

| Grupa | Zawartość (przykładowo) |
|---|---|
| `corvid-base` | `base`, `base-devel`, `linux-firmware`, `networkmanager`, `sudo`, `git`, `reflector` |
| `corvid-btrfs` | `btrfs-progs`, `snapper`, `snap-pac`, `grub-btrfs` |
| `corvid-gnome` | patrz `desktop-gnome.md` |
| `corvid-hyprland` | patrz `desktop-hyprland.md` |
| `corvid-gaming` | patrz `gaming.md` |
| `corvid-dev` | patrz `dev-environment.md` |

Grupy definiowane jako metapaczki we własnym repo (`pkgbuilds`) — instalator instaluje
np. `pacman -S corvid-gnome corvid-gaming` zamiast wypisywać dziesiątki pakietów ręcznie.

## TBD
- Dokładna zawartość `corvid-base` (czy dorzucamy `zram-generator` domyślnie?)
- Czy `reflector` dobiera mirrory tylko z kraju użytkownika, czy z całego regionu
