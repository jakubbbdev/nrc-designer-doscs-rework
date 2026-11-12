# 4. Texture

← [Model](03-Model) · **4 / 15** · [Animation →](05-Animation)

---

Nachdem du das Modell fertig hast, geht es zur **Textur**.

## Style-Guide

Die Texturen sollten im **16x** oder Maximal **32x** Spektrum gehalten werden. **Zu detailreiche** Emotes/Cosmetics passen nicht in den Style von NRC und werden voraussichtlich **nicht akzeptiert**.

![Beispiel-Textur in NRC-Style](images/image-10.png)

---

## Transparente Pixel

Transparente und halbtransparente Pixel sind **erlaubt** — sie werden ingame durchsichtig dargestellt und nicht mehr als volle Fläche gefüllt.

---

## Glow (leuchtende Pixel)

Für leuchtende Stellen legst du eine **zweite Textur** neben die normale:

```
meine_wings/
├── meine_wings.png         ← normale Textur
└── meine_wings_glow.png    ← Glow-Textur
```

- Gleiche Größe und gleiches Layout wie die normale `.png`.
- **Alle Pixel, die nicht schwarz sind, leuchten** und werden über die normale Textur gelegt.
- Male also **nur** die Pixel ein, die leuchten sollen — in der Farbe, in der sie leuchten sollen. Alles andere bleibt **schwarz**.

> 💡 Ein dunkelgrauer Pixel leuchtet auch — nur schwach. Was nicht leuchten soll, muss wirklich `#000000` sein.

---

## Color Change (Farbe wechseln)

Damit Spieler die Farbe ihres Cosmetics ändern können, legst du **Graustufen-Texturen** zusätzlich zur normalen Textur in den Ordner. Die Graustufen werden ingame mit der gewählten Farbe eingefärbt.

```
meine_wings/
├── meine_wings.png                 ← normale Textur
├── meine_wings_tint_federn.png     ← Graustufen, Teil „federn“
└── meine_wings_tint_rand.png       ← Graustufen, Teil „rand“
```

- Name: **`<cosmeticname>_tint_<teil>.png`**
- Du kannst **eine Datei pro Teil** machen (jeder Teil bekommt seine eigene Farbe) oder **eine Datei für das ganze Cosmetic**.
- Hell = kräftige Farbe, dunkel = dunkle Farbe. Pixel, die sich nicht einfärben sollen, bleiben in der `_tint`-Datei leer.

---

## Mehrere Texturen (multiTexture)

Soll ein Cosmetic in verschiedenen Texturen wählbar sein:

1. In der `.norisk.json` `"multiTexture": true` setzen
2. Im Cosmetic-Ordner einen Unterordner **`textures/`** anlegen
3. Alle möglichen Texturen dort hineinlegen

```
meine_wings/
├── meine_wings.norisk.json        ← "multiTexture": true
├── meine_wings.geo.json
├── meine_wings.png
└── textures/
    ├── red.png
    ├── blue.png
    └── green.png
```

Alle Texturen müssen zum selben Modell (gleiches UV-Layout) passen.

---

← [Model](03-Model) · **4 / 15** · [Animation →](05-Animation)
