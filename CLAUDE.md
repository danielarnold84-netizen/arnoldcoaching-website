# arnoldcoaching.de — Regeln für den Seitenkopf

Statische Seite auf GitHub Pages, Repo `danielarnold84-netizen/arnoldcoaching-website`. Kein CMS, kein Build-Step. Was hier committet und gepusht wird, ist wenige Minuten später live.

## ⛔ Gesperrte Wörter in Maschinenfeldern

In `<title>`, `<meta name="description">`, allen `og:`-Feldern und im JSON-LD dürfen diese Wörter **nicht** vorkommen:

```
Sprachschule · Sprachtraining · Sprachcoaching · language school
```

**Warum.** Google hat die Domain als Sprachschule klassifiziert. Die Seite rankt auf Position 5,9 für „sprachschule zwickau" und hat null Impressionen für Kommunikationscoaching, Kommunikationstraining, Führungskräfte und Geschäftsführer. Die Maschinenfelder sind die Ursache. Am 12.07.2026 wurden sie deshalb auf „Kommunikationscoaching" umgestellt (Commit `2b24433`).

**Was schon einmal schiefging.** Am 15.09.2026 hat Commit `2d0eb34` den Seitenkopf aus einer Vorlage neu erzeugt und drei dieser Felder auf das alte Vokabular zurückgeschrieben. Es blieb zwei Monate unbemerkt und wurde zusätzlich auf die fünf neuen Unterseiten vererbt. Genau das soll diese Datei verhindern.

## Trennung nach Ebene

Die Sperre gilt **nur** für Maschinenfelder. Die sichtbare Copy ist davon nicht betroffen.

| Ebene | Begriff |
|---|---|
| Sichtbar: Eyebrow, Headline, Fließtext | „Sprach- und Kommunikationstraining" bleibt richtig |
| Maschine: title, description, og, JSON-LD | „Kommunikationscoaching" |

Der Satz „Die Sprache verbessert sich, weil die Situation real ist" bleibt bewusst stehen. Es heißt „Sprachschule raus", nicht „Sprache raus".

Quelle: `arbeit/marketing/governance/core-positioning.md`, Abschnitt „Regel" und die Präzisierung vom 12.07.2026. Beschlusslage im Detail: `arbeit/marketing/positionierung-drift-notiz-2026-07-12.md` §6.

## Prüfung vor jedem Push

```bash
grep -rniE "sprachschule|sprachtraining|sprachcoaching|language school" \
  --include="*.html" . | grep -v progress | grep -v angebote
```

Kein Treffer heißt sauber. Ein Treffer heißt: nicht pushen, erst korrigieren.

`progress/` und `angebote/` sind kundenprivate Seiten, per robots.txt ausgeschlossen und von der Regel ausgenommen.

## Weitere stehende Regeln

- **Alt-Texte ohne Keywords.** Das Porträt heißt „Porträt von Daniel Arnold". Direktive vom 12.07.2026, gilt weiter.
- **„Beratung", „beratend", „Unternehmensberatung"** dürfen nirgends im Außentext stehen, solange die B38-Erklärung läuft. Stattdessen Coaching, Training, Moderation. Quelle: `arbeit/finanzen/foerdermittel.md`, Wortregel vom 14.09.2026.
- **Keine Förderseite zu BAFA.** Die Rolle als registrierter Berater ist seit 14.09.2026 geparkt, bis die Empfänger-Projekte abgerechnet sind.
- **`sitemap.xml` mitpflegen.** Wer eine Seite ändert, setzt ihr `lastmod`.
- **Hero und Überschriften nicht umformulieren.** Die sind am 12.07.2026 entschieden, live und korrekt.
