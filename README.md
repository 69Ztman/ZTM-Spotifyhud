# Spotify HUD – Minecraft 1.21.11 (Fabric)

Dies ist ein **Quellcode-Projekt / Entwicklungsstand 0.2**, keine fertig kompilierte JAR.

## Enthalten
- HUD standardmäßig oben rechts, kompakt
- Taste **Ö** öffnet die Einstellungen (physische Semikolon-Taste auf deutschem Tastaturlayout); Taste **H** blendet das HUD ein/aus
- Position oben rechts / unten rechts / oben links / unten links
- Transparenzregler
- Farbverlauf ein/aus und Animationsoption
- Schalter für Albumcover und Lyrics (UI-Vorbereitung)
- Spotify-Abfrage und API-Aufrufe für Pause, Weiter, Zurück und Lautstärke als Java-Methoden

## Noch nicht fertig integriert
Die aktuelle Oberfläche zeigt Titel und Künstler. Das Albumcover wird aus Spotifys API zwar geliefert, aber noch nicht als Minecraft-Textur gerendert. Lyrics sind noch nicht eingebunden. Die sichtbaren Schalter sind derzeit Vorbereitungen und schalten diese Inhalte noch nicht live zu. Es gibt auch noch keine OAuth-Anmeldeseite/Refresh-Token-Verwaltung; die API benötigt daher einen gültigen Access Token als `SPOTIFY_ACCESS_TOKEN`. Spotify-Wiedergabesteuerung und Lautstärke benötigen in der Regel Spotify Premium und ein aktives Wiedergabegerät.

## Voraussetzungen
- Minecraft Java 1.21.11
- Fabric Loader 0.18.1+
- Fabric API 0.141.4+1.21.11
- Java 21

## Bauen
Mit installiertem Gradle im Projektordner:
```bash
gradle wrapper --gradle-version 8.14.3
./gradlew build
```
Windows:
```bat
gradle wrapper --gradle-version 8.14.3
gradlew.bat build
```
Die JAR sollte danach in `build/libs/` liegen. Der Build wurde in dieser Umgebung nicht ausgeführt oder verifiziert.

## Spotify Token
Ein Token muss den Scope `user-read-currently-playing`, `user-modify-playback-state` und `user-read-playback-state` besitzen. Token als Umgebungsvariable setzen:
PowerShell: `$env:SPOTIFY_ACCESS_TOKEN="DEIN_TOKEN"`
Linux/macOS: `export SPOTIFY_ACCESS_TOKEN="DEIN_TOKEN"`
Token niemals teilen oder in öffentliche Dateien hochladen.

## Technische Referenzen
Fabric 1.21.11 verwendet Loom 1.14 und Loader 0.18.1. Siehe https://www.fabricmc.net/2025/12/05/12111.html

### HUD-Design wechseln
Im Einstellungsmenü gibt es jetzt den Ein-Klick-Schalter **HUD-Design**. Er wechselt zwischen **Oben rechts** und **Oben mittig** und speichert die Auswahl in `config/spotifyhud.json`.
