# Lernjournal 1 Python

## Repository und Library

| Repository (URL)  | https://github.com/maniyman/Lernjournal-1-Bildverarbeitung-Python |
|-------------------|-------------------------------------------------------------------|
| Kurze Beschreibung der App-Funktion | Web-App zum Hochladen von Bildern mit Analyse (Größe, Modus, Farbanzahl) |
| Verwendete Library aus PyPi (Name) | Flask |
| Verwendete Library aus PyPi (URL) | https://pypi.org/project/Flask/ |
| Verwendete Library aus PyPi (Name) | Pillow |
| Verwendete Library aus PyPi (URL) | https://pypi.org/project/Pillow/ |

Das Projekt wurde in einer sauberen Verzeichnisstruktur aufgebaut, die sowohl Backend (Flask-App), Frontend (HTML, JS) als auch die Konfigurationsdateien umfasst. Die Library-Verwaltung erfolgt über `requirements.txt`, welche mit `pip freeze` erzeugt wurde.

![Projektstruktur im Explorer](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/RepoLib1.jpg?raw=true)
> 📁 *Die Abbildung zeigt die strukturierte Ordneransicht im Projektverzeichnis. Zu sehen sind u. a. die `app.py`, der `web/`-Ordner mit HTML und JavaScript sowie die `requirements`-Dateien zur Abhängigkeitsverwaltung.*

![Erstellung der requirements.txt](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/RepoLib2.jpg?raw=true)
> ⚙️ *Hier ist der Terminal-Befehl zur Erstellung der `requirements.txt` zu sehen – ein essenzieller Schritt für Deployment und Reproduzierbarkeit auf anderen Systemen.*

---

## App, Funktionalität

* Flask Backend mit POST-Endpunkt `/analyze` zur Bildverarbeitung
* Web-Frontend mit HTML + Bootstrap
* JavaScript sendet das Bild via Fetch an Backend
* Rückgabe erfolgt als JSON mit Bilddetails (Größe, Farbinformationen)

Die folgende Abbildung zeigt die lokale Version der Bildanalyse-Web-App im Browser unter `http://127.0.0.1:8000`.

![Bildanalyse lokale App](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/App1.jpg?raw=true)
> 🖼️ *Der Benutzer kann ein Bild auswählen und per Klick auf „Bild analysieren“ eine Analyse starten. Die Analyse erfolgt serverseitig in Python mit Hilfe von Flask und Pillow.*

---

### 🧪 **Lokale Tests**

Die Anwendung wurde lokal mit Flask gestartet und lief erfolgreich unter `http://127.0.0.1:8000`. Über die Konsole konnte überprüft werden, dass die Endpunkte korrekt arbeiten und keine Fehler auftreten.

![Lokale Ausführung im Terminal](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/App3.jpg?raw=true)
> 📸 *Die Abbildung zeigt die lokale Ausführung der Flask-App im Terminal. Die Konsole bestätigt, dass der Server unter `http://127.0.0.1:8000` erreichbar ist – ein Zeichen dafür, dass die Entwicklungsumgebung korrekt eingerichtet wurde.*

---

### ☁️ **Azure Deployment**

Nach dem lokalen Test wurde die Anwendung erfolgreich über Local Git auf Azure App Service deployed. Dabei wurden einige Anpassungen vorgenommen (z. B. Port, Startkommando), um sicherzustellen, dass Flask korrekt startet.

![Web-App live auf Azure](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/App2.jpg?raw=true)
> 🌐 *Der Screenshot zeigt die Weboberfläche der Bildverarbeitungs-App, wie sie online über Azure erreichbar ist. Dies beweist, dass sowohl Frontend als auch Backend wie gewünscht auf der Cloud-Plattform funktionieren.*

---

## Dependency Management

* Virtuelle Umgebung mit `venv` erstellt
* Abhängigkeiten in `requirements.in` gepflegt
* `pip-compile` oder `pip freeze` zur Erstellung von `requirements.txt`
* Reproduzierbare Installation für andere Umgebungen möglich

Für die Verwaltung der Python-Abhängigkeiten wurde eine virtuelle Umgebung eingerichtet. Mit dem Befehl `pip freeze > requirements.txt` wurden alle aktuell installierten Pakete automatisch in eine Textdatei geschrieben. Diese Datei dient als Basis für die Reproduzierbarkeit und das Deployment, z. B. auf Azure.

![pip freeze zur Erstellung der requirements.txt](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/DepenMgt1.jpg?raw=true)
> 🛠️ *Der Screenshot zeigt die Konsole beim Ausführen des Befehls `pip freeze > requirements.txt`. Damit wird eine Liste aller aktuell in der virtuellen Umgebung installierten Pakete generiert.*

![Inhalt der requirements.txt](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/DepenMgt2.jpg?raw=true)
> 📄 *Hier ist der Inhalt der automatisch erzeugten `requirements.txt` zu sehen. Sie enthält alle benötigten Libraries wie `flask` und `pillow`, die später auch beim Deployment auf Azure installiert werden.*

---

## Deployment

* Deployment via Azure App Service mit Local Git
* App läuft auf: https://bildverarbeitung-maniyman.azurewebsites.net
* Startup Command: `python app.py` (port 8000, host 0.0.0.0)
* Logs über Kudu + Live-Log-Streaming geprüft
* Probleme mit `master/main` + Port wurden erfolgreich gelöst

![Azure Overview](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/Deployment1.jpg?raw=true)
> 📊 *Die Azure-Übersichtsseite zeigt grundlegende Informationen zur App wie Status, Ressourcengruppe und Standort. Dies bestätigt, dass die Ressource korrekt erstellt und aktiv ist.*

![Deployment Center – Git URL](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/Deployment2.jpg?raw=true)
> 🔗 *Im Deployment Center ist die Git-URL sichtbar, über die der Code direkt aus dem lokalen Repository zu Azure gepusht wurde. Dies war entscheidend für das automatische Deployment.*

![Log Stream – Live Logs](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/Deployment3.jpg?raw=true)
> 🧾 *Der Log Stream in Azure zeigt Live-Ausgaben der laufenden App. Dieses Tool war hilfreich beim Debuggen – zum Beispiel bei Portfehlern oder Startproblemen.*

![Live-WebApp in Azure](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal1-python/images/Deployment4.jpg?raw=true)
> 🌐 *Abbildung der live laufenden Web-App im Azure-Browserfenster. Dies bestätigt, dass sowohl das Deployment als auch der Zugriff über das Internet erfolgreich funktionieren.*

---

## Reflexion

* Ich habe viel über Flask, Deployment mit Azure und Dependency Management gelernt.
* Besonders spannend war das Debugging bei Azure und die Lösung mit dem Port 8000.
* In Zukunft würde ich z. B. Gunicorn einsetzen für produktionsnahe Apps.
