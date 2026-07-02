# Setup. Reproduce the deploy from zero

These are the exact, verified steps used to bring the stack up.

## Prerequisites

- Docker + Docker Compose (verified on Docker 29.x / Compose v5.x)
- (Phase 5) A Proxmox or VMware VM if reproducing the homelab deployment

## Steps

1. **Clone the repo** and enter it.

2. **Create your environment file** and set a strong database password.
   ```bash
   cp .env.example .env
   # edit .env and set GLPI_DB_PASSWORD to a strong value
   ```
   `.env` is gitignored. It never gets committed.

3. **(Optional) Validate the compose file** resolves correctly.
   ```bash
   docker compose config -q && echo VALID
   ```

4. **Bring the stack up.**
   ```bash
   docker compose up -d
   ```
   First run pulls `glpi/glpi:11.0.7` and `mariadb:11` (a few hundred MB).

5. **Wait for first-boot init** (~15-30s). The GLPI container waits for MariaDB,
   then starts Apache. Watch it with:
   ```bash
   docker compose logs -f glpi
   ```
   You should see `The database is now ready and reachable.`, then Apache
   `resuming normal operations`. A one-time `config_db.php is missing` message from
   the cron worker is **normal** here. The database isn't installed yet, because we
   intentionally run the installer by hand (`GLPI_SKIP_AUTOINSTALL=true`).

6. **Confirm GLPI is serving** the installer.
   ```bash
   curl -s -o /dev/null -w "%{http_code}\n" http://localhost:8080/   # expect 200
   ```

7. **Open the web installer.** Browse to `http://localhost:8080` and run the GLPI
   installer. When asked for the database connection, use:
   - **SQL server (host).** `mariadb`
   - **SQL user.** `glpi`
   - **SQL password.** The `GLPI_DB_PASSWORD` from your `.env`
   - **Database.** `glpi`

8. **Log in** (default admin `glpi` / `glpi`) and **immediately change the four default
   account passwords** (`glpi`, `tech`, `normal`, `post-only`) as a first hardening step.

## Stopping and starting

```bash
docker compose stop      # stop without removing data
docker compose up -d     # start again
docker compose down      # remove containers (named volumes/data persist)
```
