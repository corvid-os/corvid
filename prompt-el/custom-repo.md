# Własne repozytorium pakietów

Szczegóły implementacyjne dla repo [`pkgbuilds`](https://github.com/corvid-os/pkgbuilds)
(patrz też `design.md` → Infrastruktura).

## Co siedzi w repo

| Pakiet | Rola |
|---|---|
| `corvid-installer` | Corvid Installer (z repo `installer`) |
| `corvid-gnome-config` | dconf defaults, rozszerzenia, motyw GNOME |
| `corvid-hyprland-config` | domyślny config Hyprland/waybar/itd. |
| `corvid-plymouth-theme` | motyw ekranu ładowania |
| `corvid-grub-theme` | motyw GRUB |
| `corvid-wallpapers` | zestaw domyślnych tapet |
| `corvid-gnome` / `corvid-hyprland` / `corvid-gaming` / `corvid-dev` / `corvid-base` / `corvid-btrfs` | metapaczki grupujące (patrz `package-management.md`) |

## Hosting

- Paczki budowane w **GitHub Actions** (CI w repo `pkgbuilds`) przy każdym
  merge do `main`
- Zbudowane paczki + baza repo (`corvid.db.tar.zst`) publikowane jako
  **GitHub Releases** (assets), aktualizowane przez CI (`repo-add` + upload)
- Serwowane statycznie — GitHub Releases URL wpięty bezpośrednio jako serwer
  repo w `pacman.conf` klientów (bez potrzeby własnego serwera/domeny na start)

## Podpisywanie (GPG)

- Repo podpisane własnym kluczem GPG organizacji (`corvid-os`)
- Klucz publiczny dystrybuowany w pakiecie `corvid-keyring` (instalowanym jako
  jeden z pierwszych kroków przez instalator, zanim pacman zacznie ufać repo)
- `SigLevel = Required DatabaseOptional` dla repo `corvid` w `pacman.conf`

## Wpis w `pacman.conf` (klient)

```ini
[corvid]
SigLevel = Required DatabaseOptional
Server = https://github.com/corvid-os/pkgbuilds/releases/latest/download
```

## TBD
- Wersjonowanie: rolling (nadpisywanie `latest` release) czy tagowane wydania paczek
- Czy w przyszłości przechodzimy na własny serwer (koszt/skala) zamiast GitHub Releases
- Automatyczne rebuildy przy nowych wersjach AUR-owych zależności (bot? cron w CI?)
