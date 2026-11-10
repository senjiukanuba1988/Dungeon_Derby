# Dungeon Derby – Fragen: Technik, Netzwerk und Plattform

Anforderungen aus dem Kampfdokument (Abschnitt 14): Host autoritativ, LAN und Internet, Windows/Mac/Linux, feste Simulationsschritte, Cheatschutz unwichtig.

## 7.1 Sprache und Engine

1. Womit wird das Spiel gebaut? Das Projekt ist derzeit als PHP-Projekt in PhpStorm angelegt; PHP passt nicht zu einem Echtzeit-Spiel. Mögliche Richtungen:
   - **Godot** (kostenlos, gute 2D-Unterstützung, Export für alle drei Systeme, eingebautes Netzwerk),
   - **Unity** (C#, sehr verbreitet, Lizenzbedingungen beachten),
   - **Browser-Spiel** mit TypeScript (keine Installation; Host bräuchte einen kleinen Server),
   - **Framework ohne Editor** wie MonoGame (C#), LÖVE (Lua) oder Bevy (Rust).
2. Welche Sprachen kennst du schon gut, und welche würdest du gerne lernen?
3. Wie wichtig ist ein visueller Editor (für Räume, Animationen) im Vergleich zu reinem Code?
4. Soll die IDE PhpStorm bleiben, oder ist ein Wechsel (z. B. Rider, VS Code, Godot-Editor) in Ordnung?

## 7.2 Netzwerkmodell

1. Synchronisation: Der Host schickt regelmäßig den Spielzustand (einfacher, mehr Daten), oder alle simulieren gleichzeitig und tauschen nur Eingaben aus (Lockstep, weniger Daten, verlangt exakten Determinismus)?
2. Soll die eigene Bewegung sofort reagieren, auch wenn der Host weit weg ist (Vorhersage beim Client), oder ist eine kleine Verzögerung über das Internet akzeptabel?
3. Welche Verzögerung ist über das Internet noch akzeptabel (z. B. 100 ms)?
4. Laufen beide Teams in einer Simulation auf dem Host (zwei Dungeon-Kopien in einem Prozess)?

## 7.3 Verbindung herstellen

1. Ist es akzeptabel, dass der Host im Router einen Port freigibt, oder muss es ohne Einrichtung funktionieren?
2. Falls ohne Einrichtung: Relay-Server (kostet evtl. Geld, muss betrieben werden), NAT-Punching, Steam-Netzwerk, oder ein VPN-Tool wie Tailscale/ZeroTier, das Kollegen installieren?
3. LAN: Sollen Spiele im lokalen Netz automatisch gefunden werden, oder gibt man die IP-Adresse ein?
4. Wie wird sichergestellt, dass alle dieselbe Spielversion haben?

## 7.4 Vertrieb und Updates

1. Wie bekommen die Kollegen das Spiel: Download-Link, itch.io, Steam, selbst bauen?
2. Wie werden Updates verteilt?
3. Ist das Repository öffentlich oder privat? Unter welcher Lizenz?
4. Mac: Nicht signierte Programme werden blockiert. Ist eine Anleitung zum Umgehen akzeptabel, oder soll signiert werden (Apple-Entwicklerkonto kostet Geld)?

## 7.5 Generierung und Determinismus

1. Generiert nur der Host den Dungeon und schickt ihn an die Clients, oder generiert jeder aus demselben Seed? (Letzteres verlangt identische Ergebnisse auf allen Systemen.)
2. Wie werden die geseedeten Zufallsgeneratoren pro Item (Kampfdokument, Abschnitt 2) im Netzwerk synchron gehalten?

## 7.6 Speichern

1. Muss eine Partie speicherbar sein (siehe Frage 1.1.3)?
2. Sollen Partien als Wiederholung aufgezeichnet werden können?

## 7.7 Entwicklung und Tests

1. Welche Debug-Werkzeuge werden gebraucht? Vorschläge: Hitboxen anzeigen (im Kampfdokument empfohlen), Etage überspringen, Seed wählen, Unverwundbarkeit, alle Items geben.
2. Wie wird mit wenigen Leuten getestet: mehrere Fenster auf einem PC, Bots als Mitspieler?
3. Sollen Generator und Regeln automatisch getestet werden (Unit-Tests, Lösbarkeitsprüfung über viele Seeds)?
4. Was soll der erste spielbare Prototyp enthalten? Vorschlag: ein Raum, ein Spieler, Bewegung, Schwert, ein Gegnertyp; danach Netzwerk mit zwei Spielern; danach Generator.

## 7.8 Darstellung und Systemanforderungen

1. Feste interne Auflösung (Pixelart) mit ganzzahliger Skalierung, oder freie Skalierung?
2. Fenster, Vollbild oder beides?
3. Gibt es Mindestanforderungen (alte Laptops von Kollegen)?
4. Frei belegbare Tasten?
5. Controller-Unterstützung später denkbar, oder bewusst nur Tastatur?
