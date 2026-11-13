# Dungeon Derby – Gegner und Bosse: Entscheidungen

Nov 12, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_04_gegner_bosse.md` sind beantwortet. Das Dokument baut auf den Entscheidungen zu Spielablauf, Dungeon-Generierung, Rätseln und Kampfsystem auf.

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

## 4.1 Gegner-Auswahl

**Anzahl:** Etwa 8 bis 10 allgemeine Gegner, die überall vorkommen, plus 4 bis 5 pro Thema; es dürfen auch mehr werden. Über Mindestetagen tauchen pro Etage 2 bis 3 neue Gegner auf. Für den Prototyp reichen etwa 6.

**Grundtypen:** Zufällig wandernd, verfolgend, Fernkämpfer, Schildgegner, springend, unsichtbar (Phantome, siehe 4.7), beschwörend, explodierend, fallenartig.

- **Schildgegner** sind nur von hinten verwundbar und wenden sich immer dem nächsten Spieler zu.
- **Beschwörer:** Beschworene Gegner droppen nichts.
- **Fallenartige Gegner** (z. B. rollende Stachelkugeln) sind unverwundbar, man weicht nur aus. Sie zählen nicht für „alle Gegner besiegen“.

**Waffen und Rüstung von Gegnern:** Viele Gegner tragen Waffen (Skelette mit Bogen, Gegner mit Schild oder anderen Waffen). Meistens droppen sie diese nicht. Ist ein Waffen- oder Rüstungsdrop vorgesehen, wählt der Generator nach Möglichkeit einen Gegner, der genau dieses Teil trägt. Gibt es im Thema keinen solchen Gegner, droppt es ein anderer.

- Bogenschützen dürfen ihren Bogen erst in Bereichen droppen, die hinter dem Fundort des Puzzle-Items Bogen liegen (vorher keine Fernkampfwaffe, siehe 3.1).

**Elite-Varianten:**

- Doppelte HP, etwa +50 % Angriff.
- Wo es passt, doppelt so groß (2 × 2 statt 1 × 1 Kacheln), z. B. beim Oger, nicht unbedingt beim Magier.
- Hohe Chance auf ein verbessertes Item mit 1 bis 2 Bonuseffekten (z. B. kürzere Abklingzeit).
- Zusatzfähigkeiten sind an der Farbe erkennbar (z. B. grün = giftig).
- Zählen höher für das Content-Rating.

**Nur mit bestimmten Items besiegbar:** Gelegentlich, z. B. ein Eisgolem nur mit der Fackel oder ein Panzerkäfer, den man mit dem Kraft-Armband umdreht. Der Generator behandelt sie wie ein Rätsel: Sie stehen nur dort, wo das Item verfügbar ist, und gelten als Bedingung, wenn sie einen Weg blockieren.

## 4.2 Verhalten (KI)

**Wahrnehmung:** Gegner bemerken alle Spieler im Raum sofort. Ausnahmen als besonderes Verhalten einzelner Typen:

- Schlafende Gegner (z. B. Oger) wachen auf, wenn jemand nahe kommt oder sie trifft.
- Patrouillierende Wachen sehen nur in einem Kegel vor sich. Sie eignen sich für Schleich-Rätsel, in denen man die Wache nicht normal besiegen kann. Wird ein Spieler entdeckt, packt sie ihn und wirft ihn zum Raumeingang: gleicher Effekt wie ein Sturz in den Abgrund, inklusive Schaden, nur anders dargestellt. Danach patrouilliert sie weiter. Solche Räume sind Rätselräume.

**Zielwahl:**

- Standard ist der nächste Spieler. Gegner prüfen etwa alle 2 Sekunden, wer ihr Ziel ist, und wechseln gegebenenfalls. Das verhindert Hin-und-her-Zappeln.
- Manche Gegner wählen kein Ziel und bewegen sich zufällig.
- Manche wählen ein zufälliges Ziel und wechseln es nie.
- Einzelne Typen haben eigene Regeln, z. B. ein Assassine, der den Spieler mit den wenigsten HP sucht, oder ein Nahkämpfer, der immer den Spieler angreift, der seinem Fernkampf-Partner am nächsten ist.

**Tank:** Keine Provokations- oder Spott-Fähigkeit. Der Schildträger zieht Gegner auf sich, indem er vorne steht.

**Raumgrenzen:** Gegner verlassen ihren Raum nie. Einzige Ausnahme ist der Dieb (siehe 4.7).

**Gefahren:** Gegner meiden von selbst Abgründe, tiefes Wasser, Lava und alles, was sie direkt töten würde, und landen dort nur durch Stoßen. Gefahren mit Verzögerung, z. B. Stacheln, die erst nach einer Sekunde herausschießen, dürfen sie betreten.

**Determinismus:** Eigener geseedeter Zufallsgenerator pro Gegner (aus 2.6).

**Zusammenarbeit:** Ab mittleren Etagen gibt es Unterstützer, z. B. einen Schamanen, der andere heilt, einen Schildträger, der einen Bogenschützen deckt, oder Beschwörer. Das schafft Prioritätsziele.

## 4.3 Platzierung und Respawn

**Gegner pro Raum:** Ergibt sich aus Spawn-Bereichen, Content-Budget und Etage. Grobe Orientierung für ein Team aus 2 Spielern: 2 bis 4 Gegner auf frühen, 4 bis 8 auf späten Etagen. **\[Test\]** Füllräume sind eng (oft nur ein Korridor) und haben höchstens einzelne Gegner. Viele Rätselräume sind leer.

**Respawn:**

- Getötete Gegner bleiben grundsätzlich tot, auch bei Rückkehr auf eine Etage.
- Ausnahmen: Bomben-Gegner und Beschwörungen eines lebenden Beschwörers.
- **Räume mit „alle Gegner besiegen“ (auch Arenen):** Verlässt das Team den Raum unfertig, erscheinen beim nächsten Betreten alle Gegner neu, und der Raum beginnt von vorn. Bereits einmal besiegte Gegner droppen dann weder Items noch Gold, nur Heilung (neu ausgewürfelt, geseedet).

**Skalierung mit Teamgröße:** Pro Gegnertyp festgelegt. Normale Gegner skalieren vor allem über die Anzahl (etwa ein Gegner mehr pro zwei zusätzlichen Spielern) und leicht über HP (etwa +15 % pro Spieler über zwei). Große Einzelgegner wie ein Elite-Oger skalieren deutlich über HP und erscheinen nicht doppelt. **\[Test\]** Die Loot-Menge wächst ebenfalls mit der Teamgröße.

**Aktivierung:** In normalen Räumen sind alle Gegner gleichzeitig aktiv, Wellen gibt es nur in Arenen.

## 4.4 Werte und Skalierung

**Kurve:** HP und Schaden steigen exponentiell um 10 % pro Etage. Etage 2 ist der Basiswert, Etage 1 (Tutorial) liegt bei 50 %.

```latex
\text{Faktor}(n) = 1{,}1^{\,n-2} \quad (n \ge 2), \qquad \text{Faktor}(1) = 0{,}5
```

Gerundet: Etage 3 = 110 %, 5 = 133 %, 7 = 161 %, 10 = 214 %. Eventuell steiler, **\[Test\]**. Die Ausrüstung muss in etwa demselben Tempo besser werden, sonst dauern Kämpfe auf späten Etagen spürbar länger.

**Gegnertypen über die Etagen:** Jeder Typ hat eine Mindest- und Höchstetage und verschwindet irgendwann aus dem Pool. Innerhalb seines Bereichs skaliert er mit der Kurve.

**Kontaktschaden:** Fast alle Gegner machen Kontaktschaden, auch Magier, etwa halb so viel wie ihr Angriff. Schildgegner können stattdessen schieben, z. B. in Räumen, in denen sie Spieler in Abgründe drängen. **\[Test\]**

**Projektile:**

| Projektil | Schild | Spiegelschild | Schwert oder Keule |
| --- | --- | --- | --- |
| Pfeil | blockt | blockt | kein Effekt |
| Stein, Wurfspieß | blockt | blockt | kein Effekt |
| Feuerball | blockt | wirft zurück | kein Effekt |
| Magiekugel (langsam, groß) | blockt | wirft zurück | schlägt zurück |
| Laser | blockt nicht | wirft zurück | kein Effekt |
| Giftspucke | blockt | blockt | kein Effekt |

**Treffer bis zum Tod** mit Schwert und Ausrüstung passend zur Etage: normale Gegner 2 bis 4, robuste wie Oger 6 bis 10, Elite etwa doppelt so viele wie ihre normale Variante. Schwächere Waffen brauchen entsprechend mehr, z. B. Wurfmesser 5 bis 10 Treffer für einen normalen Gegner. **\[Test\]**

**Selbstheilung:** Manche Gegner heilen sich regelmäßig selbst, mit sichtbarem Effekt.

## 4.5 Belohnungen

**Drops:** Heilung (wie Herzen bei Zelda, z. B. 40 HP), Verbrauchsgüter (Tränke, Bomben) und selten Ausrüstung. Alles wird pro Gegner beim Generieren festgelegt; Heilung respawnter Gegner wird geseedet neu ausgewürfelt.

**Gold** landet nicht auf dem Boden, sondern direkt in der gemeinsamen Teamkasse. Jeder kann damit beim Händler einkaufen.

**Aufheben:**

- Drops liegen auf dem Boden. Ein Item zu berühren hebt es auf; wer zuerst kommt, bekommt es.
- Wer ein Item abwirft, legt es auf ein freies Feld neben sich, bevorzugt vor sich. Er kann es erst wieder aufheben, nachdem er sich vom Feld entfernt hat.
- Ist das Inventar voll, bleibt das Item liegen.

**Verschwinden:** Items und Verbrauchsgüter verschwinden nie. Heilung verschwindet nach etwa 15 Sekunden. **\[Test\]**

**Keine Erfahrungspunkte und keine Stufen,** Fortschritt nur über Ausrüstung. Dazu gibt es Herzcontainer, die das HP-Maximum erhöhen:

- Normale Herzcontainer gelten für einen Spieler.
- Bosse droppen Herzcontainer, die für das ganze Team gelten: Einer hebt ihn auf, jeder im Team bekommt die HP.

## 4.6 Bosse

**Bosse verlangen Puzzle-Items.** Beim Generieren werden zuerst die Bosse gewählt. Ihre benötigten Items werden als feste Bedingung in die Item-Reihenfolge eingetragen, sodass sie vor dem Boss verfügbar sind. Bosse haben wie Rätselvorlagen eine Mindestspielerzahl, falls sie Items in verschiedenen Händen verlangen. Es werden später mehrere Bosse entworfen.

**Grundprinzip Skalierung:** Bosse, bei denen alle die ganze Zeit Schaden machen, skalieren schlecht mit der Teamgröße (mehr Spieler bringen zugleich mehr HP-Pool und mehr Schaden). Besser sind Verwundbarkeitsfenster mit Schadensobergrenze: Dann bestimmt die Mechanik das Tempo, nicht die Spielerzahl.

**Ideen:**

- **Steinwächter** (für den Prototyp): großer Golem, wendet sich dem nächsten Spieler zu, nur am Kristall auf dem Rücken verwundbar, stampft Schockwellen. In Phase 2 brechen Steine von der Decke, die man mit dem Kraft-Armband werfen kann. Für richtige Bosse zu simpel.
- **Lichkönig** (Richtung für richtige Bosse): teleportiert sich, beschwört Skelette, wirft Magiekugeln, die man mit Schwert oder Spiegelschild zurückschlagen kann. Seine Barriere fällt nur, wenn vier Kristalle in den Raumecken innerhalb weniger Sekunden angeschlagen werden. In der letzten Phase verdunkelt er den Raum, und die Fackel wird gebraucht.

**Phasen:** Immer mehrere. Phasenwechsel nach HP, nach Zeit oder ereignisgesteuert, z. B.: Die Spieler lösen in Phase 1 etwas aus, in Phase 2 ist der Boss verwundbar, nach einer Schadensmenge oder Zeit geht es zurück in Phase 1. Wechsel sind gut erkennbar.

**Teamarbeit:** Spieler müssen verschiedene Dinge etwa gleichzeitig tun, um den Boss verwundbar zu machen, und dann gemeinsam angreifen. Weitere Bausteine: Schwachstelle auf der Rückseite, Beschwörungen abfangen, Boss an eine bestimmte Stelle locken, Angriffe, bei denen Spieler Abstand halten oder zusammenstehen müssen. World of Warcraft ist eine gute Inspirationsquelle.

**Bossraum und Kampfablauf:**

- Beim Betreten erscheint groß der Name, z. B. „BOSS: LICHKÖNIG“, für ein paar Sekunden.
- Der Raum hat einen klar abgegrenzten Startbereich, in dem sich das Team sammeln kann, ohne den Kampf auszulösen.
- Verlässt jemand den Startbereich, beginnt der Kampf und die Tür schließt sich. Wer dann im Raum ist (auch im Startbereich), kämpft mit; der Startbereich ist ab dann keine sichere Zone mehr.
- Respawnte Spieler warten draußen. Rückweg zum Bossvorraum über den Teleporter.
- Sterben alle Spieler im Raum, öffnet sich die Tür, und der Boss setzt sich zurück: volle Heilung, zurück auf Phase 1.

**Teamgröße:** Für den Prototyp skalieren Bosse über HP, ihre Beschwörungen über die Anzahl. **\[Später\]** Eigene Bossvarianten für 2, 3 oder 4 Spieler. **\[Später\]** Pool aus 2 bis 3 Bossen pro Bossplatz.

**Belohnung:** Beim ersten Boss ein Herzcontainer für das ganze Team plus seltene Items, die nur Bosse droppen. Beim letzten Boss ist der Sieg die Belohnung.

**Minibosse:**

- Gelegentlich auf anderen Etagen, z. B. ein Elite-Gegner, der einen Schlüssel oder eine Truhe bewacht. Sie zählen als Rätselraum.
- Eine Phase. Man muss etwas tun, um sie kurz verwundbar zu machen (z. B. mit dem Kraft-Armband einen Fels auf sie werfen), und pro Fenster lässt sich höchstens etwa ein Drittel ihrer HP abziehen.
- Gedacht für 1 bis 2 Spieler. Mehr Spieler machen den Kampf sicherer, aber nicht schneller, und fehlen dafür beim Erkunden.
- Erhöhte Chance auf gute Drops.

## 4.7 Besondere Gegner

**Phantome** (unsichtbare Gegner; nicht „Geist“, um Verwechslung mit der Spielerrolle zu vermeiden):

- Hinweise: leichtes Flimmern in der Luft und ein Geräusch, das lauter wird, wenn sie näherkommen. Diese Hinweise müssen sich deutlich von den Spuk-Effekten des Spieler-Geists unterscheiden.
- Beim Angreifen und nach einem Treffer werden sie kurz sichtbar.
- Im Licht der Fackel sind sie ganz sichtbar, als Bonus, nicht als Pflicht.

**Gegner mit Rätselelementen:** Sparsam. Beispiel Kobold-Raum (Rätselraum):

- Ein Kobold rennt zu einem Hebel und schließt die Tür, sobald er Spieler sieht.
- Ein zweiter Gegner steht im Weg, sodass man um ihn herum muss, um den Kobold abzufangen, aber keine Zeit hat, ihn zuerst zu besiegen.
- Gelöst ist der Raum, wenn alle Gegner besiegt sind und der Hebel nicht umgelegt wurde. Erreicht der Kobold den Hebel, erscheinen beim nächsten Betreten alle Gegner neu.
- Gegner verändern nur Dinge in ihrem Raum und zerstören nie einen gelösten Zustand.

**Mimics:** Ab Etage 4, gelegentlich. Mit kleinem, fairem Erkennungsmerkmal (z. B. die Truhe atmet leicht). Besiegt, droppen sie den Inhalt, den die Truhe gehabt hätte.

**Diebe:**

- Stehlen Gold aus der Teamkasse oder ein Verbrauchsgut, nie Schlüssel oder Puzzle-Items.
- Mit Beute rennen sie etwa 2 Sekunden im Raum herum und dann zu einer der Türen.
- Wer sie vorher besiegt, bekommt die Beute zurück. Entkommen sie durch die Tür, verschwinden sie samt Beute. Einzige Ausnahme von „Gegner verlassen ihren Raum nie“.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Konkrete Bosse entwerfen, zunächst Steinwächter für den Prototyp und Lichkönig
- [ ] Steigung der Werte-Kurve, eventuell steiler als 10 % pro Etage (Playtest)
- [ ] Skalierungswerte mit Teamgröße pro Gegnertyp (Playtest)
- [ ] Konkrete Gegnerliste pro Thema

**Auswirkungen auf andere Dokumente:**

- **Dungeon-Generierung 2.3:** Bosse werden zuerst gewählt; ihre benötigten Items sind feste Bedingungen in der Item-Reihenfolge.
- **Dungeon-Generierung 2.4:** Die Tür zum Bossraum schließt sich während des Kampfes (dort angepasst).
- **Rätsel 3.1:** Die Reihenfolge der Puzzle-Items ist zufällig, aber durch die Anforderungen der Bosse eingeschränkt.
- **Kampfsystem / Ausrüstung:** Die Ausrüstung muss mit etwa 10 % pro Etage besser werden, damit sie mit der Gegnerkurve mithält. Herzcontainer erhöhen das HP-Maximum.
