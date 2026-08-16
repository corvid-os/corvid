# Roadmapa projektu

Kamienie milowe od stanu obecnego do pierwszego publicznego wydania.

| Etap | Cel | Repo(a) | Definicja "zrobione" |
|---|---|---|---|
| **M0 — Design** *(obecny etap)* | Kompletny, spójny design całego systemu | `corvid` | Wszystkie sekcje `design.md` i plików szczegółowych bez `TBD` blokujących start kodu |
| **M1 — Szkielet instalatora** | Działające okno GTK4/libadwaita, 2-3 pierwsze kroki (welcome, keyboard, network) w trybie `--dry-run` | `installer` | Da się przejść wizardem, backend loguje zamiast wykonywać |
| **M2 — Minimalne Live ISO** | `archiso` profil budujący bootowalne GNOME live ISO (bez jeszcze pełnego instalatora) | `iso` | ISO odpala się w VM, GNOME działa, apki z `apps.md` obecne |
| **M3 — Instalator kompletny (ścieżka GNOME)** | Wszystkie 14 kroków z `installer-steps.md` działają end-to-end na VM | `installer`, `iso` | Świeża instalacja GNOME + Btrfs/snapper bootuje się sama z siebie |
| **M4 — Ścieżka Hyprland** | Krok "Środowisko graficzne" realnie instaluje i konfiguruje Hyprland | `installer`, `pkgbuilds` | Instalacja z wyborem Hyprland bootuje się do działającego configu z `desktop-hyprland.md` |
| **M5 — Branding i custom repo na poważnie** | Realne assety (logo, Plymouth, GRUB theme), repo `pkgbuilds` buduje i publikuje paczki przez CI | `branding`, `pkgbuilds` | `pacman -Syu` na świeżym systemie widzi i instaluje z repo `corvid` |
| **M6 — Alpha release** | Pierwsze publiczne ISO do pobrania, ogłoszenie | wszystkie | Release na GitHub z ISO, changelogiem, znanymi ograniczeniami spisanymi |

## Zasada priorytetów między etapami
Nie przechodzimy do kolejnego M, dopóki poprzedni nie działa end-to-end w VM —
unikamy sytuacji "wszystko na 80% ukończone, nic w pełni działające".

## TBD
- Konkretne daty/deadline'y (na razie brak presji czasowej — projekt hobby/side)
- Czy M6 to jeszcze "alpha" czy od razu "0.1" w jakimś schemacie wersjonowania
  (patrz też: `TBD` w `roadmap` dot. wersjonowania ISO — do dopisania jak dojdziemy do M5/M6)
