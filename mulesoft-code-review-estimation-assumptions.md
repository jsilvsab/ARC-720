# MuleSoft Code Review — Estimation & Assumptions

## 1. Introduction

This document provides the assumptions and high-level estimation for performing a **MuleSoft Code Review** across all APIs, based on the standardized review sheet.  
The review will assess each API implementation against the defined **Rule Descriptions**, grouped by topics such as Project Structure, Logging, Error Handling, Security, and Performance.  

The goal is to ensure that all APIs follow MuleSoft best practices and organizational standards, and to provide visibility on gaps and remediation areas.  

---

## 2. Assumptions

- **Scope**  
  - The review is limited to static analysis of code, configurations, and design artifacts.  
  - Each API will be reviewed against the rules listed in the Code Review Sheet.  
  - No load testing, penetration testing, or production validation is included.  
  - Each API receives one completed review document.  

- **Access**  
  - Read-only access to Git repositories containing the Mule projects.  
  - Read-only access to Anypoint Exchange (RAML/**RESTful API Modeling Language** or **OAS – OpenAPI Specification**) and API Manager (policies applied).  
  - Documentation of NFRs (**Non-Functional Requirements**) is available if referenced in the sheet.  

- **Consistency**  
  - The same template and checklist will be applied across all APIs.  
  - Missing information will be flagged as *Not Available* instead of investigated further.  

- **Effort Unit**  
  - One working day equals **8 hours (1 Person-Day, PD)**.  
  - Estimates are per API; overheads are listed separately.  

- **Out of Scope**  
  - Creating missing RAML/OAS/WSDL.  
  - Writing or executing tests (MUnit or others).  
  - Fixing code or CI/CD pipeline validation.  

---

## 3. Estimation per Topic (per API)

| Topic / Rule Group               | Effort (h) | What’s included |
|----------------------------------|------------|-----------------|
| **I. Project Structure**         | **0.8** | Mavenization; `.gitignore`; `src/main` vs `src/test`; DW (**DataWeave**) files location; sample data; RAML/WSDL presence; environment properties; package layout. |
| **II. Naming & Versioning**      | **0.5** | Repo vs project/artifactId alignment; API naming conventions; semantic versioning; WSDL versioning. |
| **III. Properties & Configuration** | **0.8** | Environment-specific properties; secure properties; no hard-coded secrets; `finalName` in POM. |
| **IV. Logging Practices**        | **1.0** | Structured logs; **CID (Correlation ID)** propagation; log levels; exclusion of sensitive data. |
| **V. Error Handling**            | **1.1** | Global error handlers; taxonomy; standard error responses; retry strategies; batch error handling. |
| **VI. Security**                 | **1.5** | API Manager policies (Client-ID Enforcement, **OAuth2**, **JWT – JSON Web Token** validation); **TLS – Transport Layer Security**; secrets storage; outbound credentials. |
| **VII. Testing & Quality**       | **0.9** | Presence of `src/test` with MUnit tests; sample data in resources; assertions visible in code. |
| **VIII. Performance & Resilience** | **1.0** | Timeouts, retries, circuit breakers; streaming; payload size; batch concurrency/locks; DLQ (**Dead Letter Queue**) usage. |
| **IX. Documentation & Governance** | **0.4** | Exchange documentation; RAML/OAS annotations; README; alignment with governance standards. |
| **Total per API**                | **8.0h (≈ 1 PD)** | — |

---

## 4. Overall Estimation (all APIs)

- **Per API**: 1 PD (8h)  
- **Total for 28 APIs**: **28 PD**  

**Overheads**  
- Template alignment & kick-off: 1–1.5 PD  
- Consolidation & cross-API synthesis (summary tables, top gaps/quick wins): 2–3 PD  
- Buffer (10% of subtotal): ~2.8 PD  

**Grand Total:** ~33–35 PD  

---

## 5. Deliverables

- Completed **Code Review Sheet** for each API (Excel).  
- Consolidated overview of findings per topic (summary table).  
- Highlighted gaps and quick recommendations.  

---

## 6. Glossary

- **PD – Person-Day**: one working day (8h).  
- **RAML – RESTful API Modeling Language**: contract definition for REST APIs.  
- **OAS – OpenAPI Specification**: contract definition for REST APIs (formerly Swagger).  
- **WSDL – Web Services Description Language**: contract definition for SOAP APIs.  
- **DW/DWL – DataWeave / DataWeave Language file**: MuleSoft transformation language files.  
- **TLS – Transport Layer Security**: HTTPS-based encryption.  
- **JWT – JSON Web Token**: token format for authentication/authorization.  
- **CID – Correlation ID**: unique identifier passed across calls for tracing.  
- **DLQ – Dead Letter Queue**: queue used to capture failed messages.  
- **NFR – Non-Functional Requirement**: requirements like performance, scalability, reliability.  
