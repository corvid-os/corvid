# Środowisko graficzne — GNOME

Szczegóły implementacyjne dla ścieżki GNOME z `design.md` → Środowisko graficzne.
GNOME jest też środowiskiem Live ISO / instalatora (patrz `apps.md`).

## Rozszerzenia (domyślnie włączone)

| Rozszerzenie | Rola |
|---|---|
| Dash to Dock | dock w stylu bardziej klasycznym (łatwiejsze wejście dla nie-GNOME-purystów) |
| AppIndicator and KStatusNotifierItem | wsparcie ikon tray dla apek spoza GNOME (np. Steam) |
| Blur my Shell | subtelne rozmycie tła paneli — pasuje do ciemnego, "premium" brandingu |
| Just Perfection *(lub Forge)* | drobne dopracowanie zachowania Shell (do ustalenia dokładne opcje) |

Zasada: rozszerzeń jak najmniej, tylko te które realnie poprawiają UX — GNOME
domyślnie ma być stabilny i szybki, nie oblepiony customizacją.

## Motyw
- Akcent systemowy: `corvid-violet` (patrz `branding-palette.md`) przez natywny
  mechanizm `accent-color` libadwaita (GNOME 46+)
- Ciemny motyw wymuszony domyślnie po instalacji (użytkownik może przełączyć w Ustawieniach)
- GTK3 apps: motyw zgodny przez `libadwaita-theme`/`adw-gtk3` dla spójności

## dconf defaults (nadpisywane przy pierwszym logowaniu)
- Dock: auto-hide wyłączony domyślnie (widoczny stale, mniej "znikającego UI" dla nowych użytkowników)
- Night Light: włączony automatycznie wg lokalizacji
- Touchpad: naturalne przewijanie włączone, tap-to-click włączony

## Domyślne aplikacje GNOME (część `corvid-gnome` — patrz `package-management.md`)
- `nautilus` (Pliki), `gnome-console` (Terminal), `gnome-text-editor`,
  `gnome-calculator`, `gnome-weather`, `gnome-calendar`, `loupe` (podgląd zdjęć),
  `gnome-software` (opcjonalnie — czy w ogóle, skoro mamy paru? patrz TBD)

## TBD
- Czy `gnome-software` w ogóle instalujemy (ryzyko: dwa równoległe menedżery pakietów
  w głowie usera — pacman/paru vs GUI store) — rozważyć `gnome-software` tylko dla Flatpaków
- Dokładna lista rozszerzeń — do przetestowania pod kątem wydajności/stabilności między wersjami GNOME
- Flatpak: czy włączamy Flathub domyślnie (dla apek spoza repo Arch/AUR)
