# GLPI Ticketing Lab

> Self-hosted GLPI (open-source ITSM) stack, deployed with Docker and configured to
> demonstrate core IT service-management workflows: incident management, service-request
> fulfillment, SLAs, asset/inventory tracking, and a knowledge base.

<!-- TODO (Phase 4): tighten to a 3–4 sentence overview once the build is done. -->

## What this demonstrates

<!-- TODO (Phase 4): fill in from what was ACTUALLY configured in Phase 3. Candidates: -->
- Incident categorization and incident management
- Service-request fulfillment
- SLA definition with response/resolution targets and escalation
- IT asset / inventory management
- Knowledge base / documentation
- Ticket routing / queue management (users, groups, assignment rules)

## Stack

- **GLPI** — official `glpi/glpi` image (Docker)
- **MariaDB** — database backend
- **Docker Compose** — single-command bring-up

## Run it yourself

<!-- TODO (Phase 4): finalize after Phase 2 verification. See docs/setup.md for full steps. -->

```bash
cp .env.example .env      # then edit .env with a real DB password
docker compose up -d
# open http://localhost:8080 and run the installer
```

## Documentation

- [docs/setup.md](docs/setup.md) — reproduce the deploy from zero
- [docs/configuration.md](docs/configuration.md) — what was configured and why it matters
- [docs/screenshots/](docs/screenshots/) — proof of the running instance

## License

[MIT](LICENSE)
