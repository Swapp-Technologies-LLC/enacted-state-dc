# Jurisdiction Go-Live Checklist: DC Enacted Law (`DCCouncil/law-xml`)

**Source:** `DCCouncil/law-xml` (District of Columbia Enacted Law)  
**Publisher:** Council of the District of Columbia  
**Checklist Version:** v1 (Nov 1, 2026; approved Nov 4, 2026, 16:23 ET)  
**Evaluation Date:** 2026-11-04  
**Data Repository:** `enacted-state-dc` (`staging/enacted-state-dc`)  

---

## Part 1 — Before going live

### A. Identify the source
- [x] **A1. Publisher.** PASS.  
  Publisher is the Council of the District of Columbia (Office of the General Counsel). Hosted on GitHub under the official `DCCouncil` organization.  
  *Evidence:* `terms.md`, `README.md`.
- [x] **A2. Official route first.** PASS.  
  Official bulk XML Git repository (`DCCouncil/law-xml`). Specifically requested by `code.dccouncil.gov`: "Please do not scrape. Instead, bulk download the HTML or XML."  
  *Evidence:* `terms.md`, `index.xml`.
- [x] **A3. Not an aggregator.** PASS.  
  Direct legislative source; not Municode, American Legal Publishing, or eCode360.  
  *Evidence:* `SOURCE_ACCESS_REGISTER.md` §2.

### B. Robots.txt (R1, ruled Nov 1)
- [x] **B1. Every host's robots.txt saved.** PASS.  
  Saved locally with status lines and raw response bodies:
  - `robots/api.github.com_2026-11-04.txt` (HTTP/1.1 404 Not Found)
  - `robots/raw.githubusercontent.com_2026-11-04.txt` (HTTP/1.1 404 Not Found)
  - `robots/github.com_2026-11-04.txt` (HTTP/1.1 200 OK)
  - `robots/dccouncil.gov_2026-11-04.txt` (HTTP/1.1 200 OK)  
  *Evidence:* `robots/*.txt`.
- [x] **B2. Every path allowed under R1.** PASS.  
  - `api.github.com`: 404 -> Allowed under R1.
  - `raw.githubusercontent.com`: 404 -> Allowed under R1.
  - `github.com`: 200 -> Allowed (does not disallow repo/raw/API paths).
  - `dccouncil.gov`: 200 -> Allowed (empty disallow).
  - `lims.dccouncil.gov`: Blocked site-wide; zero paths read by EnactedCrawler.  
  *Evidence:* `robots/*.txt`.
- [x] **B3. 401/403 person check.** PASS.  
  Zero 401 or 403 responses returned. No `person_checks.md` required.

### C. Terms and licence
- [x] **C1. Terms read.** PASS.  
  GitHub Terms of Service §H (API terms) & Acceptable Use Policies §7 (Information usage and automated access) quoted. `code.dccouncil.gov` bulk request quoted. Full page copies preserved outside git at `policy_buddy/private/terms_copies/dc/law-xml/`.  
  *Evidence:* `terms.md`.
- [x] **C2. Licence tag.** PASS.  
  Dedicated to the public domain under CC0 1.0 Universal by the Council of the District of Columbia (`dc-law/README.md`, `resources/LICENSE.md`).  
  *Evidence:* `terms.md`.
- [x] **C3. No conflict, or escalated.** PASS.  
  Public domain dedication (CC0) contains no reuse restrictions.  
  *Evidence:* `terms.md`.
- [x] **C4. Permission when needed.** PASS.  
  No special permission required for CC0 public domain bulk download.

### D. Permissions per source (R5, ruled Nov 1)
- [x] **D1. Permissions recorded.** PASS.  
  Draft recorded in `permissions.yaml` with proposed: yes across read, store, display, commercial use; awaiting founder ruling.  
  *Evidence:* `permissions.yaml`.

| Level | Allowed? | Evidence |
|---|---|---|
| Read (crawler may fetch) | proposed: yes (ruled: null) | `robots/*`, `terms.md` |
| Store (keep copies in data repo) | proposed: yes (ruled: null) | `terms.md` (CC0 public domain) |
| Display publicly (enacted.app, social) | proposed: yes (ruled: null) | `terms.md` (CC0 public domain) |
| Commercial use (paid alerts, HouseOver Pro) | proposed: yes (ruled: null) | `terms.md` (CC0 public domain) |

### E. Currency and authority
- [x] **E1. Current.** PASS.  
  Newest commit on default branch (`main`): `4bf03a58c3cb98cb1ff8923ed5d5f2af7738e643` (2026-11-03T23:24:07Z, Alexis Byrd, "11-3-26 commits"). Highest-numbered act: `26-460.xml` committed 2026-11-03T23:24:07Z.  
  *Evidence:* GitHub REST API commits endpoint.
- [x] **E2. Official text.** PASS.  
  Repository contains uncodified session laws and codified acts. The governing statutory source is the enacted act published by the Council and recorded in the DC Register (`73 DCR 5079`).  
  *Evidence:* `terms.md`, `us/dc/council/periods/26/acts/26-281.xml`.
- [ ] **E3. Who to ask.** PENDING (founder).  
  `authority.yaml` contains the Office of the Zoning Administrator, but does not currently contain an entry for the Council (publisher of acts).  
  *Evidence:* `district_of_columbia/authority.yaml`.

### F. Records and accuracy
- [ ] **F1. Supervised first run.** PENDING (founder).  
  Supervised zoning ingest run scheduled with the founder.
- [x] **F2. Integrity gates green.** PASS.  
  All 10 verification gates pass in `verify_corpus_integrity.py`.  
  *Evidence:* `verify_corpus_integrity.py` test run output.
- [ ] **F3. Field accuracy.** PENDING (founder).  
  Act 26-281 status source (`status_source_url`) verified. `published_date` (`2026-03-27`) from LIMS remains unverified against `law-xml` (which records only citation `73 DCR 5079` without publication date), awaiting founder ruling R-DC1.
- [x] **F4. No inference.** PASS.  
  Rule 10 observed; zero inferred calculations.
- [x] **F5. Boundaries.** PASS.  
  Enacted legislative acts do not define geographic zoning polygon boundaries.

### G. Public copy
- [ ] **G1. Approved copy.** PENDING (founder).  
  Coverage page and notices pending founder release board approval.
- [ ] **G2. Coverage pending.** PENDING (founder).  
  Pending founder ruling.

### H. Sign-off
- [ ] **H1. SESSION_LOG sign-off.** PENDING (founder).  
  Awaits SESSION_LOG sign-off and Release Board tick.
