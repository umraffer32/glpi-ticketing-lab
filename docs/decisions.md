# Decisions

A running log of the non-obvious engineering choices made building this lab, and why.
Newest entries at the bottom. Each entry covers the decision, the reasoning, and the
alternative that was rejected.

## Deployment

### Official `glpi/glpi` image (not the community `diouxx/glpi` image)
GLPI now publishes a first-party image maintained by the project itself, with built-in
install and update handling. Chose it over the popular community image for first-party
support and predictable behavior.
*Rejected.* `diouxx/glpi`. Community-maintained, no upstream guarantee.

### Pinned to `glpi/glpi:11.0.7` (not `:latest`)
Pinning an explicit version makes the stack reproducible. Anyone cloning the repo gets the
exact build documented here, and the deployment can't silently change under a moving `:latest`.
*Rejected.* `:latest`. Convenient, but not reproducible.

### `GLPI_SKIP_AUTOINSTALL=true`. Run the web installer by hand
The official image can auto-install the database on first boot. Disabled that so the database
installation happens explicitly through the installer, making each step of the install
observable and verifiable instead of hidden.
*Rejected.* Default auto-install. Faster, but opaque.

### MariaDB with a random root password and a least-privilege app user
`MARIADB_RANDOM_ROOT_PASSWORD=yes` means no fixed or known root password exists. GLPI connects
with a dedicated `glpi` user that only owns its own database. That's standard least-privilege.
*Rejected.* A fixed shared root password used by the app.

### Port mapping `8080:80`
GLPI is published on host port `8080` so it needs no elevated privileges (ports below 1024) and
won't collide with anything already on port 80. Only the web port is exposed; the database is
reachable only on the internal compose network.

### Named volumes (`glpi_data`, `db_data`)
Application and database state live in named volumes so container restarts and recreates don't
wipe tickets or configuration.

## Repository and workflow

### Secrets kept out of git
Real credentials live in `.env` (gitignored). The repo ships `.env.example` with placeholders
only. The internal planning notes are gitignored as well, so the public repo contains only the
runnable lab and its documentation.

### SSH key and GitHub CLI for repo access
Pushes authenticate with a dedicated `ed25519` SSH key; `gh` handles repo creation and
management.
*Rejected.* HTTPS with a stored password or token in the URL.

### Default branch `main`
Renamed the initial branch from `master` to `main` to match the current GitHub default.
