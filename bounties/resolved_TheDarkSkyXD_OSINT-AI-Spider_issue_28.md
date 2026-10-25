# Automated Bounty Resolution

- **Issue:** https://github.com/TheDarkSkyXD/OSINT-AI-Spider/issues/28
- **Title:** Define investigation template defaults and acceptance criteria
- **Reward:** $50 USDT (BEP-20)
- **Payout Address:** `0x1c088878957d52736337ec7a000d335a204e9b71`
- **Submitted By:** @Dungsky
- **Timestamp:** 2026-10-25T17:59:09.942Z

## Solution Summary
Created a comprehensive, versioned investigation template defaults and acceptance criteria specification covering general, missing-person, criminal, cyber, financial, GitHub/code, and bug-bounty investigations.

## Solution Code / Content
```
# OSINT-AI-Spider Investigation Templates & Acceptance Criteria Specification

Version: `1.0.0`
Target Framework: Wayfinder AI OSINT Spider

## Overview
This document defines the versioned defaults, intake fields, Capability packs, sensitivity levels, authorization requirements, bounded research plans, workflow guidance, and completion/review criteria for the 7 core approved investigation templates.

--- 

## 1. General Investigation Template (`general-v1.0.0`)

### Intake Fields
- `target_identifier` (String, Required): Name, alias, domain, or handle.
- `objective_statement` (Text, Required): High-level summary of the inquiry goal.
- `timeframe_focus` (Enum: `recent`, `historical`, `all`, Default: `all`).

### Suggested Capability Packs
- `core-search`, `social-profiler`, `metadata-extractor`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `Low-Medium`
- `authorization_requirement`: `Standard Terms Acknowledgment`
- `pii_redaction`: `Enabled`

### Bounded Research-Plan Defaults
- `max_depth`: `3`
- `allowed_sources`: `Public Web, Open Repositories, Public Social Media`
- `excluded_sources`: `Deep Web, Dark Web, Restricted Databases`

### Workflow Guidance
1. Run broad entity resolution.
2. Aggregate public footprints.
3. Synthesize findings into structured timeline.

### Completion & Review Criteria
- `completion_trigger`: All intake entities queried across approved capability packs.
- `review_criteria`: Verification of source URL validity, elimination of duplicate profiles, compliance with PII redaction policy.

---

## 2. Missing Person Investigation Template (`missing-person-v1.0.0`)

### Intake Fields
- `full_name` (String, Required)
- `last_known_location` (String, Required)
- `last_seen_timestamp` (Datetime, Required)
- `distinguishing_features` (Text, Optional)
- `known_digital_handles` (List of Strings, Optional)

### Suggested Capability Packs
- `geo-locator`, `social-profiler`, `emergency-aggregator`, `image-forensics`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `High`
- `authorization_requirement`: `Next-of-Kin or Law Enforcement Verification`
- `pii_redaction`: `Disabled (for authorized operational use)`

### Bounded Research-Plan Defaults
- `max_depth`: `5`
- `allowed_sources`: `Public Social Media, Local News, Public Records, Geo-tagged Feeds`
- `excluded_sources`: `None (High-priority override enabled)`

### Workflow Guidance
1. Immediate digital footprint scan on known handles.
2. Geolocation analysis of last active posts/pings.
3. Cross-reference public emergency data feeds.

### Completion & Review Criteria
- `completion_trigger`: Exhaustion of all digital footprint nodes and real-time social activity matching.
- `review_criteria`: Human-in-the-loop validation mandatory prior to publishing lead summaries. High sensitivity protocol engagement.

---

## 3. Criminal Investigation Template (`criminal-v1.0.0`)

### Intake Fields
- `case_reference_number` (String, Required)
- `suspect_identifiers` (List of Strings, Required)
- `allegation_summary` (Text, Required)
- `jurisdiction` (String, Required)

### Suggested Capability Packs
- `blockchain-tracer`, `dark-web-monitor`, `public-records`, `telecom-analyzer`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `Critical`
- `authorization_requirement`: `Formal Warrant/Subpoena or Agency ID Validation`
- `pii_redaction`: `Strict Chain-of-Custody Logging Enabled`

### Bounded Research-Plan Defaults
- `max_depth`: `4`
- `allowed_sources`: `Court Records, Regulatory Filings, Public Blockchain, Surface Web Archives`
- `excluded_sources`: `Unverified Social Media Rumor Mills`

### Workflow Guidance
1. Strict evidence tagging and cryptographic hashing of gathered artifacts.
2. Asset and transaction mapping.
3. Association network generation.

### Completion & Review Criteria
- `completion_trigger`: Completion of node association graph and transaction tracing.
- `review_criteria`: Mandatory legal/compliance review of evidence chain and verification of authorized investigative scope.

---

## 4. Cyber Investigation Template (`cyber-v1.0.0`)

### Intake Fields
- `ioc_list` (List of IPs/Domains/Hashes, Required)
- `attack_vector_suspected` (Enum: `phishing`, `malware`, `ddos`, `ransomware`, `unauthorized_access`, Default: `malware`)
- `incident_timestamp` (Datetime, Required)

### Suggested Capability Packs
- `threat-intel`, `dns-recon`, `whois-analyzer`, `sandbox-runner`, `github-code-scanner`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `High`
- `authorization_requirement`: `Asset Ownership or Incident Response Mandate`
- `pii_redaction`: `Standard`

### Bounded Research-Plan Defaults
- `max_depth`: `3`
- `allowed_sources`: `Threat Intelligence Feeds, VirusTotal, Censys, Shodan, Public DNS/WHOIS`
- `excluded_sources`: `Active Offense/Exploitation Modules`

### Workflow Guidance
1. Automated IOC enrichment and threat intelligence lookup.
2. Infrastructure mapping (ASN, hosting provider, certificate transparency logs).
3. Attribution hypothesis generation based on TTPs.

### Completion & Review Criteria
- `completion_trigger`: Full enrichment of all submitted IOCs and infrastructure correlation graph.
- `review_criteria`: Confidence scoring on attribution claims; exclusion of false-positive threat indicators.

---

## 5. Financial Investigation Template (`financial-v1.0.0`)

### Intake Fields
- `entity_name` (String, Required)
- `wallet_addresses_or_accounts` (List of Strings, Required)
- `transaction_hashes` (List of Strings, Optional)
- `time_window` (Date Range, Required)

### Suggested Capability Packs
- `blockchain-tracer`, `regulatory-filings`, `corporate-registry`, `sanctions-checker`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `High`
- `authorization_requirement`: `AML/KYC Compliance Mandate or Financial Audit Scope`
- `pii_redaction`: `Financial Privacy Regulations Compliant`

### Bounded Research-Plan Defaults
- `max_depth`: `5`
- `allowed_sources`: `Public Blockchains, SEC/EDECAR, Offshore Leaks Databases, Global Sanctions Lists`
- `excluded_sources`: `Private Financial Institutions Direct Access`

### Workflow Guidance
1. Multi-hop transaction clustering and taint analysis.
2. Beneficial ownership registry cross-referencing.
3. Sanctions list screening.

### Completion & Review Criteria
- `completion_trigger`: Exhaustion of 5-hop transaction graph or dead-end mixing services.
- `review_criteria`: Verification of heuristic cluster accuracy and documentation of fund flow pathways.

---

## 6. GitHub / Code Investigation Template (`github-code-v1.0.0`)

### Intake Fields
- `repository_url_or_org` (String, Required)
- `target_secrets_or_artifacts` (List of Strings, Optional)
- `commit_history_depth` (Integer, Default: `100`)

### Suggested Capability Packs
- `github-code-scanner`, `secret-detector`, `dependency-auditor`, `author-profiler`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `Medium-High`
- `authorization_requirement`: `Repository Access Authorization or Public Scope Verification`
- `pii_redaction`: `Developer Email Hashing Optional`

### Bounded Research-Plan Defaults
- `max_depth`: `3`
- `allowed_sources`: `Public GitHub/GitLab Repositories, Commit Logs, Issue Trackers, Package Registries`
- `excluded_sources`: `Private Repositories without explicit token`

### Workflow Guidance
1. Deep commit history scan for hardcoded secrets, API keys, and credentials.
2. Dependency vulnerability and supply chain footprint analysis.
3. Contributor alias consolidation and attribution mapping.

### Completion & Review Criteria
- `completion_trigger`: Complete AST scan and commit history parsing for target repository.
- `review_criteria`: Validation of discovered secrets to eliminate false positives; confirmation of clean dependency graph report.

---

## 7. Bug Bounty Investigation Template (`bug-bounty-v1.0.0`)

### Intake Fields
- `program_scope_url` (String, Required)
- `target_assets` (List of Domains/IPs, Required)
- `allowed_attack_types` (List of Strings, Required)

### Suggested Capability Packs
- `subdomain-enum`, `port-scanner`, `tech-stack-fingerprinter`, `endpoint-discovery`, `github-code-scanner`

### Sensitivity & Authorization Defaults
- `sensitivity_level`: `Medium`
- `authorization_requirement`: `Bug Bounty Program Scope Verification & Rules of Engagement Agreement`
- `pii_redaction`: `Standard`

### Bounded Research-Plan Defaults
- `max_depth`: `3`
- `allowed_sources`: `In-Scope Assets Only, Certificate Transparency Logs, Wayback Machine`
- `excluded_sources`: `Out-of-Scope Assets, Third-Party Infrastructure`

### Workflow Guidance
1. Comprehensive subdomain enumeration and asset discovery.
2. Technology stack and outdated component fingerprinting.
3. Endpoint and parameter mapping for vulnerability surface analysis.

### Completion & Review Criteria
- `completion_trigger`: Full asset inventory enumeration within defined program scope boundaries.
- `review_criteria`: Strict adherence to rules of engagement (RoE); verification that zero out-of-scope assets were scanned or queried.
```
