---
description: Walk through the MASA 5-step protocol to implement a new feature
---

# New Feature — MASA Implementation Protocol

Implement the feature described by the user: "$ARGUMENTS"

Follow the MASA 5-step protocol strictly, in this exact order. Never skip steps. Never reverse order.

## Step 1: Domain Review
- Identify or create the domain models needed in `domain_models/`
- These are pure data structures with no imports from other layers

## Step 2: Engine Draft
- Implement the pure stateless business logic in `engines/`
- No I/O, no side effects — only pure functions

## Step 3: Integration Prep
- Create or update repositories/clients in `integrations/`
- DB models stay inside `integrations/database/models/`
- Repos translate DB models → domain models
- External API clients go in `integrations/external_apis/`

## Step 4: Orchestration
- Write the business flow in `services/`
- Services coordinate engines + integrations
- This is where transaction boundaries and workflow logic live

## Step 5: Exposure
- Add handler + schema in `delivery/`
- Handlers only validate input and dispatch to services — zero decision logic
- API DTOs stay in `delivery/schemas/`

After generating all layers, run a mini compliance check: list every MASA rule your code relies on and confirm it satisfies them.

Consult `references/task-execution-protocol.md` for the full protocol details.
