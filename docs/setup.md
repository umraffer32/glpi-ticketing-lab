# Setup — reproduce the deploy from zero

<!-- Placeholder. Filled in Phase 4 with the EXACT commands run in Phase 2. -->

## Prerequisites

- Docker + Docker Compose
- (Phase 5) A Proxmox or VMware VM if reproducing the homelab deployment

## Steps

1. Clone the repo.
2. `cp .env.example .env` and set a strong `GLPI_DB_PASSWORD`.
3. `docker compose up -d`
4. Open `http://localhost:8080` and run the GLPI web installer, pointing it at DB host `mariadb`.
5. Log in and immediately change the four default account passwords (glpi / tech / normal / post-only).

<!-- TODO: paste verified commands and any boot-time fixes from Phase 2. -->
