# Ravinto — Claude Code aloitusopas

## 1. Projektikansion valmistelu

Lataa tämä kansio koneellesi ja avaa se terminaalissa:

```
ravinto-projekti/
├── CLAUDE.md              ← Claude Code lukee tämän automaattisesti
├── ROADMAP.md             ← Kehityssuunnitelma ja tehtävälista
└── ravinto-ohjelma.html   ← Sovellus (kaikki koodi tässä)
```

## 2. Claude Code — ensimmäinen käynnistys

Avaa Claude Code -sovellus ja navigoi projektikansioon:

```bash
cd ravinto-projekti
claude
```

Ensimmäisellä kerralla Claude Code pyytää sinua kirjautumaan sisään.
Sen jälkeen se lukee automaattisesti `CLAUDE.md`-tiedoston ja tuntee projektisi.

## 3. Kokeile näitä ensimmäiseksi

### Tutki projektia
```
Lue ravinto-ohjelma.html ja kerro mitä parannettavaa näet koodissa.
```

### Tee pieni muutos
```
Lisää Iltapala-kategoriaan uusi ateria: Proteiini-smoothie (kcal 320, P 35g, HH 28g, R 8g).
Testaa että se näkyy oikein.
```

### Isompi tehtävä
```
Katso ROADMAP.md ja toteuta Vaihe 1: Päiväkirja-välilehti.
Lisää uusi tab "Päiväkirja" ja mahdollisuus merkitä syödyt ateriat.
```

## 4. Hyödyllisiä komentoja Claude Codessa

| Komento | Mitä tekee |
|---------|-----------|
| `Esc` | Pysäyttää Clauden kesken toiminnan |
| `Esc` + `Esc` | Avaa rewind-valikon (palaa aiempaan tilaan) |
| `/compact` | Tiivistää keskusteluhistorian (säästää kontekstia) |
| `/clear` | Tyhjentää keskustelun kokonaan |
| `/model` | Vaihda mallia (Opus 4.6 / Sonnet 4.6) |
| `/config` | Muokkaa asetuksia |

## 5. Vinkkejä tehokkaaseen käyttöön

**Ole tarkka pyyntöjen kanssa.** Sen sijaan että sanot "paranna sovellusta",
sano esim. "Lisää päiväkirja-välilehti jossa voi merkitä syödyt ateriat
ja nähdä päivän kcal-toteuman vs. tavoite."

**Korjaa heti.** Jos Claude menee väärään suuntaan, paina `Esc` ja anna
uusi ohje. Älä anna sen tehdä turhaa työtä.

**Testaa vaiheittain.** Pyydä Claudea tekemään yksi ominaisuus kerrallaan
ja tarkista selaimessa ennen seuraavaa.

**Käytä ROADMAPia.** Sano esim. "Katso ROADMAP.md ja aloita Vaihe 1"
niin Claude tietää mitä tehdä.

## 6. Esimerkkipyyntöjä joita voit kokeilla

```
Toteuta ROADMAP.md:n Vaihe 1 — päiväkirja-välilehti.
Kun käyttäjä klikkaa ateriaa, se merkitään syödyksi ja makrostrippi päivittyy.
```

```
Ateriatietokannasta puuttuu välipaloja. Lisää 3 uutta terveellistä
välipalavaihtoehtoa jotka sopivat 250-350 kcal haarukkaan.
```

```
Paino-välilehden SVG-graafi ei näytä hyvältä kun on vain 2 datapistettä.
Korjaa niin että graafi skaalautuu kauniisti myös pienellä datalla.
```

```
Lisää sovellukseen yksinkertainen PWA-manifest ja service worker
niin että sen voi asentaa puhelimen kotinäytölle.
```
