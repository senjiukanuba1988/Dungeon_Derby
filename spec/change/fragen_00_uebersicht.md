# Dungeon Derby – Offene Themen: Übersicht

Grundlage: `ideas.md` und `dungeon_derby_kampfsystem.md`. Jedes Thema hat ein eigenes Fragen-Dokument im Umfang ähnlich dem Kampfsystem. Aus den Antworten entsteht pro Thema ein Entscheidungsdokument im Stil von `dungeon_derby_kampfsystem.md` (mit **[Test]** und **[Offen]**).

## Themen und empfohlene Reihenfolge

| # | Datei | Thema | Warum an dieser Stelle |
|---|---|---|---|
| 1 | `fragen_01_spielablauf.md` | Spielablauf, Teams, Geist | Legt Partiedauer, Siegbedingung und Teamregeln fest; fast alles andere hängt davon ab. |
| 2 | `fragen_02_dungeon_generierung.md` | Dungeon-Generierung und Etagenaufbau | Raumformat und Fortschrittsgraph bestimmen Rätsel, Gegnerplatzierung und Loot. |
| 3 | `fragen_03_raetsel.md` | Rätsel, Puzzle-Items, Gelände | Baut auf dem Generator auf. |
| 4 | `fragen_04_gegner_bosse.md` | Gegner und Bosse | Braucht Etagenaufbau und Kampfsystem. |
| 5 | `fragen_05_items_wirtschaft.md` | Items, Loot, Inventar, Wirtschaft | Braucht Gegner (Drops) und Etagenaufbau (Truhen, Shops). |
| 6 | `fragen_06_kampf_schaden.md` | Kampfsystem Teil 2: Schaden, Überleben, Statuseffekte, Waffenkatalog | Der im Kampfdokument angekündigte nächste Abschnitt, plus dessen offene Punkte. |
| 7 | `fragen_07_technik.md` | Technik, Netzwerk, Plattform | Die Engine-Frage sollte trotzdem **früh** beantwortet werden, siehe unten. |
| 8 | `fragen_08_praesentation.md` | Grafik, Sound, UI, Menüs | Kann parallel zu allem anderen geklärt werden. |

**Hinweis zur Technik:** Das Projekt ist in PhpStorm als PHP-Projekt angelegt. PHP eignet sich nicht für ein Echtzeit-Spiel mit Desktop-Clients. Die Wahl von Sprache und Engine (Frage 7.1) beeinflusst, wie aufwendig vieles andere wird, und sollte deshalb vor dem ersten Code stehen.

## Widersprüche zwischen den bisherigen Dokumenten

Diese Punkte tauchen auch in den jeweiligen Fragen-Dokumenten auf.

1. **Anzahl der Etagen:** `ideas.md` startet auf „floor 0“ und endet nach „level 10“ (wären 11 Etagen); das Kampfdokument sagt 10 Etagen. → Frage 1.3
2. **Begegnung der Teams:** Laut Kampfdokument begegnen sich die Teams nie. Laut `ideas.md` können sie sich beim wandernden Händler treffen, und dessen Vorrat ist zwischen beiden Teams geteilt. Das verletzt außerdem die Loot-Fairness. → Fragen 1.4 und 5.5
3. **Gegner-Skalierung:** `ideas.md` nennt einmal +10 % pro Etage und einmal +50 % von Etage 1 auf 2. → Frage 4.4
4. **Zauber-Ladungen:** Laut `ideas.md` starten Zauber beim Anlegen mit 0 Ladungen; im Kampfdokument steht dazu nichts. → Frage 6.6
5. **Fehlende Datei:** Das Kampfdokument verweist auf `combat_design_checklist.md`, die nicht im Repository liegt.
