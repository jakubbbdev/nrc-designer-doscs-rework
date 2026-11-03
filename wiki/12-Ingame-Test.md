# 12. Ingame-Test

← [Test-Setup](11-Test-Setup) · **12 / 15** · [Cosmetic-Typen →](13-Cosmetic-Typen)

---

Je nach Permissions kannst du nun folgenden Command ausführen, um auf den neu angelegten Designer-Ordner zuzugreifen:

```
/nrc designer source toggle
```

![Command: designer source toggle](images/image-41.png)

## Im Shop sehen

Wenn du alles richtig gemacht hast, sollten jetzt deine Cosmetics und Emotes **im Shop** angezeigt werden:

![Cosmetic im Shop](images/image-42.png)

## Local Test — Cosmetics ausrüsten

Du kannst Cosmetics auch **local** testen — also ausrüsten ohne sie wirklich zu besitzen:

```
/nrc cosmetics designer toggle <name>
```

![Command: cosmetics designer toggle](images/image-43.png)

## Local Test — Emotes abspielen

Emotes natürlich genauso:

```
/nrc emote play <name>
```

![Command: emote play](images/image-44.png)

> 💡 **Neue Dateien hinzugefügt?** Solange der Designer-Modus an ist, werden neue Files erst nach einem Rescan gefunden:
>
> ```
> /nrc designer source rescan
> ```
>
> Geänderte, schon vorhandene Files werden direkt neu gelesen.

## Alle Designer-Commands

| Command | Was passiert |
|---------|--------------|
| `/nrc designer source toggle` | Designer-Ordner an/aus |
| `/nrc designer source on` / `off` | Designer-Ordner gezielt an/aus |
| `/nrc designer source status` | Zeigt, ob der Designer-Ordner gerade aktiv ist |
| `/nrc designer source rescan` | Liest den Ordner neu ein (neue Files) |
| `/nrc cosmetics designer toggle <name>` | Cosmetic lokal an-/ausziehen |
| `/nrc cosmetics designer togglebundle <name>` | Ganzes Bundle lokal an-/ausziehen |
| `/nrc cosmetics designer offset X\|Y\|Z <wert> <name>` | Cosmetic live verschieben, um die richtige Position zu finden |
| `/nrc cosmetics designer mirror <modus> <name>` | Render-Modus testen (`ORIGINAL`, `MIRROR`, `BOTH`) |
| `/nrc cosmetics designer customSkin [clear] <input> <name>` | Eigene Textur auf das Cosmetic legen |
| `/nrc cosmetics designer toggleModel` | Zwischen breitem und schmalem Skin-Modell wechseln |
| `/nrc emote play <name>` | Emote abspielen |
| `/nrc emote stop` | Emote stoppen |
| `/nrc emote list` | Alle Emotes auflisten |
| `/nrc emote sound list` / `play` | Sounds auflisten / abspielen |

> 👀 Alles, was du mit `/nrc cosmetics designer` anziehst, siehst **nur du**. Andere Spieler bekommen davon nichts mit.

> ⚠️ Der Designer-Modus ersetzt **alle** NRC-Assets durch den Designer-Ordner. Lass deshalb den kompletten `nrc-cosmetics`-Ordner aus dem ZIP drin — sonst fehlen Texturen in der UI.

---

## Ohne Permission testen: der Test-Ordner

Für schnelle Tests gibt es zusätzlich den Ordner **`NoRiskClient/test`**. Dafür brauchst du **keine** Designer-Permission, und Änderungen werden **automatisch** neu geladen — kein Rescan nötig.

| Command | Was passiert |
|---------|--------------|
| `/nrc test folder` | Öffnet den Test-Ordner |
| `/nrc test reload` | Lädt den Ordner von Hand neu |
| `/nrc test emote` | Listet alle Emotes im Test-Ordner |
| `/nrc test emote <name>` | Spielt ein Emote aus dem Test-Ordner ab |

So sortierst du ein:

- **Einzelne `.animation.json`** direkt in den Ordner → wird als **Emote** erkannt.
- **Ein Ordner** pro Emote oder Cosmetic, Files heißen wie der Ordner (`wings/wings.geo.json` …). Mit einer `.norisk.json`, die einen `type` hat, wird es ein **Cosmetic**, sonst ein **Emote**.
- Erlaubt sind nur Kleinbuchstaben, Ziffern, `.`, `_` und `-` im Namen.

---

## Geht nicht?

| Problem | Lösung |
|---------|--------|
| Neue Datei taucht nicht auf | `/nrc designer source rescan` |
| `toggle <name>` sagt *Unknown cosmetic* | Einmal den Wardrobe öffnen, dann den Command nochmal ausführen |
| Nach einem Rescan ist dein Outfit unsichtbar | Das Test-Cosmetic einmal aus- und wieder anziehen |
| Cosmetic taucht gar nicht auf | Im Log (`logs/latest.log`) nach deinem Dateinamen suchen — fehlende/doppelte `id` oder kaputtes JSON stehen nur dort |
| Auf Windows geht's, auf Mac/Linux fehlt die Textur | Dateiname hat Großbuchstaben — alles klein schreiben |
| Particle erscheint am falschen Spieler | Particle immer an einen **Locator** hängen |
| Particle/Sound fehlt bei Loop-Emotes am Anfang | Keyframe nicht genau auf `0` oder auf das Ende legen |
| Von mehreren Particles auf einem Keyframe kommt nur eins | Keyframes leicht versetzen |
| UI sieht im Designer-Modus kaputt aus | Den kompletten `nrc-cosmetics`-Ordner im Designer-Ordner lassen |

---

## Fertig! 🎉

**Viel Spaß beim Testen :3**

Weiter geht's mit den Nachschlage-Kapiteln: [Cosmetic-Typen](13-Cosmetic-Typen) · [Referenz](14-Referenz) · [Blockbench-Plugin](15-Blockbench-Plugin)

— Tinus aka. p2pe ❤️

---

← [Test-Setup](11-Test-Setup) · **12 / 15** · [Cosmetic-Typen →](13-Cosmetic-Typen)
