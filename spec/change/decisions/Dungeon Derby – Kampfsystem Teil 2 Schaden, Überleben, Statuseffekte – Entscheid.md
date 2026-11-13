# Dungeon Derby – Kampfsystem Teil 2: Schaden, Überleben, Statuseffekte – Entscheidungen

Nov 12, 2026 · @Matthias Dierberger

Alle Fragen aus `fragen_06_kampf_schaden.md` sind beantwortet. Das Dokument setzt `dungeon_derby_kampfsystem.md` fort und entscheidet dessen offene Punkte, soweit sie nicht in anderen Dokumenten stehen.

Markierungen: **\[Test\]** = Richtung festgelegt, endgültiger Wert wird im Playtest entschieden. **\[Offen\]** = noch nicht entschieden. **\[Später\]** = vorgemerkt, aber nicht für die erste Version geplant.

**Größenordnung der Zahlen: alles mal 10.** Bei 20 Start-HP und Treffern um 2 verschwinden Prozentwerte durch das Aufrunden (30 % weniger von 2 ergibt wieder 2), und die Etagenkurve springt unregelmäßig. Deshalb gilt: 200 Start-HP, und alle bisher genannten Schadens- und HP-Werte werden mit 10 multipliziert. Die Regel „immer aufrunden, mindestens 1“ bleibt.

## 6.1 Schadensformel

- **Ganze Zahlen** für alle HP- und Schadenswerte. Intern wird mit Kommazahlen gerechnet, gerundet wird am Ende.
- **Waffenschaden:** Ein gewöhnliches Schwert der Stufe 2 macht 50 Schaden, etwa ein Viertel der Spieler-HP. Stufe 1 = 25, Stufe 10 etwa 107 (Kurve +10 % pro Stufe). Spieler sind vom Schaden her zu ihren eigenen HP ausbalanciert, damit Bosse mit Gedankenkontroll-Mechanik sowie Fallen und Bomben (die Spieler und Gegner gleich treffen) funktionieren. **\[Test\]**
- **Rüstung:** Grundsätzlich prozentual. Manche Gegenstände haben zusätzlich eine feste Reduktion; sie hilft gegen viele kleine Angriffe (z. B. einen Fledermausschwarm), aber wenig gegen große.
- **Zusammenrechnen:** Prozentuale Reduktionen von Rüstung, Kopfbedeckung und Schild wirken multiplikativ (40 % und 33 % ergeben etwa 60 %, nicht 73 %). Keine Obergrenze, gegebenenfalls im Playtest nachjustieren. **\[Test\]**
- **Mindestschaden:** Immer mindestens 1.

**Reihenfolge:**

```latex
\text{Schaden} = \max\left(1,\; \left\lceil \text{Roh} \cdot \prod_i (1 - r_i) \right\rceil - F\right)
```

Dabei sind die r die prozentualen Reduktionen und F die Summe der festen Reduktionen.

**Anzeige:** Eine HP-Leiste direkt an der eigenen Figur und über den Teamkameraden, damit man den Zustand auf einen Blick sieht. Die genaue Zahl steht nur im HUD, nicht über der Figur.

## 6.2 Schadensarten und Resistenzen

**Schadensarten:** Physisch, Feuer, Eis, Gift und Magie. Magie umfasst Magiekugeln, Zauber und Laser. **\[Später\]** Blitz.

**Zweck:** Resistenzen und Statuseffekte, keine Rätselwirkung (die bleibt den Puzzle-Items vorbehalten).

**Chance auf Statuseffekte:**

- Gegnerangriffe lösen ihren Effekt immer aus, ohne Würfeln: Ein Feuerball setzt immer in Brand, eine Giftspucke vergiftet immer.
- Spieler-Items lösen Effekte über Zusatzeffekte mit einer Chance von 20 bis 50 % aus, als geseedeter Pseudozufall pro Item. **\[Test\]**

**Resistenzen und Rüstung:**

