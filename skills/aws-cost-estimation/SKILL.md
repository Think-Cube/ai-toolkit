---
name: aws-cost-estimation
description: Estimate and compare AWS infrastructure costs using documented assumptions, current public pricing, and transparent calculation methods. Use for architecture estimates, service comparisons, regional pricing analysis, and cost-driver identification and cost-optimization recommendations.
---

# AWS Cost Estimation & Optimization

Use this skill to prepare transparent, decision-ready AWS cost estimates for architecture sizing, pre-sales estimates, implementation planning, service comparisons, and cost-optimization reviews.

## Core Responsibilities

- Translate the architecture into a bill of materials: AWS service, region, configuration, usage unit, quantity, billing model, and expected consumption.
- Use the AWS Pricing Calculator, the AWS Price List APIs, and current official AWS pricing pages. Prefer current, source-linked prices over remembered values.
- Match the exact region, instance family and size, operating system, licensing model, tenancy, storage class, and meter unit before using a price.
- Do not mix on-demand, Spot, Savings Plans, and Reserved Instance rates in a total unless the proposed usage model explicitly uses each one.
- Calculate recurring and consumption-based costs for compute, storage, requests, data transfer, monitoring, backup, and usage as applicable.
- Separate recurring infrastructure costs from non-comparable items such as migration effort, licensing, taxes, and one-time costs. Provide monthly and, where useful, annual totals.
- Compare on-demand pricing, Savings Plans, and Reserved Instances only when their eligibility and terms are explicitly stated.
- Identify the largest cost drivers, uncertainty ranges, architectural trade-offs, and optimization opportunities for each service.

## Required Inputs

Request or explicitly state the AWS region, billing currency, environments, service configuration, expected usage profile, availability and resilience requirements, billing assumptions, discount assumptions, and inclusions/exclusions.

For usage-sensitive services, capture hours, requests, API calls, data transfer, storage size and growth, IOPS or throughput, retention, log volume, and monthly active usage as applicable. When material inputs are missing, use clearly labeled low/expected/high assumptions; never silently invent workload volumes, utilization, or discounts.

## Estimation Workflow

1. Confirm scope, region, currency, time period, billing model, and environments.
2. Produce a bill of materials covering all measurable AWS services and meters.
3. Find official current prices and record the source URL or API query plus the retrieval date.
4. Calculate each line item with its stated meter unit and show the formula.
5. Include applicable data transfer, NAT Gateway, load balancing, public IPv4 costs, AWS Support plans, licensing, taxes, and excluded costs.
6. Keep recurring, consumption-based, and one-time totals separate. Provide monthly and, where useful, annual totals.
7. Present low/expected/high ranges for uncertain or variable consumption.
8. Validate units, locations, currencies, pricing terms, and quantities. Flag missing information and pricing ambiguity.
9. Offer prioritized optimization options without compromising required resilience, security, performance, or compliance.

## Required Output Format

### Assumptions

List the region, currency, price retrieval date, month length, workload assumptions, billing model, discounts, and explicit exclusions.

### Monthly Cost Estimate

| Service | Configuration / meter | Quantity and usage | Unit price | Monthly estimate | Pricing source |
|---|---|---|---|---|---|

### Cost Summary

| Category | Monthly cost | Annualized cost | Notes |
|---|---|---|---|

### Cost Drivers and Optimization Opportunities

Rank each recommendation with estimated saving, prerequisite, trade-off, and risk.

### Limitations

State price volatility, exclusions, usage uncertainty, and that the result is an estimate rather than an invoice or contractual quote.

## Pricing and Calculation Rules

- Treat public AWS prices as list prices. They do not represent private pricing, enterprise discounts, taxes, credits, promotions, partner pricing, or the final invoice.
- Do not mix on-demand, Spot, Savings Plans, and Reserved Instance rates in a total unless the proposed usage model explicitly uses each one.
- Model tier thresholds and free-tier allowances where relevant.
- Treat data transfer as a separate cost driver. Identify traffic paths, availability zones, regions, destinations, and volumes before pricing it.
- Do not assume that an AWS service includes CloudWatch logs, NAT Gateway, public IPv4, backup, KMS, or network-transfer costs.
- Do not use or expose account credentials, invoices, contracts, or CUR exports, or customer billing data unless explicitly authorized and available through an approved runtime method.

## Optimization Principles

- Right-size compute from measured or forecast utilization and headroom.
- Use Savings Plans or Reserved Instances only for stable baseline usage; use on-demand capacity for variable demand and Spot only for interruptible work.
- Review non-production schedules, autoscaling, storage tiers, lifecycle policies, idle resources, data-transfer paths, log retention, and NAT use.
- Explain the reliability, security, operational, and performance effect of every cost-saving recommendation.

## Quality Expectations

- Provide reproducible arithmetic and units for every non-trivial line item.
- Cite official price sources and retrieval dates.
- Ask targeted follow-up questions when missing inputs materially affect cost.
- Keep the estimate independently reviewable by technical and financial stakeholders.
