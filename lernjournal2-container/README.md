# 📦 Lernjournal 2 – Containerprojekt

## 🔹 Eigene Docker Web-Applikation: Drupal + MariaDB

### 🐳 Verwendete Docker Images

| Komponente | Beschreibung |
|------------|--------------|
| **drupal:10** | CMS Web-Applikation ([Docker Hub](https://hub.docker.com/_/drupal)) |
| **mariadb:10.6** | Datenbankserver ([Docker Hub](https://hub.docker.com/_/mariadb)) |

Zusätzlich wurde **Docker Compose** lokal verwendet (kein externes Repo erforderlich).

---

### ⚙️ Manuelles vs. Docker-Compose Deployment

Das manuelle Deployment wurde durch **Docker Compose** ersetzt. Vorteil:
- Strukturierter und besser wartbar
- Ideal für Multi-Container-Setups

---

### ⚙️ Docker Compose Setup

```yaml
version: '3.3'

services:
  drupal:
    image: drupal:10
    ports:
      - "8083:80"
    restart: always
    volumes:
      - drupal-data:/var/www/html
    environment:
      DRUPAL_DB_HOST: mariadb
      DRUPAL_DB_NAME: drupal
      DRUPAL_DB_USER: drupal
      DRUPAL_DB_PASSWORD: drupal
    depends_on:
      - mariadb

  mariadb:
    image: mariadb:10.6
    restart: always
    environment:
      MYSQL_DATABASE: drupal
      MYSQL_USER: drupal
      MYSQL_PASSWORD: drupal
      MYSQL_ROOT_PASSWORD: rootpass
    volumes:
      - mariadb-data:/var/lib/mysql

volumes:
  drupal-data:
  mariadb-data:
```

Start der Applikation:
```bash
docker-compose up -d
```

📍 Zugriff: [http://localhost:8083](http://localhost:8083)  
📂 Datenbank-Zugang: `drupal / drupal / mariadb`

![Laufende Container (Drupal + MariaDB) via Docker Compose im Terminal](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Docker-Compose%20Deployment.jpg?raw=true)

![Drupal-Webseite nach erfolgreichem Setup auf localhost:8083](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Docker-Compose%20Deployment2.jpg?raw=true)

---

## 🤖 ML-App Deployment – ONNX Image Classification

### 🧠 Projektwahl

| Option | Gewählt |
|--------|---------|
| ONNX Sentiment Analysis | ❌ |
| ONNX Image Classification | ✅ |

🔗 GitHub Repo: [mosazhaw/onnx-image-classification](https://github.com/mosazhaw/onnx-image-classification)  
🔗 Docker Hub: [maniyman/onnx-image-classification](https://hub.docker.com/r/maniyman/onnx-image-classification)

---

### 🖥️ Lokales Deployment

```bash
# Schritt 1: Repo klonen
git clone https://github.com/mosazhaw/onnx-image-classification
cd onnx-image-classification

# Schritt 2: Image bauen
docker build -t onnx-image-classification .

# Schritt 3: Container starten
docker run --name onnx-image-classification -p 9000:5000 -d onnx-image-classification
```

📍 Zugriff: [http://localhost:9000](http://localhost:9000)

![ONNX-Image-Classifier lokal im Browser unter localhost:9000 geöffnet](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20lokales%20Deployment2.jpg?raw=true)

---

### ☁️ Deployment in die Cloud

#### ✅ Azure Web App

- **Ressourcengruppe:** `mdm-appservice`
- **Container:** `maniyman/onnx-image-classification:latest`
- **Plan:** Free Tier (F1)
- **URL:** `https://onnx-img-<dein-name>.azurewebsites.net`

![Azure Web App mit Container-Einstellungen im Azure Portal](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20Azure%20Web%20App.jpg?raw=true)

![Web App erfolgreich geöffnet im Browser](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20Azure%20Web%20App2.jpg?raw=true)

#### ✅ Azure Container Apps (ACA)

- **Ressourcengruppe:** `mdm-aca`
- **Container App:** `onnx-aca-final`
- **Umgebung:** `onnx-env`
- **Ingress:** Öffentlich
- **URL:**  
  `https://onnx-aca-final.westeurope.azurecontainerapps.io`

![ACA Übersicht mit aktivierter Ingress-Option und laufender App](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20ACA.jpg?raw=true)

![ACA App im Browser erfolgreich geöffnet](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20ACA2.jpg?raw=true)

#### ✅ Azure Container Instances (ACI)

- **Ressourcengruppe:** `mdm-aci`
- **DNS:** `onnx144`
- **Protokoll/Port:** TCP / 5000
- **URL:**  
  `http://onnx144.e6czc3a5fnb7aef0.southindia.azurecontainer.io:5000`

  ![Azure Container Instance – Übersicht der laufenden Instanz](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20ACI.jpg?raw=true)

![ACI-App erfolgreich im Browser aufgerufen](https://github.com/maniyman/MDM-LernJournal/blob/main/lernjournal2-container/images/Dokumentation%20Deployment%20ACI2.jpg?raw=true)

---

## Reflexion

Durch das Containerprojekt konnte ich praxisnah lernen, wie man Web- und Datenbankdienste mit Docker Compose effizient kombiniert. Besonders spannend war der Einsatz von Volumes und die Konfiguration von Umgebungsvariablen für eine funktionierende Drupal-MariaDB-Integration. Das Deployment der ML-App in Azure (Web App, ACA, ACI) hat mir einen wertvollen Einblick in moderne Cloud-Dienste gegeben. Insgesamt hat mir das Projekt geholfen, mein Verständnis für Containerisierung und Cloud-Deployment deutlich zu vertiefen.



---


