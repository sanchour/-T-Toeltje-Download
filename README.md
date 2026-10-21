# T Toeltje downloaden

De downloadpagina van de desktop-app T Toeltje (Alexander Impact).
De pagina staat op GitHub Pages: https://sanchour.github.io/T-Toeltje-download/

De app zelf wordt gebouwd in de repo `-T-Toeltje` (branch `desktop-app`, `npm run maak-windows`).
De .exe-bestanden staan **niet** in deze repo, maar bij **Releases**. De knoppen op de pagina wijzen altijd naar de nieuwste release:

- `https://github.com/sanchour/T-Toeltje-download/releases/latest/download/T-Toeltje-Setup.exe`
- `https://github.com/sanchour/T-Toeltje-download/releases/latest/download/T-Toeltje-portable.exe`
- later voor de Mac: `.../releases/latest/download/T-Toeltje.dmg`

## Eenmalig instellen

1. Maak op GitHub een **openbare** repo `T-Toeltje-download` (leeg, zonder README).
2. Zet deze map erin (`git push`).
3. Settings → Pages → Branch `main`, map `/ (root)` → Save.

## Een nieuwe versie uitbrengen

1. Verhoog in `-T-Toeltje/package.json` het veld `version` (bijvoorbeeld 1.0.1) en bouw opnieuw: `npm run maak-windows`.
2. Ga hier naar **Releases → Draft a new release**. Tag: `v1.0.1`. Titel: `T Toeltje 1.0.1`.
3. Sleep `release/T-Toeltje-Setup.exe` en `release/T-Toeltje-portable.exe` erin. Houd precies deze bestandsnamen aan, anders werken de knoppen niet.
4. Publish release. De knoppen wijzen meteen naar de nieuwe versie.
5. Pas in `index.html` het versienummer aan (zoek op `1.0.0`, staat er twee keer in).

## Mac-versie toevoegen (later)

Bouw op een Mac met `npm run maak-mac`; dat maakt `release/T-Toeltje.dmg`. Zet die bij dezelfde release.
Vervang daarna in `index.html` het label "Mac · binnenkort" door een knop naar `releases/latest/download/T-Toeltje.dmg`.

## Inhoud

- `index.html`: de hele pagina (stijl staat erin).
- `fonts/`: DM Serif Text en Titillium Web, zelf gehost.
- `img/`: logo en schermafbeeldingen van de app.
