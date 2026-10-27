# T Toeltje downloaden

De downloadpagina van de desktop-app T Toeltje (Alexander Impact).
De pagina staat op GitHub Pages: https://sanchour.github.io/-T-Toeltje-Download/

Twee repo's:

- `-T-Toeltje`: de tool zelf en de webversie (https://sanchour.github.io/-T-Toeltje/). Daar bouw je ook de .exe (`npm run maak-windows`, uitkomst in `release/`).
- `-T-Toeltje-Download` (deze): alleen deze pagina.

De .exe-bestanden staan **niet op GitHub**, maar op OneDrive of Google Drive. De pagina linkt ernaar.

## Eenmalig instellen

1. Zet `T-Toeltje-Setup.exe` en `T-Toeltje-portable.exe` (uit `-T-Toeltje/release/`) op OneDrive of Google Drive.
2. Deel elk bestand: **Iedereen met de link** mag bekijken. Kopieer de link.
3. Zet de twee links in `index.html`, helemaal onderaan bij `DOWNLOADS` (tussen de aanhalingstekens):
   ```js
   var DOWNLOADS = {
     setup: "https://drive.google.com/file/d/.../view?usp=sharing",
     portable: "https://drive.google.com/file/d/.../view?usp=sharing"
   };
   ```
   Een link naar één bestand op Google Drive wordt vanzelf een directe download. Een OneDrive-link opent de OneDrive-pagina met een knop Downloaden.
   Nu staan er twee OneDrive-links naar losse bestanden. Een link naar een **map** mag ook: de knop opent de map en zegt welk bestand je moet kiezen (`FILES`).
   Zolang een link leeg is, toont de knop "Binnenkort".
4. Maak op GitHub een **openbare** repo `-T-Toeltje-Download` (leeg), en push deze map.
5. Settings → Pages → Branch `main`, map `/ (root)` → Save.

## Een nieuwe versie uitbrengen

1. Verhoog in `-T-Toeltje/package.json` het veld `version` (bijvoorbeeld 1.0.1) en bouw opnieuw: `npm run maak-windows`.
2. Vervang de bestanden op dezelfde plek, zodat de link hetzelfde blijft:
   - Google Drive: rechtermuisknop op het bestand → Bestandsgegevens → **Versies beheren** → Nieuwe versie uploaden.
   - OneDrive: upload het nieuwe bestand met precies dezelfde naam in dezelfde map en kies **Vervangen**.
3. Pas in `index.html` het versienummer aan (zoek op `1.0.0`, staat er twee keer in).

## Mac-versie

De Mac-app (`T-Toeltje.dmg`, voor Apple-chip en Intel) bouwt GitHub op een Mac: repo `-T-Toeltje` → **Actions** → **Mac-app bouwen**.
Download onder **Artifacts** het bestand `T-Toeltje-mac`, pak het uit en zet `T-Toeltje.dmg` op OneDrive naast de Windows-bestanden.
Zet de deellink bij `DOWNLOADS` als `mac: "…"`. De Mac-knop en de Mac-stappen verschijnen dan vanzelf.

## Inhoud

- `index.html`: de hele pagina (stijl en downloadlinks staan erin).
- `fonts/`: DM Serif Text en Titillium Web, zelf gehost.
- `img/`: logo, pictogram en vier schermafbeeldingen van de app (WebP). Nieuwe maken: open de app, maak een schermafbeelding van 1440×900 en zet hem om naar WebP.

## Vormgeving
De pagina volgt de huisstijl 2027 (ALEX ANDER): Rubik One en Atkinson Hyperlegible (in `fonts/`), logo's in `img/logo-2027-*.png`.
De achtergrond wisselt tijdens het scrollen: elk blok met `data-bg="#…"` begint een nieuwe kleur, en het script onderaan laat de kleur bij de rand van dat blok kort overlopen. Nu vier kleuren: paars (intro en cijfers), geel (Wat is het), cyaan (voorbeelden), blauw (installeren tot en met de footer). Meer of minder kleuren = `data-bg` toevoegen of weghalen.
Overdracht en plan voor het hele product: `docs/OVERDRACHT.md` en `docs/PLAN-HUISSTIJL-2027.md` in de repo `-T-Toeltje`.
