# ArchiCost AI — Automated ROM Estimation & Quantity Surveying Platform

Target market: Nigeria construction & real estate (global-capable).

## Vision
Bridge concept design to financial readiness:
- **Layer 1 (Instant ROM):** Upload 3D BIM/CAD (`.IFC/.OBJ/.FBX`) → parametric Rough Order of Magnitude estimate (±10–15%) in under 30 seconds.
- **Layer 2 (QS Marketplace & BOQ Workspace):** Commission verified Quantity Surveyors for AI-assisted takeoff and certified BOQ (±2–5%) with escrow + 10–15% platform fee.

## How it works
`[3D Model] → [Mesh/Layer Parsing] → [Style + Region] → [ROM Estimate] → [Commission QS] → [AI Takeoff + Local Rates] → [Certified BOQ PDF/XLSX/JSON]`

Costing: `Cost_ROM = Σ(Qty_i × BaseRate_i × M_style × M_location) × M_contingency`
- Classical 1.35–1.60, Modern 1.20–1.45, Standard 1.00
- Zones: Lagos Metro / Abuja FCT / Inland differentials

## Tech stack
React/Next.js + Three.js, `web-ifc` / Forge, Node.js + Python FastAPI, PostgreSQL (PostGIS) + Redis, PyTorch/TensorFlow, Paystack/Flutterwave.

## Roadmap
- **Phase 1 (M1–4):** Layer 1 engine, 3D viewer, style matrix, ROM PDF.
- **Phase 2 (M5–8):** QS onboarding + NIQS check, takeoff workspace, escrow split.
- **Phase 3 (M9–12):** ML refinement, live supplier prices, mobile viewer.

## Repo contents
- `ArchiCost_AI_Product_Requirement_Document.md` — PRD v1.0 (Sept 2026)
- `README.md` — this profile

Targets: <30s estimate, 22% ROM→BOQ conversion, QS coverage Lagos/Abuja/PHC in 6 months.
