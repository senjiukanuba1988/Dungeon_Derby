# Dungeon Derby – Fragen: Dungeon-Generierung und Etagenaufbau

## 2.1 Raumformat

1. Wie groß ist ein Raum in Kacheln (NES-Zelda: 16 × 11, Link's Awakening: 10 × 8)?
2. Wie groß ist eine Kachel in Pixeln (z. B. 16 × 16)?
3. Gibt es Räume, die größer als ein Bildschirm sind und scrollen, z. B. für Bosse?
4. Raumwechsel: Scrollen wie bei Zelda, harter Schnitt oder Überblendung?
5. Wo können Ausgänge liegen: nur in der Mitte jeder Wand (wie Zelda) oder an beliebiger Stelle?
6. Gibt es neben Türen weitere Verbindungen zwischen Räumen, z. B. Löcher in den Raum darunter, Treppen innerhalb einer Etage, Teleporter?

## 2.2 Raumvorlagen

1. Werden Räume von Hand gebaut, vollständig prozedural erzeugt, oder handgebaute Vorlagen mit zufälligen Variationen (Gegner, Deko, Fallen)?
2. Wie viele Vorlagen braucht der erste Prototyp, wie viele die fertige Version?
3. Womit werden Vorlagen erstellt: Tiled, eigener Editor, Textdateien?
4. Dürfen Vorlagen gedreht und gespiegelt werden, um mehr Vielfalt zu bekommen?
5. Jeder Raum hat einen festgelegten Eingang. Was passiert, wenn Spieler den Raum später über einen anderen Ausgang betreten (Rückweg)? Muss jede Vorlage aus jeder Richtung sinnvoll sein, oder sind Einbahnstraßen erlaubt (z. B. einseitige Kanten)?
6. Sind Vorlagen an bestimmte Etagen gebunden (Mindest- oder Höchstetage)?

## 2.3 Fortschrittsgraph

1. Werden die Abhängigkeitsketten („Gelber Schlüssel → Feder → Blauer Schlüssel → Ausgang“) von Hand pro Etage vorgegeben oder aus Bausteinen zufällig zusammengesetzt?
2. Wie viele Schritte hat eine Kette, und wie wächst das pro Etage?
3. Wie stark darf sich der Graph verzweigen? Soll er das Team bewusst zum Aufteilen bringen?
4. Wie viele optionale Räume (Schätze, Shops, Sackgassen) gibt es im Verhältnis zu Pflichträumen?
5. Raumanzahl: `ideas.md` nennt 12 auf der ersten und 30 auf der letzten Etage. Gleichmäßig steigend, oder nach Bossen ein Sprung?
6. Schlüssel: Wird ein Schlüssel beim Öffnen verbraucht, oder öffnet ein farbiger Schlüssel alle Türen seiner Farbe?
7. Gibt es mehrere Schlüssel derselben Farbe auf einer Etage?
8. Muss der Spieler mit dem Schlüssel selbst an die Tür, oder gilt ein Schlüssel für das ganze Team (gemeinsamer Schlüsselbund)?
9. Gelten Schlüssel nur auf ihrer Etage, oder kann man sie mitnehmen?

## 2.4 Etagen-Layout

1. Liegen die Räume einer Etage auf einem Raster (wie die Zelda-Karte), sodass Türen geometrisch zusammenpassen müssen?
2. Wo landet man auf der neuen Etage? Gibt es dort eine Treppe zurück nach oben?
3. Gibt es Etagen-Themen (z. B. Etage 1–3 Höhle, 4–5 Kerker, 6–9 Tempel, 10 Burg) mit eigenem Tileset, eigenen Gegnern und eigenen Bodenarten?
4. Welche besonderen Raumtypen gibt es: Shop, Händler, Heilquelle, Bomben-Respawn-Raum, Schatzkammer, Geheimraum, Fallenraum, Arena (Türen schließen, Wellen von Gegnern)?
5. Wie viele Shops gibt es pro Etage, und wo werden sie platziert (nahe am Start, zufällig)?
6. Gibt es Geheimräume (z. B. hinter sprengbaren Wänden)? Gibt es Hinweise auf sie?
7. Wie sieht der Bossraum aus: ein großer Raum, ein Vorraum mit Heilzone, ein Rückweg-Teleporter für tote Spieler?

## 2.5 Lösbarkeit und Softlocks

1. Muss jede Etage auch mit nur 2 Spielern pro Team lösbar sein? Wie viele Spieler darf ein Rätsel höchstens gleichzeitig erfordern?
2. Wie wird verhindert, dass ein Team feststeckt: verbrauchte Schlüssel an falscher Tür, Block in die falsche Ecke geschoben, Item in einen Abgrund gestoßen?
3. Setzen sich verschobene Blöcke und Schalter zurück, wenn alle den Raum verlassen (wie die Gegner)?
4. Soll der Generator die Lösbarkeit nur über den Graphen garantieren, oder zusätzlich mit einem automatischen Löser prüfen?
5. Wie lange darf die Generierung dauern (z. B. höchstens ein paar Sekunden beim Start)?
6. Wird der ganze Dungeon beim Start generiert oder Etage für Etage (beides identisch für beide Teams)?

## 2.6 Fairness

1. Sind alle zufälligen Vorgänge während des Spiels geseedet (Gegner-Verhalten, Fallen, Respawns), sodass beide Teams dieselben Bedingungen haben?
2. Gibt es etwas, das bewusst nicht identisch sein darf?
3. Soll der Seed vor Spielbeginn wählbar sein (z. B. um einen guten Dungeon erneut zu spielen)?
