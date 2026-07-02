# Configuration

What was configured in this GLPI instance and why it matters operationally. Written in plain
first person, and **only** for items actually configured by hand — anything skipped is marked
as skipped, not described as done.

Each section follows the same shape:

> **What** — what was configured
> **How** — the steps taken in GLPI
> **Why it matters** — the operational purpose
> **Screenshot** — proof in `docs/screenshots/`
> **Status** — done / skipped

<!-- TEMPLATE — copy per item:
### <Item name>
- **What:**
- **How:**
- **Why it matters:**
- **Screenshot:** ![](screenshots/<file>.png)
- **Status:** done
-->

---

## Security hardening
- **What:** Rotated the passwords on all four default GLPI accounts that ship with well-known credentials — `glpi` (super-admin), `tech`, `normal`, and `post-only`.
- **How:** Under **Administration → Users**, opened each of the four accounts and set a new strong, unique password. The built-in `glpi-system` account was intentionally left untouched — it is a non-interactive system account with no default login password, and altering it can interfere with GLPI's internal/inventory functions.
- **Why it matters:** GLPI ships with publicly documented default credentials; rotating them immediately closes a standard initial-access risk before any other configuration. On a fresh install GLPI shows a security banner naming the at-risk accounts; clearing them removes the warning.
- **Screenshots:**
  - Default credentials created at install: ![](screenshots/install-default-accounts.png)
  - Security warning **before** hardening (banner naming the at-risk default accounts): ![](screenshots/glpi-dashboard.png)
  - The accounts, managed under Administration → Users: ![](screenshots/users-list.png)
  - **After** hardening — warning cleared: ![](screenshots/dashboard-secured.png)
- **Status:** done

## Incident categorization
- **What:** A small ITIL-style category tree with four top-level categories: Hardware, Software, Network, Access.
- **How:** Under **Setup → Dropdowns → ITIL categories** (in the Assistance group), added each of the four categories via **+ Add**.
- **Why it matters:** Consistent categories make tickets routable and reportable instead of free-text chaos, and they are the key an assignment rule uses to send a ticket to the right team.
- **Screenshot:** ![](screenshots/ticket-categories.png)
- **Status:** done

## Incident management & service-request fulfillment
- **What:** Logged a couple of incidents and a couple of service requests.
- **How:** _TODO (Phase 3)_
- **Why it matters:** Demonstrates the two core ticket workflows — unplanned disruptions vs. standard requests — handled distinctly.
- **Screenshot:** _TODO_
- **Status:** _pending_

## SLA monitoring & escalation
- **What:** An SLA with response + resolution targets and an escalation rule.
- **How:** _TODO (Phase 3)_
- **Why it matters:** Time-bound targets and automatic escalation are how a queue stays accountable instead of tickets going stale.
- **Screenshot:** _TODO_
- **Status:** _pending_

## IT asset / inventory management
- **What:** Added a handful of assets (computers, monitors, a software entry).
- **How:** _TODO (Phase 3)_
- **Why it matters:** Tying assets to tickets gives context for support and a basis for inventory tracking.
- **Screenshot:** _TODO_
- **Status:** _pending_

## Knowledge base / documentation
- **What:** A knowledge base article (e.g. a password-reset how-to).
- **How:** _TODO (Phase 3)_
- **Why it matters:** Documented, reusable answers reduce repeat tickets and speed resolution.
- **Screenshot:** _TODO_
- **Status:** _pending_

## Ticket routing / queue management
- **What:** Users + groups + an assignment rule routing a category to a group.
- **How:** _TODO (Phase 3)_
- **Why it matters:** Rule-based routing puts tickets in front of the right team automatically instead of by manual triage.
- **Screenshot:** _TODO_
- **Status:** _pending_

## Automated notifications (optional)
- **What:** Email notifications on ticket update.
- **How:** _only document if actually configured and working_
- **Why it matters:** Keeps requesters and technicians informed without manual follow-up.
- **Screenshot:** _TODO_
- **Status:** _not yet attempted — will be marked skipped if not completed_
