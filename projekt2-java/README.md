# Projekt 2 – Car Recognizer (Java + TensorFlow)

## Übersicht

| Kategorie                  | Inhalt                                                                 |
|----------------------------|------------------------------------------------------------------------|
| **Variante**               | Vorhandenes Modell + Eigener Datensatz                                |
| **Datensatz (selbstgewählt)** | Format: Bilddaten (.jpg, .png)<br>Beschreibung: Bilder von Automarken (BMW, Audi, Mercedes, etc.), ca. 100 Bilder pro Marke |
| **Datensatz URL**          | Nicht öffentlich – eigene Sammlung und Quellen wie Google/Bing Images |
| **Modell URL**             | Nicht öffentlich – lokal trainiertes TensorFlow SavedModel            |
| **ML-Algorithmus**         | Convolutional Neural Network (CNN) mit TensorFlow                     |
| **Repo URL**               | [https://carrecognizer-fkh5cscmdvf7hcex.southindia-01.azurewebsites.net](https://carrecognizer-fkh5cscmdvf7hcex.southindia-01.azurewebsites.net) |

---

## 📁 Daten

- Eigener Datensatz mit Bildern von verschiedenen Automarken
- Erweiterung durch Data Augmentation (Flip, Rotation, Zoom)

<img src="images/AutoMarken Bilder icrawler.jpg" alt="AutoMarken Bilder icrawler" style="max-width: 100%; height: auto;">

---

## ⚙️ Training

- CNN-Modell mit TensorFlow
- Optimizer: Adam
- Loss: Categorical Crossentropy
- ca. 10 Epochen Training mit über 25.000 Bildern

<img src="images/Training Modell.jpg" alt="Training Modell" style="max-width: 100%; height: auto;">
<img src="images/Model umbau.jpg" alt="Model umbau" style="max-width: 100%; height: auto;">

---

## 🤖 Inference / Serving

- Eingebunden in ein Spring Boot Backend (Java)
- REST API Endpoint `/predict` zur Bildklassifikation
- Modell wird beim Start aus `src/main/resources/model/` geladen

<img src="images/Car Reco App.jpg" alt="Car Reco App" style="max-width: 100%; height: auto;">
<img src="images/PredictController.jpg" alt="PredictController" style="max-width: 100%; height: auto;">
<img src="images/PredictionService.jpg" alt="PredictionService" style="max-width: 100%; height: auto;">

---

## 🚀 Build & Deployment

- Maven Build (`mvn clean package`)
- Dockerized Anwendung (`Dockerfile` mit Java + Python + TensorFlow)
- Bereitstellung via Azure Container Registry (ACR) und Azure App Service
- Zugriff über Azure App URL:  
  [https://carrecognizer-fkh5cscmdvf7hcex.southindia-01.azurewebsites.net](https://carrecognizer-fkh5cscmdvf7hcex.southindia-01.azurewebsites.net)

<img src="images/MVN clean package.jpg" alt="MVN clean package" style="max-width: 100%; height: auto;">
<img src="images/MVN Installation.jpg" alt="MVN Installation" style="max-width: 100%; height: auto;">
<img src="images/pomxml.jpg" alt="pom.xml" style="max-width: 100%; height: auto;">
<img src="images/Pillow Installation.jpg" alt="Pillow Installation" style="max-width: 100%; height: auto;">
<img src="images/Docker Build.jpg" alt="Docker Build" style="max-width: 100%; height: auto;">
<img src="images/Docker Run.jpg" alt="Docker Run" style="max-width: 100%; height: auto;">
<img src="images/Azure Push.jpg" alt="Azure Push" style="max-width: 100%; height: auto;">
<img src="images/BuildSuccess.jpg" alt="Build Success" style="max-width: 100%; height: auto;">
<img src="images/Projektstruktur.jpg" alt="Projektstruktur" style="max-width: 100%; height: auto;">
<img src="images/Maven Clean start.jpg" alt="Maven Clean start" style="max-width: 100%; height: auto;">
