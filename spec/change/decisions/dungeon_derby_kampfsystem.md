# Dungeon Derby – Kampfsystem: Entscheidungen

*Stand: Abschnitte „Bewegung und Zielen“ sowie „Angriffs-Timing und Hit-Erkennung“ abgeschlossen. Ergänzt `combat_design_checklist.md`.*

Markierungen: **[Test]** = Richtung festgelegt, endgültiger Wert oder Variante wird im Playtest entschieden. **[Offen]** = noch nicht entschieden.

---

## 1. Spielrahmen

- 2D-Top-down-Dungeon-Crawler im Stil von NES-Zelda und Link's Awakening. Chip's Challenge als Inspirationsquelle für Rätsel (Eis, Förderbänder, Schalterböden usw.).
- Zwei Teams erkunden einen **identischen, zufällig generierten Dungeon**. Generator-Regeln stellen die Lösbarkeit sicher.
- Monster, Drops und Loot werden beim Generieren festgelegt und sind für beide Teams identisch.
- Ein Dungeon hat **10 Etagen**, mit einem Boss am Ende von Etage 5 und Etage 10.
- Die Teams begegnen sich nicht; keine Sabotage zwischen Teams.
- Bei ungerader Spielerzahl wird der übrige Spieler zum **Geist**: Er schaut zu und kann das führende Team verlangsamen und ärgern. Balancing erfolgt später, wenn der Rest geklärt ist.
- **Keine Progression zwischen Runs**; jedes Spiel beginnt bei null.
- Jeder Spieler spielt auf seinem eigenen PC (Windows, Mac, Linux) mit eigener Ansicht.

## 2. Ausrüstung

### Slots
Fünf Slots: **Mainhand, Offhand, Rüstung, Kopfbedeckung, Puzzle-Item.**
*(Hinweis: Abschnitt 1 der Checkliste nennt noch vier Slots und muss angepasst werden.)*

- **Mainhand:** immer eine Waffe.
- **Offhand:** Waffe, Schild oder Zauberspruch.
- **Rüstung:** reduziert Schaden. Beispiel „Schwere Rüstung“: deutlich weniger Schaden, aber 20 % langsamer.
- **Kopfbedeckung:** beliebige Effekte, z. B. Helm mit zusätzlicher Rüstung oder Zaubererhut, der das Aufladen von Zaubern beschleunigt.
- **Puzzle-Item:** Rätselwerkzeuge wie das Kraft-Armband (schwere Gegenstände heben) oder die Sprungfeder.

### Zaubersprüche
- Nutzen Cooldowns statt Mana; manche haben mehrere Ladungen, die nacheinander gewirkt werden können.
- Jeder Zauber hat im Inventar einen Tooltip, der seine Bedienung erklärt.

### Schild
- Blockt Projektile von vorne mit hoher Wahrscheinlichkeit und reduziert eingehenden Schaden.
- Schildträger dürfen gleichzeitig blocken und mit der Mainhand angreifen. Das ist gewollt: Wer einen Schild trägt, verzichtet auf eine zweite Waffe oder einen Zauber und übernimmt damit die Tank-Rolle.

### Item-Varianten und Zufall
- Von jedem Item gibt es verbesserte Versionen.
- Schaden ist grundsätzlich fest. Verbesserte Versionen können Zufallseffekte haben, z. B.:
  - 5 % Crit-Chance (doppelter Schaden),
  - 50 % Chance auf Gift: 1 Schaden alle 2 Sekunden für 10 Sekunden.
- Zufall ist **geseedeter Pseudozufall pro Item**: Das Item trägt den Zustand seines Zufallsgenerators, sodass beide Teams gleich verteilte Erfolge bekommen. Wechselt ein Item den Besitzer, wandert der Zustand mit.

### Lebenspunkte
- Spieler starten mit **20 HP**; Rüstung, Helm und Schild können das Maximum erhöhen.
- **[Offen]** Verhalten beim An- und Ablegen. Vorschlag: Zusätzliche HP kommen beim Anlegen leer hinzu, beim Ablegen werden die aktuellen HP auf das neue Maximum gekappt. Das verhindert Heilen durch Umziehen.

### Bogen
- Mainhand-Waffe, auch für Rätsel nutzbar.
- Bis zu 5 Pfeile im Vorrat; solange weniger als 5 vorhanden sind, kommt alle 10 Sekunden ein Pfeil dazu.

