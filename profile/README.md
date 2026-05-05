<div align="center">
  <img src="https://raw.githubusercontent.com/symphonix-health/symphonix-health-docs/main/brand/logos/symphonix-health-logo-dark.svg" alt="Symphonix Health" width="400"/>
  <br/><br/>
  <strong>Governed connectivity for healthcare AI.</strong>
  <br/>
  Move clinical and AI data safely, reliably, and at national scale.
</div>

---

`FHIR R4 · HL7v2 · CDA · X12 · DICOM · SNOMED CT · ICD-10/11 · OpenHIE · GHARRA · Nexus A2A`

---

## PLATFORM

Symphonix Health is the orchestration layer for health systems deploying AI. Four planes — Integration, Communication, Intelligence, and Execution — running as a single coherent platform across national and organisational boundaries.

| Product | Role | Repo |
|---|---|---|
| **BulletTrain** | FHIR R4-native health information exchange. 160+ microservices. SignalBox capability control plane. FCG persona governance. OpenHIE-aligned. | [BulletTrain](https://github.com/symphonix-health/BulletTrain) |
| **GHARRA** | Global Healthcare Agent Registry & Routing Authority. DNS for healthcare AI agents. Three-tier federation (Root → Sovereign → Org). Zero-PHI, ABAC, 13-point route admission. | [global-agent-registry](https://github.com/symphonix-health/global-agent-registry) |
| **Nexus A2A** | Agent-to-agent JSON-RPC 2.0 protocol for clinical delegation chains. 25 agents across ED triage, hospital, telemed, consent, and multi-network groups. | [nexus-a2a-protocol](https://github.com/symphonix-health/nexus-a2a-protocol) |
| **Bevan LLM** | In-house clinical reasoning model for terminology mapping, diagnostics, and safety validation. | *(private)* |

---

## AGENT ECOSYSTEM

| Repo | What it does |
|---|---|
| [caid-agent](https://github.com/symphonix-health/caid-agent) | Full-SDLC AI orchestrator. 440-pattern taxonomy, multi-agent teams (2–4 engineers), CSAA integration, ISO/IEC 25010:2023 NFR derivation. |
| [REA-Agent-mcp](https://github.com/symphonix-health/REA-Agent-mcp) | Requirements Engineering Agent — 18 MCP tools. Pattern-to-requirement derivation, QA (12 smells), ISO 29148 SRS, BDD Gherkin, HL7v2→FHIR bridge. |
| [signalbox-mcp](https://github.com/symphonix-health/signalbox-mcp) | Browser automation testing MCP server. 20 tools, 15 assertion types, persona-aware RBAC testing, visual regression. `pip install signalbox-mcp`. |
| [csaa](https://github.com/symphonix-health/csaa) | Clinical Safety Assurance Agent. DCB0129/DCB0160 scope classification, hazard-log seeding, CRMP + Clinical Safety Case Report generation. |
| [prompt-engine](https://github.com/symphonix-health/prompt-engine) | YAML-driven composable prompt assembly. Reasoning clauses, governance policies, multi-agent optimisation. Domain-agnostic. |
| [triage-api](https://github.com/symphonix-health/triage-api) | Clinical risk triage FastAPI reference. 20-component observability (9 traditional + 11 AI-specific), Prometheus metrics, multi-model coexistence. |

---

## CLINICAL APPLICATIONS

All applications are built on Python 3.12 + FastAPI + React 18 + Vite + TypeScript, generated and quality-gated by caid-agent.

### Acute & Emergency

| Repo | Summary |
|---|---|
| [ambulance-ems](https://github.com/symphonix-health/ambulance-ems) | CAD/EMS platform. Manchester Triage, Haversine geospatial dispatch, PostGIS, SSE+WebSocket, ePRF. DCB0129/DCB0160/UK ARP. |
| [picis-system](https://github.com/symphonix-health/picis-system) | Acute clinical information system. ADT context, ED flow, ward/ICU/theatre boards, critical results, BCMA, handover, safety hazards. |
| [blood-transfusion](https://github.com/symphonix-health/blood-transfusion) | Blood transfusion and blood-bank workflow surface. BulletTrain IJM Layer 2 sibling. |
| [triage-api](https://github.com/symphonix-health/triage-api) | Standalone clinical risk scoring API with full AI observability stack. |

### Primary & Community Care

| Repo | Summary |
|---|---|
| [gp-system](https://github.com/symphonix-health/gp-system) | England primary care. Prescribing, referrals, results, GP Connect, national RBAC. Full CAID/REA artefacts. |
| [community-nursing](https://github.com/symphonix-health/community-nursing) | District nursing: caseload priority, geographic visit planning, wound-care evidence, syringe-driver records, CSDS extracts. |
| [epaccs](https://github.com/symphonix-health/epaccs) | Electronic Palliative Care Coordination System. ReSPECT v3, ADRT, DNACPR, preferred-place authoring, LPA H&W proxy, consent envelope. |
| [screening-recall](https://github.com/symphonix-health/screening-recall) | Population screening recall and invitation management. BulletTrain HIE sibling. |
| [clinical-pathways](https://github.com/symphonix-health/clinical-pathways) | NICE/WHO pathway personalisation and execution engine. FHIR R4 ServiceRequest emission, 90-day dedup, BridgeSDK integration. |

### Maternity & Neonatal

| Repo | Summary |
|---|---|
| [maternity-system](https://github.com/symphonix-health/maternity-system) | Integrated maternity record: booking to discharge, MSDS, CTG-linked escalation, perinatal outcomes, PMRT package creation. |

### Pharmacy & Prescribing

| Repo | Summary |
|---|---|
| [pharmacy-system](https://github.com/symphonix-health/pharmacy-system) | Hospital dispense. FHIR MedicationRequest inbound, dispense FSM, CD register (Schedule 2/3), FP10 national BSA reimbursement, GPhC validation. |
| [eps](https://github.com/symphonix-health/eps) | Electronic Prescription Service clinical workflow simulator. BulletTrain HIE sibling. |
| [etps](https://github.com/symphonix-health/etps) | Electronic Transfer of Prescriptions transport simulator. Wire-pair with `symphonix-eps-ig`. |

### Diagnostics & Imaging

| Repo | Summary |
|---|---|
| [lis](https://github.com/symphonix-health/lis) | Laboratory Information System. Specimen FSM, Westgard QC (6 rules), MLLP HL7 (port 2575), ASTM E1394, RCPath critical-value paging. ISO 15189. |
| [pacs-ris](https://github.com/symphonix-health/pacs-ris) | DICOM C-STORE (AE title PACS_RIS, port 11112), DICOMweb WADO-RS, radiology report FSM, IR(ME)R 2017 justification, critical-finding paging ≤60 min SLA. |
| [genomics-interpretation](https://github.com/symphonix-health/genomics-interpretation) | Genomics variant interpretation and clinical reporting. BulletTrain HIE sibling. |

### Mental Health & Legislation

| Repo | Summary |
|---|---|
| [mha-administration](https://github.com/symphonix-health/mha-administration) | Mental Health Act administration. Statutory detention workflows, tribunal management, Section tracking. |

### Mortuary & Death Certification

| Repo | Summary |
|---|---|
| [mortuary-and-me](https://github.com/symphonix-health/mortuary-and-me) | Medical Examiner death-certification system. MCCD drafting and signing, coroner referral, mortuary chain-of-custody, organ/tissue donation. Health and Care Act 2022 s.169. |

### Oncology

| Repo | Summary |
|---|---|
| [cancer-pathway-tracker](https://github.comix-health/cancer-pathway-tracker) | Cancer pathway tracking. 62-day RTT targets, MDT coordination, staging, treatment planning. BulletTrain HIE sibling. |

### Administrative & Financial

| Repo | Summary |
|---|---|
| [appointment-system](https://github.com/symphonix-health/appointment-system) | FHIR R4 Slot/Appointment booking. Nexus-A2A JSON-RPC inbound, GHARRA federated discovery, BT notification centre. 500/500 acceptance scenarios. |
| [provider-portal](https://github.com/symphonix-health/provider-portal) | Clinician + receptionist portal. Write-path into BulletTrain HIE. TOTP MFA, AES-256-GCM at rest, bcrypt ≥12, WCAG 2.2 AAA. |
| [insurance-eclaims](https://github.com/symphonix-health/insurance-eclaims) | X12 EDI clearinghouse. 837P/I/D, 835, 270/271, 278. AS2/SFTP ingest, deterministic adjudication, CARC+RARC denial management. HIPAA / HITECH. |
| [erp](https://github.com/symphonix-health/erp) | Healthcare enterprise ERP. GL, AP, AR, Procurement, Inventory, HR, Payroll. Period-close gate, four-eyes approval, multi-currency, national GAM / FRS 102 compliance. |
| [supply-chain-erp](https://github.com/symphonix-health/supply-chain-erp) | Hospital supply-chain. Multi-stockroom inventory, allocation FSM, PO automation (X12 850), 3PL integration, cold-chain breach, MHRA/FDA UDI. |
| [scheduling-gateway](https://github.com/symphonix-health/scheduling-gateway) | Modality router (port 8135). Routes FHIR R4 ServiceRequest referrals between appointment-system and orchestra-telemedicine. |
| [analytics-bi](https://github.com/symphonix-health/analytics-bi) | Healthcare analytics BI. Star-schema warehouse, ETL from 6 sibling services, embedded dashboards, row-level security, freshness-SLA. |

### Population Health

| Repo | Summary |
|---|---|
| [HMIS](https://github.com/symphonix-health/HMIS) | WHO-aligned aggregate health reporting. Validation rules, approval workflow, derived indicators, surveillance alerts, FHIR R4 MeasureReport to analytics-bi. PII-free. |
| [kenya-uhc-implementation](https://github.com/symphonix-health/kenya-uhc-implementation) | Kenya SHA/SHIF UHC digitalisation. 1,200 test scenarios across 12 use cases. Makueni County 90-day pilot. 100% pass rate. |

---

## INFRASTRUCTURE & SDKS

| Repo | What it does |
|---|---|
| [symphonix-bridge-sdk](https://github.com/symphonix-health/symphonix-bridge-sdk) | Protocol translation SDK. 12 adapters: FHIR R4, HL7v2, DICOM, X12, CDA, REST, Nexus A2A, MCP, Kafka, gRPC, WebSocket, SSE. CanonicalEnvelope pivot. |
| [symphonix-emulator-kit](https://github.com/symphonix-health/symphonix-emulator-kit) | External-system emulator framework. Fixture / LLM / proxy backends, `@touchpoint` decorator, coverage reporting. Used by all sibling services. |
| [symphonix-eps-ig](https://github.com/symphonix-health/symphonix-eps-ig) | FHIR R4 Implementation Guide for EPS. SUSHI profiles, extensions, ValueSets, CapabilityStatements. national Digital EPS / IHE Pharm MPD aligned. CC0-1.0. |
| [design-system](https://github.com/symphonix-health/design-system) | Brand, visual language, and UI kit. Deep indigo-violet palette, DM Sans, JetBrains Mono, 8-stop rainbow ECG motif. |
| [symphonix-health.github.io](https://github.com/symphonix-health/symphonix-health.github.io) | Documentation site (Jekyll). Getting started, architecture, Nexus A2A spec, per-product docs. |
| [symphonix-health-docs](https://github.com/symphonix-health/symphonix-health-docs) | Brand assets, marketing, country pages (🇬🇭 🇰🇪 🇷🇼 🇳🇬 🇬🇧 🇮🇪 🇦🇪), research, strategy. |
| [symphonix-public](https://github.com/symphonix-health/symphonix-public) | Public marketing website. Cloudflare Pages deployment. |

---

## EXTERNAL SIBLINGS

These products share Symphonix ecosystem patterns (port-config, emulator-kit, design-system, scenario runner) but operate under independent governance, licensing, and mission.

| Product | Organisation | Summary |
|---|---|---|
| [africa-marketplace](https://github.com/Tedam-Technologies-Ghana/africa-marketplace) | Tedam Technologies Ghana | OneGhana — open, chat-native, voice-first marketplace. 15 services, 1,753 pytest passing, 44 Playwright E2E. Ghana pilot → pan-African rollout. Apache 2.0. |
| [elocute](https://github.com/Tedam-Technologies-UK-Ltd/elocute) | Tedam Technologies UK Ltd | Quadrimodal accent acquisition and transformation. Elocute Learn (6-stage RL cycle, 44 RP phonemes) + Elocute Live (real-time, 250ms latency budget, HiFi-GAN/Wav2Lip). 167 requirements, 1,200 test scenarios. Proprietary. |

---

## STANDARDS & COMPLIANCE

`FHIR R4` · `HL7 v2` · `DICOM` · `X12 EDI` · `OpenHIE` · `IHE` · `SNOMED CT` · `ICD-10/11` · `LOINC` · `RxNorm` · `dm+d`  
`DCB0129` · `DCB0160` · `ISO 15189` · `IR(ME)R 2017` · `national GAM` · `UK FRS 102` · `SOX` · `HIPAA` · `HITECH`  
`EU AI Act` · `GDPR` · `Data Protection Act 2019` · `EU MDR 2017/745` · `GDHCN` · `WHO HMIS guidelines`

---

## TARGET MARKETS

🇬🇭 Ghana · 🇰🇪 Kenya · 🇷🇼 Rwanda · 🇳🇬 Nigeria · 🇬🇧 United Kingdom · 🇮🇪 Ireland · 🇦🇪 UAE

---

<div align="center">
  <a href="https://symphonix.health">symphonix.health</a> &nbsp;·&nbsp;
  <a href="https://github.com/symphonix-health/symphonix-health.github.io">Documentation</a> &nbsp;·&nbsp;
  <a href="mailto:hello@symphonix.health">hello@symphonix.health</a>
</div>