- Resistenzen sind prozentual pro Schadensart. Gegner können auch ganz immun sein, Spieler nicht.
- Rüstung wirkt voll gegen physischen Schaden und halb gegen alle anderen Arten (aus 40 % werden 20 %). Feste Reduktionen wirken nur gegen physischen Schaden.
- Alles wird multiplikativ verrechnet wie in 6.1.

**Quellen für Resistenzen:** Zusatzeffekte auf Rüstung, Schild und Kopfbedeckung, Grundtypen wie der Feuerumhang und das Gegengift (30 Sekunden Giftimmunität).

**Schwächen bei Gegnern:** Am Aussehen und Thema ablesbar (Eiswesen bläulich und anfällig für Feuer, Feuerwesen umgekehrt). Ein Treffer gegen eine Schwäche blinkt stärker und klingt anders, ein Treffer gegen eine Resistenz klingt dumpf und blinkt grau.

## 6.3 Statuseffekte

| Effekt | Wirkung | Quelle, Dauer |
| --- | --- | --- |
| Gift | 2 % der maximalen HP pro Sekunde | Dauer je nach Angriff |
| Brennen | Pro Sekunde 20 % des auslösenden Treffers, ohne direkten Schaden (Fackel, Brandzauber) ein fester Wert nach Etagenkurve | 3 Sekunden |
| Verlangsamung | 40 % langsamer | etwa 3 Sekunden |
| Einfrieren | bewegungsunfähig | siehe Kontrolleffekte |
| Betäubung | handlungsunfähig | siehe Kontrolleffekte |
| Rüstung geschwächt | 20 % weniger Reduktion | 10 Sekunden, z. B. durch Säure |

Alle Werte **\[Test\]**. Keine Blindheit (im Multiplayer schwer fair umzusetzen); „Schaden erhöht“ gibt es als Krafttrank.

- **Erneut zugefügt:** Die Dauer wird zurückgesetzt, nicht verlängert und nicht verstärkt.
- **Kontrolleffekte** (Einfrieren, Betäubung): Normale Gegner höchstens 1,5 Sekunden. Bosse legen die Dauer selbst fest, z. B. eine längere Betäubung, auf die ein gut sichtbar ausgeholter Spezialangriff folgt, oder „eingefroren, bis ein Teamkamerad hilft“ (wie man befreit, wird pro Boss festgelegt). Danach 3 Sekunden Immunität gegen denselben Kontrolleffekt.
- **Verlangsamung** wird jedes Mal neu angewendet, ohne Immunität.

**Bosse und Minibosse:**

- Gift wirkt mit einem Viertel der normalen Stärke.
- Gegen Verlangsamung, Einfrieren und Betäubung sind sie immun, außer eine Boss-Mechanik sieht es vor (z. B. ein geworfener Stein betäubt den Boss kurz, damit man eine Schwachstelle treffen kann).

**Anzeige:** Die Figur färbt sich je nach Effekt (grün bei Gift, flackernd orange bei Brennen, bläulich bei Verlangsamung, Eisblock beim Einfrieren, kreisende Sterne bei Betäubung). Für den eigenen Spieler zusätzlich Symbole mit Restdauer im HUD, nicht über der Figur.

**Aufheben:** Gegengift hebt Gift auf, flaches Wasser löscht Brennen, sonst endet alles mit der Zeit. Heiltränke entfernen keine Effekte.

## 6.4 Heilung und Tod

- **Gegenseitig heilen:** Über Zauber (z. B. Heilwelle) und Relikte. Tränke kann man nicht werfen, sie wirken nur auf einen selbst.
- **Wiederbeleben vor Ablauf der 10 Sekunden:** Mit der Phönixfeder (aus 5.6).
- **Heilzonen:** 5 % der maximalen HP pro Sekunde, eventuell langsamer. **\[Test\]**
- **Respawn:** Im Startraum der Etage, auf der man gestorben ist.
- **Verluste beim Tod:** Nichts außer Zeit. Gold bleibt in der Teamkasse, Items und Schlüssel behält man.
- **Unverwundbar nach Respawn:** 2 Sekunden.

