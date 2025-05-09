# Dashy - Homelab Dashboard

Ein modernes, anpassbares Dashboard für Ihr Homelab, das alle Ihre Dienste und Anwendungen an einem zentralen Ort zusammenführt.

## Features

- 🎨 Anpassbare Benutzeroberfläche
- 📱 Responsive Design
- 🔒 Integrierte Sicherheitsfunktionen
- 🔄 Automatische SSL/TLS-Konfiguration
- 📊 Statusüberwachung für Dienste
- 🔍 Suchfunktion für schnellen Zugriff

## Installation

1. Stellen Sie sicher, dass Docker und Docker Compose installiert sind
2. Klonen Sie dieses Repository
3. Starten Sie den Container:
   ```bash
   docker-compose up -d
   ```

## Konfiguration

### Umgebungsvariablen

- `PUID`: Benutzer-ID (Standard: 1000)
- `PGID`: Gruppen-ID (Standard: 1000)
- `TZ`: Zeitzone (Standard: Europe/London)

### Ports

- Intern: 8080
- Extern: 8090

### Volumes

- `dashy_data`: Persistente Speicherung der Benutzerdaten

## Netzwerk

Der Container ist in zwei Netzwerke eingebunden:
- `homelab_network`
- `default` (Docker-Standardnetzwerk)

## Gesundheit & Wartung

- Automatischer Neustart bei Fehlern
- Regelmäßige Gesundheitsüberprüfungen
- Persistente Datenspeicherung

## Lizenz

Dieses Projekt verwendet Dashy unter der MIT-Lizenz. Weitere Informationen finden Sie auf der [offiziellen Dashy-Website](https://dashy.to/).
