# Legal Provenance & Ingestion Specifications: District of Columbia Corpus

**Repository:** `enacted-state-dc`  
**Parent Entity:** Swapp Technologies LLC (Organized in Maryland)  
**Corpus Scope:** Primary Government Records of Enacted District of Columbia Law  

---

## 1. The Hard Generation Rule (Record Integrity)

No legislative record file exists in this repository without a primary government source document fetched at generation time (HTTP 200), verified by cryptographic hash and recorded timestamp. Quoted statutory text is mechanically extracted from the fetched document, never drafted from memory.

### Required Record Metadata Fields
Every legislative record file in `council_bills/` carries structured YAML frontmatter:
* `primary_source_url`: The canonical government legislative matter or portal URL.
* `source_pdf`: Direct download URL of the primary enacted instrument.
* `source_sha256`: Cryptographic SHA-256 hash of the exact binary payload fetched at generation time.
* `source_fetched_at`: Actual wall-clock ISO 8601 UTC timestamp of the retrieval that produced `source_sha256`.
* `action_status`: Legislative status (`Enacted`, `Adopted`, `Introduced`, `Worksession`, `Withdrawn`, `Vetoed`). Unknown dates render `[pending verification]`, never null.
* `effective_date`: Authoritative date the enactment takes legal effect.

---

## 2. Authoritative Primary Sourcing & Hard Aggregator Blocklist

All corpus records are ingested exclusively from official government portals:
* **Council of the District of Columbia:** (`dccouncil.gov` and `lims.dccouncil.gov`)
* **District of Columbia Office of Zoning:** (`dcoz.dc.gov`)
* **DC Water:** (`dcwater.com`)

### Hard Blocklist
Third-party code aggregators and commercial publishers are strictly prohibited from serving as sources:
* `municode.com` (CivicPlus / Municode)
* `amlegal.com` (American Legal Publishing)
* `ecode360.com` (General Code)
