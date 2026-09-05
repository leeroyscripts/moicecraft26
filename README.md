# MoiceCraft 26.2 – Downloadseite

Eine einzelne Seite: das 3D-Logo dreht sich, darunter ein Minecraft-Hebel, der beim Umlegen den
Download startet. Die Datei selbst liegt in der Dropbox, die Seite leitet aber nicht dorthin
weiter – der Link endet auf `dl=1`, dadurch schickt Dropbox die Datei direkt als Download.

## Dateien
```
index.html   die komplette Seite, alles darin
logo.glb     das 3D-Logo (wird gedreht)
logo.png     flaches Logo als Rückfall, falls WebGL fehlt
icon.png     Favicon
```

## Auf GitHub Pages veröffentlichen
1. Auf github.com ein neues Repository anlegen, zum Beispiel `moicecraft`.
2. Diese vier Dateien hochladen (Add file → Upload files → alles reinziehen → Commit).
3. Im Repository auf **Settings → Pages**.
4. Bei *Source* **Deploy from a branch** wählen, Branch `main`, Ordner `/ (root)`, speichern.
5. Nach ein bis zwei Minuten ist die Seite unter
   `https://<dein-name>.github.io/moicecraft/` erreichbar.

Per Kommandozeile geht es genauso:
```bash
cd "moicecraft-site"
git init && git add . && git commit -m "MoiceCraft 26.2 Downloadseite"
git branch -M main
git remote add origin https://github.com/<dein-name>/moicecraft.git
git push -u origin main
```

## Download-Link ändern
In `index.html` steht die Adresse an einer einzigen Stelle:

```js
const DOWNLOAD_URL = "https://www.dropbox.com/scl/fi/.../MoiceCraft-26.2-Installer.zip?rlkey=...&dl=1";
```

Wichtig ist das `dl=1` am Ende. Mit `dl=0` landen die Leute auf der Dropbox-Vorschauseite,
mit `dl=1` startet der Download sofort.

## Gut zu wissen
- Beim Überfahren des Hebels zeigt der Browser unten trotzdem `dropbox.com` an. Das lässt sich
  nur mit einem eigenen Server verstecken, der die Datei durchreicht.
- Dropbox drosselt öffentliche Links, wenn sehr viel Traffic darüber läuft. Für eine Handvoll
  Leute ist das kein Thema.
- Die Seite lädt three.js und die Pixel-Schrift aus dem Netz. Klappt eines davon nicht, zeigt
  sie automatisch das flache Logo und normale Schrift – der Download funktioniert weiterhin.
- Text ändern: alles steht direkt im `<main>`-Block in `index.html`.
