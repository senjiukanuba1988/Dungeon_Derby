# Dungeon Derby – Spielablauf, Teams und Geist: Entscheidungen

Nov 10, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_01_spielablauf.md` sind beantwortet. Das Dokument ergänzt die Entscheidungen zum Kampfsystem (`dungeon_derby_kampfsystem.md`).

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

## 1.1 Partiedauer

- **Richtwert:** etwa 90 Minuten pro Partie. Grober Richtwert, kein hartes Ziel.
- **Wachsende Etagen:** Die Etagen werden mit der Tiefe größer, z. B. 8 Räume auf Etage 1, 10 auf Etage 2 usw. bis etwa 30 Räume auf der letzten Etage. Die Zeit pro Etage ist also nicht konstant.
- **\[Test\]** Raumanzahl gegen Partiedauer: Bei 8 bis 30 Räumen über 10 Etagen kommen rund 190 Räume zusammen, das sind unter 30 Sekunden pro Raum. Lösungen: flachere Kurve, mehr schnelle Durchgangsräume oder längere Partie. Aufteilen des Teams entschärft das.
- **\[Offen\]** Anzahl der Etagen: 10 oder 8. Bei 8 Etagen liegen die Bosse auf Etage 4 und 8.
- **Kurzvariante:** Nicht geplant. Für Tests werden kürzere Szenarien gebaut.
- **Speichern und später fortsetzen:** **\[Später\]**, als Option vorgemerkt.
- **Skalierung mit Teamgröße:** Gegneranzahl und Gegner-HP skalieren mit der Teamgröße, nicht mit der Zahl der Spieler im Raum. Layout und Rätsel bleiben gleich.

## 1.2 Lobby und Teams

**Lobby als begehbarer Raum.** Die Spieler laufen frei herum und wählen ihr Team, indem sie sich auf Druckplatten stellen.

- Links liegen rote, rechts blaue Druckplatten. Bei ungerader Spielerzahl gibt es in der Mitte eine Druckplatte mit Geist-Symbol.
- Jedes Mal, wenn ein Spieler der Lobby beitritt oder sie verlässt, erscheinen alle Spieler in der Mitte, aber nie auf einer Druckplatte.
- **Erdbeben-Knopf:** Jeder Spieler kann ihn drücken. Alle fliegen durch den Raum und landen danach klar verteilt: die Hälfte links, die Hälfte rechts, bei ungerader Zahl einer nahe der Geist-Platte. Niemand landet direkt auf einer Platte.
- **Start:** Sind alle Platten gedrückt, läuft ein kurzer Countdown. Wer in dieser Zeit von einer Platte steigt, bricht ihn ab. Die Teams ergeben sich aus den Platten.
- **Ein Team gegen die Zeit:** Das Spiel startet auch, wenn alle Spieler auf Platten derselben Farbe stehen und die andere Seite leer ist.

**Spielerzahl:** 2 bis 12. Möglich sind 1 gegen 1, 1 gegen 1 mit Geist sowie ein einzelnes Team gegen die Zeit.

- Für jeden Rätselraum wird festgehalten, wie viele Spieler er benötigt. Hat ein Team weniger Spieler, verwendet der Generator diesen Raum nicht.

**Ungleiche Teams:** Nicht erlaubt. Der Geist ist der Ausgleich bei ungerader Zahl.

**Aussehen:** Das Team bekommt die Farbe Rot oder Blau. Die Spieler tragen Kleidung oder Rüstung mit farblichen Elementen in dieser Farbe.

**Beitritt:** Nach Spielbeginn kommen keine neuen Spieler hinzu. Wiedereinstieg nach Verbindungsabbruch ist möglich (siehe 1.6).

## 1.3 Ablauf einer Partie

- **Zählung:** Etagen 1 bis 10. Die Lobby gehört nicht zum Dungeon.
- **Start:** Beide Teams starten nach dem Lobby-Countdown gleichzeitig auf Etage 1.
- **Etage 1 als Tutorial:** Sehr einfache Gegner, ein paar einfache Rätsel und etwas Ausrüstung. Es liegt pro Spieler eine Waffe auf Etage 1, sodass das ganze Team ausgerüstet auf Etage 2 ankommt. Kein separates Tutorial.
- **\[Später\]** Waffen und Trainingspuppe zum Ausprobieren in der Lobby.
- **Treppe:** Jeder Spieler kann einzeln zur nächsten Etage wechseln, auch wenn andere noch oben sind. Die Treppe wird automatisch auf der Karte markiert.
- **Zurückkehren:** Erlaubt, z. B. um vergessene Items zu holen oder beim Händler einzukaufen, wenn vorher das Gold fehlte. Spieler auf früheren Etagen spielen dort ganz normal weiter.
- **Respawn:** Am Eingang der Etage, auf der man gestorben ist. Klärt den offenen Punkt aus dem Kampfsystem-Dokument (Abschnitt 12).
- **Siegbedingung:** Die Zeit eines Teams stoppt, sobald es den Boss der letzten Etage besiegt hat. Kein Lauf zum Ausgang.
- **Nach dem Sieg:** Ist das erste Team fertig, läuft gegebenenfalls der Geist-Bonus-Countdown für das andere Team (siehe 1.7). Danach steht der Sieger fest. Das andere Team darf zu Ende spielen; die Sieger schauen wie der Geist unsichtbar zu.
- **Aufgeben:** Möglich. **\[Offen\]** Wie genau, z. B. per Abstimmung im Team.

## 1.4 Wissen über das andere Team

**Fortschrittsrangfolge.** Die Rangfolge ist bewusst feinkörnig, damit meistens ein Team führt und der Geist etwas zu tun hat. Verglichen wird in dieser Reihenfolge:

1. Tiefste erreichte Etage.
2. Hat ein Team das Puzzle-Item dieser Etage gefunden, das andere noch nicht?
3. Welches Team hat auf dieser Etage mehr Schlüssel gefunden?

Annahme: Jede Etage hat genau ein Puzzle-Item.

**Anzeige:** Die Spieler sehen nur eine Fortschrittsleiste im Inventar-Menü, ohne Details, was das andere Team erreicht hat. Es gibt keine Meldungen wie „Team Rot hat Etage 3 erreicht“. Nur wenn ein Team fertig ist, erscheint eine Meldung und gegebenenfalls der Geist-Bonus-Countdown.

**Tod:** Ein gestorbener Spieler sieht den Raum, in dem er gestorben ist, und einen Countdown. Er kann die Kamera nicht bewegen und nichts erkunden. Zuschauen beim anderen Team ist nicht möglich.

- **Wiederbelebung:** Mit der seltenen Phönixfeder kann ein Teamkamerad den Gestorbenen während des Countdowns an Ort und Stelle mit 25 % HP wiederbeleben (siehe Items-Dokument 5.6).

**Teams begegnen sich nie.** Der Widerspruch zu `ideas.md` ist aufgelöst. Händler sind in beiden Dungeons identisch, aber unabhängig: Kauft Team 1 beim ersten Händler die Schwere Rüstung, ist sie für Team 2 beim ersten Händler in dessen Dungeon weiterhin verfügbar.

## 1.5 Kommunikation im Team

**Sprachchat** läuft extern (Discord o. ä.), nicht im Spiel.

**Textchat im Spiel:**

- Enter öffnet das Eingabefenster. Nachrichten gehen standardmäßig ans Team; Tab wechselt zwischen Team und Alle.
- Nachrichten erscheinen mittig oder am Rand und bleiben einige Sekunden sichtbar.
- Bei offenem Chatfenster ist der Verlauf sichtbar und per Mausrad scrollbar.

**Karte im Inventar-Menü:**

- Zeigt die besuchten Räume der Etage plus offene Verbindungen zu noch unbesuchten Räumen (z. B. eine Tür nach Norden in einen noch nicht betretenen Raum).
- Das ganze Team sieht dieselbe Karte.
- Ein findbares Karten-Item deckt die ganze Etage auf. Besuchte und unbesuchte Räume bleiben unterscheidbar.
- Die Treppe wird automatisch markiert.
- Teamkameraden werden mit dem Raum angezeigt, in dem sie sich befinden, nicht mit ihrer genauen Position.

**Markierungen** setzen die Spieler selbst auf der Karte, statt temporärer Pings:

- „Gruppe benötigt“ (Rätsel oder schwerer Kampf für das ganze Team)
- „Puzzle-Item benötigt“
- „Schlüssel benötigt (Farbe)“

So sieht das Team, wo es gemeinsam hinmuss, und nach dem Fund eines Puzzle-Items oder Schlüssels, wo es eingesetzt werden kann. Jeder im Team kann eine Markierung per Klick wieder entfernen.

## 1.6 Verbindungsabbruch und Pausen

- **Figur bei Abbruch:** Verschwindet sofort. Alle sehen die Meldung „Verbindung zu Spieler XYZ verloren“.
- **Wiedereinstieg:** An derselben Stelle, mit den HP, die der Spieler beim Abbruch hatte. Exploits sind unter Kollegen kein Thema.
- **Schlüssel und Puzzle-Item:** Fallen beim Abbruch an der Stelle des Spielers zu Boden, damit das Team weiterkommt. Die übrige Ausrüstung behält er. Schlüssel werden immer von einem einzelnen Spieler getragen, es gibt keinen gemeinsamen Schlüsselzähler.
- **Dauerhafter Verlust:** Bestätigen die verbliebenen Spieler des betroffenen Teams und der Geist, wechselt der Geist als Spieler in dieses Team. Er erscheint an der Stelle des verlorenen Spielers, übernimmt dessen Ausrüstung und muss Schlüssel und Puzzle-Item selbst aufheben. Eine Zeitgrenze für „dauerhaft“ gibt es nicht.
- **Host verliert die Verbindung:** **\[Offen\]**, wird mit der Technik geklärt.
- **Pause:** Jeder Spieler kann pausieren. Es erscheint „3 … 2 … 1 … PAUSE“, und das Spiel hält für beide Teams an. Jeder Spieler kann die Pause wieder aufheben.

## 1.7 Geist

Der Geist ist ein Fallback für ungerade Spielerzahlen. Er ärgert das jeweils führende Team und sammelt dafür Chaospunkte.

**Beobachten:** Der Geist kann zwischen beiden Dungeons wechseln und bleibt dabei an genau seiner Position. Führt das Team, das er gerade nicht beobachtet, bekommt er einen Hinweis, dass er dort ärgern kann. Seine Fähigkeiten wirken nur beim führenden Team.

**Fähigkeiten und Abklingzeiten:**

- Alle Fähigkeiten haben eigene Abklingzeiten.
- Jeder Einsatz löst eine gemeinsame Abklingzeit von 5 Sekunden auf alle Fähigkeiten aus. Fähigkeiten, die bereits länger als 5 Sekunden abklingen, bleiben unverändert.
- Effekte sind nur vorübergehend und nutzen ausschließlich Elemente, die im Dungeon schon vorhanden sind (z. B. eine bestehende Falle auslösen, keine neue platzieren). Damit bleibt der Grundsatz identischer Dungeons gewahrt.
- Der Geist verursacht keinen direkten Schaden. Schaden entsteht nur durch vorhandene Gegner und Fallen.

**Chaos-Meter:** Keine Ressource, sondern der Highscore des Geists. Es füllt sich, wenn er erfolgreich ärgert. Erfolg wird je Fähigkeit gemessen, zum Beispiel:

- Ein verlangsamter Spieler nimmt Schaden, weil er nicht ausweichen kann.
- Ein Spieler wartet an einer vom Geist geschlossenen Tür; Punkte je nach Wartezeit nahe der Tür.

Die Punkte werden getrennt pro Team erfasst.

**Bonuszeit am Ende:**

- Besiegt ein Team den letzten Boss zuerst und hat der Geist gegen das andere Team mehr Punkte gesammelt, bekommt das andere Team Bonuszeit.
- Die Bonuszeit hängt von der Punktedifferenz ab, beträgt höchstens 30 Sekunden und ist immer deutlich kleiner als die verursachte Verzögerung.
- Sie erscheint für alle Spieler als Countdown. Wird das andere Team währenddessen fertig, gewinnt es.
- Wurde das fertige Team stärker geärgert, ist die Bonuszeit 0 und es gewinnt sofort.
- **\[Test\]** Gemeinsame Punkteskala über alle Fähigkeiten: etwa 1 Chaospunkt pro Sekunde verursachter Verzögerung. Umrechnung in Bonuszeit etwa 8:1 (8 Sekunden Warten an einer Tür ergeben etwa 1 Sekunde Bonus).

**Präsenz:** Wo der Geist ist, wackeln Dinge, Vorhänge flattern usw., ohne Einfluss aufs Spiel. Das gilt immer, auch wenn kein Team führt, und zeigt den Spielern, dass er da ist. Setzt er eine Fähigkeit ein, blitzt er kurz halbtransparent auf.

**Nicht geplant:** Rotation der Geist-Rolle während der Partie (höchstens später als Option) und Items zur Geister-Abwehr.

**\[Offen\] Hausregel (Vorschlag):** Geist und zuschauende Sieger verraten dem anderen Team über Discord keine Lösungen. Technisch lässt sich das nicht verhindern.

## 1.8 Ende der Partie

**Statistiken auf dem Endbildschirm:**

- Etagenzeiten beider Teams nebeneinander. Da der Dungeon identisch ist, sieht man so direkt, wo welches Team Zeit verloren hat.
- Pro Spieler: Tode, Abgrundstürze, ausgeteilter und erhaltener Schaden, Heilung, gesammeltes und ausgegebenes Gold, gelöste Rätsel, besuchte Räume.
- Geist: Chaos-Meter, aufgeteilt nach Teams, und die daraus berechnete Bonuszeit.

**Auszeichnungen:** Ein Pool, aus dem pro Partie 3 bis 5 vergeben werden, gern auch spöttische wie „Häufigster Sturz in Abgründe“ oder „Längste Wartezeit an einer Geistertür“.

**Seed:** Der Endbildschirm zeigt den Seed; in der Lobby kann man einen Seed eingeben. Da Rätselräume je nach Teamgröße ausgeschlossen werden, gilt ein Seed immer zusammen mit der Teamgröße.

**\[Später\]** Bestzeiten als einfache lokale Liste pro Seed und Teamgröße.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Anzahl der Etagen: 10 oder 8 (1.1)
- [ ] Raumanzahl pro Etage gegen Partiedauer abstimmen (1.1, Playtest)
- [ ] Ablauf beim Aufgeben (1.3)
- [ ] Wiederbelebungs-Consumable während des Todes-Countdowns (1.4) – entschieden: Phönixfeder (Items 5.6)
- [ ] Verhalten beim Verbindungsabbruch des Hosts (1.6, Technik)
- [ ] Punkteskala und Umrechnung Chaospunkte in Bonuszeit (1.7, Playtest)
- [ ] Hausregel gegen Lösungsverrat über Discord (1.7)

**Auswirkungen auf andere Dokumente:**

- **Kampfsystem, Abschnitt 12:** Respawn erfolgt am Eingang der Etage, auf der man gestorben ist.
- **Rätsel- und Raumdesign:** Jeder Rätselraum braucht eine Angabe, wie viele Spieler mindestens nötig sind. Der Generator schließt Räume aus, die das Team nicht erfüllen kann.
- **Rätsel- und Raumdesign:** Jede Etage hat genau ein Puzzle-Item (Annahme aus 1.4).
- **Geist-Fähigkeiten:** Jede Fähigkeit braucht eine eigene Erfolgsmessung für das Chaos-Meter.
