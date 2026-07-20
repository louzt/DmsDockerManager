# Docker Compose Multi-Config & Fallback Specification

## Architecture & Flow

```mermaid
flowchart TD
    A[Docker Compose Trigger] --> B{Check Compose Version}
    B -->|Compose V2| C[docker compose -f config1.yml -f config2.yml]
    B -->|Compose V1 Legacy| D[docker-compose -f config1.yml]
    C --> E[Execute Project Action]
    D --> E[Execute Project Action]
```

## Fix Summary
- Support multi-file `-f` compose declarations in project status checks.
- Fall back gracefully when legacy `docker-compose` binary is present instead of plugin `docker compose`.
