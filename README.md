# Miholja Računari — sajt

Jednostrana prezentacija za sklapanje, prodaju i servis računara. Bez frameworka, bez build koraka, bez zavisnosti koje se instaliraju — čist HTML, CSS i malo JavaScript-a u jednom fajlu.

## Sadržaj foldera

```
index.html        ceo sajt (HTML + CSS + JS u jednom fajlu)
preview.html      pomoćni prikaz: desktop 1440px i mobilni 375px jedan pored drugog
img/
  build-final.png gotov build — koristi se u hero-u i u slajderu
  workbench.jpg   radni sto — koristi se za hotspotove i u slajderu
  logo.jpg        logotip (rezerva, trenutno se ne učitava na stranici)
  favicon.svg     ikonica u tabu
robots.txt        dozvola za indeksiranje + putanja do sitemap-a
sitemap.xml       jedna adresa, za Google Search Console
.nojekyll         govori GitHub Pages-u da ne pokreće Jekyll obradu
```

## Kako da ga postaviš na GitHub Pages

1. Napravi novi repozitorijum, npr. `miholja-racunari`. Neka bude **Public** — GitHub Pages na besplatnom nalogu radi samo sa javnim repozitorijumima.
2. Prevuci **sadržaj ovog foldera** (ne sam folder) u repozitorijum preko `Add file → Upload files`, pa `Commit changes`.
3. Otvori `Settings → Pages`.
4. Pod **Source** izaberi `Deploy from a branch`, pa granu `main` i folder `/ (root)`. Sačuvaj.
5. Sačekaj minut-dva. Sajt će biti na `https://KORISNIK.github.io/miholja-racunari/`.

### Ako želiš svoj domen (npr. `miholjaracunari.rs`)

1. U `Settings → Pages → Custom domain` upiši domen i sačuvaj — GitHub će sam napraviti `CNAME` fajl.
2. Kod registrara domena dodaj `A` zapise ka `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, i `CNAME` za `www` ka `KORISNIK.github.io`.
3. Kad se DNS propagira, uključi **Enforce HTTPS**.

## Obavezno pre nego što pustiš uživo

- [ ] **Cene tri konfiguracije** — trenutno stoje `89.900` / `189.900` / `389.900` RSD kao primer. Traži `rig-price` u `index.html`.
- [ ] **Zameni `KORISNIK`** pravim GitHub korisničkim imenom (ili domenom) na 4 mesta: `canonical`, `og:url` u `index.html`, pa u `robots.txt` i `sitemap.xml`.
- [ ] **Radno vreme** — nedostaje u kontakt listi i footeru.
- [ ] **Tekst recenzija** — imena (Andrej, Dušan, Stefan) stoje, ali su citati napisani kao primer. Prepiši prave sa svog profila.
- [ ] **Više fotografija** — sajt trenutno vrti dve slike. Zadnja strana kućišta sa kablovima, krupni plan paste i još par gotovih rigova bi ga značajno podigli.

## Česte izmene — gde šta stoji

| Šta menjaš | Gde u `index.html` |
|---|---|
| Boje | blok `:root` na vrhu — `--orange`, `--blue`, `--ink` |
| Tekst hotspotova na fotografiji | niz `const DATA = [...]` u `<script>` na dnu |
| Pozicije hotspotova | CSS klase `.hs1`–`.hs4` (dva seta: desktop i ispod 980px) |
| Tekst dijagnostičkog terminala | niz `const LOG = [...]` u `<script>` |
| Broj recenzija (565) | `<div class="num up" id="cUp">` i brojač na dnu skripte |
| Kontakt podaci | sekcija `id="kontakt"` i kolona `Kontakt` u footeru |

## Napomene

- **Fontovi** se povlače sa Google Fonts. Ako želiš da sajt radi i bez interneta, skini `Archivo` i `JetBrains Mono` u `img/` (ili novi folder `fonts/`) i zameni `<link>` sa `@font-face` pravilima.
- **Mapa** je `<iframe>` sa upitom po adresi, bez API ključa. Ne učitava se kad otvoriš fajl lokalno (`file://`) — na hostovanom sajtu radi normalno.
- **Strukturirani podaci** (`application/ld+json`) opisuju lokalni biznis za Google. Namerno **nisu** uključene ocene (`aggregateRating`) — Google kažnjava strukturirane ocene koje ne može da potvrdi na samoj stranici. Ako budeš dodavao, neka odgovaraju stvarnim brojevima.
- **`preview.html`** je alat za tebe, ne za kupce. Slobodno ga obriši pre postavljanja ako ne želiš da je javno dostupan.
