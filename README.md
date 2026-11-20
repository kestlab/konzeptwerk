# Konzeptwerk

Web-App, mit der du Softwarekonzepte für Vibe-Coding entwickelst: Name, Ziel, Key-Funktionen und Ablaufdiagramm. Konzepte lassen sich speichern, exportieren und importieren, als PDF präsentieren und als fertiger Prompt an Claude übergeben.

Die ganze App steckt in **einer Datei** (`index.html`). Sie kommt ohne Server, Build-Schritt und externe Bibliotheken aus.

## Funktionen

| Bereich | Inhalt |
|---|---|
| Übersicht | Name, Kurzbeschreibung, Version, Status, Autor/in, Projekt, Vertraulichkeit, Steckbrief mit Fortschritt |
| Ziel | Ausgangslage, Ziel, Erfolgskriterien, Abgrenzung |
| Zielgruppe & Rollen | Zielgruppe, Rollen mit Aufgaben und Rechten |
| Key-Funktionen | Funktionen mit MoSCoW-Priorität (Must / Should / Could / Won't), sortierbar |
| Ablauf | Diagramm-Editor (siehe unten), mehrere Diagramme pro Konzept |
| Daten & Technik | Plattform, Tech-Stack, Datenmodell, Schnittstellen |
| Offene Punkte & Risiken | Annahmen, offene Fragen mit Status, Risiken mit Bewertung und Maßnahme |
| Vibe-Coding-Prompt | Erzeugt aus dem Konzept einen fertigen Prompt (Zielplattform und Vorgehen wählbar), dazu Markdown-Export |

### Ablaufdiagramm
Für das Diagramm gibt es zwei Wege, die sich frei kombinieren lassen:

- **Schrittliste:** Du gibst Schritte und Verbindungen per Formular ein. Mit „Schnell hinzufügen“ und Enter entsteht ein Ablauf in Sekunden.
- **Zeichenfläche:** Ein Doppelklick legt einen neuen Schritt an oder ändert einen Text. Schritte lassen sich verschieben. Ziehst du am ⊕ eines Schritts, entsteht eine Verbindung (lässt du auf freier Fläche los, entsteht dabei ein neuer Schritt). Zoomen geht mit dem Mausrad bzw. zwei Fingern, die Ansicht verschiebst du durch Ziehen auf der freien Fläche.
- **Auto-Layout** ordnet alles sauber an, vertikal oder horizontal. Schleifen und Verzweigungen werden dabei automatisch geführt.
- Elementtypen: Start, Schritt, Entscheidung, Ein-/Ausgabe, Datenspeicher, Ende.
- Export als **PNG** (z. B. für PowerPoint), **SVG** oder **Mermaid**-Code.

### Speichern, Export & Import
- Die App speichert alles **automatisch im Browser** (localStorage). Unter „Konzept ▾“ findest du alle Konzepte: öffnen, neu anlegen, duplizieren, löschen.
- **Export** (oder Strg+S) speichert das aktuelle Konzept als `.konzept.json`-Datei.
- **Import** lädt eine solche Datei wieder. Alternativ ziehst du sie einfach ins Browserfenster.
- Der Browser-Speicher gilt nur für das jeweilige Gerät und den jeweiligen Browser. Willst du sichern, das Gerät wechseln oder das Konzept an Kollegen weitergeben, nutze die JSON-Datei (z. B. in OneDrive ablegen).

### PDF
Klick auf **PDF**, Abschnitte auswählen (z. B. für Kunden ohne „Offene Punkte“) und dann im Druckdialog **„Als PDF speichern“** wählen. Das PDF enthält Deckblatt, Inhaltsverzeichnis, Tabellen, Diagramme und Seitenzahlen.
Tipp: Im Druckdialog die Browser-Kopf- und Fußzeilen ausschalten und die Hintergrundgrafiken einschalten.

### Tastenkürzel
| Kürzel | Aktion |
|---|---|
| Strg/⌘ + S | Export als JSON |
| Strg/⌘ + Z / Y | Rückgängig / Wiederholen (außerhalb von Eingabefeldern) |
| Entf | Markierten Schritt bzw. markierte Verbindung löschen |
| F2 | Text des markierten Elements bearbeiten |
| Esc | Auswahl aufheben |

## Einrichtung auf GitHub Pages

1. Lege auf GitHub ein neues Repository an, z. B. `konzeptwerk`.
2. **Add file → Upload files** → `index.html` und `README.md` hochladen → **Commit changes**.
3. **Settings → Pages**: Unter *Build and deployment* bei *Source* „Deploy from a branch“ wählen, dann Branch `main` und Ordner `/ (root)` einstellen → **Save**.
4. Nach ein bis zwei Minuten ist die App unter `https://<dein-github-name>.github.io/konzeptwerk/` erreichbar. Lege dir den Link als Lesezeichen an, auch auf dem iPad.

Für ein **Update** ersetzt du einfach `index.html` im Repository (Upload mit gleichem Namen).

### Hinweise zu Datenschutz & Sichtbarkeit
- Mit einem kostenlosen GitHub-Konto funktioniert GitHub Pages nur bei **öffentlichen** Repositories, und die Seite selbst ist dann öffentlich erreichbar.
- Deine **Konzeptinhalte liegen trotzdem nicht auf GitHub**: Sie bleiben in deinem Browser bzw. in deinen exportierten JSON-Dateien. Öffentlich ist nur die leere App.
- Lege exportierte Konzepte daher **nicht** in ein öffentliches Repository, wenn sie vertraulich sind.
- Die App funktioniert auch ohne GitHub: `index.html` per Doppelklick lokal öffnen.

## Technik
- Vanilla HTML/CSS/JavaScript in einer Datei, keine Abhängigkeiten, keine Cookies, kein Tracking.
- Datenformat: JSON (`schema: "konzeptwerk/1"`). Ältere oder unvollständige Dateien werden beim Import automatisch ergänzt.
- Getestet in Chrome (Desktop und Smartphone-Ansicht). Edge, Safari und Firefox in aktuellen Versionen sollten ebenso funktionieren.
