# Docker CouchDB Setup

This repository contains configuration files to easily run CouchDB using Docker Compose. It also includes functionality to create backups of the database.

## Prerequisites

- Docker
- Docker Compose

## Setup and Launch

### Starting the CouchDB Server

```bash
sudo docker-compose up -d
```

This command starts the CouchDB server in the background.

### Accessing CouchDB

- URL: http://localhost:5984
- Username: `admin` (by default)
- Password: `admin_password` (by default)

### Stopping the Service

```bash
sudo docker-compose down
```

## Backup Functionality

### Creating Manual Backups

To create a backup at any time, run the following command:

```bash
sudo docker-compose run --rm backup
```

This creates a timestamped backup file in the `./backups` directory.

### Backup File Location

Backup files are stored at:
```
./backups/couchdb_backup_[YYYYMMDD_hhmmss].tar.gz
```

## Advanced Usage

### Removing All Resources (Containers, Volumes, Images)

```bash
sudo docker-compose down --volumes --rmi all --remove-orphans
```

This command removes containers, networks, volumes (including data), and images.

### Checking Container Status

```bash
sudo docker-compose ps
```

### Viewing Logs

```bash
sudo docker-compose logs
```

## Important Notes

- The default username and password are not secure. Always change them in production environments.
- This setup is optimized for local development.
- Data is stored in the Docker volume `couchdb_data`, so it persists even after running `docker-compose down`.
- To completely remove data, use the `--volumes` option.
