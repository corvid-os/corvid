# Branding — paleta i szczegóły wizualne

Rozwinięcie sekcji "Branding" z `design.md`. Motyw: kruk (corvid) — czarne
pióra z fioletowo-niebieskim iridescencyjnym połyskiem.

## Paleta kolorów (dark, domyślna)

| Rola | Nazwa | Hex |
|---|---|---|
| Tło główne | `corvid-void` | `#0E0B14` |
| Powierzchnia (karty/panele) | `corvid-surface` | `#181420` |
| Powierzchnia podniesiona | `corvid-surface-raised` | `#221C2E` |
| Akcent podstawowy | `corvid-violet` | `#7B5CFA` |
| Akcent jasny (hover/focus) | `corvid-violet-light` | `#9B82FF` |
| Akcent głęboki (aktywne/pressed) | `corvid-indigo` | `#5433C7` |
| Tekst podstawowy | `corvid-text` | `#EDEAF6` |
| Tekst wyciszony | `corvid-text-muted` | `#A79FC0` |
| Sukces | `corvid-feather-green` | `#4ADE80` |
| Ostrzeżenie | `corvid-amber` | `#F5A623` |
| Błąd | `corvid-crimson` | `#F0476B` |

## Paleta jasna (opcjonalna, do dopracowania proporcji)

| Rola | Hex |
|---|---|
| Tło główne | `#F7F5FC` |
| Powierzchnia | `#FFFFFF` |
| Akcent (ten sam) | `#7B5CFA` |
| Tekst podstawowy | `#1A1622` |

## Zastosowanie

- **GNOME**: libadwaita 4.14+ wspiera `accent-color` — ustawiamy `purple`/custom
  najbliższy `corvid-violet` jako domyślny akcent systemowy
- **Plymouth**: tło `corvid-void`, spinner/logo w `corvid-violet`
- **GRUB**: tło `corvid-void` z akcentem `corvid-violet` na zaznaczonej pozycji menu,
  wpisy snapshotów (grub-btrfs) wizualnie wyróżnione (inny odcień/ikona)
- **Terminal (domyślny theme)**: paleta ANSI budowana wokół tych samych wartości
  (fiolet jako kolor 4/12, itd. — do dopracowania jako osobny plik `.theme` w repo `branding`)

## Typografia

| Kontekst | Font |
|---|---|
| UI (GNOME/GTK4) | **Inter** (systemowy fallback: domyślny Adwaita Sans) |
| Terminal / monospace | **JetBrains Mono** |
| Logo / wordmark | do zaprojektowania — kierunek: geometryczny, ostre kąty (nawiązanie do dzioba/skrzydeł kruka) |

## Logo / maskotka — kierunek koncepcyjny
Geometryczna, minimalistyczna sylwetka kruka (nie realistyczna ilustracja) —
dobrze skaluje się do małych rozmiarów (favicon, ikona aplikacji), pasuje do
płaskiego stylu GNOME/libadwaita. Kolor: gradient `corvid-indigo` → `corvid-violet-light`.

## Ikony
Baza: **Papirus** (dobre pokrycie aplikacji, aktywnie rozwijany) z nałożonym
folder-color w `corvid-violet` przez `papirus-folders`. Własny pełny icon theme
— rozważane na później (duży nakład pracy), nie blokuje pierwszego wydania.

## TBD
- Finalny SVG loga (do zrobienia w narzędziu graficznym, poza zakresem tego repo)
- Dokładna paleta jasnego motywu (kontrastowe warianty akcentu)
- Motyw terminala jako gotowy plik (Kitty/GNOME Console/foot config)
