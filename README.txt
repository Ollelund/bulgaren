BULGAREN PWA v3

Nyheter i v3:
- Statistikvy med startvikt, total ökning och antal godkända pass.
- Milstolpar: första datumet varje maxvikt klarades.
- Utvecklingsgraf över maxvikt per pass.
- Komplett historik med detaljer för alla 8 set.
- Inställbar vilotid, viktsteg, stångvikt och viktskivor.
- Viktskiveberäkning per sida.
- Ett pip vid 30 sekunder kvar och två pip när vilan är slut.
- Valbar vibration.
- Robust sluttidsbaserad vilotimer.
- Ångra senaste set.
- Export/import av backup som JSON.
- Försök att hålla skärmen vaken under aktivt pass via Wake Lock API.
- Offline-stöd och installerbar PWA.

GitHub Pages:
1. Ladda upp index.html, manifest.json, sw.js och båda ikonfilerna till repositoryts rot.
2. Settings > Pages > Deploy from a branch > main > /(root).
3. Vänta på publicering och öppna GitHub Pages-adressen.
4. Installera via Chrome/Android.

Obs:
Wake Lock, vibration och bakgrundsbeteende beror på webbläsare/telefon. PWA:n använder en faktisk sluttid för vilan, så tiden korrigeras direkt när appen åter blir aktiv.
