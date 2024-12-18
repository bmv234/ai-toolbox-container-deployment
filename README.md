# Container Deployment with Dockge

This directory contains container deployment configurations managed by Dockge, a lightweight Docker compose stack manager.

## Setup

1. Start Dockge:
```bash
cd dockge
docker compose up -d
```

2. Access Dockge UI:
   - Open your browser and navigate to `http://localhost:5001`
   - Use the UI to deploy and manage individual stacks

## Available Stacks

### 1. Whoami Service
- Port: 8082
- Description: Simple service that displays container information
- Usage: Access `http://localhost:8082` to see container details

### 2. Uptime Kuma
- Port: 3001
- Description: Self-hosted monitoring tool
- Usage: Access `http://localhost:3001` to set up monitoring

### 3. Ollama Stack
- Ollama:
  - Port: 11434
  - Description: Run AI models locally
  - Usage: API endpoint for AI model interactions

- Open WebUI:
  - Port: 3000
  - Description: Web interface for Ollama
  - Usage: Access `http://localhost:3000` to interact with AI models
  - Note: Automatically connects to Ollama service

### 4. Text-to-Speech API Server
- Port: 8050
- Description: GPU-accelerated Text-to-Speech service
- Features:
  - Persistent model storage
  - GPU acceleration support
  - Audio generation caching
- Usage: Access `http://localhost:8050` for TTS API endpoints

### 5. Speech-to-Text API Server
- Port: 8060
- Description: GPU-accelerated Speech-to-Text service
- Features:
  - Persistent model storage
  - GPU acceleration support
  - Audio processing cache
- Usage: Access `http://localhost:8060` for STT API endpoints

### 6. Translation API Server
- Port: 8070
- Description: GPU-accelerated Translation service
- Features:
  - Persistent model storage
  - GPU acceleration support
  - Translation caching
- Usage: Access `http://localhost:8070` for Translation API endpoints

### 7. PostgreSQL Database
- Port: 5432
- Description: PostgreSQL database server
- Default Credentials:
  - Username: pguser
  - Password: changeMe123
  - Database: myapp

## Directory Structure
```
.
├── dockge/                # Dockge manager configuration
│   └── docker-compose.yml
├── stacks/                # Container stack configurations
│   ├── whoami-stack/
│   │   └── compose.yaml
│   ├── uptime-kuma-stack/
│   │   └── compose.yaml
│   ├── postgres-stack/
│   │   └── compose.yaml
│   ├── ollama-stack/
│   │   └── compose.yaml
│   ├── tts-service-stack/
│   │   └── compose.yaml
│   ├── stt-service-stack/
│   │   └── compose.yaml
│   └── translate-service-stack/
│       └── compose.yaml
└── data/                  # Dockge data directory
```

## Managing Stacks
1. Create a new directory in `stacks` with `-stack` suffix
2. Add your `compose.yaml` file in the stack directory
3. Use the Dockge UI to manage and deploy stacks:
   - Navigate to `http://localhost:5001`
   - Click on a stack to view its details
   - Use the UI controls to start, stop, or manage the stack
4. Add appropriate labels for better organization:
   ```yaml
   labels:
     - "dockge.description=Your description"
     - "dockge.icon=icon-name"
     - "dockge.note=Additional notes"
   ```

## Security Notes
- Change default passwords before deploying to production
- Review and adjust port mappings based on your needs
- Consider using Docker networks for inter-container communication