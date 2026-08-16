# Gaming — szczegóły

Rozwinięcie profilu *Gaming* z `installer-steps.md` (krok 8) i `package-management.md`.

## Kernel
- **`linux-zen`** jako domyślny kernel (niższe opóźnienia, dobre pod gaming,
  wciąż mainstream/stabilny) — instalowany niezależnie od wybranego profilu
  (korzysta z niego też Dev/Minimal, bo to po prostu dobry domyślny kernel desktopowy)
- `linux` (stock) dostępny jako alternatywa w GRUB (zawsze instalowany jako fallback)
- TBD: `linux-cachyos` jako opcjonalny "performance" kernel do rozważenia w przyszłości
  (własne repo CachyOS jako zależność — na razie za duże ryzyko/złożoność)

## Sterowniki GPU (auto-detekcja w instalatorze)

| Producent GPU | Pakiety |
|---|---|
| NVIDIA (Turing i nowsze) | `nvidia-open-dkms` lub `nvidia-dkms` (do ustalenia próg generacji), `nvidia-utils`, `lib32-nvidia-utils` |
| AMD | `mesa`, `lib32-mesa`, `vulkan-radeon`, `lib32-vulkan-radeon` |
| Intel | `mesa`, `lib32-mesa`, `vulkan-intel`, `lib32-vulkan-intel` |

Detekcja przez `lspci` w backendzie instalatora (`backend/disk.py`-analogiczny
moduł `backend/hardware.py` — patrz `hardware-support.md`), instalowane w kroku 13.

## Stack gamingowy (pakiet `corvid-gaming`)
- **Steam** (multilib wymagane — patrz `package-management.md`)
- **gamemode** — automatyczna optymalizacja CPU governor/priorytetów podczas gry
- **mangohud** — nakładka FPS/temperatur/obciążenia, domyślnie skonfigurowana
  (skrót klawiszowy do toggle)
- **Proton-GE** — instalowany/zarządzany przez `protonup-qt` (GUI do zarządzania
  wersjami Proton-GE), nie wbudowany na sztywno w Steam
- Kontrolery: `xpadneo` (DKMS, lepsza obsługa padów Xbox Wireless) + `steam-devices`
  (udev rules dla popularnych kontrolerów)

## Opcjonalnie (TBD czy domyślnie czy do doinstalowania)
- `gamescope` — micro-compositor do gier w trybie pełnoekranowym/handheld-style,
  ciekawe pod Hyprland, mniej istotne pod GNOME
- `lutris` — launcher do gier spoza Steam (Epic, GOG, emulatory)
- `vkBasalt` — post-processing (reshade-like) dla Vulkan/OpenGL

## TBD
- Dokładny próg generacji NVIDIA dla `nvidia-open` vs `nvidia` (proprietary) —
  open kernel modules wspierane od Turing (RTX 20xx) wzwyż, ale dojrzałość różni się per generacja
- Czy `lutris` wchodzi do domyślnego `corvid-gaming`, czy zostaje opcjonalny
- Domyślny skrót do MangoHud toggle (żeby nie kolidował z Hyprland/GNOME keybindami)