## 6.5 Werte für Treffer

- **Unverwundbarkeit nach einem Treffer:** 1 Sekunde, die Figur blinkt. Gift und Brennen ticken weiter und lösen selbst keine Unverwundbarkeit aus.
- **Sturz in einen Abgrund:** 10 % der maximalen HP, und der Sturz dauert etwa 2 bis 3 Sekunden, kostet also auch Zeit. Tiefes Wasser, Lava (plus Brennen) und die Wache aus 4.2 machen denselben Anfangsschaden. **\[Test\]**
- **Knockback und Ausrüstung:** Schwere Rüstung verringert den Rückstoß, ebenso der Zusatzeffekt Rückstoßresistenz.

## 6.6 Waffen- und Zauberkatalog

**Waffen:** Rätselnutzen haben Waffen nicht, außer dass jede Nahkampfwaffe Kristalle anschlagen kann.

| Waffe | Hände | Reichweite | Tempo | Besonderheit | Sonderangriff |
| --- | --- | --- | --- | --- | --- |
| Schwert | 1 | kurz, Bogen nach vorn | mittel | ausgewogen, schlägt Magiekugeln zurück | Wirbelattacke |
| Dolch | 1 | sehr kurz | schnell | höhere Crit-Chance von hinten | schnelle Dreierkombo |
| Keule | 1 | kurz | langsam | starker Rückstoß, schlägt Magiekugeln zurück | Bodenstampfer, betäubt kleine Gegner kurz |
| Wurfmesser | 1 | Fernkampf | schnell | wenig Schaden, gut als Offhand | – |
| Zweihandschwert | 2 | weiter Halbkreis | langsam | hoher Schaden, trifft alles im Bogen | – |
| Speer | 2 | lang, nur geradeaus | mittel | gut gegen Gegner hinter Hindernissen | Sturmstoß nach vorn |
| Bogen | 2 | Fernkampf | mittel | Puzzle-Item, Pfeile regenerieren | – |

- **Fernkampfwaffen** (auch Wurfmesser) erscheinen erst in Bereichen hinter dem Fundort des Bogens.
- **Sonderangriffe** werden durch Gedrückthalten der Angriffstaste aufgeladen und haben eine Abklingzeit je nach Waffentyp. Ein Geräusch zeigt an, wann der Angriff voll aufgeladen ist. **\[Test\]**
- **Offhand:** Dieselbe Wirkung wie in der Mainhand, nur eine andere Taste. Bei Schwert und Keule kommt der Schlag aus der Offhand von der anderen Seite. Schilde gehen nur in die Offhand.

**Zauber:** Zaubern heißt stillstehen; Zauber haben Ladungen.

| Zauber | Wirkung | Ladungen | Aufladen |
| --- | --- | --- | --- |
| Feuerball | Feuerschaden mit Brennen | 3 | eine alle 10 s |
| Magiegeschoss | schnelles Magieprojektil | 5 | eine alle 5 s |
| Heilwelle | heilt Verbündete im Umkreis um 20 % ihrer maximalen HP | 1 | 30 s |
| Schutzzauber | Verbündete im Umkreis nehmen 5 s lang 30 % weniger Schaden | 1 | 30 s |

Alle Werte **\[Test\]**.

- Zauber haben kein Friendly Fire; Bomben und Fallen schon.
- Zauber starten beim Anlegen mit 0 Ladungen, auch beim Wechsel zwischen zwei Zaubern.

**Schilde und Kopfbedeckungen:**

- Holzschild: wenig Reduktion, kein Nachteil.
- Eisenschild: mittlere Reduktion, etwas langsamer.
- Turmschild: hohe Reduktion, deutlich langsamer; der Tank-Schild.
- Spiegelschild: Puzzle-Item, wirft Magie zurück.
- Alle Schilde blocken Projektile von vorn.
- Kopfbedeckungen: Lederkappe (wenig Schutz), Helm (mehr Schutz), Zauberhut (Zauberboni statt Schutz).

