# T Toeltje downloaden

De downloadpagina van de desktop-app T Toeltje (Alexander Impact).
De pagina staat op GitHub Pages: https://sanchour.github.io/T-Toeltje-download/

Twee repo's:

- `-T-Toeltje`: de tool zelf en de webversie (https://sanchour.github.io/-T-Toeltje/). Daar bouw je ook de .exe (`npm run maak-windows`, uitkomst in `release/`).
- `T-Toeltje-download` (deze): alleen deze pagina.

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
   Een Google Drive-link wordt vanzelf een directe download. Een OneDrive-link opent de OneDrive-pagina met een knop Downloaden.
   Zolang een link leeg is, toont de knop "Link volgt binnenkort".
4. Maak op GitHub een **openbare** repo `T-Toeltje-download` (leeg), en push deze map.
5. Settings → Pages → Branch `main`, map `/ (root)` → Save.

## Een nieuwe versie uitbrengen

1. Verhoog in `-T-Toeltje/package.json` het veld `version` (bijvoorbeeld 1.0.1) en bouw opnieuw: `npm run maak-windows`.
2. Vervang de bestanden op dezelfde plek, zodat de link hetzelfde blijft:
   - Google Drive: rechtermuisknop op het bestand → Bestandsgegevens → **Versies beheren** → Nieuwe versie uploaden.
   - OneDrive: upload het nieuwe bestand met precies dezelfde naam in dezelfde map en kies **Vervangen**.
3. Pas in `index.html` het versienummer aan (zoek op `1.0.0`, staat er twee keer in).

## Mac-versie toevoegen (later)

Bouw op een Mac met `npm run maak-mac`; dat maakt `release/T-Toeltje.dmg`. Zet die ook op OneDrive of Drive.
Vervang daarna in `index.html` het label "Mac · binnenkort" door een knop met `data-dl="mac"` en zet de link bij `DOWNLOADS` als `mac: "…"`.

## Inhoud

- `index.html`: de hele pagina (stijl en downloadlinks staan erin).
- `fonts/`: DM Serif Text en Titillium Web, zelf gehost.
- `img/`: logo en schermafbeeldingen van de app.
