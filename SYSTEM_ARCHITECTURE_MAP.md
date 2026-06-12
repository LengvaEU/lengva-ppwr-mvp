# PPWR MVP - System Architecture Map (1 page view)

## Purpose
This document provides a single-page structural overview of the entire PPWR MVP system.

It defines how data, logic, and AI interact without redefining system behavior.

---

## 🟦 LAYER 1: REALITY (Google Sheets)

The source of truth is:

PPWR_Data_Core

Contains:

- Products_Master (SKU compliance core)
- Supplier_Batches (incoming material tracking)
- Europola_Invoices (sales/outbound layer)
- Batch_Allocation (traceability bridge)
- Generated_Docs (compliance outputs)
- System_Config (system settings)

👉 This layer is the ONLY source of truth for data.

---

## 🟨 LAYER 2: BUSINESS LOGIC (GitHub)

GitHub defines interpretation rules, not data.

Modules:

- SYSTEM_PROMPT.md
- ARCHITECTURE.md
- BUSINESS_RULES.md
- DATA_MODEL_MAPPING.md
- CODEX_VIEW.md

Responsibilities:

- Define compliance logic
- Define traceability rules
- Define AI interpretation constraints
- Prevent simplification of real system

👉 This layer does NOT store operational data.

---

## 🟩 LAYER 3: AI TOOLS

Includes:

- ChatGPT
- Gemini
- Codex
- Claude (future)

Responsibilities:

- Analyze system
- Validate logic consistency
- Suggest improvements
- Detect contradictions

👉 AI does NOT define system truth.

---

## 🔁 SYSTEM FLOW

SKU + Document + Batch + Invoice + Allocation

→ processed via Business Rules (GitHub)

→ evaluated against real data (Sheets)

→ output generated in Generated_Docs

---

## ⚠️ SAFETY PRINCIPLES

- AI must not collapse system into simplified SKU-only model
- Batch layer is mandatory, not optional
- Invoice layer is mandatory, not optional
- GitHub defines rules, not reality
- Google Sheets is immutable operational truth

---

## 🧠 SYSTEM TYPE

This is a:

Hybrid Compliance + Traceability + Document Generation system

NOT ERP
NOT pure compliance tool

It is a layered hybrid system with strict separation of concerns.