### Spiegelschild
- Rätselrelevantes Item, das wie der Bogen in einem normalen Slot (Offhand) getragen wird.
- Kann z. B. Laser-Projektile und manche Zauber zurückwerfen.
- Hinweis zur Lösbarkeit: Wie beim Bogen muss der Generator berücksichtigen, dass jemand im Team das Item auch ausrüsten muss.

### Bomben
- Für Rätsel nutzbar (z. B. Wände sprengen).
- Werden im Inventar getragen und über den aktiven Slot benutzt (siehe unten).
- Werden zunächst **abgelegt**; Zündzeit **3 Sekunden**. Man kann eine liegende Bombe hochheben und werfen (Parabel-Flugbahn).
- Verletzen Spieler, die zu nah stehen (Friendly Fire), verursachen aber **keinen Knockback**.
- Gegen Softlocks: Räume mit respawnenden Gegnern, die Bomben droppen. Empfehlung: diese Räume nahe an Stellen platzieren, an denen Bomben gebraucht werden.
- **[Offen]** Maximale Anzahl Bomben; ob jeder Bomben hochheben kann oder nur mit Kraft-Armband; Explosionsradius und Schaden.

### Inventar und aktiver Slot
- Inventar mit einer **festen Anzahl Slots**. **[Offen]** Anzahl.
- Enthält Ersatzausrüstung (z. B. einen Umhang gegen Feuerschaden, den man nur bei Bedarf statt der Rüstung anzieht), Bomben, Heiltränke, andere Tränke und weitere Verbrauchsgegenstände.
- Ein Inventarslot ist **aktiv**: Das Item darin wird per Taste benutzt. Ein Trank wird getrunken, eine Bombe abgelegt.
- Denkbare Tränke: feste Sofortheilung, größere Heilung über Zeit, schnelleres Laufen, mehr Schaden, weniger erlittener Schaden (jeweils für eine Dauer).
- **[Offen]** Wie der aktive Slot gewechselt wird; Regeln für Ausrüstungswechsel im Kampf (gehört in den Abschnitt „Ausrüstung“ der Checkliste).

## 3. Steuerung

- Ausschließlich Tastatur; Maus eventuell optional.
- Bewegung mit WASD oder Pfeiltasten.
- Aktionstasten nahe der Tastaturmitte, z. B. J = Mainhand, K = Offhand, L = Puzzle-Item.
- Eine weitere Taste für den aktiven Inventarslot. **[Offen]** Welche Taste.
- **[Test]** Gegensätzliche Richtungen gleichzeitig (A + D): Tendenz Stillstand.
- **[Test]** Input-Puffer während der Erholungsphase von Angriffen.

## 4. Bewegung

