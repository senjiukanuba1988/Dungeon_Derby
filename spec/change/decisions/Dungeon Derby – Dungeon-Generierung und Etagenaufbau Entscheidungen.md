# Dungeon Derby – Dungeon-Generierung und Etagenaufbau: Entscheidungen

Nov 11, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_02_dungeon_generierung.md` sind beantwortet. Das Dokument baut auf den Entscheidungen zu Spielablauf, Teams und Geist sowie zum Kampfsystem auf.

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

## 2.1 Raumformat

| Größe | Wert |
| --- | --- |
| Kachel | 16 × 16 Pixel |
| Raum (inkl. 1 Kachel Wand ringsum) | 24 × 12 Kacheln = 384 × 192 Pixel |
| Spielfläche | 22 × 10 Kacheln |
| HUD-Leiste | 24 Pixel hoch |
| Interne Auflösung | 384 × 216 Pixel (16:9) |

- **Skalierung:** Nur ganzzahlig, für scharfe Pixel: 1080p ×5, 4K ×10, bei 1440p ×6 mit schmalen Rändern.
- **16 statt 20 Pixel pro Kachel**, damit fertige Pixel-Art-Pakete (fast immer 16 × 16) nutzbar sind. Die Kachelgröße ändert nichts am Platz im Raum.
- **Großräume:** 1 × 2, 2 × 1 oder 2 × 2 Rasterfelder, z. B. für Bosse und Arenen. Dort scrollt die Kamera; die eigene Figur bleibt mittig, außer am Rand des Raums.
- **Raumwechsel:** Scrollen wie bei Zelda, etwa eine halbe Sekunde, nur auf dem Bildschirm des wechselnden Spielers. Die Figur gleitet in dieser Zeit für die anderen sichtbar von der letzten Kachel des einen zur ersten Kachel des anderen Raums und ist unverwundbar.
- **Ausgänge:** Immer in der Wandmitte, 2 Kacheln breit. Großräume haben pro Rasterfeld-Seite einen möglichen Türplatz.
- **Verbindungen:** Türen, Treppe zwischen den Etagen, einseitige Durchgänge (z. B. Kante zum Herunterspringen) und Teleporter (im Grundset). Keine Löcher in den Raum darunter; Abgründe bleiben wie im Kampfsystem geregelt.
- **\[Später\]** Verbindungstunnel mit Seitenansicht wie bei Link's Awakening.

## 2.2 Raumvorlagen

**Handgebaute Vorlagen mit zufälligen Variationen.** Sie werden in [Tiled](https://www.mapeditor.org/) gebaut (Ebenen für Boden, Höhe und Objekte, eigene Eigenschaften, JSON-Export), nicht von Hand als Arrays. **\[Später\]** Eigener Editor im Spiel, falls Tiled an Grenzen stößt.

**Gegner:** Im Editor werden Spawn-Bereiche als Rechtecke markiert, mit Eigenschaften wie maximaler Anzahl und erlaubten Gegnertypen. Welche und wie viele Gegner erscheinen, wählt der Generator je nach Etage; tiefere Etagen haben mehr und andere Gegner. Einschränkungen verhindern unfaire Stellen, z. B. kein Nahkämpfer direkt hinter einem Sprung über einen Abgrund.

**Content-Rating:** Jede Vorlage bekommt ein Rating für ihren Inhalt (anspruchsvolles Rätsel oder viele Gegner = hoch, Korridor = niedrig).

- Statt einer festen Raumanzahl hat jede Etage ein Content-Budget, das mit der Tiefe wächst.
- Ein Mindestanteil der Räume muss über einem bestimmten Rating liegen, damit keine Etage fast nur aus Korridoren besteht.
- **\[Test\]** Budgets, Mindestanteil und ob das Rating mit den zufällig gewählten Gegnern steigt.

**Anzahl:** Für den Prototyp etwa 20 Vorlagen mit echtem Inhalt plus Füllräume. Für die fertige Version eher 100 bis 200.

**Spiegeln:** Horizontal und vertikal erlaubt, Drehen um 90° nicht (Raum ist nicht quadratisch). Richtungsabhängige Kacheln (Nord- und Südwand, Förderbänder, einseitige Kanten) werden gegen ihr Gegenstück getauscht. Jede Vorlage gibt an, ob sie gespiegelt werden darf.

**Verbindungstabelle statt festem Eingang:** Jede Vorlage gibt ihre Türplätze an und unter welcher Bedingung man von welcher Tür zu welcher kommt, z. B. „Nord nach Süd: frei. Süd nach Nord: nur mit Sprungfeder. West nach Ost: nach gelöstem Rätsel.“ Einbahnstraßen sind damit erlaubt.

**Weitere Eigenschaften pro Vorlage:** Mindest- und Höchstetage, Mindestspielerzahl (höchstens 4), Thema und Content-Rating.

## 2.3 Fortschrittsgraph

**Aufbau einer Etage, vom Start aus gedacht:**

1. Zuerst wird die Item-Reihenfolge festgelegt, z. B. gelber Schlüssel, dann Sprungfeder, dann grüner Schlüssel. Sie darf sich verzweigen (ein Bereich braucht z. B. gelben Schlüssel und Sprungfeder).
2. Es werden nur Hindernisse verbaut, deren Item auf der Etage vorkommt. Keine rote Tür, die nie geöffnet werden kann.
3. Daraus ergeben sich Bereiche: alles, was mit den bisherigen Items erreichbar ist. Jedes Item liegt in dem Bereich, den das vorherige freischaltet.
4. Bedingungen hängen an Türen, an Wegen innerhalb von Räumen (Verbindungstabelle aus 2.2) und an Truhen. Entscheidend ist der Fundort, nicht der Raum: Der Raum mit dem grünen Schlüssel kann von Anfang an offen sein, wenn die Truhe darin die Sprungfeder braucht.
5. Das nächste Item liegt eine Mindestanzahl Räume vom nächstgelegenen Eingang des neuen Bereichs entfernt. **\[Test\]**
6. Bereichsgrenzen dürfen überall liegen, also auch eine grüne Tür direkt am Start, die man erst spät öffnen kann.

**Umfang:**

- Kettenlänge: 2 bis 3 Schritte auf Etage 1, wachsend bis etwa 6 bis 8 auf der letzten Etage. **\[Test\]**
- Verzweigung ist erwünscht und darf mehr Äste haben, als das Team Spieler hat. Die Spieler erkunden und arbeiten Äste nach und nach ab.
- Optionale Räume (Schätze, Händler, Sackgassen mit Loot): 30 bis 50 % des Budgets.
- Das Content-Budget wächst zunächst gleichmäßig von Etage zu Etage.

**Schlüssel:**

- Pro Etage gibt es von jeder Farbe genau einen Schlüssel. Er wird nicht verbraucht und öffnet alle Türen seiner Farbe auf dieser Etage.
- Ein Schlüssel wird von einem Spieler getragen, der selbst an die Tür muss.
- Schlüssel gelten nur auf ihrer Etage. Nimmt der Träger die Treppe, bleibt der Schlüssel neben der Treppe liegen und kann bei einer Rückkehr wieder aufgehoben werden.

## 2.4 Etagen-Layout

**Raster:** Räume liegen auf einem Raster wie die Zelda-Karte; Türen in der Wandmitte passen automatisch zusammen.

**Start- und Treppenraum:**

- Man kommt auf jeder Etage in einem Startraum an, der die Treppe zurück nach oben enthält, frei von Gegnern ist und als Respawn-Punkt dient.
- Der Treppenraum mit der Treppe nach unten ist ebenfalls leer bis auf die Treppe, damit zurückgelassene Schlüssel dort Platz haben.

**Themen:** Etagen haben Themen mit eigenem Tileset, eigenem Gegnerpool und eigenen Mechaniken, z. B. Eis mit Schlitter-Rätseln wie bei Chip's Challenge oder Vulkan, wo Wasser einen Lavasee in begehbaren Boden verwandelt.

- Die Reihenfolge ist zufällig; zwei Etagen hintereinander dürfen dasselbe Thema haben.
- Etage 1 hat ein festes, neutrales Thema ohne Spezialmechaniken, weil sie als Tutorial dient.
- Jedes Thema braucht Vorlagen für alle Schwierigkeitsstufen, da es auf jeder Etage landen kann.
- Für den Prototyp reicht ein Thema.

**Raumtypen:** Startraum, Treppenraum, Füllraum (Korridore, Ecken, Kreuzungen mit wenig Inhalt), Kampfraum, Rätselraum, Händler, Heilquelle, Bomben-Respawn-Raum, Schatzkammer, Geheimraum, Fallenraum, Arena (Türen schließen, Gegnerwellen), Bossvorraum und Bossraum.

**Händler** (Shop und Händler sind dasselbe):

- Einer auf Etage 2 oder 3, einer im Bossvorraum auf Etage 5, einer auf Etage 7 oder 8, einer im Bossvorraum auf Etage 10.
- Außerhalb der Bossvorräume zufällig platziert, nicht im Startraum. So sammeln die Spieler erst etwas Gold.

**Geheimräume:** Hinter sprengbaren Wänden, erkennbar an einem dezenten Riss. Sie enthalten nur Optionales.

**Boss:**

- Bossraum mit 2 × 2 Rasterfeldern, davor ein Bossvorraum mit Heilzone und Händler.
- Der Respawn bleibt im Startraum. Im Bossvorraum steht ein Teleporter, der beim ersten Berühren den Gegenpart im Startraum aktiviert.
- Die Tür zum Bossraum schließt sich, sobald der Kampf beginnt; Respawnte warten draußen. Sterben alle im Raum, öffnet sie sich, und der Boss setzt sich zurück (Details im Dokument Gegner und Bosse, 4.6).

## 2.5 Lösbarkeit und Softlocks

**Spielerzahl:** Jede Vorlage hat eine Mindestspielerzahl, höchstens 4. Der Generator verwendet nur Vorlagen, die zur Teamgröße passen. **\[Test\]**

**Softlocks verhindern:**

- Schlüssel werden nicht verbraucht, können also nicht an der falschen Tür verschwendet werden.
- Fallen Schlüssel oder Puzzle-Items in einen Abgrund oder in Lava, erscheinen sie wieder an ihrem ursprünglichen Fundort.
- **Was man ohne Item betreten kann, muss man ohne Item verlassen können.** Items gehören einzelnen Spielern, also prüft der Generator einseitige Wege aus Sicht eines Spielers mit leeren Händen.

**Zurücksetzen:**

- Rätsel innerhalb eines Raums setzen sich zurück, wenn niemand mehr im Raum ist.
- Raumübergreifende Rätsel (Schalter in Raum 1 bewirkt etwas in Raum 2) werden nicht zurückgesetzt; bei ihnen kann man nichts falsch machen.
- Gelöst bleibt gelöst: Eine durch ein Rätsel geöffnete Tür bleibt offen.
- Es gibt keinen Reset-Hebel. Zurückgesetzt wird nur durch Verlassen des Raums (siehe Rätsel-Dokument 3.4).
- Getötete Gegner bleiben tot (wie im Kampfsystem), damit kein Team zusätzlichen Loot farmen kann.

**Garantie:** Über den Fortschrittsgraphen plus eine Prüfung nach dem Generieren, die alle Bereiche mit den jeweils verfügbaren Items durchläuft. Ob ein einzelnes Rätsel lösbar ist, wird beim Bauen der Vorlage sichergestellt, am besten per Testspiel aus dem Editor.

**Zeitpunkt und Dauer:**

- Der ganze Dungeon wird beim Start generiert und geprüft, nicht Etage für Etage.
- Generierung und Prüfung dürfen bis etwa 10 Sekunden dauern.
- Da die Generierung von der Teamgröße abhängt, startet sie erst, wenn alle auf ihren Druckplatten stehen. Danach folgt ein kurzer Ladebildschirm, oder der Countdown läuft, bis der Dungeon fertig ist.

## 2.6 Fairness

- **Zufall während des Spiels** ist vollständig geseedet, und zwar pro Objekt wie bei den Items: Jeder Gegner, jede Falle und jeder Respawn-Punkt hat einen eigenen Zufallsgenerator aus Dungeon-Seed und Objekt-ID. So verhält sich derselbe Gegner in beiden Dungeons gleich, solange die Spieler ihn gleich behandeln.
- **Bewusst nicht identisch** sind nur die Geist-Aktionen (wirken nur beim führenden Team) und rein Optisches wie Partikel oder die Spuk-Effekte des Geists. Diese dürfen ungeseedet sein.
- **Seed wählbar:** Eingabe in der Lobby (aus 1.8). Ein Seed gilt immer zusammen mit der Teamgröße.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Herkunft der Pixelgrafiken: fertige Pakete, selbst zeichnen oder beides (vermutlich im Dokument zur Präsentation)
- [ ] Content-Budgets pro Etage, Mindestanteil an Inhaltsräumen und Rating-Anpassung durch Gegner (Playtest)
- [ ] Mindestabstand des nächsten Items vom Bereichseingang (Playtest)
- [ ] Konkrete Themen und ihre Spezialmechaniken (Rätsel- und Raumdesign)

**Auswirkungen auf andere Dokumente:**

- **Spielablauf 1.1:** Die feste Raumanzahl pro Etage (8 bis 30) wird durch das Content-Budget ersetzt. Die Partiedauer wird darüber eingestellt.
- **Spielablauf 1.4:** Die Platzierung der dort erwähnten Händler ist in 2.4 festgelegt.
- **Kampfsystem, Abschnitt 10:** Rätsel innerhalb eines Raums setzen sich wie Gegner zurück, wenn niemand im Raum ist.
