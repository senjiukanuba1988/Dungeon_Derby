# Dungeon Derby – Items, Loot, Inventar und Wirtschaft: Entscheidungen

Nov 12, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_05_items_wirtschaft.md` sind beantwortet. Das Dokument baut auf den Entscheidungen zu Spielablauf, Dungeon-Generierung, Rätseln, Gegnern und Kampfsystem auf.

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

## 5.1 Stufen und Seltenheit

**Stufe** = Etage, auf der ein Item normalerweise gefunden wird. Die Werte folgen derselben Kurve wie die Gegner (+10 % pro Stufe), damit die Ausrüstung mithält. Händler bieten Items ein bis zwei Stufen höher an.

**Seltenheit** hängt an der Zahl der Zusatzeffekte:

| Seltenheit | Farbe | Zusatzeffekte | Anteil bei Drops normaler Gegner |
| --- | --- | --- | --- |
| Gewöhnlich | weiß | 0 | 6/9 |
| Verbessert | grün | 1 | 2/9 |
| Selten | blau | 2 | 1/9 |
| Relikt | gold | besonderer Effekt | einmalig pro Dungeon |

**Zusatzeffekte** (immer positiv, höchstens 2):

- Waffen: Crit-Chance, Giftchance, schnellere Angriffe, mehr Schaden, stärkerer Rückstoß.
- Rüstung und Schild: Feuer- oder Giftresistenz, Schaden absorbieren, HP-Regeneration, schnelleres Laufen, Rückstoßresistenz, längere Unverwundbarkeit nach Treffern.
- Kopfbedeckung: wie Rüstung, aber auch andere Effekte, z. B. Zauberhüte mit Zauberboni.
- Zauber: schnellere Ladung, kürzere Abklingzeit, zusätzliche Ladung.

**Nachteile** gehören zum Grundtyp, nie zu Zufallseffekten: schwere Rüstung (langsamer), Zweihandschwert (langsames Ausholen), Speer (nur nach vorne).

**Relikte:** Einzigartige, auffällige Items, die helfen, ohne die Gruppe zu einer anderen Spielweise zu zwingen, besonders nützlich im Bosskampf. Sie stammen von Bossen, Minibossen oder aus Schatzkammern. Kein Relikt darf ein Puzzle-Item ersetzen. Beispiele:

- Kopfbedeckung, die alle 10 Sekunden den Verbündeten mit den wenigsten HP im selben Raum um 10 HP heilt.
- Zauber, der einem Verbündeten 20 Sekunden lang einen Schutzschild gibt, der bis zu 40 Schaden absorbiert; 20 Sekunden Abklingzeit.
- Rückspul-Relikt im Puzzle-Slot: setzt Position und HP um 5 Sekunden zurück. Intern wird jede Sekunde ein Schnappschuss gespeichert (Position, HP, Schwung auf Eis), höchstens 5; beim Benutzen springt man zum ältesten. Ein Raumwechsel löscht alle Schnappschüsse. Gibt es noch keinen, passiert nichts und keine Abklingzeit startet.

**Erkennung:** Rahmenfarbe im Inventar zeigt die Seltenheit; Stufe und Details stehen im Tooltip, wenn man das Item im Inventar auswählt. Am Boden glitzern seltene Items in ihrer Farbe.

## 5.2 Fundorte und Verteilung

- **Quellen:** Truhen, Gegner und Händler, ohne feste Quote. Truhen enthalten immer ein Item, Gegner nur manchmal; wie sich das verteilt, hängt davon ab, wie viele Truhen und Gegner der Generator anlegt.
- **Menge:** Skaliert mit der Teamgröße. Startwert etwa 1,5 Ausrüstungsteile pro Spieler und Etage, plus Extras auf Boss-Etagen. So wird jeder Slot etwa alle 2 bis 3 Etagen besser. **\[Test\]**
- **Erste Waffe:** Man startet ohne Ausrüstung. Etage 1 enthält mindestens eine Waffe pro Spieler, alle im ersten Bereich (ohne Schlüssel oder Item erreichbar), eine davon in einem Raum direkt neben dem Startraum.
- **Truhen:** Der Inhalt springt beim Öffnen vor der Truhe auf den Boden; wer ihn berührt, hebt ihn auf.
- **Weitergabe:** Abwerfen auf ein freies Feld, bevorzugt vor sich (aus 4.5).
- **Verschwinden:** Items verschwinden nie (aus 4.5).

## 5.3 Inventar

**Größe:** 20 Slots, großzügig für Puzzle-Items, Schlüssel, Verbrauchsgüter und Ersatzausrüstung. Puzzle-Items und Schlüssel liegen ganz normal im Inventar und können abgeworfen werden.

**Stapeln:** Verbrauchsgüter desselben Typs teilen sich einen Slot: Tränke bis 5, Bomben bis 10.

**Nicht im Inventar:** Gold (Teamkasse) und Pfeile (regenerieren).

**Aktiver Slot:**

- Q und E schalten durch, die Zifferntasten wählen direkt. Die Leertaste benutzt das Item im aktiven Slot.
- Alles außer Schlüsseln ist benutzbar. Tränke und Bomben werden direkt eingesetzt.
- Ausrüstung wird beim Benutzen angelegt und tauscht mit dem getragenen Teil: Rüstung, Kopfbedeckung und Puzzle-Item in ihren Slot; Waffen in die Mainhand; Zweihandwaffen ersetzen auch die Offhand; reine Offhand-Items in die Offhand, wobei eine getragene Zweihandwaffe ins Inventar wandert.
- Ist für ein verdrängtes Teil kein Slot frei, landet es auf dem Boden.
- Ausrüstungswechsel ist auch im Kampf sofort möglich.

**Inventar-Menü:**

- Tab öffnet es als Überlagerung, mit eingeblendeter Tastenlegende. Das Spiel läuft weiter; die Figur steht still und bleibt verwundbar.
- WASD bewegt den Cursor. J rüstet in die Mainhand aus (bzw. benutzt), K in die Offhand, L in den Puzzle-Slot. X wirft ab. Tab oder Escape schließt. Optional geht auch die Maus.
- Beim Auswählen erscheint der Tooltip des gewählten Items mit den Werteunterschieden zum getragenen Gegenstück (grün oder rot), aber nicht dessen eigener Tooltip.

## 5.4 und 5.5 Händler

Shop und Händler sind dasselbe (aus 2.4). Händler stehen auf Etage 2 oder 3, im Bossvorraum auf 5, auf Etage 7 oder 8 und im Bossvorraum auf 10.

- **Platzierung:** Beim Generieren festgelegt, für beide Teams auf derselben Etage an derselben Stelle. Er bleibt dauerhaft; man kann zu ihm zurückkehren.
- **Vorrat:** Getrennt und identisch pro Team (aus 1.4).
- **Sortiment:** Verbrauchsgüter (unbegrenzt) und Ausrüstung ein bis zwei Stufen über der Etage (jedes Teil einmal). Dazu pro Händler ein teurer Herzcontainer. Keine Phönixfedern und keine Relikte.
- **Preise:** Grundpreis nach Seltenheit (gewöhnlich ×1, verbessert ×1,5, selten ×2), multipliziert mit 1,2 hoch (Stufe − 2). Ein gewöhnliches Item der Stufe 2 kostet 100 Gold. **\[Test\]**
- **Verkaufen:** Für 25 % des Ladenpreises.
- **Sicherheit:** Der Händlerraum ist frei von Gegnern. Das Händlermenü pausiert das Spiel nicht, eine Zeitbegrenzung gibt es nicht.

## 5.6 Verbrauchsgegenstände

**Tränke:**

| Trank | Wirkung | Dauer |
| --- | --- | --- |
| Heiltrank | 25 % der maximalen HP | sofort |
| Regenerationstrank | 50 % der maximalen HP | über 10 s |
| Eiltrank | 30 % schneller laufen | 30 s |
| Krafttrank | 30 % mehr Schaden | 30 s |
| Schutztrank | 30 % weniger erlittener Schaden | 30 s |
| Gegengift | heilt Gift, danach immun | 30 s |

Alle Werte **\[Test\]**.

- **Rundung:** Immer aufrunden, auch beim erlittenen Schaden (11 Schaden mit Krafttrank = 15; 1 Schaden mit Schutztrank bleibt 1).
- **Mehrere Buffs:** Verschiedene Tränke wirken gleichzeitig. Derselbe Trank erneut verlängert die Dauer (zwei Krafttränke = 60 Sekunden), ohne Obergrenze; die Wirkung wird nicht stärker.
- **Trinken:** Etwa eine halbe Sekunde Animation, in der man stillsteht. Rückstoß unterbricht sie, der Trank bleibt dann erhalten. **\[Test\]**
- **Abklingzeit:** Heil- und Regenerationstrank teilen sich 10 Sekunden. Buff-Tränke sind nur durch ihre Dauer begrenzt.

**Weitere Verbrauchsgüter:**

- **Rückkehrrolle:** Teleportiert zum Startraum der aktuellen Etage.
- **Etagenkarte:** Deckt die Karte der aktuellen Etage auf (das Karten-Item aus 1.5).
- **Phönixfeder:** Ein Teamkamerad benutzt sie während des Todes-Countdowns beim Gestorbenen; dieser steht sofort an Ort und Stelle mit 25 % HP wieder auf. Selten, nicht beim Händler erhältlich.

**Bomben:**

- Bis zu 10 pro Slot. Werden abgelegt, Zündzeit 3 Sekunden (aus dem Kampfsystem).
- Sie blinken in immer schnellerem Rhythmus, sodass man den Zeitpunkt der Explosion abschätzen kann.
- Jeder kann eine liegende Bombe hochheben, ein Kraft-Armband ist nicht nötig. Steht man direkt bei einer Bombe, hebt die Leertaste sie auf, egal was im aktiven Slot liegt; erneutes Drücken wirft sie. Wer neben einer Bombe einen Trank trinken will, hebt also die Bombe auf. Eine getragene Bombe explodiert nach Ablauf der Zündzeit trotzdem.
- Explosionsradius etwa 1,5 Kacheln. Schaden an Gegnern etwa das Doppelte eines Schwerttreffers der Etage, an Spielern etwa 20 % ihrer maximalen HP. **\[Test\]**

**Pfeile:** Regenerieren, kaufen ist nicht nötig. Spezialpfeile gibt es als Zusatzeffekt des Bogens, nicht als Verbrauchsgut. Sie wirken nur im Kampf: Feuerpfeile zünden keine Fackelhalter an, Eispfeile frieren kein Wasser, damit sie keine Puzzle-Items ersetzen.

## 5.7 Gold und Wertgegenstände

- **Goldmenge:** Startwert etwa 50 Gold pro Spieler und Etage, multipliziert mit 1,2 hoch (Etage − 2). Pro Händlerbesuch reicht das ungefähr für ein gutes Item pro Spieler plus ein paar Tränke oder für einen Herzcontainer. Ob es zu viel oder zu wenig ist, zeigt der Playtest. **\[Test\]**
- **Edelsteine** sind größere Goldfunde, vor allem in Truhen und Schatzkammern. Sie gehen direkt in die Teamkasse und haben keine weitere Funktion. Der Name „Relikt“ ist für die einzigartigen Items reserviert.
- **Weitere Ausgaben:** Nur beim Händler. **\[Später\]** Optionale Abkürzungstüren, die sich gegen Gold öffnen lassen; nicht im Prototyp.
- **Tod:** Man verliert kein Gold.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Konkrete Werte für Tränke, Bomben, Preise und Goldmenge (Playtest)
- [ ] Ausrüstungsmenge pro Spieler und Etage (Playtest)
- [ ] Weitere Relikte entwerfen

**Auswirkungen auf andere Dokumente:**

- **Spielablauf 1.4:** Das offene Wiederbelebungs-Item ist entschieden: Phönixfeder (dort angepasst).
- **Spielablauf 1.5:** Das Karten-Item ist ein Verbrauchsgut (Etagenkarte).
- **Kampfsystem (Markdown-Datei):** Folgende offene Punkte sind hier entschieden und sollten dort nachgetragen werden: Inventar mit 20 Slots; aktiver Slot per Q/E und Zifferntasten, benutzen mit Leertaste; Bomben bis 10 pro Slot, jeder kann sie hochheben, Radius und Schaden wie oben; Regeln für Ausrüstungswechsel im Kampf (sofort).
