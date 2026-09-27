**Product Requirement Document (PRD)**

*ArchiCost AI — Automated ROM Estimation & Quantity Surveying Platform*

| Product Name: | ArchiCost AI (Working Title) |
| :---- | :---- |
| **Author / Role:** | Product Management (20+ Yrs Enterprise PM Experience) |
| **Target Market:** | Nigeria Construction & Real Estate Sector (Global Expansion Capable) |
| **Document Version:** | 1.0 | Date: September 2026 |

**1\. Executive Summary & Strategic Vision**

The traditional workflow between concept design and procurement-ready documentation in construction is fragmented, slow, and prone to severe cost overruns. In rapidly growing markets such as Nigeria, property developers and individual clients often wait weeks for initial cost feedback from professional consultants, only to discover that their conceptual architectural design significantly exceeds their available budget.

ArchiCost AI bridges the critical gap between architectural concept design and financial execution readiness. The platform delivers a dual-environment workflow:

* **1\. Layer 1 (Instant Rough Order of Magnitude \- ROM):** A client-facing parametric engine that ingests 3D BIM/CAD models (.IFC, .OBJ, .FBX) and generates an immediate Rough Order of Magnitude (ROM) cost estimate within \+-10% to \+-15% accuracy, heavily driven by architectural style classification and automated structural segment parsing.  
* **2\. Layer 2 (QS Marketplace & Automated BOQ Workspace):** A professional cloud workspace that empowers registered Quantity Surveyors (QS) with AI-assisted measurement, localized rate libraries, and automated Bill of Quantities (BOQ) generation tools. Rather than disintermediating professionals, Layer 2 expands work volume for QS practitioners while monetizing via a platform transaction fee per engagement.

**2\. Product Objectives & Target Metrics**

* **Concept-to-Estimate Latency:** Reduce preliminary cost feedback time from 14+ business days to under 30 seconds for Layer 1 automated model estimates.  
* **Cost Accuracy Targets:** Deliver Class 4 estimate accuracy (+-10% to \+-15%) automatically at Layer 1; deliver Class 1 execution accuracy (+-2% to \+-5%) via Layer 2 professional QS sign-off.  
* **QS Network Onboarding:** Onboard verified professional Quantity Surveyors across key commercial hubs (Lagos, Abuja, Port Harcourt) within the first 6 months of launch.  
* **Work Conversion Rate:** Convert at least 22% of users who generate Layer 1 preliminary estimates into Layer 2 commissioned BOQ projects.

**3\. User Personas & Core Workflows**

**3.1 Target Personas**

* **The Client / Real Estate Developer:** Needs quick, reliable financial viability checks without paying high upfront consultant fees during the conceptual exploration phase.  
* **The Architect / Design Lead:** Wants to guide clients on realistic budgeting before completing working drawings and entering formal tender processes.  
* **The Quantity Surveyor (QS):** Seeks digitized tools, automated takeoff mechanisms, and direct client leads while maintaining professional fee-earning power.

**3.2 Dual-Environment Architecture**

| LAYER 1: CLIENT ROM WORKFLOW \[3D Model Upload (.IFC/.OBJ)\] ──\> \[Mesh/Layer Parsing\] ──\> \[Style & Region Selection\]                                                                    │                                                                    ▼                                                    \[Automated ROM Estimate (±10–15%)\]                                                                    │                                                                    ▼LAYER 2: QS WORKSPACE & MARKETPLACE \[Commission Registered QS\] ──\> \[AI Automated Takeoff Workspace\] ──\> \[Localized Price Book\]                                                                    │                                                                    ▼                                                    \[Final Certified BOQ Export (PDF/XLSX)\] |
| :---- |

**4\. Comprehensive Technical Requirements**

**4.1 System Architecture & Tech Stack Strategy**

| Component | Recommended Tech | Technical Justification |
| :---- | :---- | :---- |
| Frontend Web App | React / Next.js, Three.js, WebGL | High-performance browser rendering of 3D models without plugin requirements. |
| 3D Parsing Engine | Autodesk Forge API / open-source web-ifc | Parses BIM metadata (geometry, material volumes, layer categorizations). |
| Backend Services | Node.js / Python (FastAPI) | Microservices architecture for mesh processing, rate engine, and API management. |
| Database & Storage | PostgreSQL (PostGIS) \+ Redis Cache | Spatial querying capabilities for geographic pricing; cached rate lookups. |
| AI / ML Pipeline | PyTorch / TensorFlow (Geometric DL) | Mesh classification, element segmentation, automated rate mapping. |
| Payments & Escrow | Paystack / Flutterwave API | Supports local NGN transactions, card processing, direct transfers, and escrow splits. |

