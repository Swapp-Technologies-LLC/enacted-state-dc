# Enacted: District of Columbia Legal Repository (`enacted-state-dc`)

This repository contains verified primary-source records of enacted District of Columbia land-use, housing, and building law, and public water quality measurement records.

**Parent Entity:** Swapp Technologies LLC (Organized in Maryland)  
**Repository Scope:** District of Columbia Land-Use, Municipal Zoning Law & Public Water Quality  
**Posture:** This repository records the enacted law. It does not advise, approve, determine, or certify anything.  

---

## 1. What This Repository Is

Enacted records what changed, when it took effect, and who to ask:
1. **Verbatim Statutory & Measurement Records**: Quoted provisions mechanically extracted from primary enacted instruments and official agency reports.
2. **Deterministic Version History**: Structured changes and legislative chronologies with exact effective dates.
3. **Primary Municipal Contacts**: Official municipal planning, zoning, and utility departments responsible for administering the District.

### Standard Verification Line
*This repository records the enacted law. It does not advise, approve, determine, or certify anything.*  
All text quotes, reports, shows, and records primary government documents. It does not provide legal advice or apply law to specific facts.

---

## 2. Sourcing Standards & Aggregator Blocklist

All records in this repository are derived strictly from primary government portals (Council of the District of Columbia LIMS, District of Columbia Office of Zoning DCOZ, and official water quality publications).

### Aggregator Hard Blocklist
Under Swapp Technologies LLC record integrity rules, third-party code aggregators are strictly blocklisted:
* **Municode** (`municode.com` / CivicPlus)
* **American Legal Publishing** (`amlegal.com`)
* **eCode360** (`ecode360.com` / General Code)

---

## 3. Ingestion Conventions & Multi-Topic Topology

* **Multi-Topic State Repository**: Repositories are organized per state/district (`enacted-state-dc`) containing all topics for that jurisdiction (Land-Use/Zoning, Public Water Quality, Housing).
* **Measurement Records**: Public water measurement records live under `water/measurements/<system_slug>/<parameter>_<year>.md` with explicit per-system attribution, governing limits, compliance dates, and basis.
* **Primary Document Hashes**: Every record file includes the full 64-character SHA-256 hash of the source document fetched at generation time (`source_sha256`).
* **Fetch Timestamps**: Every record file includes the actual wall-clock ISO 8601 UTC timestamp of retrieval (`source_fetched_at`).
