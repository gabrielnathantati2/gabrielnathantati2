# Grupo Futura — Connected Business Technology Ecosystem

**Status:** In development  
**Products:** Futura Desk · Futura Cloud · Futura Mail  
**Product direction:** Connected business workspace, cloud infrastructure and business email, designed around a more approachable, AI-enabled user experience.

## Overview

Grupo Futura is developing a connected ecosystem of business technology products. Rather than treating CRM, cloud infrastructure and business email as unrelated services, the product vision brings them together through shared identity, organisation-aware access and service integrations.

The ecosystem is centred on three products:

| Product | Role | Public address |
|---|---|---|
| **Futura Desk** | Main business workspace and product experience, including CRM and the full Creative Studio | https://futuradesk.space |
| **Futura Cloud** | Cloud hosting control panel and infrastructure platform | https://cloud.futuradesk.space |
| **Futura Mail** | Business email and webmail product | Repository architecture currently references https://mailserver.futuradesk.space |

All three products are in development. The architecture and implementation status below distinguish existing foundations from planned capabilities.

## Futura Cloud

Futura Cloud is the cloud hosting and infrastructure product. Its repository is `nmultimidia/futurahost3`.

### Product experience

The Next.js panel is designed to provide a single workspace for managing hosting resources and related services. The documented navigation and product areas include:

- Websites and website tools.
- Domains and DNS management.
- Email accounts, integrated through the Futura Mail administration API.
- VPS management, including console, firewall, snapshots and networking.
- Marketplace for deployable applications.
- Creative Studio hosting flow for websites, stores, landing pages, apps, bots and automations.
- Advanced developer workflow for Git-based deployments, previews, environment variables, logs, domains and edge configuration.
- Account settings, notifications, billing and country-aware preferences.
- Agency and platform administration.

**Important status note:** the repository's implementation plan explicitly identifies many panel screens as still using example data and lists the work needed to replace mocks with real API calls. Some infrastructure functions are already implemented, while other product areas depend on later infrastructure phases or the future Futura Account service. The navigation above describes the designed product surface, not a claim that every feature is production-ready.

### Architecture

The repository separates the cloud platform into three main parts:

| Component | Technology | Responsibility |
|---|---|---|
| Web panel | Next.js 15, React 19, TypeScript | Customer and administrator workspace |
| Control plane API | TypeScript, Hono, Drizzle; PostgreSQL or PGlite | Node registry, regions, scheduler, node credentials and command queue |
| Node agent | Go | Joins infrastructure nodes, sends heartbeats, reconnects and executes an allowlisted set of commands |
| Shared contracts | TypeScript and Zod | Typed communication between panel, API and agent |

The documented Phase 0 foundation includes region and node management, one-time node enrollment tokens, a command queue, a scheduler, an agent using outbound WebSocket connections, a systemd installer and a Super Admin interface for nodes. The platform documentation reports API tests and Go agent tests as part of its development workflow.

### Infrastructure direction

The long-term architecture is a multi-node cloud platform:

- A central control plane coordinates infrastructure.
- Lightweight agents run on Linux nodes.
- A scheduler is intended to place workloads according to region, available resources and node type.
- Private node communication is planned around WireGuard.
- Website runtimes, databases, backups, VPS, build pipelines and AI workloads are part of the phased roadmap.
- A region-aware model is intended to support Brazil, Angola, Portugal, the wider EU and international customers.

The roadmap separates the foundation from later phases for website hosting, developer deployments, AI infrastructure, VPS and multi-region scaling.

### Multi-product integration

The architecture defines clear data ownership: Hosting owns domains, DNS, nodes, websites, databases, backups, VPS and AI infrastructure. It integrates with Futura Mail through the Mail administration API and is intended to connect with Futura Desk's Creative Studio through the Hosting API.

## Futura Mail

Futura Mail is the business email and webmail product, developed in a separate repository: `nmultimidia/Futura-Mail`.

The repository contains a Next.js and TypeScript webmail application with Supabase integration. The implemented interface and application code include email folders, search, selection, read/unread state, starring, archive, delete, drafts, compose, reply, forward and moving messages between folders.

The product architecture also documents:

- A modular interface with a Super Admin module registry.
- Administrative control over module availability.
- A webmail sidebar driven by registered modules.
- Integration points for the Futura Cloud panel to manage email resources through an administration API.
- A broader email-service direction that includes SMTP, IMAP, JMAP and calendar/contact protocols.

**Implementation and security status:** the Mail repository contains unfinished items for MFA, email transport and authentication standards, DNS templates, privacy workflows and OAuth. Its security overview contains claims that are not consistent with its own TODO checklist. This case study therefore does not claim ISO certification, completed compliance, or that every mail protocol and security control is fully operational.

## Futura Desk

Futura Desk is the main business workspace and the origin of the ecosystem's product experience and design language. Its separate repository documents a B2B multi-tenant SaaS foundation with:

- CRM and sales pipeline.
- Kanban boards and cards.
- Prospecting and customer management.
- Projects and tasks.
- Financial management.
- Company and team roles.
- Platform Super Admin console.
- Customer portal.
- Tenant-level module availability and access controls.

The ecosystem architecture positions the full Creative Studio in Futura Desk, while Futura Cloud provides a hosting-oriented creation and publishing flow. The products are intended to share identity and organisation context through a future Futura Account service.

## Shared architecture principles

The official ecosystem architecture records several key design principles:

1. **Product data ownership:** each product owns its own data. Products integrate through APIs, OIDC and signed webhooks rather than directly reading or writing another product's database.
2. **Organisation-aware access:** resources are associated with an organisation, with access scoped to the active organisation.
3. **Single sign-on direction:** Futura Account is planned as the central identity provider for users, organisations, roles and entitlements.
4. **Country-aware experience:** currency, fiscal identity, payment methods, tax and language are intended to adapt to the customer's country.
5. **AI-native direction:** MCP and AI Gateway capabilities are part of the architecture direction, with customer-controlled permissions and approval for sensitive automated actions.
6. **Human-centred interface:** the product aims to make complex business and infrastructure tasks accessible to non-technical users, while keeping advanced controls available to developers.

Futura Account is an architectural component planned in the official design; it should not be described as already launched.

## My work

I am building and coordinating the development of this product ecosystem through Grupo Futura, with work spanning product architecture, web application development, integrations and AI-enabled workflows.

The repositories show hands-on implementation across the Futura Cloud panel and its infrastructure foundation, the Futura Mail web application and the Futura Desk business platform.

The goal is to connect these services into a coherent workspace: business management, hosting and email, with intelligent automation supporting the user experience.

## Repositories

- [Futura Cloud / FuturaHost infrastructure](https://github.com/nmultimidia/futurahost3)
- [Futura Mail](https://github.com/nmultimidia/Futura-Mail)
- [Futura Desk](https://github.com/nmultimidia/fd)
- [N Multimídia GitHub organisation](https://github.com/nmultimidia)

## Product links

- [Futura Desk](https://futuradesk.space)
- [Futura Cloud](https://cloud.futuradesk.space)

The official FuturaHost architecture document currently references the Mail service at `mailserver.futuradesk.space`. Confirm the preferred public Mail URL before publishing it in the portfolio.

---

*Portfolio case study based on the product repositories and their architecture documentation. The ecosystem is in development; planned capabilities are identified separately from implemented foundations.*
