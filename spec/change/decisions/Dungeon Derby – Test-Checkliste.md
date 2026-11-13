# Dungeon Derby – Test-Checkliste

Nov 12, 2026 · @Matthias Dierberger

Hier stehen alle Punkte, die in den Entscheidungsdokumenten mit **\[Test\]** markiert sind: Die Richtung ist festgelegt, der endgültige Wert soll im Playtest entschieden werden. Nach einem Testspiel bringst du dieses Dokument mit, und wir gehen die Punkte im Interview durch: Was hat sich gut angefühlt, was nicht, was ändern wir. Abgehakt wird, was bestätigt oder angepasst ist.

Die Punkte aus `dungeon_derby_kampfsystem.md` und den beiden technischen Dokumenten sind noch nicht enthalten und werden später ergänzt.

## Spielablauf, Teams und Geist (Dokument 1)

- [ ] **Geist-Punkteskala (1.7):** Etwa 1 Chaospunkt pro Sekunde verursachter Verzögerung, Umrechnung in Bonuszeit etwa 8:1, höchstens 30 Sekunden. Fühlt sich der Ausgleich fair an?

## Dungeon-Generierung (Dokument 2)

- [ ] **Partiedauer und Content-Budget (1.1, 2.2):** Richtwert 90 Minuten. Passt das Budget pro Etage dazu, und wie viele Räume ergibt das?
- [ ] **Mindestanteil an Inhaltsräumen (2.2):** Fühlen sich Etagen zu leer oder zu voll an?
- [ ] **Content-Rating und Gegner (2.2):** Soll das Rating mit den zufällig gewählten Gegnern steigen?
- [ ] **Kettenlänge (2.3):** 2 bis 3 Schritte auf Etage 1, bis 6 bis 8 auf der letzten Etage.
- [ ] **Mindestabstand des nächsten Items (2.3):** Wie viele Räume vom Bereichseingang entfernt?
- [ ] **Mindestspielerzahl bei Rätseln (2.5):** Höchstens 4. Ist das für große Teams richtig?

## Rätsel, Puzzle-Items und Gelände (Dokument 3)

- [ ] **Renn-Stiefel (3.1):** Gegenwind, zerbröselnder Boden, rissige Säulen, Sturmangriff mit Rückstoß. Funktionieren die Effekte, sind die Säulen erkennbar?
- [ ] **Abklingzeiten der Puzzle-Items (3.1):** Von etwa 1 Sekunde bis länger, pro Item.
- [ ] **Fallenschaden (3.5):** Orientiert an einem normalen Gegnertreffer der Etage.
- [ ] **Vorrat an Rätselvorlagen (3.6):** Reicht er, damit Rätselräume einmalig pro Dungeon bleiben, oder weicht der Generator zu oft auf Kampfräume aus?

## Gegner und Bosse (Dokument 4)

- [ ] **Gegner pro Raum (4.3):** 2 bis 4 auf frühen, 4 bis 8 auf späten Etagen (Team aus 2 Spielern).
- [ ] **Skalierung mit Teamgröße (4.3):** Etwa ein Gegner mehr pro zwei zusätzlichen Spielern, +15 % HP pro Spieler über zwei; große Einzelgegner über HP.
- [ ] **Werte-Kurve (4.4):** +10 % pro Etage exponentiell, Etage 1 bei 50 %. Eventuell steiler.
- [ ] **Kontaktschaden (4.4):** Etwa halb so viel wie der Angriff.
- [ ] **Treffer bis zum Tod (4.4):** Normale Gegner 2 bis 4 Schwerttreffer, robuste 6 bis 10, Elite doppelt.
- [ ] **Heilung verschwindet (4.5):** Nach etwa 15 Sekunden.

## Items, Loot, Inventar und Wirtschaft (Dokument 5)

- [ ] **Ausrüstungsmenge (5.2):** Etwa 1,5 Teile pro Spieler und Etage. Hält die Ausrüstung mit der Gegnerkurve mit?
- [ ] **Preise (5.4):** Gewöhnliches Item der Stufe 2 = 100 Gold, Faktor 1,2 pro Stufe, verbessert ×1,5, selten ×2.
- [ ] **Goldmenge (5.7):** Etwa 50 Gold pro Spieler und Etage, Faktor 1,2 pro Etage. Zu viel oder zu wenig?
- [ ] **Tränke (5.6):** Heilung 25 % sofort bzw. 50 % über 10 s, Buffs 30 % für 30 s, Heil-Abklingzeit 10 s.
- [ ] **Trinkdauer (5.6):** Etwa eine halbe Sekunde, unterbrechbar durch Rückstoß.
- [ ] **Bomben (5.6):** Radius etwa 1,5 Kacheln, doppelter Schwertschaden gegen Gegner, 20 % der maximalen HP gegen Spieler.

## Kampfsystem Teil 2 (Dokument 6)

- [ ] **Waffenschaden (6.1):** Schwert der Stufe 2 = 50 Schaden bei 200 Spieler-HP.
- [ ] **Rüstung ohne Obergrenze (6.1):** Multiplikative Reduktionen. Wird jemand zu unverwundbar?
- [ ] **Chance auf Statuseffekte (6.2):** 20 bis 50 % bei Spieler-Items.
- [ ] **Statuseffekt-Werte (6.3):** Gift 2 %/s, Brennen 20 % des Treffers pro Sekunde für 3 s, Verlangsamung 40 %, Rüstung geschwächt 20 %.
- [ ] **Heilzonen (6.4):** 5 % der maximalen HP pro Sekunde, eventuell langsamer.
- [ ] **Sturz (6.5):** 10 % der maximalen HP plus 2 bis 3 Sekunden Zeitverlust.
- [ ] **Sonderangriffe (6.6):** Aufladezeit und Abklingzeit pro Waffentyp.
- [ ] **Zauber (6.6):** Ladungen, Aufladezeiten und Wirkungen von Feuerball, Magiegeschoss, Heilwelle und Schutzzauber.
- [ ] **Gegner-HP (6.7):** Normal 100 bis 200, robust 300 bis 500, Boss 30- bis 50-mal normal (Etage 2).
