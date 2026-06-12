# PPWR MVP Business Rules (Lengva System)

## 1. Core Principle

All compliance must be strictly evidence-based.
No assumptions, no inheritance, no probabilistic compliance.

If there is no valid document → compliance does NOT exist.

---

## 2. Compliance Flow Rule

SKU → Supplier Document → Extracted Compliance Claims → Customer Output

This is the only valid data flow.

---

## 3. Document Ownership Rule

A ComplianceSourceDocument:
- can apply to one or many SKUs
- must explicitly define scope
- does NOT automatically apply to all manufacturer products

---

## 4. Inheritance Prohibition Rule

Compliance is NOT inherited from:
- Manufacturer
- Material group (unless explicitly documented)
- Product family (unless explicitly documented)

Each SKU must be explicitly covered by a document mapping.

---

## 5. Claim Extraction Rule

A single document can contain multiple claims:

Examples:
- PFAS_Free = Yes
- REACH_Compliant = Yes
- Food_Contact = Approved

Each claim must be:
- explicitly extracted
- linked to the source document
- mapped to specific SKUs

---

## 6. Document Lifecycle Rule

Each document has:
- Issue Date (mandatory)
- Expiry Date (optional)
- Status: Active / Superseded

Old documents are NEVER deleted.

They remain in audit history.

---

## 7. Evidence Requirement Rule

Customer document generation is allowed ONLY if:

- At least one valid document exists
- Document is Active
- Document explicitly supports all required claims for SKU

If any required evidence is missing → generation is BLOCKED.

---

## 8. Scope Boundary Rule

This system is NOT:
- ERP system
- warehouse tracking system
- production batch system

It is ONLY:
- compliance documentation and validation system

---

## 9. Open Logic Area

Trigger timing for compliance evaluation is not fixed:
- Invoice date vs generation date vs hybrid model
This remains intentionally undecided.
