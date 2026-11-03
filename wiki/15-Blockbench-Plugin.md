# 15. Blockbench-Plugin

← [Referenz](14-Referenz) · **15 / 15** · [🏠 Home](Home)

---

Statt Template + GeckoLib-Export kannst du auch unser eigenes Blockbench-Plugin **NoRisk Client Cosmetics** benutzen. Es bringt das Spieler-Rig, die Emote-Einstellungen und einen Export mit, der alle Files auf einmal richtig benennt.

## Installation

1. Plugin-Datei herunterladen: **[nrc_cosmetics.js](https://github.com/NoRiskClient/nrc-blockbench-plugins/blob/master/plugins/nrc_cosmetics/nrc_cosmetics.js)**
2. In Blockbench: **File → Plugins → Load Plugin from File** → `nrc_cosmetics.js` auswählen
3. Blockbench neu starten

> 💡 Das GeckoLib-Plugin aus [1. Grundlagen](01-Grundlagen) kannst du trotzdem installiert lassen.

---

## Neues Emote oder Cosmetic

**File → New → NoRisk Client Emote** bzw. **NoRisk Client Cosmetic**

- Das Projekt startet direkt mit dem Spieler-Rig (`bipedRig`, `bipedHead`, `bipedBody`, Arme und Beine) und allen `armor`-Knochen inklusive `armorRightArmSlim` / `armorLeftArmSlim` für schmale Skins.
- Bei **Emotes** kannst du aus Vorlagen wählen oder leer starten.
- Bei **Cosmetics** wird direkt eine Animation `nrc.idle` als Loop angelegt.
- Die Cubes des Rigs sind nur zur Orientierung — exportiert werden **nur deine eigenen** Cubes.

### Vorschau mit deinem Skin

**Set Preview Skin** → Minecraft-Namen eingeben → das Rig trägt deinen Skin.

---

## Emote-Einstellungen

**Animation → Edit NoRisk Client Emote Settings**

Hier stellst du alles aus der [Referenz](14-Referenz#extra-einstellungen-in-der-animationjson-emotes) per Klick ein, ohne die JSON anzufassen:

- **Disable on move** / **Disable on hit** (Hinweis: „hit“ heißt *zuschlagen*, nicht Schaden nehmen)
- **First person** / **Stay in first person**
- **Immersive camera**
- **Vanilla-Knochen sperren** — pro Knochen einzeln

Den Loop-Modus nimmt das Plugin direkt aus Blockbench (Play Once / Loop / Hold On Last Frame).

## Easing

Bei Emotes kannst du jedem Keyframe ein **Easing** geben (Sine, Quad, Back, Bounce, Elastic …) — siehe [6. Keyframes](06-Keyframes#easing-nur-mit-dem-nrc-plugin).

## Particles & Sounds

Im Panel **Emote Effects** fügst du Particles und Sounds hinzu — auch **Vanilla-Sounds** aus Minecraft. Beim Export werden die Files automatisch mitkopiert und richtig benannt.

## Molang Guide

**Molang Guide** zeigt die verfügbaren Molang-Funktionen mit **Live-Beispielen** am Rig. Beim Tippen von Molang in Keyframes gibt's außerdem **Autovervollständigung** (z.B. `query.head_x_rot`).

---

## Export

**File → Export → Export NoRisk Client Emote** bzw. **Cosmetic**

Du wählst, was rausgeschrieben wird — alles landet in einem Ordner und heißt automatisch gleich:

| File | Wann |
|------|------|
| `<name>.animation.json` | Immer, wenn es Animationen gibt |
| `<name>.geo.json` | Wenn du eigene Cubes hast (Gegenstand, Cosmetic) |
| `<name>.png` | Textur |
| `<name>.png.mcmeta` | Bei animierten Texturen |
| Particles / Sounds | Alle Effekte aus dem Effects-Panel |
| `<name>.norisk.json` | Metadaten: Name, Creator, Preis, Rarity, Typ |

Den fertigen Ordner sortierst du dann wie in [11. Test-Setup](11-Test-Setup) ein.

## Import

**File → Import → Import NoRisk Client Emote / Cosmetic** öffnet einen fertigen Ordner wieder in Blockbench — praktisch, um alte Emotes oder Cosmetics weiterzubearbeiten. Mit **Import … Animation** holst du nur die Animation in dein aktuelles Projekt.

---

## Bekannte Einschränkungen

| Einschränkung | Was du tun musst |
|---------------|------------------|
| Die exportierte `.norisk.json` für **Emotes** enthält kein `emoteFile` und keine `category` | Beide Felder von Hand ergänzen (siehe [11. Test-Setup](11-Test-Setup)), sonst erscheint das Emote nicht richtig im Shop |
| Typ **`BUDDY`** fehlt in der Auswahl | Als `ACCESSORIES` exportieren und `type` von Hand auf `"BUDDY"` ändern |
| `UNOBTAINABLE` fehlt bei der Rarity | Von Hand eintragen |
| Keine Eingabe für `features`, `animationSettings`, `multiTexture`, `variant`, `color` … | Von Hand eintragen → [Referenz](14-Referenz) |
| Bei Cosmetics wird nur `nrc.idle` angelegt | Weitere Animationen (`nrc.walking` …) selbst anlegen → [5. Animation](05-Animation) |
| Interaktive Emotes werden nicht unterstützt | Von Hand nach [Referenz](14-Referenz#interaktive-emotes) |
| Zwei Animationen mit gleichem Namen | Nur die letzte wird exportiert — das Plugin warnt dich |

---

← [Referenz](14-Referenz) · **15 / 15** · [🏠 Home](Home)
