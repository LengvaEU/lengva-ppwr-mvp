SYSTEM ARCHITECTURE & BUSINESS SPECIFICATION: LENGVA PPWR MVP
Role & Context:

You are an expert Solutions Architect, Business Analyst, and Senior Software Engineer. You are reviewing the foundations for a compliance and document management system called "Lengva PPWR MVP". This system is designed to handle EU Packaging and Packaging Waste Regulation (PPWR) and PFAS compliance tracking, using a lightweight Google Sheets + Google Apps Script architecture.

PART 1: PROJECT OVERVIEW & STRATEGIC GOALS
1.1 Purpose & Scope Boundaries
The primary objective of Lengva PPWR MVP is to serve as an administrative compliance shield and document automation tool. It is explicitly NOT a full-scale ERP (Enterprise Resource Planning), MES (Manufacturing Execution System), or a live warehouse batch-tracking engine.

Physical warehouse picking is location-based, and outgoing sales are not actively mapped to physical incoming purchase lots.

The system must remain lightweight, avoiding over-engineering and complex multi-stage production chain modeling.

1.2 Core MVP Features
Supplier Document Management: Centralizing, versioning, and tracking the validity of incoming supplier declarations.

Compliance Claim Mapping: Extracting and structured logging of dynamic regulatory statements (e.g., PFAS status).

Customer Document Generation: Automatically creating outbound PDF declarations for clients based on valid, verified upstream evidence.

Historical Audit Trail: Maintaining an immutable and reliable history of what documentation was active and used over time.

PART 2: CORE BUSINESS RULES & LOGICAL LAWS
2.1 The Core Compliance Vector
The central axis of the entire system data flow is strictly product-centric and linear:

SKU / Item → Supplier Document → Compliance Claim → Customer Document

2.2 Document-to-Item Cardinality (One-to-Many Matrix)
A single supplier document (ComplianceSourceDocuments) does not have a forced 1:1 relationship with a single product. Based on real supplier practices (e.g., large-scale material suppliers), a single uploaded PDF may apply to:

One specific SKU.

A specific list of multiple distinct SKUs.

An entire product family, material group, or product range.
The database schema and relational logic must natively allow one document to map its compliance validity to multiple target SKUs concurrently.

2.3 Compliance Claims & Strict Ownership Guardrails
Compliance claims (ComplianceClaims) must originate strictly from a specific Supplier Document, never generally or automatically from a Manufacturer profile. A manufacturer may produce hundreds of items, and a PFAS-free statement on one material type does not guarantee compliance across their entire catalog.

Inheritance Protection: Newly created SKUs do not automatically inherit compliance claims just because they share a Manufacturer with existing items. Every item requires explicit coverage by a valid document mapping.

Dynamic Scope Extraction: A single supplier document may contain multiple distinct regulatory claims (e.g., a combined PFAS-free, REACH, and Food-Contact declaration). The system must support extracting multiple key-value claims from one single document entry.

2.4 Document Lifecycle, Timeframes & Validity
Supplier documents rarely have strict expiration dates; they are legally bound by their issuance date and replacement lifecycle.

Metadata Fields: Every document entry must support a mandatory Issue Date, an optional Expiry Date, and a Lifecycle Status (e.g., Active, Superseded).

Versioning & History: A document remains legally active from its Issue Date forward until it is explicitly marked as Superseded or Replaced by an administrative manager tracking a newer file version.

Audit Retention: Superseded documents must never be deleted or simply toggled off. They must remain in the database history with their active timeframes (Valid From / Valid Until or Issue Date / Superseded Date) intact to preserve historical audit capabilities.

2.5 Evidence-Based Document Generation (No Blind Approvals)
Outbound customer declarations operate strictly on an "explicit proof" basis.

A customer declaration can only be generated if there is an active, unexpired, and verified supplier document explicitly backing the required claim for that specific SKU.

Missing Data Handling: If a SKU has one active document stating PFAS_Free = Yes but another required document is missing or unverified, generation is blocked due to insufficient evidence. The system does not need a complex conflict-resolution engine; if there is no explicit valid proof, document generation simply halts.

PART 3: ARCHITECTURE CONSTRAINTS & DATA OBJECTS
3.1 The 5 Core MVP Entities
To prevent scope creep and over-engineering, the system database layout must be restricted to these 5 primary conceptual entities:

Items (SKUs): The product catalog holding unique codes, descriptions, and material groupings.

Manufacturers: Supplier and manufacturer profiles, including specific data confidentiality tags.

ComplianceSourceDocuments: Metadata and storage links for incoming supplier PDFs (tracking File Link/ID, Issue Date, Expiry Date, and Superseded Status).

ComplianceClaims: The dynamic regulatory statements extracted from documents (e.g., ClaimType: PFAS_Free, Value: Yes) flexibly mapped to their target SKUs.

CustomerDocuments: A historical log and registry of all outbound declarations generated and issued to clients.

3.2 Technical Constraints & Open Architecture Questions
No Batch Tracking: Tables like BatchMaterials, BatchComponents, or structural purchase-lot links are completely out of scope for this milestone. Do not design any database-level batch layers.

Abstract Time Anchoring: The exact trigger logic for customer document generation (whether it evaluates compliance based on the historical Invoice Date or the live Generation Date) is currently an open business question. The architecture must keep this evaluation layer abstract and decoupled from the hard data schema.

Cryptographic Hashing (Deferred): Advanced cryptographic integrity measures (e.g., selecting between data-level SnapshotHash or file-level SHA-256) are deferred to later security implementation stages. Do not implement them now.

PART 4: IMMEDIATE INSTRUCTIONS FOR THE AI
Depending on the task you are assigned, you must adhere to the following rules:

If performing an Audit: Map the status-quo of the current files/code against these rules. List the gaps and parts that already fit perfectly.

If proposing a Schema: Use the 5 Core Entities. Ensure the mapping allows one document to link to many SKUs, and that claims are dynamic key-value pairs (to allow future PPWR recycling content metrics or heavy metal limits without schema redesign).

No Code Execution: Do not write, refactor, or modify any executable code unless explicitly commanded in a follow-up prompt.
