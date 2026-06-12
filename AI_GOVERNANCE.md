# PPWR MVP - AI Governance Rules (v2)

## Purpose

This document defines how AI systems may participate in the design, review, and implementation of the Lengva PPWR MVP project.

It exists to prevent uncontrolled architecture changes, over-engineering, and accidental loss of traceability.

---

## AI Roles

### ChatGPT

* Architecture analysis
* Business rule validation
* Risk identification
* Gap analysis

### Gemini

* Alternative solution proposals
* Concept exploration
* Challenge assumptions

### Codex

* Code review
* Impact analysis
* Implementation of approved designs

### Claude

* Consistency review
* Contradiction detection
* Documentation audit

---

## Rule 1: No Single AI Authority

No AI system is allowed to define architecture independently.

All outputs are proposals until validated against:

* Business requirements
* Existing system structure
* Product Owner decisions

---

## Rule 2: Reality Overrides Theory

Real business processes take priority over theoretical models.

Architecture decisions must reflect actual Europola operations rather than idealized ERP or MES concepts.

---

## Rule 3: Preserve Existing Structure

The existing PPWR_Data_Core structure must be preserved until formally reviewed.

Current layers include:

* Products
* Documents
* Batches
* Invoices
* Allocations
* Generated Documents

AI systems may propose improvements, abstractions, or simplifications, but may not remove existing layers without explicit approval.

---

## Rule 4: No Automatic Refactoring

AI systems must not:

* Delete existing entities
* Collapse existing relationships
* Introduce major architectural changes

unless explicitly requested.

---

## Rule 5: Traceability First

When a conflict exists between:

* Simplicity
* Traceability

traceability takes priority.

---

## Rule 6: Change Control

Any proposed architecture change must:

1. Describe the current state.
2. Describe the proposed state.
3. Explain benefits.
4. Explain risks.
5. Receive explicit approval.

---

## Rule 7: Documentation Before Code

Architecture and business rules must be reviewed before implementation.

Code changes must never become the primary source of system design.

---

## System Safety Principle

The system prioritizes:

* Auditability
* Traceability
* Historical integrity
* Controlled evolution

over aggressive simplification.
