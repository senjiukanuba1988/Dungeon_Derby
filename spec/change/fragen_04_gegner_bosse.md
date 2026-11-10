# Dungeon Derby – Fragen: Gegner und Bosse

## 4.1 Gegner-Auswahl

1. Wie viele Gegnertypen soll es insgesamt geben, und wie viele neue kommen pro Etage hinzu?
2. Welche Grundtypen sollen vorkommen? Vorschläge: zufällig wandernd, verfolgend, Fernkämpfer, Gegner mit Schild (nur von hinten oder der Seite verwundbar), springend, unsichtbar, beschwörend, explodierend, Fallen-ähnlich (unverwundbar, nur ausweichen).
3. Gegner mit spielerähnlichen Waffen: Droppen sie diese Waffen?
4. Gibt es Elite-Varianten bekannter Gegner (stärker, andere Farbe, Zusatzfähigkeit)?
5. Gibt es Gegner, die nur mit bestimmten Waffen oder Puzzle-Items besiegbar sind (z. B. nur mit Feuer, nur von oben mit Bomben)?

## 4.2 Verhalten (KI)

1. Bemerken Gegner jeden Spieler im Raum sofort, oder nur in Sichtlinie oder Reichweite?
2. Wen greift ein Gegner an, wenn mehrere Spieler im Raum sind: den nächsten, einen zufälligen, den, der ihn zuletzt getroffen hat, den schwächsten?
3. Braucht die Tank-Rolle eine Mechanik, mit der der Schildträger Gegner auf sich zieht (Aggro, Provokation)?
4. Verlassen Gegner ihren Raum oder folgen sie Spielern durch Türen?
5. Weichen Gegner Abgründen und Fallen aus, oder können sie hineinfallen (z. B. durch Knockback)?
6. Ist das Gegnerverhalten deterministisch (geseedet), damit beide Teams dieselben Bedingungen haben?
7. Sollen Gegner zusammenarbeiten (z. B. Heiler, Schildträger, der andere schützt)?

## 4.3 Platzierung und Respawn

1. Wie viele Gegner hat ein normaler Raum? Gibt es bewusst leere Räume?
2. Respawnen Gegner außer den Bomben-Droppern jemals (z. B. wenn man auf eine Etage zurückkehrt)?
3. Sollen Gegner mit der Teamgröße skalieren? (Beide Teams sind gleich groß, aber eine Etage für 2 Spieler fühlt sich anders an als für 6.) Falls ja: mehr Gegner oder mehr HP?
4. Werden Gegner in einem Raum gleichzeitig aktiv, oder kommen sie in Wellen?

## 4.4 Werte und Skalierung

1. **Widerspruch:** `ideas.md` nennt +10 % HP und Schaden pro Etage, an anderer Stelle +50 % von Etage 1 auf 2. Welche Kurve gilt?
2. Skaliert man bestehende Gegner über die Etagen weiter, oder werden schwächere Typen durch neue ersetzt?
3. Wie viel Kontaktschaden machen Gegner im Verhältnis zu ihren Angriffen?
4. Welche Gegner-Projektile gibt es, und wie reagieren sie auf Schild, Spiegelschild und Schwert (siehe Kampfdokument, Abschnitt 13)?
5. Wie viele Treffer soll ein normaler Gegner mit Ausrüstung passend zur Etage ungefähr aushalten?

## 4.5 Belohnungen

1. Was droppen Gegner: Gold, Heilung (wie Herzen bei Zelda), Verbrauchsgegenstände, Ausrüstung?
2. Wem gehört ein Drop: Liegt er auf dem Boden für den, der ihn zuerst aufhebt, oder bekommt ihn der, der den letzten Treffer gelandet hat?
3. Ist Gold eine gemeinsame Teamkasse oder persönlich?
4. Bestätigung: Es gibt keine Erfahrungspunkte und Stufen; Fortschritt kommt nur über Ausrüstung?
5. Verschwinden Drops nach einer Zeit?

## 4.6 Bosse

1. Konkrete Ideen für den Boss auf Etage 5 und auf Etage 10?
2. Haben Bosse mehrere Phasen?
3. Welche Mechaniken erzwingen Teamarbeit? `ideas.md` nennt: Einer muss hinter den Boss, damit die anderen ihn von vorne verwunden können. Weitere Beispiele: Schalter gleichzeitig drücken, den Boss auf eine bestimmte Stelle locken, Adds bekämpfen, während andere den Boss angreifen.
4. Müssen alle Teammitglieder im Bossraum sein, damit der Kampf beginnt?
5. Schließen sich die Türen des Bossraums? Können später ankommende oder respawnte Spieler noch hinein?
6. Wie kommen gestorbene Spieler zurück zum Boss (Respawn am Etagenanfang ist evtl. weit weg)?
7. Wann setzt sich der Boss zurück: wenn alle tot sind, wenn alle den Raum verlassen?
8. Skalieren Bosse mit der Teamgröße?
9. Gibt es Zwischen- oder Minibosse auf anderen Etagen?
10. Welche Belohnung gibt es für den Bosssieg (laut `ideas.md` seltene Items, die nur dort droppen)?

## 4.7 Besondere Gegner

1. Unsichtbare Geister ab Etage 3: Gibt es Hinweise auf ihre Position, solange sie unsichtbar sind (Geräusch, Schatten, Staub)?
2. Gibt es Gegner, die Rätselelemente nutzen (Schalter drücken, Blöcke schieben, Türen schließen)?
3. Gibt es Mimics (Truhen, die angreifen)?
4. Gibt es Gegner, die Ausrüstung oder Gold stehlen?
