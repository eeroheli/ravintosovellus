# Ravinto — Suomenkielinen ravinto-ohjelmasovellus

## Mikä tämä on
Yksittäinen HTML-tiedosto (`ravinto-ohjelma.html`) joka toimii ravintosovelluksena. Kaikki koodi (HTML + CSS + JS) on samassa tiedostossa. Sovellus on suomenkielinen.

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
- Pääsovellus: välilehdet — Ohjelma, Paino, Asetukset (+ tuleva Päiväkirja)
- Ateriatietokanta: `MEAL_DB`-objekti kategorioittain (Aamiaiset, Lounas, Välipala, Päivällinen, Iltapala)
- Makrolaskenta: `calcMacros()` (Mifflin-St Jeor), `deriveMacros()` (laskee HH automaattisesti kcal/P/R:stä)

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

## Testaus
Avaa `ravinto-ohjelma.html` selaimessa ja tarkista:
1. Onboarding toimii loppuun asti
2. Ateriat näkyvät ja reseptikortit aukeavat
3. Paino-kirjaus tallentuu ja näkyy
4. Konsolissa ei ole virheitä

## Kehityssuunnitelma
Katso `ROADMAP.md` seuraavista vaiheista.
