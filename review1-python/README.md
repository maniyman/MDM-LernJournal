# Review 1 Python

## Beurteiltes Projekt

|       | Bitte ausfüllen |
|-------|-----------------|
| Review von (ZHAW-Kürzel) | djeladri |
| Review durch (ZHAW-Kürzel) | maniyman |
| Datum Review, von/bis | 25.03.2025, 16:15-17:00|

## Review

| Thema                                                                      |   Skala | Mängel*                                                                                             | Verbesserungsmöglichkeiten*                                                                                         |
|:---------------------------------------------------------------------------|--------:|:----------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------------------------------------------------------|
| Datenquelle klar definiert (Projekt 2: zusätzlich Abgrenzung zu Projekt 1) |       1 | Datenquelle ist vorhanden, aber nicht sehr ausführlich dokumentiert.                                | Klare Beschreibung der Datenquelle in README oder Dokumentation ergänzen; Abgrenzung zu Projekt 1 explizit angeben. |
| Scraping vorhanden                                                         |       2 | Scraping-Skript ist vorhanden und funktioniert, könnte aber robuster sein.                          | Fehlertoleranz und Logging verbessern; Beispielausführung oder Demo-Notebook hinzufügen.                            |
| Scraping automatisiert                                                     |       1 | Teilweise automatisiert, aber es braucht manuelle Anpassungen (z.B. Konfiguration, Start per Hand). | CLI-Tool oder Automatisierung per Cronjob/Workflow ergänzen.                                                        |
| Datensatz vorhanden                                                        |       2 | Datensatz wird aus Scraping generiert und liegt vor.                                                | Eventuell Beispiel-Datensatz im Repository ablegen, damit man ohne Scraping starten kann.                           |
| Erstellung Datensatz automatisiert, Verwendung Datenbank                   |       1 | Erstellung halbautomatisch, Datenbank nicht verwendet.                                              | Automatisierte Speicherung in eine SQLite- oder PostgreSQL-Datenbank einbauen.                                      |
| Datensatz-Grösse ausreichend, Aufteilung Train/Test, Kennzahlen vorhanden  |       1 | Datensatzgröße eher klein; Train/Test-Aufteilung kaum dokumentiert; keine klaren Kennzahlen.        | Datensatz vergrößern, Aufteilung und Kennzahlen (z. B. Verteilung, Anzahl Beispiele) explizit dokumentieren.        |
| Modell vorhanden                                                           |       2 | Einfaches Modell vorhanden und trainiert.                                                           | Komplexität erhöhen oder mehr Modelle vergleichen.                                                                  |
| Modell-Versionierung vorhanden (ModelOps)                                  |       0 | Keine Modellversionierung erkennbar.                                                                | Einsatz von DVC, MLflow oder zumindest Benennung von Modellversionen.                                               |
| App: auf lokalem Rechner gestartet und funktional                          |       2 | App startet lokal und funktioniert, aber Setup kann etwas holprig sein.                             | Installationsanleitung präzisieren, evtl. Setup-Skript ergänzen.                                                    |
| App: mehrere unterschiedliche Testcases durch Reviewer ausführbar          |       1 | Einfache Testcases möglich, aber es fehlen vorbereitete Szenarien.                                  | Beispiel-Testcases dokumentieren; eventuell UI verbessern.                                                          |
| Deployment: Falls bereits vorhanden, funktional und automatisiert          |       0 | Kein Deployment vorhanden.                                                                          | Deployment z. B. per Streamlit Share, Heroku oder Docker-Compose ergänzen.                                          |
| Code: Git-Repository vorhanden, Arbeiten mit Branches / Commits            |       2 | Git-Repository ist vorhanden; Branch-Nutzung eher begrenzt.                                         | Branch-Strategie nutzen (z. B. feature-branches, pull requests), Commit-Messages verbessern.                        |
| Code: Dependency Management, Dockerfile, Build funktional                  |       1 | Requirements-Datei vorhanden; kein Dockerfile; Build nicht automatisiert.                           | Dockerfile erstellen, CI/CD-Workflow ergänzen, Requirements in Pipfile oder poetry migrieren.                       |

* wenn fehlend: mögliche Schwierigkeiten und Lösungen besprechen

## Skala

| Skala | Beschreibung       |
|-------|--------------------|
| 0     | fehlt              |
| 1     | mit Lücken        |
| 2     | alles vorhanden   |
| 3     | übertroffen       |

## Hinweise

Der Projekt-Review fliesst nicht in die Beurteilung der Leistungsnachweise ein, soll aber dem Studierenden dazu dienen, bis zur Abgabe noch Verbesserungsmöglichkeiten zu erkennen. Der Review *des fremden Projektes* muss als Teil des *eigenen* Lernjournals abgegeben werden.
