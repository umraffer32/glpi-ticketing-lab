# GLPI Ticketing Lab

A self-hosted GLPI (open-source ITSM) stack, deployed with Docker and configured by hand from a
blank install. The default admin credentials get rotated first, before anything else, then the
rest gets built on top: ticket categories feeding a routing rule, an SLA with a real escalation,
a small asset inventory, and a knowledge base article. Every item in `docs/configuration.md` was
actually clicked through and screenshotted, not just described.

## What this demonstrates

- Security hardening (default account password rotation)
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

See [docs/setup.md](docs/setup.md) for the full walkthrough. Short version:

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
