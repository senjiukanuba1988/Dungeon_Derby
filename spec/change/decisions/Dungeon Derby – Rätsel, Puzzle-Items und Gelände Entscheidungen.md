# Dungeon Derby – Rätsel, Puzzle-Items und Gelände: Entscheidungen

Nov 12, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_03_raetsel.md` sind beantwortet. Das Dokument baut auf den Entscheidungen zu Spielablauf, Dungeon-Generierung und Kampfsystem auf.

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

## 3.1 Puzzle-Items

Es gibt 9 Puzzle-Items. Jedes taugt für Rätsel und zusätzlich für Kampf oder Fortbewegung, ohne übermächtig zu sein.

| Item | Slot | Rätsel | Kampf und Mobilität |
| --- | --- | --- | --- |
| Bogen | Mainhand | Kristallschalter aus der Ferne, alles, was Fernkampf braucht | Fernkampfwaffe |
| Spiegelschild | Offhand | Laser reflektieren: laserblockierte Wege begehen, Laser-Empfänger auslösen | Magische Projektile zurückwerfen |
| Sprungfeder | Puzzle-Slot | Kurze Abgründe überspringen (etwa 2 Kacheln) | Fortbewegung |
| Enterhaken | Puzzle-Slot | Sich über lange Abgründe zu Ankerpunkten ziehen | Kleine Gegner heranziehen |
| Kraft-Armband | Puzzle-Slot | Schwere Steine und Krüge heben und werfen, vor allem um Wege freizuräumen | Gegenstände auf Gegner werfen, besonders im Bosskampf |
| Fackel | Puzzle-Slot | Fackelhalter anzünden, Spinnweben und Ranken verbrennen, Licht für alle im Umkreis | Gegner in Brand setzen |
| Renn-Stiefel | Puzzle-Slot | Gegen Gegenwind anrennen, über zerbröselnden Boden sprinten, rissige Säulen durch Anrennen zerstören **\[Test\]** | Sturmangriff mit Rückstoß **\[Test\]** |
| Frostrute | Puzzle-Slot | Wasser zu begehbarem Eis frieren | Gegner kurz einfrieren |
| Windfächer | Puzzle-Slot | Fackeln ausblasen, Windräder drehen, giftigen Nebel vertreiben | Gegner wegstoßen, auch in Abgründe; wirkt nicht auf Projektile |

**Grundregeln:**

- Bogen und Spiegelschild zählen als Puzzle-Items, obwohl sie in Mainhand und Offhand liegen. Sie sperren Fortschritt wie andere Puzzle-Items, sodass sie garantiert gefunden werden, und Rätsel lassen sich klar klassifizieren („benötigt den Bogen“).
- Der Bogen ist eines der ersten Puzzle-Items. Vorher wird keine andere Fernkampfwaffe gefunden, und unter den Waffen auf Etage 1 ist kein Bogen.
- Jede Etage bringt höchstens ein neues Puzzle-Item, in zufälliger Reihenfolge. Etage 1 bekommt ein einfaches Einsteiger-Item. Bei 9 Items und 10 Etagen hat eine späte Etage kein neues Item.
- Puzzle-Items werden auf die nächsten Etagen mitgenommen. Ab ihrem Fund können Rätsel sie verlangen, auch in Kombination (z. B. einer macht Licht, ein anderer springt mit der Feder über Abgründe).
- Keine verbesserten Versionen; lieber alles unterschiedliche Items.
- Alle Items sind unbegrenzt nutzbar, können aber eine Abklingzeit haben (von etwa 1 Sekunde bis länger).
- Bomben sind Verbrauchsgut, kein Puzzle-Item. Braucht ein Rätsel Bomben, muss der Raum mit den Bomben-Gegnern aus diesem Bereich erreichbar sein, ohne dass man dafür schon Bomben braucht.
- Fällt ein Gegner in einen Abgrund, erscheint sein Loot an der Stelle, wo er zuletzt stand.

**Gestrichen:** Grav-Brücke (zu viele Abgrund-Items), Block-Beschwörung (macht Schieberätsel trivial), Spiegelscherbe (das Spiegelschild war gemeint).

## 3.2 Besitz und Weitergabe

- **Ein Exemplar pro Team.** Weitergabe durch Fallenlassen: Das Item landet vor dem Spieler auf dem Boden, und jeder kann es aufheben. **\[Später\]** Direkte Übergabe.
- **Mehrere Items:** Ein Spieler kann Puzzle-Items im Inventar tragen, muss sie aber ausrüsten, um sie zu benutzen.
- **Wechsel:** Über das Inventar-Menü, sofort ohne Wartezeit. Das Spiel läuft dabei weiter.
- **Tod:** Der Träger behält alle Items beim Respawn.
- **Zwei Items gleichzeitig:** Kein Spieler muss zwei Puzzle-Items gleichzeitig benutzen, ein Team aber schon. Solche Rätsel haben eine Mindestspielerzahl von 2.
- **Erkennbarkeit:** Jedes Item hat Hindernisse mit unverwechselbarem Aussehen, etwa Hakenpfosten, Fackelhalter, Laser-Emitter, schwere Steine oder Windräder. Ein extra Symbol ist nicht nötig.

## 3.3 Rätseltypen

**Schalter:**

| Schalter | Auslösen | Verhalten |
| --- | --- | --- |
| Hebel | Benutzen | Bleibt in seiner Stellung, lässt sich zurückstellen |
| Druckplatte | Gewicht | Aktiv, solange etwas daraufsteht |
| Einrastende Druckplatte | Gewicht | Bleibt gedrückt; muss klar anders aussehen als die normale |
| Kristall | Mit Waffe oder Pfeil anschlagen | Schaltet um |
| Fackelhalter | Fackel | Bleibt an, je nach Variante dauerhaft oder für eine Weile |
| Windrad | Windfächer | Aktiv, solange es sich dreht |
| Laser-Empfänger | Laserstrahl | Aktiv, solange ein Laser ihn trifft |

- **Gewicht auf Druckplatten:** Spieler, Gegner (auch eingefrorene), Blöcke, schwere Steine und Krüge. Keine Bomben, keine herumliegenden Items.
- **Zeitschalter:** Sparsam, z. B. eine Tür, die 10 Sekunden offen bleibt, mit hörbarem Ticken und sichtbarem Zeitgeber.
- **Raumübergreifende Schalter:** Ohne Zeitbegrenzung. Schalter und Ziel haben dieselbe Farbe; es wird nicht angezeigt, wo sich etwas verändert hat.
- **Erfolgsgeräusch:** Ein einheitliches Geräusch, wann immer ein Schalter oder Rätsel erfolgreich ausgelöst wird, bei allen Rätseln gleich.
- **Team-Rätsel:** Mindestspielerzahl pro Vorlage, höchstens 4. Rätsel über zwei Räume haben eine Mindestspielerzahl von 2.

**Elemente:**

- Aus Chip's Challenge: Eis (Eis-Thema), Wasser, Förderbänder, Teleporter, Schalterwände (farbige Wände, die beim Umschalten verschwinden oder erscheinen), Block ins Wasser schieben ergibt Boden. Keine Feuerböden.
- Laser und Spiegel: Neben dem Spiegelschild gibt es feste, drehbare Spiegel, die man durch Anschlagen um 90° dreht.
- Dunkle Räume: Die Fackel leuchtet für alle in ihrem Umkreis; angezündete Fackelhalter erhellen den Raum.
- Kampf: „Alle Gegner im Raum besiegen“ lässt eine Truhe erscheinen oder öffnet eine Tür. Gegner auf Druckplatten zu locken ist möglich, wird aber nie benötigt.
- Zeitdruck: Nur über die kurzen Zeitschalter, keine größeren Countdown-Rätsel.

## 3.4 Zustand und Zurücksetzen

- **Zustand:** Rätsel innerhalb eines Raums setzen sich zurück, wenn niemand mehr drin ist. Raumübergreifende Rätsel bleiben. Gelöst bleibt gelöst (aus 2.5).
- **Zurücksetzen:** Nur durch Verlassen des Raums. Es gibt keinen Reset-Hebel und keinen Menüpunkt. Die Spieler werden einmal darauf hingewiesen, falls sie es nicht selbst merken.
- **Blöcke:**
  - In Wasser oder Lava geschoben, wird der Block zu Boden.
  - In einen Abgrund geschoben, verschwindet er und erscheint nach kurzer Zeit an seiner Ausgangsposition.

## 3.5 Gelände und Fallen

| Boden | Wirkung |
| --- | --- |
| Eis | Schlittern (Eis-Thema) |
| Schlamm | Verlangsamt |
| Flaches Wasser | Vor allem Verzierung; löscht Feuer, wenn ein Spieler brennt |
| Tiefes Wasser | Wie ein Abgrund, nur anders gezeichnet; versenkte Blöcke werden zu Boden |
| Lava | Gleicher Anfangsschaden wie beim Abgrund, zurück zum Raumeingang, danach brennt der Spieler kurz (zusätzlicher Schaden); versenkte Blöcke werden zu Boden (Vulkan-Thema) |
| Abgrund | Wie im Kampfsystem: Schaden, zurück zum Raumeingang |
| Förderband | Bewegt alles darauf in eine Richtung |
| Einseitige Kante | Nur in eine Richtung passierbar |
| Stacheln | Siehe unten |
| Teleporter | Verbindet zwei Punkte |
| Zerbröselnder Boden | Bricht nach Betreten ein (Renn-Stiefel) |

**Stacheln** sind kleine Löcher im Boden. Sie schießen entweder eine Sekunde nach dem Betreten heraus oder erscheinen in Bereichen zeitgesteuert und verschwinden wieder. Wer getroffen wird, nimmt Schaden; sonst haben sie keinen Effekt.

**Fallen:** Pfeilfallen, rotierende Klingen, ausfahrende Stacheln, Steinschlag und Flammenwerfer. Fallgruben ergeben sich aus zerbröselndem Boden. Der Schaden richtet sich nach einem normalen Gegnertreffer der jeweiligen Etage. **\[Test\]**

**Gegner:**

- Bodenarten und Fallen wirken auf Gegner genauso wie auf Spieler. Fliegende Gegner ignorieren Bodenarten.
- Gegner, die sich zufällig oder auf Spieler zu bewegen, laufen nie selbst in Abgründe, tiefes Wasser oder Lava. Sie landen nur darin, wenn man sie hineinstößt.
- Gegner in Fallen zu locken ist als Taktik erwünscht, wird aber nie benötigt.

## 3.6 Schwierigkeit und Hilfen

- **Schwierigkeit:** Überwiegend kurze Aha-Momente unter einer Minute. Räume mit hohem Content-Rating dürfen auf späteren Etagen 2 bis 3 Minuten dauern.
- **Geschicklichkeitsrätsel:** Daneben gibt es Fleißaufgaben ohne Aha-Moment, z. B. viele Blöcke nacheinander ins Wasser schieben, um eine Brücke zu bauen. Das Team kann sie gemeinsam optimieren, oder einer erledigt sie, während die anderen weiter erkunden.
- **Kein Hilfesystem.** Rätsel müssen gut lesbar gebaut sein; unklare Räume fliegen im Playtest raus.
- **Einführung eines Puzzle-Items:**
  - Beim Aufheben ein kurzer Tooltip mit dem Item und den passenden Hindernissen; derselbe Tooltip ist im Inventar abrufbar.
  - Der erste Einsatz ist ein einfacher Fall. Vorlagen bekommen ein Merkmal „Einführung“, und der Generator wählt für die erste Verwendung eines neuen Items eine solche Vorlage.
- **Steigerung:** Vor allem zahlreicher und kombinierter, weil mehr Items verfügbar sind. Einzelne Rätsel werden über die Mindestetage der Vorlagen nur moderat schwerer.
- **Rätselräume einmalig:** Jede Rätselvorlage kommt höchstens einmal pro Dungeon vor; gespiegelte Varianten zählen als derselbe Raum. Kampf- und Füllräume dürfen mehrfach vorkommen. **\[Test\]** Reicht der Vorrat an passenden Rätselvorlagen nicht, weicht der Generator auf Kampfräume aus.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Effekte der Renn-Stiefel bestätigen (Gegenwind, zerbröselnder Boden, Säulen, Sturmangriff)
- [ ] Abklingzeiten der einzelnen Puzzle-Items (Playtest)
- [ ] Schaden von Fallen und Brand nach Lava (Playtest, hängt an der HP-Skala im Kampfsystem)
- [ ] Größe des Vorrats an Rätselvorlagen, damit Rätselräume einmalig bleiben können

**Auswirkungen auf andere Dokumente:**

- **Dungeon-Generierung 2.5:** Kein Reset-Hebel in Schieberätseln (dort bereits angepasst).
- **Dungeon-Generierung 2.2:** Vorlagen bekommen die Merkmale „Rätselraum“ (einmalig pro Dungeon) und „Einführung“ (erster Einsatz eines Puzzle-Items).
- **Dungeon-Generierung 2.3:** Die Item-Reihenfolge enthält Bogen und Spiegelschild; der Bogen gehört zu den ersten Items.
- **Kampfsystem:** Spiegelschild und Bogen sperren Fortschritt wie Puzzle-Items. Auf Etage 1 liegt keine Fernkampfwaffe. Der Brand-Effekt nach Lava nutzt den Feuerschaden des Kampfsystems; flaches Wasser löscht ihn.
