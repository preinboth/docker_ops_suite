# Wekan - Das Open Source Kanban Board

Dieses Repository enthält eine Docker-Konfiguration für Wekan, eine Open-Source Kanban-Board-Anwendung.

## Voraussetzungen

- Docker und Docker Compose
- Traefik als Reverse Proxy
- Eine Domain für Wekan

## Installation

1. Repository klonen:
   ```bash
   git clone https://github.com/yourusername/docker_wekan.git
   cd docker_wekan
   ```

2. Umgebungsvariablen konfigurieren:
   ```bash
   cp env.example .env
   ```
   Bearbeiten Sie die `.env`-Datei und setzen Sie Ihre Domain ein:
   ```
   WEKAN_HOST=wekan.ihredomain.com
   ```

3. Container starten:
   ```bash
   docker-compose up -d
   ```

## Konfiguration

### Umgebungsvariablen

- `WEKAN_HOST`: Die Domain, unter der Wekan erreichbar sein soll (ohne https://)

### Persistente Daten

Die folgenden Daten werden in Docker-Volumes gespeichert:
- `wekan_db_data`: MongoDB-Datenbank
- `wekan_files`: Wekan-Uploads

## Features

- HTTPS-Unterstützung durch Traefik
- Automatische SSL-Zertifikate durch Let's Encrypt
- REST-API aktiviert für Export-Funktionen
- Persistente Datenspeicherung
- Automatischer Neustart bei Systemreboot

## Wartung

### Backup

Die Daten werden in Docker-Volumes gespeichert. Um ein Backup zu erstellen:

```bash
# Backup der MongoDB-Daten
docker run --rm -v wekan_db_data:/source -v $(pwd)/backup:/backup alpine tar -czf /backup/wekan_db_backup.tar.gz -C /source .

# Backup der Wekan-Dateien
docker run --rm -v wekan_files:/source -v $(pwd)/backup:/backup alpine tar -czf /backup/wekan_files_backup.tar.gz -C /source .
```

### Update

Um auf die neueste Version zu aktualisieren:

```bash
docker-compose pull
docker-compose up -d
```

## Lizenz

Dieses Projekt ist unter der MIT-Lizenz lizenziert. Siehe [LICENSE](LICENSE) für Details.

## Weitere Informationen

- [Wekan GitHub Repository](https://github.com/wekan/wekan)
- [Wekan Dokumentation](https://wekan.github.io/)