- 8 Richtungen (4 Hauptrichtungen und 4 Diagonalen).
- **Diagonal gleich schnell:** Pro Achse wird mit dem Faktor ≈ 0,7 (1/√2) bewegt.
- Gleiche Grundgeschwindigkeit für alle; Ausrüstung kann sie verändern.
- Geschwindigkeitsmodifikatoren werden **multipliziert**. **[Test]** Untergrenze, voraussichtlich 50 %.
- **Sofortiges Starten und Stoppen**, ohne Verzögerung beim Loslaufen. Ausnahmen über Bodenarten (z. B. Eis).
- **[Test]** Freie Bewegung (wie Link's Awakening) wird bevorzugt; Raster vs. frei wird getestet. Falls frei: Ecken-Korrektur erwägen, damit man an Kanten entlanggleitet statt hängen zu bleiben.
- Kein Drehen im Stand: Ein Tastendruck erzeugt immer mindestens eine minimale Bewegung.
- **Kollisionsbox an den Füßen**; die Trefferfläche für Angriffe entspricht dem Sprite.
- **Keine Ausweichtaste.** Die Sprungfeder (Puzzle-Item) erlaubt es, über Projektile und Gegner zu springen.

### Technischer Hinweis: Teil-Pixel
Durch den Diagonalfaktor und kleine Geschwindigkeiten entstehen Bruchteile von Pixeln. Positionen werden intern als Kommazahlen gespeichert und erst beim Zeichnen gerundet. Ohne das ruckelt besonders die Diagonalbewegung sichtbar, weil die Figur abwechselnd auf einer Achse springt und auf der anderen stehen bleibt.

## 5. Blickrichtung und Zielen

- **Angriffe in 4 Richtungen.** Beim Diagonallaufen gilt die Richtung, deren Taste zuerst gedrückt wurde.
- **Angriffstaste halten** fixiert die Blickrichtung, egal wohin man sich danach bewegt.
- **Schwerthiebe decken einen Bogen ab:** Mainhand schlägt von rechts nach vorne, Offhand von links nach vorne. Damit sind auch diagonal stehende Gegner treffbar.
- Andere Waffen sind diagonal schwächer, haben dafür andere Vorteile (z. B. Bogen, Speer).
- **Zauber:** Die meisten wirken in Blickrichtung oder sind richtungslos.
- **Gezielte Zauber:** Da man beim Zaubern still steht, steuert WASD währenddessen einen Zielcursor. **[Test]** Ob der Zauber nach fester Zeit oder erst auf Bestätigung auslöst.
- **Schild:** schützt nur in Blickrichtung. Schräg eintreffende Projektile werden aber absorbiert, wenn sie die Vorderseite des Charakters treffen.

## 6. Aktionen während der Bewegung

- **Angreifen beim Laufen:** abhängig von der Waffe.
- **Zaubern:** Taste drücken → Spieler bleibt für die Zauberdauer stehen. Nicht abbrechbar; währenddessen ist keine andere Aktion möglich.
- **Blocken:** Taste halten; man läuft dabei langsamer.
- **Mainhand und Offhand gleichzeitig** nutzbar.
- **Puzzle-Items:** Die meisten verändern den Zustand des Charakters nicht. Ausnahme Kraft-Armband: Solange man etwas trägt, kann man nichts anderes tun.
- Geworfene schwere Gegenstände sind Projektile mit Parabel-Flugbahn.
- **[Offen]** Lässt man getragene Gegenstände fallen, wenn man getroffen wird?

## 7. Treffer, Knockback und Unverwundbarkeit

- Ein Treffer verursacht normalerweise Knockback und immer kurze Unverwundbarkeit, sofern nicht ausdrücklich anders festgelegt.
- Unverwundbarkeit betrifft nur den getroffenen Spieler.
- **Knockback:** weg von der Schadensquelle, keine Kontrolle währenddessen. **[Test]** Dauer, etwa 0,25 s.
- Knockback kann Spieler in Abgründe und Fallen stoßen.
- **[Offen]** Kann Knockback Spieler über Kanten ohne Geländer stoßen?
- **Nur Knockback unterbricht Zauber und Angriffe.** Bei Zaubern ist die Ladung dann verbraucht.
- Manche Angriffe und Effekte lösen keinen Knockback aus.
- **Gift-Ticks** lösen weder Knockback noch Unverwundbarkeit aus.
- **Kontaktschaden:** Berührung mit Gegnern verursacht Schaden. Während der Unverwundbarkeit kann man durch Gegner hindurchlaufen.

## 8. Kollision und Friendly Fire

- Spieler kollidieren miteinander.
- **Pfeile:** kein Friendly Fire. Treffen sie einen Verbündeten, verschwinden sie wirkungslos. **[Test]** Ob sie stattdessen hindurchfliegen sollen.
- **Bomben:** Friendly Fire, kein Knockback.
- **Zauber:** Friendly Fire wird pro Zauber festgelegt.
- Gitter (z. B. Gefängnisgitter) lassen Pfeile durch, aber keine Spieler.
- **[Offen]** Gibt es auch das Umgekehrte: Hindernisse, die Projektile blockieren, aber Spieler durchlassen?

## 9. Höhenebenen

- High Ground und Low Ground, verbunden über Treppen.
- Wo kein Geländer ist, kann man herunterspringen, ohne Schaden zu nehmen.
- **Geradeaus fliegende Projektile** bleiben auf ihrer Ebene und treffen keine Ziele darunter.
- **Projektile mit Parabel-Flugbahn** (geworfene Bomben, schwere Gegenstände) erreichen auch tiefere Ebenen.

## 10. Räume

- **Raum-für-Raum-Bildschirme** wie bei NES-Zelda.
- Teams dürfen sich auf verschiedene Räume aufteilen; das ist oft sinnvoll.
- Ob sich Türen schließen, solange Gegner leben, ist von Raum zu Raum unterschiedlich.
- Ist **kein Spieler** im Raum, werden Gegner zurückgesetzt und voll geheilt. Besiegte Gegner bleiben besiegt, außer respawnende Typen (z. B. Bomben-Dropper).
- **[Offen]** Wer löst das Schließen der Türen aus, wenn sich das Team aufteilt, und können Teamkameraden dann noch hinein?

## 11. Gelände

- Denkbare Bodenarten: Eis, Schlamm, Wasser, Förderbänder, einseitige Kanten. Konkrete Auswahl folgt beim Rätsel- und Raumdesign.

## 12. Tod, Abgründe und Heilung

- **Sturz in einen Abgrund:** Schaden und Rückkehr zum Eingang des Raums.
- **0 HP:** 10 Sekunden zuschauen, dann Respawn am Beginn des Levels mit 5 HP. Ausrüstung bleibt erhalten.
- **[Offen]** Bedeutet „Beginn des Levels“ den Anfang der aktuellen Etage?
- **Heilung:** Tränke, Zauber und langsame Heilzonen (z. B. heilender Nebel). Regeneration dort kostet Zeit, erlaubt aber, einen Bosskampf nach einem Scheitern mit vollen HP neu zu versuchen.

## 13. Angriffs-Timing und Hit-Erkennung

### Simulation
- Alle Zeiten werden in **festen Simulationsschritten** definiert. **[Offen]** Schritte pro Sekunde (z. B. 60).

### Angriffseingabe
- Verhalten beim Drücken und Halten ist **pro Waffe** definiert:
  - **Schwert:** Drücken löst sofort den Hieb aus. Hält man die Taste, bleibt das Schwert vor dem Spieler ausgestreckt und **verursacht Schaden** (wie in Link's Awakening).
  - **Bogen:** Drücken spannt den Bogen, Loslassen schießt.
- Halten der Taste fixiert in jedem Fall die Blickrichtung.
- **[Offen]** Bewegung mit gespanntem Bogen (normal, verlangsamt, gar nicht).
- Das Standardschwert hat keine Wirbelattacke; höherstufige Schwerter könnten eine haben.
- Grundsätzlich **keine Combos**; ein oder zwei Waffen könnten ein Combo-System haben.
- Sekundär- oder Aufladeangriffe sind denkbar, aber noch nicht festgelegt.
- Angriffsgeschwindigkeit, Ausholen, aktive Phase und Erholung sind **pro Waffe** unterschiedlich; leichte Waffen schnell, schwere Waffen mit spürbarem Ausholen.
- **[Offen]** Abbrechen laufender Angriffe; nur einbauen, falls es spielerisch einen Vorteil bringt.
- **Knockback unterbricht Angriffe.**
- Einen Gegner zu treffen unterbricht den eigenen Angriff nicht.

### Zwei Hände
- Mainhand und Offhand sind **unabhängig**. Gleichzeitiges Drücken löst beide Angriffe gleichzeitig aus.
- Wegen der Gegner-Unverwundbarkeit verursachen zwei gleichzeitige Treffer am selben Ziel keinen doppelten Schaden. **Gewollt:** Zwei Waffen dienen der Kombination verschiedener Waffen (z. B. Speer + Schwert, Schwert + Wurfmesser), nicht der Schadensverdopplung.
- Während eines Zaubers ist keine andere Aktion möglich.

### Hitboxen und Reichweite
- **[Test]** Form der Hitbox. Empfehlung: **Rechtecke pro Animationsbild**, die der sichtbaren Klinge folgen. Alternative: Kreissegment. Entscheidung nach Spielgefühl, bei Gleichstand das Einfachere. Ein Debug-Modus zum Einblenden der Hitboxen wird empfohlen.

| Waffe | Reichweite | Form |
|---|---|---|
| Schwert | 1 Kachel | Bogen (Mainhand von rechts nach vorne, Offhand von links nach vorne) |
| Zweihandschwert | 1,5 Kacheln | Halbbogen |
| Speer | 2 Kacheln | nur gerade nach vorne |

- **[Test]** Trifft die Hitbox eines Hiebs eine Wand, wird der Angriff abgebrochen. Folge: In engen Gängen sind Schwerter schwächer, was akzeptiert wird.
- **[Test]** Idee dazu: Hält man die Taste, obwohl der Hieb abgebrochen wurde, wird das Schwert trotzdem gerade nach vorne ausgestreckt.
- **[Test]** Nahkampf trifft auch zwischen High und Low Ground, für Spieler und Gegner gleichermaßen. Gerade fliegende Projektile weiterhin nicht. Kann sich nach Tests ändern.
- Die meisten Gegner sind eine Kachel groß. Es gibt Gegner mit Schild oder spielerähnlichen Waffen. Größere Bosse haben bestimmte verwundbare Stellen.

### Mehrfachtreffer und Gegnerreaktion
- Ein Angriff trifft dasselbe Ziel **höchstens einmal**.
- Ein Angriff trifft beliebig viele Ziele. **[Offen]** Eventuelle Obergrenze von 3–4 Zielen.
- **Gegner haben nach einem Treffer eine Unverwundbarkeitsphase**, auch gegenüber anderen Spielern. Spieler müssen ihre Angriffe koordinieren; das ist Teil des Spiels.
- **[Test]** Dauer der Gegner-Unverwundbarkeit hängt von der Waffe ab (Dolch kürzer als Speer), eventuell proportional zum Schaden und zu den HP des Gegners.
- *Hinweis:* Die Unverwundbarkeit, die eine Waffe auslöst, sollte kürzer sein als ihr eigenes Angriffsintervall. Sonst verpufft bei schnellen Waffen jeder zweite Treffer.
- **Gegner-Knockback** hängt von Gegner und Waffe ab. Bosse und große Gegner (z. B. Oger) sind immun. Manche Waffen (z. B. Dolche, Wurfmesser) verursachen keinen Knockback.
- **Gleichzeitige Treffer:** Treffen sich Spieler und Gegner im selben Simulationsschritt, finden beide Treffer statt. *Umsetzung:* Pro Schritt zuerst alle Treffer auswerten, erst danach Knockback und Unterbrechungen anwenden, damit nicht die Verarbeitungsreihenfolge entscheidet.

### Projektile
- **Pfeile stoppen am ersten getroffenen Ziel.** Rein optisch prallen sie ab und fallen zu Boden (Verbündete, Steinwände usw.) oder bleiben etwa eine Sekunde stecken (Gegner, Holzwände usw.). Kein Einfluss aufs Spielgeschehen.
- **Zurückwerfen** hängt vom Projektil ab: Das Spiegelschild wirft z. B. Laser und manche Zauber zurück; manche Projektile lassen sich mit Schwert oder Keule zurückschlagen.
- **Zurückgeworfene Projektile** sind danach für Gegner **und** Verbündete gefährlich.
- Gegner haben untereinander kein Friendly Fire, außer durch Bomben.
- **Projektil gegen Projektil** hängt vom Projektil ab: Pfeile eher nicht, langsame große Energiekugeln schon.
- Bomben: siehe Abschnitt 2.

### Umgebung
- Waffen können Gegenstände in der Umgebung und Schalter auslösen; welche Waffe was auslöst, wird pro Objekt festgelegt.

### Treffer-Feedback
- **Kein Hitstop**, höchstens beim letzten Treffer gegen einen Boss.
- Treffer werden durch **Aufblinken und Geräusch** angezeigt. Schadenszahlen sind denkbar.
- **Gift:** Der Gegner blinkt grün.
- **[Offen]** Wie Crits erkennbar gemacht werden.

## 14. Netzwerk – Anforderungen

*Nur Anforderungen; technische Lösungen werden im Multiplayer-Abschnitt geklärt.*

- Einsatzzweck: Spieleabend mit Kollegen. Schutz vor Cheatern hat keine Priorität.
- Ein Spieler **hostet** die Partie, die anderen treten bei (ähnlich Warcraft 3 im LAN).
- Muss im **LAN und über das Internet** funktionieren (z. B. wenn ein Kollege von zuhause mitspielt).
- Der Host ist **autoritativ**: Er entscheidet, ob Treffer zählen.
- Läuft auf Windows, Mac und Linux.
- Simulation in festen Schritten (siehe Abschnitt 13).

---

## Nächster Abschnitt

Schaden und Überleben: Schadensformel, Schadensarten, Rüstung und Resistenzen, Schaden über Zeit, Statuseffekte und Kontrolleffekte.
