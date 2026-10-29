# DocuFlow AI: Intelligent Real Estate CRM & Document Workflows

> **Turn real estate documents into intelligent business workflows.**

DocuFlow AI is an enterprise document intelligence and CRM platform tailored specifically for the Indian real estate market (residential and commercial brokerages, property managers, developers, and funds). It features an 8-stage document processing engine that extracts structured fields from lease contracts, listing mandates, sale deeds, tenant applications, and maintenance invoices, subjects them to deterministic validation, matches them against property inventory, and facilitates human-in-the-loop review and atomic CRM updates.

---

## 1. Core Features & Capabilities

- **Secure Document Vault:** Binary magic-bytes signature verification (`%PDF`, `PNG`, `JPEG`), SHA-256 content checksumming, path-traversal mitigation, and isolated organization storage.
- **8-Stage AI Processing Pipeline:**
  1. File Security & Magic Byte Scanning
  2. Optical Character Recognition (OCR)
  3. Document Category Classification
  4. Structured Field Extraction (Gemini 2.5 Flash / Provider Abstraction)
  5. Deterministic Validation Engine (Required checks, date sequences, invoice math, area units)
  6. CRM Entity Matcher (Fuzzy address & reference matching)
  7. Human Review & Compliance Sign-Off
  8. Atomic CRM Update & Automation Dispatch
- **Side-by-Side Review Workspace:**
  - Integrated document viewer with zoom controls, rotation, and original download
  - Inline field editing with full audit trail history
  - Field-level evidence quotes and confidence scores
  - CRM match suggestions with match rationale
  - Atomic approval & property linking
- **Real Estate CRM (India Edition):**
  - First-class support for Indian currency (`₹`, Lakhs, Crores) and units (`sqft`, Gaj)
  - Properties & Units with document history timeline
  - Contacts directory (Owners, Buyers, Tenants, Brokers)
  - Leads management with budget brackets and preferred localities
  - Deals Kanban pipeline (Qualification → Site Visit → Token → Documentation → Closed Won)
  - Activities & Follow-up Task reminders
- **Safe Rule-Based Automation Engine:**
  - Automated task generation on tenant document approval
  - Agent notifications on lease expiries and high-value deal milestones
  - Dry-run simulation tester to safely preview rule actions
- **Enterprise Multi-Tenancy & RBAC:**
  - Strict organization isolation enforced at the backend dependency level
  - 6 RBAC Roles: `Owner`, `Admin`, `Manager`, `Agent`, `Reviewer`, `Viewer`
- **Subscriptions & Usage Metering:**
  - Plan Tiers: Starter (₹1,999), Growth (₹4,999), Business (₹12,999), Enterprise
  - Idempotent page usage accounting (prevents double charging on retries)

---

## 2. Architecture & Technology Stack

- **Frontend:** Next.js 15 (App Router), React 19, TypeScript (strict mode), Tailwind CSS, Lucide Icons, Recharts.
- **Backend:** Python FastAPI, Pydantic v2, SQLAlchemy 2.0, Alembic, Pytest.
- **Database:** Supabase PostgreSQL compatible (with zero-config SQLite mode for local dev & testing).
- **AI & OCR:** Pluggable provider abstraction supporting Google Gemini API (`gemini-2.5-flash` via `google-genai` SDK) and a synthetic demo fallback.
- **Storage:** Private object storage vault with SHA-256 fingerprinting.

---

## 3. Quick Start (Local Development)

### Prerequisites
- Python 3.11+ (or Python 3.14 via `py` / `uv`)
- Node.js 18+ and `npm`

### Step 1: Start Backend
```bash
cd backend
# 1. Create virtual environment and install dependencies
uv venv
uv pip install -r requirements.txt

# 2. Run automated test suite (all 7 suites pass)
pytest tests -v

# 3. Seed demo data (creates Skyline Realty, properties, sample lease document)
python app/seed_data.py

# 4. Start FastAPI server
uvicorn app.main:app --reload --port 8000
```
Backend API will be running at: `http://localhost:8000` (Swagger docs: `http://localhost:8000/docs`).

### Step 2: Start Frontend
```bash
cd frontend
# 1. Install dependencies
npm install

# 2. Run Next.js development server
npm run dev
```
Frontend will be running at: `http://localhost:3000`.

### Default Demo Credentials
- **Admin / Owner:** `admin@docuflow.ai` / `password123`
- **Reviewer:** `reviewer@docuflow.ai` / `password123`
- **Agent:** `agent@docuflow.ai` / `password123`

---

## 4. Documentation Index
- [`docs/ARCHITECTURE.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/ARCHITECTURE.md): Full system architecture and component design.
- [`docs/DATABASE.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/DATABASE.md): Data dictionary for all 25+ database entities.
- [`docs/API.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/API.md): Complete REST API endpoints specification under `/api/v1`.
- [`docs/SECURITY.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/SECURITY.md): Threat model, tenant isolation, file security, and RBAC matrix.
- [`docs/DEPLOYMENT.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/DEPLOYMENT.md): Production deployment guide (Vercel, Cloud Run, Supabase).
- [`docs/PRODUCT_SCOPE.md`](file:///c:/Users/Pranav/OneDrive/Documents/DOCUFLOW%20AI/docs/PRODUCT_SCOPE.md): Product scope, real estate initial schemas, and expansion roadmap.

---

## 5. Sample Documents
Pre-built synthetic test documents are available in `sample_docs/`:
1. `sample_docs/01_Prestige_Silver_Oak_Rental_Agreement.pdf`
2. `sample_docs/02_DLF_Camellias_Luxury_Listing.pdf`
3. `sample_docs/03_Society_Maintenance_Tax_Invoice.pdf`
