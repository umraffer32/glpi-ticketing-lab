# GLPI Ticketing Lab

A self-hosted GLPI (open-source ITSM) stack, deployed with Docker. Configured by hand to
demonstrate core IT service-management workflows: incident management, service-request
fulfillment, SLAs, asset and inventory tracking, and a knowledge base.

<!-- TODO (Phase 4): tighten to a 3-4 sentence overview once the build is done. -->

## What this demonstrates

<!-- TODO (Phase 4): fill in from what was ACTUALLY configured in Phase 3. Candidates: -->
- Incident categorization and incident management
- Service request fulfillment
- SLA definition with response and resolution targets, plus escalation
- IT asset and inventory management
- Knowledge base documentation
- Ticket routing and queue management (users, groups, assignment rules)

## Stack

- **GLPI**. Official `glpi/glpi` image (Docker)
- **MariaDB**. Database backend
- **Docker Compose**. Single-command bring-up

## Run it yourself

<!-- TODO (Phase 4): finalize after Phase 2 verification. See docs/setup.md for full steps. -->

```bash
cp .env.example .env      # then edit .env with a real DB password
docker compose up -d
# open http://localhost:8080 and run the installer
```

## Documentation

- [docs/setup.md](docs/setup.md). Reproduce the deploy from zero
- [docs/configuration.md](docs/configuration.md). What was configured and why it matters
- [docs/screenshots/](docs/screenshots/). Proof of the running instance

## License

[MIT](LICENSE)
