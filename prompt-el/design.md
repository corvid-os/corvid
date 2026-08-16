# Design distro — indeks

Ten plik jest **skrótem/spisem treści** całego designu. Szczegóły każdego
tematu żyją w dedykowanym pliku — to jest rozmyślne: łatwiej edytować,
łatwiej przeglądać, mniejsze ryzyko konfliktów przy wspólnej pracy nad plikami.

## Cel / target
Wszystko naraz, nie wąska nisza: ładny wygląd, gaming, deweloperka, codzienny desktop.

## Baza
Arch Linux (rolling release), budowa ISO przez `archiso`.

## Nazwa i branding
- **Nazwa: Corvid OS** — [`naming.md`](./naming.md) (decyzja + historia odrzuconych nazw i dlaczego)
- Paleta kolorów, typografia, logo, ikony — [`branding-palette.md`](./branding-palette.md)

## Środowisko graficzne
- Live ISO / instalator: **GNOME**; do wyboru przy instalacji: **GNOME** albo **Hyprland**
- Szczegóły GNOME (rozszerzenia, motyw, dconf) — [`desktop-gnome.md`](./desktop-gnome.md)
- Szczegóły Hyprland (stack, keybindy, configi) — [`desktop-hyprland.md`](./desktop-hyprland.md)
- Ekran powitalny przy pierwszym uruchomieniu (GNOME i Hyprland) — [`onboarding.md`](./onboarding.md)

## Instalator — Corvid Installer
- Python, modularny, GUI GTK4 + libadwaita (spójne z GNOME live ISO)
- Powód własnego instalatora zamiast Calamares: dokumentacja Calamares nie
  pasuje do tego jak chcemy to rozwijać
- Pełny flow 14 kroków — [`installer-steps.md`](./installer-steps.md)
- Architektura kodu (struktura katalogów, wzorzec kroku, backend) — [`installer-architecture.md`](./installer-architecture.md)
- Repo: [`corvid-os/installer`](https://github.com/corvid-os/installer)

## Zarządzanie pakietami
- `pacman` (multilib włączone) + `paru` jako AUR helper
- Konfiguracja, mirrorlist, grupy metapaczek — [`package-management.md`](./package-management.md)
- Własne repo pakietów (`corvid-*`, hosting, podpisywanie) — [`custom-repo.md`](./custom-repo.md)
- Repo: [`corvid-os/pkgbuilds`](https://github.com/corvid-os/pkgbuilds)

## System plików / snapshoty
- **Btrfs** + **snapper** + **grub-btrfs** (bootowanie snapshotów z menu GRUB)
- Layout subwolumenów, harmonogram snapshotów, rollback — [`filesystem-btrfs-snapper.md`](./filesystem-btrfs-snapper.md)

## Aplikacje
- Zestaw dla **Live ISO** — [`apps.md`](./apps.md)
- Zestaw **po instalacji** (Core/Gaming/Dev/Oba/Minimalny) — [`post-install-apps.md`](./post-install-apps.md)

## Gaming
Kernel, sterowniki GPU, Steam/Proton/gamemode/mangohud, kontrolery — [`gaming.md`](./gaming.md)

## Deweloperka
Shell (fish+starship), kontenery (Podman), git tooling, edytor, mise — [`dev-environment.md`](./dev-environment.md)

## Bezpieczeństwo i użytkownicy
sudo, firewall (ufw), szyfrowanie dysku (LUKS), konta — [`security-users.md`](./security-users.md)

## Wsparcie sprzętowe
Firmware, GPU, laptopy (TLP), audio (PipeWire), Bluetooth — [`hardware-support.md`](./hardware-support.md)

## Infrastruktura / GitHub
- Organizacja: **[`corvid-os`](https://github.com/corvid-os)** (kontakt: `corvid-os@proton.me`)
- **Multi-repo**, nie jeden monolit:

| Repo | Zawartość |
|---|---|
| [`corvid`](https://github.com/corvid-os/corvid) | meta/dokumentacja, ewolucja promptu (`prompt-el/`), docelowo `prompt.md`/`design.md`/`code.md` |
| [`installer`](https://github.com/corvid-os/installer) | Corvid Installer |
| [`iso`](https://github.com/corvid-os/iso) | profil `archiso` |
| [`branding`](https://github.com/corvid-os/branding) | logo, ikony, motywy, paleta |
| [`pkgbuilds`](https://github.com/corvid-os/pkgbuilds) | własne repo pakietów |

- TBD: CI/CD do automatycznego budowania ISO i publikowania paczek (release pipeline)

## Roadmapa
Kamienie milowe M0 (design, obecny etap) → M6 (alpha release) — [`roadmap.md`](./roadmap.md)

## Referencje
- Notatki z Arch Wiki i innej dokumentacji — [`wiki.md`](./wiki.md)
- Same linki (bez komentarza) — [`links.md`](./links.md)

## Struktura projektu (docelowa kompresja)
Etap roboczy: świadomie dużo plików w tym katalogu — każdy temat osobno, żeby
łatwo się edytowało i rozwijało bez wzajemnego nadpisywania się. Cel końcowy:
skompresować wszystko do 3 plików w osobnym, prywatnym repo:
- `prompt.md` — finalny prompt/spec całego projektu
- `design.md` — ostateczny, scalony design systemu
- `code.md` — kod (instalator, konfiguracja archiso, itd.)

## Otwarte tematy (globalne TBD, nie przypisane do jednego pliku)
- CI/CD dla budowania ISO i publikowania paczek
- Wersjonowanie wydań ISO (rolling vs snapshoty wydań, schemat numeracji)
- Licencja projektu (do wyboru — MIT jako naturalny domyślny wybór dla kodu własnego)
