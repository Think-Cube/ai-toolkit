---
name: azure-cost-estimation
description: Estimate and compare Azure infrastructure costs using documented assumptions, current public pricing, and transparent calculation methods. Use for architecture estimates, service comparisons, regional pricing analysis, and cost-driver identification and cost-optimization recommendations.
---

# Azure Cost Estimation & Optimization

Use this skill to prepare transparent, decision-ready Azure cost estimates. It supports early-stage architecture sizing, pre-sales estimates, implementation planning, SKU and region comparisons, and cost-optimization reviews.

## Core Responsibilities

- Translate the proposed architecture into a bill of materials: Azure service, SKU or meter, region, quantity, billing model, and expected monthly consumption.
- Use the Azure Pricing Calculator or the Azure Retail Prices API as the pricing source. Prefer current, source-linked prices over remembered values.
- Use the Azure Retail Prices API endpoint: `https://prices.azure.com/api/retailprices` (or the `2023-01-01-preview` API version when savings-plan prices are required).
- Match the exact region, service, SKU, operating system, deployment option, licensing model, and meter unit before using a price.
- Calculate recurring monthly cost from hourly, per-operation, per-GB, and per-million-execution rates; include monitoring, network egress, public IP, DNS, security, log-ingestion, and support costs; do not assume they are included.
- Sum monthly totals, and where useful, annual totals. Keep one-time costs separate from recurring totals.
- Present a low/expected/high range for usage-sensitive or uncertain costs.
- Validate that units, regions, currencies, meter types, and quantities are consistent. Flag missing or ambiguous information.
- Offer prioritized optimization options without reducing required resilience, performance, security, or compliance.
- Identify the largest cost drivers, uncertainty ranges, optimization opportunities, and financial trade-offs.

## Required Inputs

Request or explicitly state the following before finalizing an estimate:

- Azure region and billing currency.
- Environment scope, such as development, test, production, disaster recovery, and sandbox.
- Service configuration: SKU, tier, instance or vCore count, storage, redundancy, operating system, and availability requirements.
- Usage profile: hours, requests, transactions, data volume, retention, bandwidth, agents, and expected growth.
- Billing assumptions: pay-as-you-go, reservation term, savings plan, Enterprise Agreement discount, Azure Hybrid Benefit, and licensing rights.
- Inclusions and exclusions, including third-party products, support tiers, implementation effort, taxes, and multi-tenant shared-platform costs.

## Estimation Workflow

1. Confirm scope, region, currency, time period, and billing model.
2. Produce a bill of materials, including every service and measurable meter.
3. Find the relevant public price using the Azure Pricing Calculator or Retail Prices API; record the source URL or API query and the retrieval date.
4. Calculate each line item using the meter's stated unit and show the formula.
5. Add well-known adjacencies: monitoring, network egress, public IP, DNS, security, log-ingestion, and support costs. Do not assume they are included.
6. Sum monthly totals, and where useful, annual totals. Keep one-time costs separate from recurring totals.
7. Present a low/expected/high range for usage-sensitive or uncertain costs.
8. Validate that units, regions, currencies, meter types, and quantities are consistent. Flag missing or ambiguous information.
9. Offer prioritized optimization options without reducing required resilience, performance, security, or compliance.

## Required Output Format

Use this structure unless the requester asks for another format:

### Assumptions

List region, currency, price retrieval date, month length, workload assumptions, billing model, discounts, and explicit exclusions.

### Monthly Cost Estimate

| Service | Configuration / meter | Quantity and usage | Unit price | Monthly estimate | Pricing source |
|---|---|---|---|---|---|

### Cost Summary

| Category | Monthly cost | Annualized cost | Notes |
|---|---|---|---|

### Cost Drivers and Optimization Opportunities

Rank the main drivers and describe the expected saving, prerequisite, trade-off, and any risk for each recommendation.

### Limitations

State price volatility, exclusions, assumptions, uncertain consumption, and the fact that this is an estimate rather than an invoice or contractual quote.

## Pricing and Calculation Rules

- Treat the Retail Prices API as public list pricing. It does not represent negotiated enterprise discounts, taxes, credits, promotions, partner pricing, or the exact final invoice.
- State that USD is the primary Microsoft retail-price currency. If another currency is used, label its source and any foreign-exchange assumption.
- Follow API pagination through `NextPageLink`; do not assume the first page contains all applicable meters.
- Do not mix consumption meters with reservation, savings-plan, or spot-price meters in the same total unless the billing scenario explicitly uses both.
- Do not claim that an estimate is exact, approved, or guaranteed.
- Do not use or expose subscription credentials, invoices, contracts, or customer billing data unless the requester explicitly authorizes the access and the runtime provides an approved method.

## Optimization Principles

- Right-size compute from measured or forecast utilization and headroom.
- Compare reserved capacity and savings plans only against stable baseline usage; retain pay-as-you-go capacity for variable demand.
- Review non-production schedules, auto-shutdown, autoscaling, storage tiers, retention periods, and log-ingestion volumes.
- Prefer architecture-specific recommendations over generic discounts.
- Explain the reliability, operational, security, and performance effect of every cost-saving recommendation.

## Quality Expectations

- Provide reproducible arithmetic and units for every non-trivial line item.
- Cite pricing sources and retrieval dates.
- Ask targeted follow-up questions when missing inputs materially affect cost.
- Keep estimates clear enough for a technical and financial stakeholder to review independently.
