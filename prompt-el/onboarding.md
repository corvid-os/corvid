# Pierwsze uruchomienie / Onboarding

Co widzi użytkownik przy pierwszym zalogowaniu do świeżo zainstalowanego
Corvid OS (zaraz po `installer-steps.md` krok 14 → reboot).

## Hyprland

✅ Ustalone: przy pierwszym starcie sesji Hyprland pokazuje się krótki ekran/
komunikat powitalny z trzema informacjami:

1. **Skąd jest ten config** — jasna wzmianka, że domyślny setup Hyprlanda
   (Noctalia + Lua) pochodzi z publicznego projektu
   **[Echilonvibin/minimaLinux](https://github.com/Echilonvibin/minimaLinux)**
   (patrz `desktop-hyprland.md`), nie jest autorstwa Corvid
2. **Że wszystko do personalizacji jest w Lua** — bar, kolory, keybindy,
   animacje, reguły okien: wszystko w czytelnych plikach `.lua` w
   `~/.config/hypr/` (patrz `desktop-hyprland.md` → struktura plików)
3. **Jak to spersonalizować** — dwa linki:
   - wideo-poradnik: **https://youtu.be/4_ADDP8x92g?t=760**
     (⚠️ **musi być z tym timestampem** — `t=760` = 12:40, dokładnie tam
     zaczyna się część o personalizacji; sam początek filmu to co innego)
   - repo źródłowe z pełną dokumentacją personalizacji:
     **https://github.com/Echilonvibin/minimaLinux**

## GNOME

Prawdopodobnie czyste/vanilla doświadczenie GNOME — natywny `gnome-tour` /
GNOME Initial Setup, **inna treść niż w Hyprlandzie** (GNOME nie potrzebuje
tłumaczenia "wszystko jest w Lua", bo personalizacja idzie przez Ustawienia
systemowe, nie przez pliki configu). Nie kopiujemy treści z Hyprlanda 1:1.

## TBD
- Techniczna implementacja ekranu powitalnego pod Hyprland — najprostsza
  opcja: skrypt w `startup.lua` odpalający się raz (flag file, np.
  `~/.config/corvid/.welcomed`), pokazujący powiadomienie Noctalii albo
  proste okno z linkami
- Czy dorzucamy cokolwiek Corvid-specific do powitania GNOME, czy zostawiamy
  w 100% vanilla `gnome-tour`
- Czy linki (wideo + repo) mają być dostępne też później niż tylko przy
  pierwszym starcie — np. wpis w cheatsheet `SUPER+H` (patrz
  `desktop-hyprland.md` → Keybindy) jako stały punkt odniesienia