## 6.7 Gegner-Seite

**Dieselben Regeln:** Gegner haben Rüstung (prozentual und fest), Resistenzen und Statuseffekte nach denselben Formeln. Unterschiede: Gegner können immun sein, und für Bosse gelten die Ausnahmen aus 6.3.

**HP-Werte** (Schwert der Stufe 2 = 50 Schaden):

| Gegner | HP auf Etage 2 |
| --- | --- |
| Normal | 100 bis 200 (2 bis 4 Schwerttreffer); Etage 1 die Hälfte |
| Robust (z. B. Oger) | 300 bis 500 |
| Elite | doppelt so viel wie die normale Variante |
| Boss | grob 30- bis 50-mal ein normaler Gegner, verteilt auf mehrere Verwundbarkeitsfenster |

Alles skaliert mit der Kurve (+10 % pro Etage) und der Teamgröße. **\[Test\]**

## 6.8 Offene Punkte aus dem Kampfdokument

1. **HP beim An- und Ablegen:** Zusätzliche Max-HP kommen leer dazu, beim Ablegen wird auf das neue Maximum gekappt.
2. **Getragenes fallen lassen bei Treffer:** Dinge in den Händen (Steine und Krüge vom Kraft-Armband, Bomben) fallen vor einem auf den Boden. Stabile Dinge wie Felsen bleiben liegen und können wieder aufgehoben werden; zerbrechliche wie Krüge sind danach weg. Das Inventar ist nicht betroffen.
3. **Knockback über Kanten:** Ja, Spieler und Gegner können über ungesicherte Kanten gestoßen werden; es gelten die normalen Sturzregeln.
4. **Hindernisse für Projektile:** Gitter lassen Projektile durch, aber keine Spieler. Kraftfelder lassen Spieler durch, aber keine Projektile.
5. **Türen bei Arenen:** **\[Offen\]** Entweder wie beim Boss (Eingangsbereich, Türen schließen sich, sobald jemand ihn verlässt; wer draußen ist, wartet) oder Fliehen erlaubt, wobei sich die Arena zurücksetzt.
6. **Simulationsschritte:** 60 pro Sekunde. Wichtig, damit beide Dungeons bei gleichen Eingaben gleich ablaufen und die Netzwerk-Synchronisierung funktioniert.
7. **Bewegung mit gespanntem Bogen:** Verlangsamt, etwa auf die Hälfte.
8. **Angriffe abbrechen:** Normale Angriffe nicht. Aufladeangriffe durch Loslassen vor dem vollen Aufladen; voll aufgeladen löst Loslassen den Angriff aus.
9. **Ziele pro Angriff:** Keine Obergrenze.
10. **Crits:** Kräftigeres Aufblinken, eigenes Geräusch und eine minimal längere Trefferpause. Falls Schadenszahlen angezeigt werden, erscheinen Crits größer und gelb.

## Offene Punkte und Querverweise

**Offen:**

- [ ] Türregel bei Arenen (6.8.5)
- [ ] Simulationsschritte pro Sekunde – entschieden: 60 (6.8.6)
- [ ] Abklingzeiten der Sonderangriffe pro Waffentyp

**Auswirkungen auf andere Dokumente:**

- **Kampfsystem (Markdown-Datei):** Start-HP sind jetzt 200, alle Werte dort mal 10 (z. B. Gift). Die offenen Punkte aus Abschnitt 12 sind hier in 6.8 entschieden.
- **Gegner und Bosse 4.5:** Heilherz 40 statt 4 HP (dort angepasst).
- **Items 5.1:** Relikt-Werte mal 10: Heilung 10 HP alle 10 Sekunden, Schutzschild absorbiert bis zu 40 (dort angepasst).
- **Items 5.6:** Bombenschaden gegen Spieler (20 % der maximalen HP) und Heiltränke sind prozentual und bleiben unverändert.
