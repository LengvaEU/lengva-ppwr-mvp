# PPWR MVP - Decisions Log

## Purpose

This document records architecture decisions that have been reviewed and accepted.

---

## Decision 001

Current PPWR_Data_Core structure remains in place.

Status: Accepted

Reason:
Existing operational data already uses this structure.

---

## Decision 002

Supplier documents are the primary source of compliance evidence.

Status: Accepted

Reason:
Compliance claims must be supported by actual supplier documentation.

---

## Decision 003

A single supplier document may apply to:

* One SKU
* Multiple SKUs
* A product family

Status: Accepted

---

## Decision 004

Compliance claims originate from documents, not from manufacturers.

Status: Accepted

Reason:
Manufacturers may produce compliant and non-compliant products simultaneously.

---

## Decision 005

New SKUs do not automatically inherit compliance claims.

Status: Accepted

Reason:
Explicit document coverage is required.

---

## Decision 006

Superseded documents remain in history.

Status: Accepted

Reason:
Historical auditability must be preserved.

---

## Decision 007

Invoice Date versus Generation Date validation remains unresolved.

Status: Open

---

## Decision 008

Future PPWR requirements must be supported without major schema redesign.

Status: Accepted

---

## Decision 009

Batch-level compliance validation remains undecided.

Status: Open

Reason:
Current supplier practice is primarily SKU/document based, but future requirements may differ.

---

## Decision 010

No code refactoring is authorized until architecture review is completed.

Status: Accepted
