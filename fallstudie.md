# Sieben Produkte mit KI-Agenten geliefert: was funktioniert, was nicht

[English version](case-study.md) · Stand: 11. November 2026

Zwischen Ende September und Mitte November 2026 habe ich sieben Produkte von der Idee bis zu einer lauffähigen Version gebracht. Den Code haben KI-Agenten geschrieben (Claude Code). Meine Rolle war die eines Product Owners und Projektleiters: Konzept, Spezifikation, Backlog, Prioritäten, Abnahme.

Dieser Text beschreibt, was dabei getragen hat und was nicht. Die Zahlen stammen aus den Repositories; wie sie gezählt sind, steht am Ende.

## Die Projekte in Zahlen

| Projekt | Zeitraum | Tage mit Commits | Commits | Automatische Tests | Stand |
| --- | --- | --- | --- | --- | --- |
| [DerKurator AI](https://github.com/seb-nsu/DerKuratorAI) | 28.09.–09.11. | 15 | 165 | 1.048 | Version 1.6.0, Pilot offen |
| [Ideenportal](https://github.com/seb-nsu/Ideaportal) | 12.10.–01.11. | 7 | 77 | 728 | vier Releases gebaut, Klicktest offen |
| [TimeLog](https://github.com/seb-nsu/Timelog) | 19.10.–10.11. | 7 | 114 | 464 | gebaut, Gerätetests offen |
| [Bitschmiede](https://github.com/seb-nsu/Bitschmiede) | 29.10.–04.11. | 5 | 201 | 739 | spielbar, Spieltest offen |
| [Digital-Helfer](https://github.com/seb-nsu/Digital-Helfer) | 31.10.–02.11. | 3 | 20 | – | in Benutzung |
| [Cloud Price Information](https://github.com/seb-nsu/Cloud-Price-Information) | 06.11.–10.11. | 4 | n. a. | 88 | Version 2.1.0 |
| [Couch Quest](https://github.com/seb-nsu/Max-against-the-world) | 06.11.–10.11. | 3 | 74 | – | in Arbeit |

Zusammen sind das gut 650 Commits in sechseinhalb Wochen. Rund neun von zehn tragen den Agenten als Autor. Die Tage mit Commits sind keine Arbeitstage: Konzept, Review und Abnahme tauchen in dieser Spalte nicht auf.

## Das Vorgehen

Jedes Projekt lief in derselben Reihenfolge:

1. **Konzept:** Zielgruppe, Nutzen, Umfang und was bewusst nicht dazugehört.
2. **Spezifikation:** Anforderungen mit Kennung und Akzeptanzkriterien, bei Rechenlogik mit von Hand gerechneten Beispielen.
3. **Bau in Etappen:** je Etappe ein Auftrag an den Agenten, ein Pull Request, eine Abnahme.
4. **Review von außen:** Ein zweites Modell prüft Konzept oder Ergebnis, ohne den bisherigen Verlauf zu kennen.
5. **Einarbeitung:** Jeder Befund wird einer Story zugeordnet, bewusst zurückgestellt oder als offener Punkt geführt.

## Was funktioniert hat

**Eine Spezifikation mit Kennungen.** Für Bitschmiede gibt es 14 Spezifikationen mit 603 Regeln und 203 Testfällen, jede mit eigener Kennung. Der Agent nennt die Kennung im Test, im Code und im Commit. Dadurch konnte ich bei der Abnahme fragen „wo ist PRD-R31 umgesetzt?“ und bekam eine Stelle statt einer Erklärung. Wo sich zwei Spezifikationen widersprachen, entschied eine Abgleichstabelle mit 47 Einträgen, einmal und für alle sichtbar.

**Review als eigener Schritt.** Das dritte Review des Bitschmiede-Konzepts fand 65 Widersprüche und Rechenfehler, bevor eine Zeile Code existierte, darunter eine Spanne, deren Mitte dem Spieler den wahren Wert verraten hätte. Beim Ideenportal brachten zwei Reviews 94 Vorschläge. Daraus wurden 50 neue oder geänderte Stories und eine neue Positionierung: KI-Ausarbeitung ist 2026 Marktstandard und taugt nicht als Alleinstellung. Diesen Befund hätte ich aus dem eigenen Konzept heraus nicht gesehen.

**Regeln statt KI-Urteil.** In DerKurator rechnet und entscheidet die KI nicht. Zahlen kommen aus Code, das Votum aus einem Regelwerk, das Sprachmodell versteht die Frage und erklärt das Ergebnis. Das machte das Produkt prüfbar: Die Auswertung über 119 Fälle zeigt 89 % richtige Voten und, wichtiger, kein einziges falsches GO. Ein Produkt, dessen Kern ein Sprachmodell ist, hätte ich so nicht abnehmen können.

**Das Regelwerk zuerst.** Bei TimeLog stand die Berechnung der Arbeitszeit mit 35 Testfällen, bevor es Server oder App gab. Alle Clients nutzen dasselbe Regelwerk. Die zwölf fachlichen Entscheidungen dahinter, etwa ob Standby ein Arbeitsende ist, sind mit den verworfenen Varianten dokumentiert.

**Offene Fragen sichtbar halten.** Die Regel für den Agenten lautete: Fehlt etwas in der Spezifikation, nimm die kleinste plausible Annahme, markiere sie im Code und trage sie in eine Liste ein. In Bitschmiede stehen 169 solche Markierungen im Code und 353 Einträge in der Liste. Das klingt nach viel und ist es auch. Aber jede davon wäre sonst eine stille Entscheidung des Agenten gewesen.

## Was nicht funktioniert hat

**„Gebaut“ ist nicht „abgenommen“.** Das ist der wichtigste Befund. Vier der sieben Projekte enden an derselben Stelle: Der Code steht, die Tests sind grün, und der Schritt mit echten Menschen fehlt. Bei TimeLog brauchen sechs von zwölf Zeilen der Statusübersicht noch einen Test an echten Geräten oder mit echten Konten. Bitschmiede wartet auf den Spieltest mit zwei Personen, das Ideenportal auf den Klicktest mit sieben bis acht. Die Agenten haben das Bauen um ein Vielfaches beschleunigt, das Prüfen mit Menschen gar nicht. Der Engpass ist gewandert, und ich habe zu lange weitergebaut, statt ihn aufzulösen.

**Der Umfang wächst, weil Bauen billig ist.** Das Ideenportal hat einen Backlog von 146 Stories in vier Releases. Gebaut waren alle vier Releases, soweit es ohne bezahlte Dienste und Nutzer geht, innerhalb weniger Tage nach dem Konzept. Im klassischen Projekt hätte nach Release 1 ein Pilot gestanden und die Releases 2 bis 4 verändert. So gibt es ein Produkt mit Firmen-Login, Schnittstellen und Wirkungsmessung, das noch kein Nutzer gesehen hat. Ein Teil davon ist vermutlich am Bedarf vorbei gebaut, und ich weiß nicht, welcher.

**Zahlen, die nur Nutzer klären.** In Bitschmiede sind viele Balancing-Werte Schätzungen. Automatische Simulationsläufe zeigen, ob die Wirtschaft kippt. Ob das Spiel Spaß macht, zeigen sie nicht. Dasselbe gilt für Fristen und Schwellen im Ideenportal und für die Pausenlogik in TimeLog.

**Dokumentation läuft dem Code davon.** Bei dem Tempo veralten Beschreibungen in Tagen. Mehrere README-Dateien nannten überholte Zahlen oder einen alten Stand. Ein Review fand beim Ideenportal Stellen, an denen Architekturentscheidung und Code nicht mehr übereinstimmten.

**Aufräumen für die Veröffentlichung.** Die Repositories waren nicht für fremde Augen gebaut. Vor der Veröffentlichung mussten persönliche Angaben, echte Domains und Demodaten mit Bezug zu echten Organisationen ersetzt werden. Bei drei Projekten ging dabei die Commit-Historie verloren, also genau der Beleg für das Vorgehen, das dieser Text beschreibt.

## Was ich beim nächsten Projekt anders mache

1. **Nach dem ersten Release wird nicht weitergebaut, bevor fünf Menschen es benutzt haben.** Der Test mit Nutzern ist ein Tor im Plan und kein Punkt auf der Liste der offenen Aufgaben.
2. **Der Umfang richtet sich nach dem, was ich abnehmen kann.** Wie viel sich bauen lässt, ist dafür kein Maßstab mehr. Ein Release, das ich nicht in einer Woche selbst durchprüfen kann, ist zu groß.
3. **Das Repository ist vom ersten Tag an öffentlich gedacht.** Keine persönlichen Angaben, keine echten Namen in Demodaten, dann bleibt die Historie erhalten.

Das einzige der sieben Projekte, das heute benutzt wird, ist das kleinste. Den Digital-Helfer habe ich in drei Tagen für meine Eltern gebaut und nach ihren Rückmeldungen umgebaut: Die Spotify-Anleitungen wanderten vom iPhone auf den PC, die Mediathek-Anleitung passt jetzt zu ihrem Fernseher. Es hat 20 Commits, keine automatischen Tests und zwei Nutzer.

## Wie die Zahlen gezählt sind

- **Commits und Tage mit Commits:** aus der Git-Historie des Hauptzweigs, einschließlich Merges. Bei DerKurator, Bitschmiede, Ideenportal und Digital-Helfer aus der ursprünglichen Historie vor der Veröffentlichung, weil die öffentlichen Repositories neu aufgesetzt wurden. Für Cloud Price Information liegt die ursprüngliche Historie nicht mehr vor.
- **Anteil der Agenten:** Autor der Commits ohne Merges, 518 von 564.
- **Automatische Tests:** gezählte Testfunktionen im Quelltext am 11.11.2026. Parametrisierte Tests zählen einmal; ein Testlauf meldet deshalb höhere Zahlen.
- **Regeln, Testfälle, offene Fragen (Bitschmiede):** eindeutige Kennungen in `docs/spec/`, Einträge in `docs/OFFENE-FRAGEN.md`, Markierungen `ANNAHME:` im Quelltext.
- **Review-Vorschläge (Ideenportal):** eindeutige Kennungen in `docs/05-review-v3/`; Stories aus der Datei `einarbeitung.md`.
- **Voten (DerKurator):** `docs/evals/EVAL_REPORT.md`, Lauf ohne Sprachmodell.
