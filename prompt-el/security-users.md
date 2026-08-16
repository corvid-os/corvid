# Bezpieczeństwo i konta użytkowników

Rozwinięcie kroków 5 i 9 z `installer-steps.md`.

## Konto użytkownika
- Tworzone w kroku 9 instalatora: login, pełna nazwa, hasło (z miernikiem siły hasła
  w UI), opcjonalny avatar
- Domyślnie użytkownik trafia do grupy `wheel` (uprawnienia administracyjne przez sudo)
  — checkbox "Ten użytkownik może administrować systemem", **zaznaczony domyślnie**
  (typowy przypadek: single-user desktop)
- **Konto root bez hasła / zalogowania bezpośredniego** — root istnieje (wymagane
  systemowo), ale logowanie jako root wyłączone; wszystko przez `sudo`

## sudo
- `sudo` (nie `doas`) — wybór z powodu dojrzałości, znajomości przez większość
  użytkowników Linuksa i lepszego wsparcia w dokumentacji/narzędziach
- `%wheel ALL=(ALL:ALL) ALL` odkomentowane w `/etc/sudoers` (przez `visudo`-safe
  edit w backendzie instalatora, nigdy bezpośredni zapis pliku)
- `NOPASSWD` — **wyłączone domyślnie** (bezpieczeństwo > wygoda), użytkownik może
  to zmienić ręcznie po instalacji jeśli chce

## Firewall
- **ufw** + **gufw** (GUI) instalowane domyślnie, `ufw` **włączony** po instalacji
  z domyślną polityką: `deny incoming`, `allow outgoing`
- Wybór `ufw` zamiast gołego `firewalld`/`iptables`: najprostszy UX dla desktopowego
  użytkownika, dobre pokrycie GUI

## Szyfrowanie dysku (krok 5, opcjonalne)
- LUKS2 na partycji root (subwolumeny Btrfs wewnątrz zaszyfrowanego kontenera)
- `/boot` **niezaszyfrowany** (ograniczenie GRUB — pełne szyfrowanie `/boot`
  wymagałoby GRUB z obsługą LUKS2 argon2, dodatkowa złożoność — TBD czy warto
  w kolejnej iteracji)
- Hasło szyfrowania **osobne** od hasła użytkownika (świadomy wybór bezpieczeństwa)

## Aktualizacje bezpieczeństwa
- TBD: czy wprowadzamy jakiś mechanizm automatycznych powiadomień o aktualizacjach
  (np. via `paru -Syu` w tle raz dziennie + powiadomienie systemowe, nie auto-apply)

## TBD
- Secure Boot — czy i jak wspieramy (shim/MOK enrollment dla własnoręcznie
  podpisanego bootloadera) — na start prawdopodobnie **nieobsługiwane**, do
  udokumentowania jako known limitation
- AppArmor/SELinux — czy włączamy cokolwiek domyślnie (raczej nie na start —
  dodatkowa złożoność, priorytet to najpierw działający, wygodny system)
- Polityka haseł (minimalna długość, itp.) w kroku 9 — konkretne progi
