# Fundamental research data model (proposed)

This is a storage proposal, not yet implemented in the production database.

## Entities

### issuer
- ticker (stable exchange identifier)
- issuer_name
- sector
- listing_status
- identifiers / aliases

### source
- source_id
- title
- publisher
- url
- source_type (issuer_report, disclosure, exchange, regulator, rating, newswire, aggregator)
- published_at
- retrieved_at
- document_period_start / document_period_end
- local_path_or_hash (optional)
- notes

### observation
- observation_id
- ticker
- metric_name
- value
- currency
- unit
- period_start
- period_end
- published_at
- retrieved_at
- as_of_date
- accounting_basis (IFRS, RAS, adjusted, estimate, etc.)
- evidence_class (reported_fact, calculated_metric, third_party_estimate)
- source_id
- formula / input references (for calculated values)
- quality_flag (verified, needs_review, conflicting, stale)

### corporate_event
- event_id
- ticker
- event_type
- event_date
- published_at
- description
- severity
- source_id
- status (confirmed, issuer_claim, alleged, unverified)

### research_assessment
- assessment_id
- ticker
- as_of_date
- verdict (CLEAR, MONITOR, VETO, INSUFFICIENT_DATA)
- confidence
- facts_summary
- interpretation
- key_risks
- missing_evidence
- what_changes_verdict
- author/reviewer
- supersedes_assessment_id

## Key design constraint
Store the publication timestamp independently from the report period. Historical queries must filter `published_at <= decision_timestamp`; otherwise the database leaks future information into past decisions.

## Valuation inputs
Market price must be date-aligned to the as-of date. Shares outstanding, treasury shares, ADR/depositary ratios and corporate actions need explicit provenance. Derived market cap and multiples must retain formulas and source observations.

## Sector-specific metric namespaces
Avoid comparing generic ratios across banks, insurers, utilities, software, pharma, retail, metals and agro. Keep sector metrics explicit and versioned.
