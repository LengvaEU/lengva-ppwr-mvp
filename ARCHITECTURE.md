# PPWR MVP Architecture (Lengva System)

## 1. System Overview

Lengva PPWR MVP is a lightweight compliance system built on:
- Google Sheets (data storage layer)
- Google Apps Script (automation layer)
- GitHub (system logic + versioned business rules)
- AI assistants (ChatGPT / Gemini / Codex / Claude)

---

## 2. Core Data Flow

SKU (Item)
→ linked to Supplier Document
→ extracted Compliance Claims
→ validated compliance output
→ Customer Document generation

---

## 3. System Constraints

- No ERP logic
- No warehouse batch tracking
- No production chain modeling
- No automatic compliance inference without document evidence

---

## 4. Core Principle

All compliance must be:
> Evidence-based, document-driven, and explicitly mapped.

No assumption-based inheritance is allowed.

---

## 5. System Layers

### 5.1 Google Sheets
Acts as:
- Database for Items, Documents, Claims
- Manual data entry + structured storage

### 5.2 Apps Script
Handles:
- Document generation
- Validation logic
- Automation triggers

### 5.3 GitHub
Stores:
- System rules
- Architecture definitions
- Business logic versioning

### 5.4 AI Layer
Used for:
- Schema design
- Rule interpretation
- Code generation (Apps Script)

---

## 6. Open Questions

- Should compliance evaluation be based on:
  - Invoice date?
  - Document generation date?
  - Hybrid model?

(This is intentionally not decided yet)
