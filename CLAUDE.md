# Ravinto — Suomenkielinen ravinto-ohjelmasovellus

## Mikä tämä on
Yksittäinen HTML-tiedosto (`ravinto-ohjelma.html`) joka toimii ravintosovelluksena. Kaikki koodi (HTML + CSS + JS) on samassa tiedostossa (~2983 riviä). Sovellus on suomenkielinen.

## Tech stack
- Puhdas HTML/CSS/JS — ei frameworkia, ei build-prosessia
- Fontti: Inter (Google Fonts CDN)
- Teema: tumma (#111 tausta, #e8b84b keltainen aksentti)
- Tiedostorakenne: kaikki yhdessä `.html`-tiedostossa

## Tallennus — kaksi ympäristöä
Sovellus tunnistaa automaattisesti ympäristön (`_hasClaudeStorage`):
- **Claude.ai**: käyttää `window.storage` API:a (artifact persistent storage)
- **Tavallinen selain / paikallinen kehitys**: käyttää `localStorage`-fallbackia (avaimet prefixillä `ravinto_`)

Kaikki tallennus/lataus kulkee `save(key, val)` ja `load(key)` funktioiden läpi. Nollaus `resetApp()`-funktiossa.

## Arkkitehtuuri
- `state`-objekti hallitsee kaiken tilan (profiili, ateriasuunnitelma, painoloki, valitut ateriat, päiväkirja)
- Onboarding: 4-vaiheinen wizard (`renderOnboarding()`, `onboardingNext()`)
- Pääsovellus: välilehdet — Ohjelma, Päiväkirja, Paino, Asetukset
- Ateriatietokanta: `MEAL_DB`-objekti kategorioittain (Aamiaiset, Lounas, Välipala, Päivällinen, Iltapala)
- Ainesosatietokanta: `AINESOSA_DB` (~160 tuotetta, kategoriat: Liha, Kala, Maito, Lisäravinteet, Viljatuotteet, Kasvikset, Hedelmät, Rasvat, Valmisruuat)
- Makrolaskenta: `calcMacros()` (Mifflin-St Jeor), `deriveMacros()` (laskee HH automaattisesti kcal/P/R:stä)

## Tuotehaku — kolmikerroksinen nopeus
1. **Sessiovälimuisti** (`cmSearchCache: Map`) — nopein, ei API-kutsuja
2. **Paikallinen FI-välimuisti** (`fiProducts`, localStorage 7pv TTL) — ladataan taustalla `showMainApp()`-kutsun yhteydessä, `searchLocalFiProducts(query)`
3. **Open Food Facts API v1** (fallback) — `search.pl?lc=fi&cc=fi`, vain jos lokaali haku ei riitä

Välimuistin avain: `ravinto_fi_products`, TTL 7 päivää, ~300 suomalaista tuotetta (3 sivua × 100).

Normalisoitu tuoteformaatti: `{name, brand, kcal, protein, carbs, fat}` — käytetään sekä lokaali- että API-tuloksissa.

## Päiväkirja-välilehti (v2)
- 4 ateriakategoriaa: Aamiainen ☀️, Lounas 🌤️, Päivällinen 🌅, Välipalat/Muut 🌙
- Tila: `state.diary[dateStr].slots.{aamiainen, lounas, paivallinen, valipala}`
- Backward-compat: `eaten` ja `freeEntries` pidetty mukana
- `DIARY_SLOTS` ja `SLOT_MAP` -vakiot määrittelevät kategoriat
- Lisäysmodi: modal jossa 3 välilehteä — Ateriasuunnitelma / Ainesosahaku / Manuaalinen
- Kalenteri: `openCalModal()` → kuukausinäkymä, värikoodatut makropisteet päiville, viikon keskiarvot

## Koodikonventiot
- Suomenkieliset UI-tekstit, englanninkieliset muuttujat ja funktiot
- CSS-muuttujat teeman väreille (`:root`-blokissa)
- Funktiot camelCase, async/await tallennukselle
- Inline-tyylit vain poikkeustapauksissa — käytä CSS-luokkia

## Tärkeät rajoitteet
- ÄLÄ jaa koodia erillisiin tiedostoihin — pidä kaikki yhdessä HTML-tiedostossa
- ÄLÄ lisää build-työkaluja (webpack, vite jne.)
- Ulkoiset skriptit vain CDN:stä (cdnjs.cloudflare.com)
- AI-ominaisuudet (Anthropic API) toimivat vain Claude.ai:ssa — paikallisesti käytetään offline-fallbackia

## Git-tilanne
- Paikallinen git-repo alustettu: `c:\Users\eeroh\Downloads\ravinto-projekti\ravinto-projekti`
- Ensimmäinen commit tehty: `5077308 Initial commit: ravinto-ohjelma HTML-sovellus`
- GitHub-repo **ei vielä luotu** — odottaa `gh auth login` -kirjautumista
- Kun kirjautunut, aja: `"/c/Program Files/GitHub CLI/gh.exe" repo create ravintosovellus --private --source="c:/Users/eeroh/Downloads/ravinto-projekti/ravinto-projekti" --remote=origin --push`

## Testaus
Avaa `ravinto-ohjelma.html` selaimessa ja tarkista:
1. Onboarding toimii loppuun asti
2. Ateriat näkyvät ja reseptikortit aukeavat
3. Päiväkirja — aterioiden lisäys eri kategorioihin toimii
4. Kalenteri-modal aukeaa ja näyttää päivät
5. Paino-kirjaus tallentuu ja näkyy
6. Konsolissa ei ole virheitä

## Kehityssuunnitelma
Katso `ROADMAP.md` seuraavista vaiheista.
