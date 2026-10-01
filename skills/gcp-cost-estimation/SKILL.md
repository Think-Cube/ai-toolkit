---
name: gcp-cost-estimation
description: Estimate and compare Google Cloud infrastructure costs using documented assumptions, current public pricing, and transparent calculation methods. Use for architecture estimates, service comparisons, regional pricing analysis, and cost-driver identification and cost-optimization recommendations.
---

# Google Cloud Cost Estimation & Optimization

Use this skill to prepare transparent, decision-ready Google Cloud cost estimates for architecture sizing, pre-sales, implementation planning, service comparisons, and cost-optimization reviews.

## Core Responsibilities

- Translate the architecture into a bill of materials: Google Cloud service, SKU, region or multi-region, quantity, configuration, usage unit, billing model, and expected consumption.
- Use Google Cloud Pricing Calculator, the Cloud Billing Catalog API, or current official Google Cloud pricing pages. Prefer current, source-linked prices over remembered values.
- Match the exact region, machine type, operating system, licensing model, disk type, and SKU unit before using a price.
- Do not mix on-demand, committed-use discounts, sustained-use discounts, Spot VMs, and enterprise discounts in a single total unless the billing scenario explicitly states it.
- Calculate recurring and consumption-based costs for compute, storage, requests, data processing, monitoring, backup, and usage as applicable.
- Separate recurring infrastructure costs from non-comparable items such as migration effort, support, licensing, taxes, and one-time costs. Provide monthly and, where useful, annual totals.
- Compare on-demand pricing, committed-use discounts, sustained-use discounts, and Spot VMs only when their eligibility and terms are explicitly stated.
- Identify the biggest cost drivers, uncertainty, architectural trade-offs, and optimization opportunities for each service.

## Required Inputs

Request or explicitly state the Google Cloud location, billing currency, environments, service configuration, expected usage profile, availability and resilience requirements, billing model, discount assumptions, and inclusions/exclusions.

For usage-sensitive services, capture hours, vCPU and memory, requests, operations, data transfer, storage and growth, retention, log volume, and monthly active usage as applicable. When material inputs are missing, use clearly labeled low/expected/high assumptions; never silently invent workload volumes, utilization, or discounts.

## Estimation Workflow

1. Confirm scope, location, currency, time period, billing model, and environments.
2. Create a bill of materials covering all measurable Google Cloud services and SKUs.
3. Find official current prices and record the source URL or Catalog API query plus the retrieval date.
4. Calculate each line item with its stated SKU unit and show the formula.
5. Include applicable network egress, external IP, load balancing, Cloud NAT, Cloud Logging ingestion and retention, backup, snapshots, KMS, and support.
6. Keep recurring, consumption-based, and one-time totals separate. Provide monthly and, where useful, annual totals.
7. Present low/expected/high ranges for uncertain or variable consumption.
8. Validate units, locations, currencies, pricing terms, and quantities. Flag missing information and pricing ambiguity.
9. Offer prioritized optimization options without compromising required resilience, security, performance, or compliance.

## Required Output Format

### Assumptions

List location, currency, price retrieval date, month length, workload assumptions, billing model, discounts, and explicit exclusions.

### Monthly Cost Estimate

| Service | Configuration / SKU | Quantity and usage | Unit price | Monthly estimate | Pricing source |
|---|---|---|---|---|---|

### Cost Summary

| Category | Monthly cost | Annualized cost | Notes |
|---|---|---|---|

### Cost Drivers and Optimization Opportunities

Rank each recommendation with estimated saving, prerequisite, trade-off, and risk.

### Limitations

State price volatility, exclusions, usage uncertainty, and that the result is an estimate rather than an invoice or contractual quote.

## Pricing and Calculation Rules

- Treat public Google Cloud prices as list prices. They do not represent negotiated enterprise discounts, taxes, credits, promotions, partner pricing, or the final invoice.
- Do not mix on-demand, Spot VM, sustained-use, and committed-use rates in a total unless the proposed usage model explicitly uses each one.
- Model tier thresholds, free allowances, and automatic sustained-use discounts where applicable; do not apply discounts that do not qualify.
- Treat network egress as a separate cost driver. Identify traffic paths, source and destination locations, and volumes before pricing.
- Do not assume that a service includes Cloud Logging, external IP, Cloud NAT, backup, KMS, or network-transfer costs.
- Do not use or expose billing-account credentials, invoices, contracts, or customer billing data unless explicitly authorized and available through an approved runtime method.

## Optimization Principles

- Right-size compute from measured or forecast utilization and headroom.
- Use committed-use discounts only for stable baseline usage; use Spot VMs only for interruptible workloads.
- Review non-production schedules, autoscaling, storage classes, lifecycle policies, idle resources, egress paths, log retention, and data processing.
- Explain the reliability, security, operational, and performance effect of every cost-saving recommendation.

## Quality Expectations

- Provide reproducible arithmetic and units for every non-trivial line item.
- Cite official price sources and retrieval dates.
- Ask targeted follow-up questions when missing inputs materially affect cost.
- Keep the estimate independently reviewable by technical and financial stakeholders.
