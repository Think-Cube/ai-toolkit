---
name: multi-cloud-cost-comparison
description: Compare Azure, AWS, and Google Cloud cost estimates using equivalent workload assumptions, transparent pricing sources, and clearly stated limitations. Use for multi-cloud architecture decisions, pre-sales comparisons, and FinOps evaluations.
---

# Multi-Cloud Cost Comparison

Use this skill to compare equivalent Azure, AWS, and Google Cloud architecture options. It does not replace cloud-specific cost-estimation skills; use those to prepare individual estimates first.

## Core Responsibilities

- Define a provider-neutral workload baseline and acceptance criteria.
- Create a mapping table from the billing scenario to Azure, AWS, and GCP services, identifying material differences.
- Provide a provider-specific bill of materials and price every line from the official current sources.
- Normalize the time period, currency, workload quantities, VM/SKU scope, and included operational services before comparing totals.
- Calculate monthly and annual totals, separating recurring, variable, and one-time costs.
- Explain cost, resilience, performance, operational portability, and skills trade-offs for each provider.
- Cite the high-level cost drivers for variable usage and identify sensitivity.
- State all limitations and the information that would materially change the recommendation.

## Required Inputs

Request or explicitly state:

- Candidate providers, regions, billing currency, and estimate date.
- Workload architecture and non-functional requirements.
- Environment count and size: production, development, test, DR, and sandbox.
- Usage profile: peak versus average demand, growth assumptions.
- Purchase model: public list price, discounts, reservations/commitments, savings plans, licensing benefits, and any third-party services.
- Whether the comparison should include only cloud consumption or total cost of ownership.

When material inputs are unknown, show low/expected/high scenarios. Never use different assumptions across providers without prominently disclosing them.

## Comparison Workflow

1. Establish a provider-neutral workload baseline and acceptance criteria.
2. Create a mapping table from the billing scenario to Azure, AWS, and GCP services, identifying material differences.
3. Provide a provider-specific bill of materials and price every line from the official current sources.
4. Normalize the time period, currency, workload quantities, VM/SKU scope, and included operational services before comparing totals.
5. Calculate monthly and annual totals, separating recurring, variable, and one-time costs.
6. Explain cost, resilience, performance, operational portability, and skills trade-offs for each provider.
7. Cite the high-level cost drivers for variable usage and identify sensitivity.
8. State all limitations and the information that would materially change the recommendation.

## Required Output Format

### Common Assumptions

List the workload baseline, regions, currency, month length, price retrieval dates, environment scope, discounts, and exclusions.

### Service Mapping

| Workload capability | Azure | AWS | Google Cloud | Equivalence notes |
|---|---|---|---|---|

### Cost Comparison

| Cost category | Azure monthly | AWS monthly | Google Cloud monthly | Comparability notes |
|---|---|---|---|---|

### Annualized Summary

| Provider | Annual recurring cost | One-time cost | Key assumptions | Pricing sources |
|---|---|---|---|---|

### Decision Factors

Describe top cost drivers, non-cost trade-offs, risks, and optimization options for each provider.

### Limitations

State pricing volatility, excluded taxes and negotiated discounts, imperfect service equivalence, usage uncertainty, and that the result is not an invoice or contractual quote.

## Comparison Rules

- Use Azure Retail Prices API or Azure Pricing Calculator, AWS Pricing Calculator or Price List APIs, and Google Cloud Pricing Calculator or Cloud Billing Catalog API as appropriate.
- Treat public prices as list prices; do not infer enterprise discounts, contractual terms, tax treatment, credits, or currency conversion rates.
- Do not compare a single-zone deployment on one provider with a highly available multi-zone deployment on another without labelling the difference.
- Do not mix on-demand and committed rates across providers unless the same commitment logic and baseline utilization are used.
- Show egress, inter-zone, NAT, observability, backup, support, licensing, and security costs separately where they materially affect the comparison.
- Keep migration, retraining, refactoring, operations, and vendor-exit costs separate from cloud consumption unless the requested scope is total cost of ownership.

## Quality Expectations

- Provide reproducible formulas and units for each material cost.
- Cite every price source and retrieval date.
- Clearly distinguish facts, assumptions, estimates, and recommendations.
- Ask targeted follow-up questions when unknown inputs could materially change the comparison.
