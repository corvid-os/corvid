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

✅ Zawsze wariant `-dkms` (nigdy goły `nvidia`/`nvidia-open`) — Corvid stawia
domyślnie na `linux-zen`, a prekompilowane pakiety `nvidia`/`nvidia-open` bez
DKMS pasują tylko do kernela `linux` (stock).

| Producent GPU / generacja | Pakiety | Uwaga |
|---|---|---|
| NVIDIA — Turing i nowsze (RTX 20xx+, część GTX 16xx) | `nvidia-open-dkms`, `nvidia-utils`, `lib32-nvidia-utils` | ✅ domyślny wybór dla tej generacji — open kernel module, rekomendowany też przez samą NVIDIA |
| NVIDIA — starsze (GTX 10xx i starsze: Pascal/Maxwell/Kepler) | `nvidia-dkms` (proprietary), `nvidia-utils`, `lib32-nvidia-utils` | open kernel module ich nie wspiera — jedyna opcja |
| AMD | `mesa`, `lib32-mesa`, `vulkan-radeon`, `lib32-vulkan-radeon` | w pełni open-source, brak dylematu |
| Intel | `mesa`, `lib32-mesa`, `vulkan-intel`, `lib32-vulkan-intel` | jw. |

Próg generacji NVIDIA wykrywany po PCI ID karty (lista Turing+ znana z
dokumentacji NVIDIA/Arch Wiki, wbudowana jako statyczna tabela w
`backend/hardware.py`, nie wykrywana "na żywo" — stabilniejsze niż heurystyki).

Detekcja przez `lspci` w backendzie instalatora (`backend/hardware.py` —
patrz `hardware-support.md`), instalowane w kroku 13, **niezależnie od
wybranego profilu** (Gaming/Dev/Minimalny — sterownik GPU to kwestia sprzętu,
nie profilu).

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
- Czy `lutris` wchodzi do domyślnego `corvid-gaming`, czy zostaje opcjonalny
- Domyślny skrót do MangoHud toggle (żeby nie kolidował z Hyprland/GNOME keybindami)
