# 11. Test-Setup

← [Export](10-Export) · **11 / 15** · [Ingame-Test →](12-Ingame-Test)

---

Um alles ingame testen zu können, brauchst du eine **`{name}.norisk.json`** Datei.

Du kannst sie entweder **selbst schreiben** oder **aus einer existierenden Datei kopieren** und alle wichtigen Felder anpassen.

## Vorbereitung

Zuerst kopieren wir die **Game-Assets** — also den gesamten **`nrc-cosmetics` Folder** — in den **`NoRiskClient/designer`** Ordner.

### 📥 Download

Den Ordner musst du dir nicht selbst zusammensuchen — wir stellen ihn als ZIP bereit:

> **[⬇ nrc-cosmetics.zip herunterladen](https://github.com/NoRiskClient/nrc-designer-docs/releases/latest/download/nrc-cosmetics.zip)** *(ca. 670 KB, immer aktueller Stand)*

> ⚙️ Das ZIP wird **automatisch** aus dem [Source-Repo](https://github.com/NoRiskClient/nrc-designer-docs/tree/main/designer) gebaut. Bei jeder Änderung am Designer-Ordner gibt's ein neues Release — du hast also immer die aktuelle Version. Alle Versionen: [Releases](https://github.com/NoRiskClient/nrc-designer-docs/releases).

**Schritte:**

1. ZIP herunterladen
2. Entpacken — du erhältst den Ordner `nrc-cosmetics/`
3. Den **gesamten Ordner** nach `NoRiskClient/designer/` kopieren
4. Deine eigenen Emote- / Cosmetic-Files an die richtigen Stellen einsortieren (siehe unten)

---

## `{name}.norisk.json` — Emotes

Die `.norisk.json` für Emotes ist deutlich übersichtlicher als die für Cosmetics. Du musst vor allem folgendes setzen:

- `id` — eindeutige UUID
- `name` — Anzeigename
- `emoteFile` — Pfad zur Animation
- `creator` — dein Name
- `category`
- `price` / `rarity`

🔧 **UUID-Generator:** https://www.uuidgenerator.net/

```json
{
  "id": "8a9e6923-97b0-4399-a05d-e683358b9bd5",
  "price": 9999,
  "rarity": "LEGENDARY",
  "name": "Dripstone",
  "creator": "Tinus",
  "emoteFile": "dripstone/dripstone.animation.json",
  "dateAdded": "2025-08-01",
  "category": "FUNNY",
  "overflow" : {
     "overflowInShop": true
  },
  "isExclusive": false
}
```

![Emote .norisk.json im Editor](images/image-34.png)

> 📚 `category` bestimmt die Gruppe im Emote-Menü (`special`, `random`, `classic`, `funny`, `dance`). Alle Felder und die Extra-Einstellungen in der `.animation.json` (z.B. `disableOnMove`) findest du in der [14. Referenz](14-Referenz).

---

## `{name}.norisk.json` — Cosmetics

Für Cosmetics wird die Datei länger, da hier zusätzlich **Scale**, **Preview** und Dinge wie das **Shop-Layout** eingestellt werden.

```json
{
    "id": "994873e3-b352-481c-bd68-2c7d76a873de",
    "name": "Pride Flag",
    "creator": "Tinus",
    "price": 500,
    "type": "ACCESSORIES",
    "path": "pride_flag",
    "overflow": {
        "overflowInShop": true
    },
    "defaultSettings": {
        "color": null,
        "scale": 1.1,
        "previewScale": 2.9,
        "offset": {
            "x": 0,
            "y": 0,
            "z": 0.0
        },
        "previewOffset": {
            "x": 0.4,
            "y": -1.0,
            "z": 0.0
        },
        "renderMode": "ORIGINAL"
    },
    "features": [],
    "compatibleCosmetics": [],
    "rarity": "UNCOMMON",
    "isExclusive": false
}
```

![Cosmetic .norisk.json im Editor](images/image-35.png)

> 📚 Welche `type`-Werte es gibt, steht in [13. Cosmetic-Typen](13-Cosmetic-Typen). Alle weiteren Felder (Regler, Farben, Varianten, Quirks …) findest du in der [14. Referenz](14-Referenz).

---

## Files einsortieren

### Cosmetics

Die `.norisk.json` für Cosmetics kommt in **denselben Ordner** wie die restlichen Files.

![Cosmetic Folder Layout](images/image-36.png)

Der gesamte Ordner wandert in den passenden ingame Ordner. Trag als `path` den Ordnernamen ein — entscheidend für den Client ist aber, dass **alle Files gleich heißen wie die `.norisk.json`** (siehe unten):

![Ingame Cosmetic-Ordner 1](images/image-37.png)

![Ingame Cosmetic-Ordner 2](images/image-38.png)

### Emotes

Für Emotes hast du **zwei verschiedene Dateien**:

**1. Die `.norisk.json`** — kommt in den `shop/emotes` Ordner:

![shop/emotes Ordner](images/image-39.png)

**2. Die `.animation.json`** (oder je nach Emote der ganze Ordner mit `.geo` / `.animation` / `.png` / Particle / Sound etc.) — kommt in den `emotes` Ordner:

![emotes Ordner](images/image-40.png)

---

## Namensregeln

Der Client findet deine Files **nur über den Dateinamen**. Halte dich deshalb an diese Regeln:

| Regel | Beispiel |
|-------|----------|
| Model, Textur und Animation heißen **genau wie die `.norisk.json`** | `wings.norisk.json` → `wings.geo.json`, `wings.png`, `wings.animation.json` |
| Nur **Kleinbuchstaben**, Ziffern, `_`, `-` und `.` | ✅ `pride_wings` · ❌ `PrideWings` (geht nur auf Windows!) |
| Emote mit Gegenstand: Ordner und Files heißen gleich, `.geo.json` **und** `.png` sind beide Pflicht | `emotes/dripstone/dripstone.animation.json`, `dripstone.geo.json`, `dripstone.png` |
| Particles: alle `*.particle.json` im Ordner werden geladen | `banhammer/trail.particle.json` |
| Textur-Varianten liegen in `textures/` und brauchen `"multiTexture": true` | `wings/textures/red.png`, `wings/textures/blue.png` |
| Übersetzungen kommen nach `lang/<sprache>.json`, neu laden mit **F3+T** | `lang/de_de.json` |

> ⚠️ **Kein Ordnername darf der Anfang eines anderen sein** — z.B. `hat` und `hat2` nebeneinander. Sonst lädt `hat` auch die Particles von `hat2`. Lieber `hat_red` und `hat_blue`.

> ⚠️ Jede `id` darf **nur einmal** vorkommen. Bei doppelten IDs gewinnt einfach eine der Dateien — ohne Fehlermeldung.

---

← [Export](10-Export) · **11 / 15** · [Ingame-Test →](12-Ingame-Test)
