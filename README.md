## Yousof Ghahremani Tabrizi

Software architect. 25 years building and running systems — telecom platforms,
messaging infrastructure, and the cloud they sit on. Toronto.

I work across .NET, Node, Angular, React, AWS and Azure, and I've spent the
last couple of years on applied AI. Most of what I do is the unglamorous part:
deciding where a boundary goes, what happens when a third party stops
answering, and which failure the on-call engineer should actually be woken for.

---

### What's here

These repositories are **sanitised rebuilds** of production systems I've
worked on. The originals hold client data and live credentials and can't be
published, so the code here was rewritten against stub endpoints. The
architecture, the domain rules and the decisions are the real ones. Each repo
says so in its README, and I'm happy to walk through the originals on a call.

Six repositories cover two related system designs: a SIM platform, its support portal and AWS infrastructure; and a messaging API, React client and Azure notification components. They are independent public samples, with integration gaps described in their READMEs.

---

### What I want this portfolio to show

I want reviewers to see how I connect backend design, frontend behaviour and cloud operations to the needs of customers and support teams.

| Area | Repository | What to look for |
|---|---|---|
| Backend domain design | [sim-platform](https://github.com/yght/sim-platform) | Carrier normalisation, lifecycle rules and failure handling |
| Support workflows | [sim-portal](https://github.com/yght/sim-portal) | Optimistic actions, rollback and permission-aware presentation |
| Cloud operations | [sim-infra](https://github.com/yght/sim-infra) | Network boundaries, usage parsing and operational alarms |
| C# API structure | [dotnet-showcase](https://github.com/yght/dotnet-showcase) | API, service and persistence boundaries in a historical sample |
| Messaging UX | [message-web](https://github.com/yght/message-web) | Client-generated IDs, reconciliation and polling |
| Azure and notification rules | [message-azure](https://github.com/yght/message-azure) | Policy precedence, managed identity and infrastructure definitions |
| Applied AI | [ad-optimizer](https://github.com/yght/ad-optimizer) | Statistical allocation, validation and bounded repair |

Each README includes a short reading path and the scope of the public sample. These repositories support a discussion of engineering decisions; they do not by themselves establish production scale, measured performance gains or a complete running system.

---

### The systems

**[sim-platform](https://github.com/yght/sim-platform)** · Node.js, 2018
One API over three carriers who agree about nothing. Bell speak in mainframe
codes, Vodafone are asynchronous, AT&T return 409 for anything they dislike.
The interesting file is the normaliser that folds all three into one vocabulary.

**[sim-portal](https://github.com/yght/sim-portal)** · Angular 6 + NgRx, 2018
The support tool for the above. Optimistic commands with rollback, and a test
that pins the front end's transition table to the backend's — because a button
that returns 409 is a support ticket about the support tool.

**[sim-infra](https://github.com/yght/sim-infra)** · Terraform + AWS, 2019–21
Three subnet tiers where the isolated one has no default route at all — the
absence is the control. Plus a nightly usage ingest across three carrier file
formats and three different unit systems.

**[dotnet-showcase](https://github.com/yght/dotnet-showcase)** · .NET, 2016–21
A historical C# messaging API sample targeting .NET Core 1.1, showing API, service and data-access boundaries. Test implementation and integration remain incomplete.

**[message-web](https://github.com/yght/message-web)** · React + TypeScript, 2020
A related client sample designed around HTTP long-polling. Your own message reaches the browser
three different ways in any order; reconciling that is the whole repo.

**[message-azure](https://github.com/yght/message-azure)** · Bicep + Functions, 2021
The Azure side. Managed identity only — key auth is disabled on both data
services, so there is no credential in the repo because there is no credential.

**[ad-optimizer](https://github.com/yght/ad-optimizer)** · Python + Claude, 2025–26
Thompson sampling to allocate ad traffic, an LLM to write the copy, and a
deterministic validator that trusts neither. 120 tests, none of which call an API.

---

### If you're short on time

Read **[sim-platform's carrier normaliser](https://github.com/yght/sim-platform/blob/main/services/carrier-service/src/domain/normalize.js)**
or **[message-web's reconciliation reducer](https://github.com/yght/message-web/blob/main/src/messages/messageReducer.ts)**.
Both expose the domain and state-management decisions directly. Read their tests and the README limitations alongside the implementation.

The SIM, React, Azure and ad-optimizer repositories have `docs/adr/` folders. Those are the decisions worth arguing
about, written up with what they cost as well as what they bought.

---

*[LinkedIn](https://www.linkedin.com/in/yousof-ghahremani-31576044/) · y.ghahremani@gmail.com*
