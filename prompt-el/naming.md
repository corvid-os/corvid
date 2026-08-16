# Nazwa

## ✅ Decyzja: **Corvid OS**

Corvid = rodzina krukowatych (kruk, wrona) — bystre, ciemne, techniczne, świetny
potencjał na maskotkę/logo (kruk). Krótkie, niekolidujące z żadnym istniejącym
dystro.

Konsekwencje nazwy do przeniesienia dalej:
- Kolorystyka: **fiolet/indygo** jako akcent — pasuje bezpośrednio do motywu:
  pióra kruka są czarne, ale mają charakterystyczny fioletowo-niebieski połysk
  (iridescencja) → czarno-fioletowa paleta ma naturalne uzasadnienie w nazwie
- Prefiks pakietów własnego repo: `corvid-*` (np. `corvid-installer`, `corvid-themes`)
- Nazwa instalatora: **Corvid Installer** (roboczo)
- Skrót/binarka: `corvid`
- GitHub org: `corvid-os` (org jeszcze niezałożona — patrz `design.md` → Infrastruktura/GitHub)

## Odrzucone nazwy — powód: kolizja z istniejącym dystro/nazwą

| Nazwa | Powód odrzucenia |
|---|---|
| **Nyxarch** | zbyt blisko istniejącej, aktywnej dystrybucji **Nyarch Linux** (Arch-based, motyw anime) — realne ryzyko mylenia projektów |
| **Solstice** *(Linux)* | nazwa dystrybucji czysta, ale login/organizacja `solstice` na GitHubie zajęta przez niepowiązaną osobę; warianty (`solsticeos`, `solsticelinux`, `getsolstice`, `solsticelabs`) też zajęte — zbyt dużo tarcia, zrezygnowano z całej nazwy |
| **Umbra** *(OS)* | istnieje "Umbra Linux" (inna baza — Linux From Scratch, nie Arch) — ta sama nazwa różnej dystrybucji = zamieszanie |

## Odrzucone propozycje — brak kolizji, po prostu nie wybrane (archiwum, do ew. powrotu)

| Nazwa | Vibe / uzasadnienie |
|---|---|
| Aurelia *(OS)* | ciepłe, "złote" skojarzenie → dobre pod jasny/elegancki motyw, uniwersalne (nie tylko gaming) |
| Emberlin | "ember" (żar) → dynamiczny, gamingowy akcent, ale wystarczająco miękkie na desktop |
| Wyvern OS | mocno gamingowo/fantasy, dobry pod agresywniejszy branding i maskotkę |
| Lumen *(OS)* | "światło" → czyste, minimalistyczne, pasuje bardziej do dev/desktop niż gaming, ale uniwersalne |
| Voidrift | ciemne, techniczne, mocno "power-user" — pasuje pod Hyprland/tiling crowd |
| Aetherix | lekko sci-fi, neutralne, dobrze skaluje się na logo/ikonografię |
| Nocturne *(OS)* | nastrojowe, eleganckie, naturalnie ciemny/premium motyw — org `nocturne-os` była wolna |
| Ferrox *(OS)* | "ferrum" (żelazo) + "-ox" — surowe, techniczne, skrót `fx` — org `ferrox-os` była wolna |

## Lekcja na przyszłość
Zanim finalizujemy jakąkolwiek kolejną nazwę własną (submoduły, narzędzia, itd.),
sprawdzamy dwa razy: (1) czy nie koliduje z istniejącą dystrybucją/projektem
(web search), (2) czy nazwa/wariant jest wolna jako login/org na GitHubie
(`gh api users/<nazwa>` → 404 = wolne).
