# Corvid Installer — kroki instalacji

Szczegółowy flow instalatora. Każdy krok = osobny moduł (patrz `installer-architecture.md`).

| # | Krok | Co robi | Walidacja |
|---|---|---|---|
| 1 | **Powitanie / język** | wybór języka instalatora i przyszłego systemu | — |
| 2 | **Układ klawiatury** | wybór layoutu (X11/TTY), test pola tekstowego | musi dać się wpisać test string |
| 3 | **Sieć** | jeśli brak połączenia — lista Wi-Fi (NetworkManager), hasło; test przez ping | dostęp do internetu (wymagany dla pobierania pakietów/mirrorlisty) |
| 4 | **Dysk i partycjonowanie** | tryb *Auto* (cały dysk, Btrfs + subwolumeny wg `filesystem-btrfs-snapper.md`) albo *Manual* (otwiera GParted z repo `iso`, live-app) | min. rozmiar dysku (np. 20 GB), potwierdzenie utraty danych |
| 5 | **Szyfrowanie (opcjonalne)** | toggle LUKS na partycji root, hasło szyfrowania | min. długość hasła |
| 6 | **Strefa czasowa i lokalizacja** | auto-detekcja przez IP (z możliwością zmiany), locale, format daty/waluty | — |
| 7 | **Środowisko graficzne** | wybór **GNOME** albo **Hyprland** (patrz `desktop-gnome.md` / `desktop-hyprland.md`) | — |
| 8 | **Profil** | wybór: *Gaming*, *Dev*, *Oba*, *Minimalny* — determinuje zestaw metapaczek z `package-management.md` | — |
| 9 | **Konto użytkownika** | login, hasło, pełna nazwa, avatar (opcjonalnie), czy konto ma być administratorem (grupa `wheel`) | login wg reguł Unix, siła hasła |
| 10 | **Bootloader** | GRUB (jedyna opcja na start — patrz `filesystem-btrfs-snapper.md` dla integracji z grub-btrfs), wybór dysku EFI | wykryty tryb UEFI/BIOS |
| 11 | **Snapshoty** | podgląd domyślnego harmonogramu snappera (edytowalny) | — |
| 12 | **Podsumowanie** | pełny przegląd wyborów przed rozpoczęciem (ostatni punkt zwrotny) | jawne potwierdzenie użytkownika |
| 13 | **Instalacja** | pasek postępu, logi na żywo (rozwijalny panel), etapy: `pacstrap` → `genfstab` → chroot config → bootloader → snapper init → sprzątanie | obsługa błędu z możliwością pokazania logu i przerwania |
| 14 | **Zakończenie** | podsumowanie, przycisk restart / pozostań w live | — |

## Zasady ogólne
- Każdy krok ma **Wstecz/Dalej**, stan wyborów trzymany centralnie (patrz `installer-architecture.md` → `InstallState`)
- Krok 12 (Podsumowanie) to jedyne miejsce gdzie realnie zaczynają się zmiany na dysku — wcześniej wszystko czysto w pamięci
- Tryb *Auto* w kroku 4 ma być na tyle bezpieczny/domyślny, żeby zwykły użytkownik nigdy nie musiał ręcznie partycjonować

## TBD
- Czy krok "Profil" (8) da się pominąć/zmienić później (post-install profile switcher jako osobne narzędzie?)
- Dokładny UX kroku szyfrowania (czy szyfrujemy też `/boot`? — ograniczenia GRUB+LUKS2)
- Zrzuty ekranu / makiety UI (poza zakresem tego pliku — do repo `installer` jak zacznie powstawać UI)
