# Wsparcie sprzętowe

Rozwinięcie detekcji sprzętu używanej w instalatorze (`installer-architecture.md`
→ `backend/hardware.py`) i profilu Gaming (`gaming.md`).

## Firmware
- `linux-firmware` — zawsze instalowane (wymagane dla większości Wi-Fi/GPU/Bluetooth)
- `sof-firmware` — audio na nowszych laptopach (Sound Open Firmware, Intel)

## GPU
Ta sama tabela detekcji co w `gaming.md` (jedno źródło prawdy — link, nie duplikacja
logiki): sterowniki dobierane automatycznie na podstawie `lspci` w kroku 13.

## Laptopy
- **TLP** — domyślnie instalowany i włączany gdy instalator wykryje baterię
  (`/sys/class/power_supply/BAT*` istnieje) — zarządzanie energią out-of-the-box
- `powertop` dostępny do ręcznego tuningu (nieinstalowany jako serwis, tylko narzędzie)
- TBD: `auto-cpufreq` jako alternatywa/uzupełnienie TLP — możliwy konflikt, do
  przetestowania które daje lepszy balans na typowym sprzęcie

## Audio
- **PipeWire** (+ `pipewire-pulse`, `pipewire-alsa`, `wireplumber`) — nowoczesny
  stack audio, zastępuje PulseAudio/JACK, dobry pod gaming (niskie opóźnienia)
  i produkcję audio jednocześnie

## Bluetooth
- `bluez` + `bluez-utils`, GUI: `blueman` (GNOME) — spójne z resztą desktopowego UX

## Drukowanie
- `cups` — **nieinstalowane domyślnie**, dostępne jako toggle/opcja (nie każdy
  potrzebuje drukowania, a to sporo zależności) — TBD dokładne miejsce tego togglea
  w flow instalatora (może część kroku "Profil"?)

## TBD
- Próg detekcji "to jest laptop" — sama obecność baterii może dawać false positive
  na niektórych desktopach z UPS-em przez USB; do przetestowania dokładniejsza heurystyka
- Wsparcie dla specyficznego sprzętu (Framework, ROG Ally i inne handheldy) —
  osobna dyskusja, nie blokuje pierwszego wydania