**4.2 Layer 1 Technical Requirements (Parametric ROM Estimation)**

* **1\. Supported Formats:** Supports .IFC, .OBJ, .FBX, .RVX (Revit export), and .DXF/.DWG 3D meshes.  
* **2\. Automated Mesh Segmentation:** Mesh parser must separate structural geometry into core zones: Substructure/Foundation, Superstructure Frame & Walls, Roof Assemblies, and Openings (Doors & Windows).  
* **3\. Volumetric & Area Takeoff Engine:** Engine must calculate Gross Floor Area (GFA), wall envelope surface area, volumetric concrete requirements, and roof plane coverage automatically upon render.

4\. Parametric Style & Finish Weighting Engine Matrix:

The calculation engine applies a dynamic mathematical weighting matrix modifying base material rates:

| Cost\_ROM \= ∑ ( Quantity\_i  ×  BaseRate\_i  ×  M\_style  ×  M\_location )  ×  M\_contingency |
| :---: |

* **Classical / Ornamental Style:** Applies coefficient multipliers (M\_style \= 1.35 to 1.60) accounting for ornate plaster moldings, cornices, balustrades, stone cladding, and complex roof structures.  
* **Modern / Contemporary Style:** Applies structural steel, expansive glass spans, frameless aluminum, and minimalist high-specification finishes (M\_style \= 1.20 to 1.45).  
* **Standard / Functional Style:** Baseline standard finish multiplier (M\_style \= 1.00).  
* **Geographic Cost Indexes:** Dynamic cost indexes for geopolitical zones (Lagos Metro vs. Abuja FCT vs. Inland state material logistics differentials).

**4.3 Layer 2 Technical Requirements (QS Marketplace & AI Workspace)**

* **Professional Verification:** Verification pipeline via NIQS (Nigerian Institute of Quantity Surveyors) membership ID check or practice certificate upload.  
* **Escrow Account & Automated Split Payment:** Client funds held in platform escrow upon commission. Automatic split payment mechanics route 10–15% platform fee to ArchiCost account and release net funds to QS upon client sign-off.  
* **Automated Takeoff Sheet Generation:** AI parses imported IFC metadata and pre-populates standard NRM2 / BESMM (Building Engineering Standard Method of Measurement) frameworks.  
* **Dynamic Professional Controls:** Custom markup adjustment controls (0–30%), inflation sliders, custom rate overrides, and live regional bulk material price feeds (cement, rebar, granite, sand).  
* **Multi-Format Export:** Export certified BOQ outputs in standardized PDF, Excel (.xlsx), and JSON formats.

**5\. Non-Functional Requirements (NFRs)**

* **Performance & Speed:** 3D Model parsing and Layer 1 ROM generation must render in \< 30 seconds for model files under 100MB. Viewer must maintain min 30 FPS on standard integrated GPUs.  
* **Security & Compliance:** TLS 1.3 encryption in transit and AES-256 at rest for proprietary architectural CAD models. Full compliance with Nigeria Data Protection Regulation (NDPR).  
* **Scalability & Reliability:** Cloud infrastructure (AWS/GCP) configured with auto-scaling microservices for mesh rendering, achieving 99.9% uptime SLA.

**6\. Release Roadmap & Implementation Phasing**

| Phase | Target Deliverables | Strategic Objective |
| :---- | :---- | :---- |
| Phase 1: MVP(Months 1–4) | Layer 1 Parametric Engine, browser 3D IFC/OBJ viewer, style multiplier matrix, instant ROM report download. | Validate market demand and client engagement speed. |
| Phase 2: QS Beta(Months 5–8) | QS onboarding portal, NIQS verification integration, AI takeoff editor workspace, payment escrow & split system. | Establish marketplace supply side and monetization pipeline. |
| Phase 3: Scale(Months 9–12) | Machine learning refinement on completed BOQs, live regional supplier API price feeds, native mobile viewer apps. | Automate accuracy gains and expand across West Africa. |

