# Ravinto — Kehityssuunnitelma

## ✅ Valmis
- [x] Onboarding (4 askelta): nimi, perustiedot, tavoite, makrot, ateriat
- [x] Ohjelma-välilehti: ateriat vaihtoehdoilla, reseptikortit, makropillerit
- [x] AI idea -nappi: generoi uusi ateriavaihtoehto Anthropic API:lla
- [x] Oma ateria -lisäys: manuaalinen aterian lisääminen makroineen
- [x] Treenipäivä-toggle: pre-workout korostus, +7% makrot
- [x] Makrostrippi: kcal/P/HH/R progress-palkit, tervehdys
- [x] Paino-välilehti: kirjaus, 14pv SVG-graafi, AI-kommentti
- [x] Asetukset: makrojen muokkaus (HH lasketaan automaattisesti), nollaus
- [x] Pysyvä tallennus window.storage API:lla
- [x] Älykäs makrolaskenta: HH derivoidaan kcal - P×4 - R×9

## 🔜 Vaihe 1 — Päiväkirja
- [ ] Uusi "Päiväkirja"-välilehti tab-bariin
- [ ] Merkitse syödyt ateriat: valitse päivän suunnitelmasta tai kirjaa vapaamuotoisesti
- [ ] Päivittäinen yhteenveto: syödyt kcal / tavoite, P/HH/R toteutuma
- [ ] Makrostripin progress-palkit päivittyvät päiväkirjan mukaan (eaten-objekti)
- [ ] Viikkonäkymä: 7 päivän historia

## 🔜 Vaihe 2 — AI-chattaus & viikkonäkymä
- [ ] AI-ruokaidea: Claude kysyy ensin mieltymykset ennen generointia
- [ ] Viikko-selaus: nuolilla eri päivien ohjelmat
- [ ] Päivän vaihto muuttaa näkyvät ateriat

## 🔜 Vaihe 3 — Viikkoraportti & ostoslista
- [ ] Viikkoraportti: paino + makrototeuma yhdistettynä
- [ ] AI ehdottaa makromuutoksia trendin perusteella
- [ ] Ostoslista: viikon aterioista automaattisesti generoitu

## 🔜 Vaihe 4 — PWA & lisäominaisuudet
- [ ] PWA-manifest + service worker
- [ ] Offline-tuki
- [ ] Ravintola-moodi: AI ehdottaa mitä tilata

## Huomioitavaa
- Jokainen vaihe pitää testata avaamalla tiedosto selaimessa
- Kaikki UI suomeksi
- Pidä yhtenäinen visuaalinen tyyli (tumma teema, keltainen aksentti)
- Älä riko olemassaolevaa toiminnallisuutta kun lisäät uutta
