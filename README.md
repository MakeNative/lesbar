# lesbar

Ein Skill für Claude Code, der ein langes Markdown-Arbeitsdokument als HTML-Seite
zum **Durchsehen** aufbereitet.

## Wofür

Ein Arbeitsdokument wird zweimal gelesen: einmal gründlich beim Schreiben,
danach nur noch im Scan-Modus — vor einem Termin, zwischen zwei Calls, auf dem
Handy. Für den zweiten Fall taugt die Quelldatei selten: Sie erzählt
chronologisch, die Entscheidungen stehen am Ende, der Status steckt im Fließtext.

`lesbar` baut die Fassung für den zweiten Fall. Aus demselben Inhalt, ohne
Zusammenfassung und ohne eigene Meinung.

## Was er macht

Er trennt vier Schichten und dreht die Reihenfolge um:

| Schicht | Was hineingehört | Wohin |
|---|---|---|
| **Entscheidungen** | alles, wo jemand wählen muss, bevor es weitergeht — samt dem, was blockiert ist, solange die Entscheidung fehlt | ganz oben |
| **Status** | erledigt, läuft, wartet, nicht anfassen | direkt darunter |
| **Arbeit** | die konkreten Schritte oder Positionen, möglichst als Tabelle | Mitte |
| **Kontext** | Begründungen, Hintergrund, Regeln | unten |

Dazu ein paar Regeln, die sich in der Praxis bewährt haben: Status wird zur
Form (Chip, Randstreifen, Farbe) und nicht nur zum Wort. Dateilisten und Deltas
bleiben Tabellen statt in Fließtext aufgelöst zu werden. Sätze mit
Zusagecharakter — eine Definition, eine Garantie, eine Regel — bleiben wörtliche
Zitate. Und die erste Bildschirmseite zeigt nie eine Einleitung.

## Antworten zurückgeben

Steht im Dokument eine offene Entscheidung, wird sie nicht nur angezeigt,
sondern ausgefüllt: die Optionen aus der Quelle zum Ankreuzen, ein Freitextfeld
daneben. Unten zählt eine Leiste mit, wie viele Fragen beantwortet sind; ein
Knopf baut daraus einen Antwortblock, zeigt ihn an und legt ihn in die
Zwischenablage. Einfügen in die Agenten-Sitzung, abschicken — die Umsetzung
läuft weiter. Unbeantwortete Fragen stehen als `— offen` darin, damit niemand
rät. Eingaben überstehen ein Neuladen.

Ein echtes „Senden" ist es nicht: eine veröffentlichte Seite läuft unter einer
Content-Security-Policy, die jeden ausgehenden Request blockiert, und es gibt
keinen Weg, von dort in eine laufende Sitzung zu schreiben. Die Zwischenablage
ist der kürzeste Weg, der wirklich funktioniert — und der einzige, der auch in
der lokalen Datei ohne Server läuft.

## Was er nicht macht

Nichts erfinden, nichts abschwächen, nichts weglassen, was eine Entscheidung
oder ein Risiko ist. Fällt beim Aufbereiten auf, dass im Quelldokument etwas
fehlt oder sich widerspricht, sagt der Skill das in der Antwort — statt es still
zu glätten.

## Installation

```bash
/plugin marketplace add MakeNative/lesbar
/plugin install lesbar@lesbar-marketplace
```

Ohne Plugin-Mechanik geht es auch: `skills/lesbar/SKILL.md` nach
`~/.claude/skills/lesbar/SKILL.md` kopieren.

## Benutzung

```
/lesbar docs/MIGRATIONSPLAN.md
```

Oder einfach im Gespräch: „mach den Plan lesbar", „bereite das als HTML auf",
„ich will das schnell verstehen".

Das Ergebnis liegt als `<name>.html` neben der Quelle — selbsttragend, ohne
externe Fonts oder Skripte, mit hellem und dunklem Theme. Auf Wunsch
veröffentlicht Claude die Seite anschließend als Artifact, wenn sie geteilt oder
vom Handy gelesen werden soll.

## Gestaltung

Die Seite ist Werkstatt, nicht Marketing: ein Dokument, auf dem gearbeitet wird.
Ein einziger kräftiger Akzent für „hier musst du ran", alles andere ruhig,
Systemschriften statt Webfont-Links, beide Themes gleichwertig bedient. Der
Skill nennt auch, welche verbreiteten KI-Looks er bewusst meidet — damit die
Ansicht nicht aussieht wie jede andere generierte Seite.

## Lizenz

MIT
