# PPWR MVP - System Architecture Map

## Purpose

This document provides a high-level overview of the current and target architecture.

It is intended to explain system structure without prescribing implementation details.

---

# Layer 1: Operational Reality

## Google Sheets (PPWR_Data_Core)

Current operational data resides in:

* Products_Master
* Supplier_Batches
* Europola_Invoices
* Batch_Allocation
* Generated_Docs
* System_Config

This is the current operational structure.

It reflects how data is stored today.

---

# Layer 2: Business Logic

## GitHub Documentation

GitHub stores:

* Business Rules
* Architecture Decisions
* AI Governance
* Future Design Reviews

GitHub defines interpretation and evolution rules.

It does not store operational business data.

---

# Layer 3: AI Assistance Layer

Tools may include:

* ChatGPT
* Gemini
* Codex
* Claude

AI tools:

* analyze
* review
* audit
* recommend

AI tools do not define truth.

---

# Current Operational Flow

Products

↓

Supplier Documents

↓

Sales Invoices

↓

Generated Customer Documents

Additional traceability data may exist through:

* Supplier_Batches
* Batch_Allocation

---

# Architecture Direction

The project is currently evolving toward a compliance-centered model:

SKU / Item

↓

Supplier Document

↓

Compliance Claim

↓

Customer Document

while preserving compatibility with existing operational data.

---

# Open Decisions

The following questions remain intentionally unresolved:

* Invoice Date vs Generation Date validation
* Future batch-level compliance requirements
* Future PPWR extensions
* Future cryptographic verification

These topics remain open until formally decided.

---

# System Type

This is a:

Compliance + Traceability + Document Automation System

It is NOT:

* ERP
* MES
* Warehouse Management System

although it may store limited traceability information.
