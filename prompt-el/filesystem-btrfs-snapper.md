# Filesystem: Btrfs + snapper + grub-btrfs

Szczegóły implementacyjne dla sekcji "System plików / snapshoty" z `design.md`.

## Layout subwolumenów

Standardowy, snapper-friendly layout (podobny do zalecanego na Arch Wiki):

| Subwolumen | Mountpoint | Cel |
|---|---|---|
| `@` | `/` | root systemu |
| `@home` | `/home` | dane użytkownika — osobno, żeby rollback roota nie ruszał `/home` |
| `@var_log` | `/var/log` | logi — osobno, żeby nie rosły w snapshotach roota |
| `@var_cache_pacman_pkg` | `/var/cache/pacman/pkg` | cache pakietów — osobno, nie ma sensu w snapshotach |
| `@snapshots` | `/.snapshots` | miejsce na snapshoty snappera |
| `@swap` *(opcjonalnie)* | `/swap` | plik swap — Btrfs wymaga wyłączenia CoW (`chattr +C`) dla plików swap |

## Opcje montowania
`noatime,compress=zstd:1,space_cache=v2` — `zstd:1` jako balans kompresji/wydajności
(niższy poziom niż domyślny dla mniejszego narzutu CPU, wciąż spory zysk miejsca).

## Konfiguracja snapper

- Config: `root` (dla `/`), utworzony przez instalator automatycznie po `pacstrap`
- Harmonogram (`TIMELINE_*` w `/etc/snapper/configs/root`):

| Typ | Ile trzymamy |
|---|---|
| hourly | 5 |
| daily | 7 |
| weekly | 4 |
| monthly | 6 |
| yearly | 0 (wyłączone) |

- `snap-pac` (pakiet) — automatyczne snapshoty **przed i po** każdej transakcji
  `pacman`/`paru` (pre/post hook), niezależnie od harmonogramu timeline

## grub-btrfs

- `grub-btrfs` generuje wpisy w menu GRUB dla snapshotów — możliwość zbootowania
  systemu ze snapshotu bezpośrednio z menu bootloadera
- `grub-btrfsd` (daemon, z pakietu `grub-btrfs`) działa jako systemd service,
  automatycznie regeneruje menu GRUB przy nowym snapshocie (nasłuchuje na
  `/.snapshots` przez inotify) — **włączony domyślnie** po instalacji

## Procedura rollback (dla użytkownika / dokumentacji)
1. Restart → w menu GRUB wybierz "Corvid OS snapshots" → wybierz snapshot → boot
2. Jeśli snapshot działa poprawnie: `snapper rollback` z działającego snapshotu
   (albo z live/rescue) żeby ustawić go jako nowy domyślny subwolumen
3. Reboot do świeżo przywróconego systemu

## TBD
- Czy instalator daje użytkownikowi wybór harmonogramu timeline, czy narzuca domyślny
- Czy `@swap` w ogóle używamy (czy wolimy zswap/zram zamiast pliku swap na Btrfs)
- Limit rozmiaru `/.snapshots` (snapper `NUMBER_LIMIT` / quota grupowa Btrfs)
