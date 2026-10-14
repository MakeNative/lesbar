---
name: lesbar
description: Macht ein langes Markdown-Dokument (Plan, Analyse, Review, Konzept, Protokoll) als HTML-Seite schnell erfassbar — Entscheidungen zuerst, Status sichtbar, Details gefiltert. Nutze diesen Skill, wenn jemand sagt „mach das lesbar", „bereite das als HTML auf", „ich will das schnell verstehen", „visualisiere den Plan" oder um einen bestehenden Arbeitsplan zum Durchsehen aufzubereiten. Nicht für neue Inhalte — der Skill bereitet auf, was schon geschrieben ist.
---

# lesbar — Dokument zum Durchsehen aufbereiten

Ein Arbeitsdokument wird zweimal gelesen: einmal gründlich beim Schreiben,
danach nur noch im Scan-Modus. Dieser Skill baut die Fassung für den zweiten
Fall.

## Was der Skill NICHT tut

Keine neuen Inhalte erfinden, keine Aussagen abschwächen, nichts weglassen, was
eine Entscheidung oder ein Risiko ist. Die HTML-Fassung ist eine Ansicht des
Dokuments, keine Zusammenfassung mit eigener Meinung. Wenn beim Aufbereiten
auffällt, dass im Quelldokument etwas fehlt oder sich widerspricht: in der
Antwort sagen, nicht still korrigieren.

## Ablauf

1. **Quelle lesen.** Vollständig, nicht nur die Überschriften.
2. **Vier Schichten trennen** (das ist die eigentliche Arbeit):
   - **Entscheidungen** — alles, wo jemand wählen muss, bevor es weitergeht.
     Inklusive der Frage, was blockiert ist, solange die Entscheidung fehlt.
   - **Status** — was ist erledigt, was läuft, was wartet.
   - **Arbeit** — die konkreten Schritte oder Positionen, möglichst als Tabelle.
   - **Kontext** — Begründungen, Hintergrund, Regeln. Gehört nach unten.
3. **Reihenfolge umdrehen, wenn nötig.** Quelldokumente erzählen meist
   chronologisch. Die Ansicht beginnt mit dem, was der Leser *tun* muss:
   Entscheidungen oben, Kontext unten. Nummerierung der Quelle beibehalten,
   damit beide Fassungen vergleichbar bleiben.
4. **HTML schreiben** nach den Bauregeln unten, als Datei neben der Quelle
   (`<name>.html`).
5. **Veröffentlichen anbieten.** Mit dem Artifact-Tool, wenn der Nutzer die
   Seite teilen oder vom Handy lesen will. Vorher `artifact-design` laden.

## Bauregeln

**Oben steht, was zu tun ist.** Die erste Bildschirmseite zeigt offene
Entscheidungen und den Status — nie eine Einleitung. Wer scrollt, will Details;
wer nicht scrollt, hat das Wichtigste gesehen.

**Status gehört in die Form, nicht nur in den Text.** Erledigt, offen,
blockiert, nicht anfassen — jeweils als erkennbares Element (Chip, Randstreifen,
Farbe). Semantische Farben sind vom Akzent getrennt.

**Tabellen bleiben Tabellen.** Datei-Listen, Deltas, Positionen: nicht in
Fließtext auflösen. Jede Tabelle bekommt einen eigenen
`overflow-x: auto`-Container, damit die Seite nie seitlich scrollt. Dateinamen
und Codes in Monospace.

**Kein Dekor, das nichts bedeutet.** Keine Emoji als Abschnittsmarker, keine
Nummerierung, die keine Reihenfolge ist, keine Icons für Stimmung. Wenn ein
Abschnitt eine Nummer trägt, muss die Nummer etwas heißen.

**Zitate bleiben wörtlich.** Sätze, an denen eine Entscheidung hängt (eine
Zusage, eine Definition, eine Regel), werden wörtlich übernommen und als Zitat
ausgewiesen — nicht paraphrasiert.

**Eine Spalte für Text, Breite nur für Tabellen.** Fließtext bei etwa 65–75
Zeichen halten; Tabellen dürfen die volle Breite nutzen.

**Beide Themes.** Palette als Custom Properties auf `:root`, im
`prefers-color-scheme: dark` nur die Tokens neu setzen, zusätzlich
`:root[data-theme="dark"]` und `:root[data-theme="light"]` bedienen.

**Selbsttragend.** Keine externen Fonts, Skripte oder Bilder — die Seite läuft
offline und unter strenger CSP. Systemschriften statt Webfont-Links.

## Gestaltung

Der Grundton ist Werkstatt, nicht Marketing: ein Dokument, auf dem gearbeitet
wird. Serifen für Überschriften, wenn die Quelle aus einem Schreib- oder
Buchprojekt stammt; sonst eine saubere Sans. Ein einziger kräftiger Akzent für
„hier musst du ran", alles andere ruhig. Neutrale Töne leicht in Richtung des
Akzents gebogen, damit sie gewählt wirken und nicht geerbt.

Vermeide die verbreiteten KI-Looks: Creme mit Terrakotta, Lila-Blau-Verlauf,
Neon auf Fast-Schwarz, Inter oder Space Grotesk als Standardschrift, alles
zentriert, überall abgerundete Karten mit Akzentstreifen.

## Abschluss

Nach dem Bauen in der Antwort nennen: wo die Datei liegt, welche Entscheidungen
die Ansicht nach oben gezogen hat, und was beim Aufbereiten an Lücken oder
Widersprüchen im Quelldokument aufgefallen ist.
