<!-- 
🔴 AI AGENTS: READ FIRST - /docs/01-foundation/data-model.md for correct object names
✅ Correct: ApplicationForm, Applicant, Account (Business), FinancialAccount
❌ Wrong: Application__c, Applicant__c, Loan__c, Business_Relationship__c
-->

# {{INTEGRATION_SOURCE}} Field Mappings - Deposit Account Opening

## 📋 Overview

**Source**: {{INTEGRATION_SOURCE}} External Application  
**Last Updated**: 2025-01-16  
**Authoritative Source**: `field-mappings-template.csv` (this directory)  
**Purpose**: Maps {{INTEGRATION_SOURCE}} external application fields to Salesforce objects

---

## 🔑 Quick Reference

**For complete field-by-field mappings, see: `field-mappings-template.csv`**

This document provides:
- Context and guidance for using the mappings
- Important implementation notes
- Data privacy requirements
- Special handling rules

---

## 📊 Mapping Summary by Object

### Account (Business)
Maps business entity information from {{INTEGRATION_SOURCE}} to Salesforce Business Accounts.

**Key Mappings:**
- `dao_business_id` → `DAOBusinessId__c` (External ID)
- `business_name` → `Name`
- `business_type` → `Type`
- `tin` → `Federal_Tax_ID_Number_zen__c`

### Applicant
Maps individual applicant information to Salesforce Applicant records.

**Key Mappings:**
- `dao_applicant_id` → `DAOApplicantId__c` (External ID)
- `first_name` → `FirstName`
- `last_name` → `LastName`
- `email` → `Email`
- `social_security_number` → `SSN__c` (Encrypted)

### ApplicationForm
Maps application metadata and status.

**Key Mappings:**
- `dao_application_id` → `DAOApplicationId__c` (External ID)
- `stage` → `Stage`
- `current_step` → `Current_Step__c`

---

## 🔒 Data Privacy & Security

### PII Fields (Encrypted Required)

The following fields contain Personally Identifiable Information and **MUST** be encrypted:

| Field | Object | Encryption Method |
|-------|--------|-------------------|
| `SSN__c` | Applicant | Shield Platform Encryption or Classic Encryption |
| `Date_of_Birth__c` | Applicant | Shield Platform Encryption or Classic Encryption |
| `Federal_Tax_ID_Number_zen__c` | Account | Shield Platform Encryption or Classic Encryption |

### Field-Level Security

All PII fields must have:
- ✅ Read-only for most profiles
- ✅ Edit access only for authorized roles
- ✅ Audit trail enabled

---

## 📝 Implementation Notes

### Address Handling

{{INTEGRATION_SOURCE}} provides multiple address types:
- **Home Address** → `PersonMailingAddress`
- **Mailing Address** (if different) → `PersonOtherAddress`
- **Business Address** → `BillingAddress` on Account

### PersonAccount vs Contact

- Use **PersonAccount** for all individual applicants
- Applicant object links to PersonAccount via `AccountId`
- AccountContactRelation links PersonAccount to Business Account

---

## 🔄 Agent Sync Instructions

**For AI Agents:**

When user updates `field-mappings-template.csv`:

1. Read the CSV file
2. Parse new/changed mappings
3. Update relevant sections in this file
4. Preserve all context sections (privacy, implementation notes, etc.)
5. DO NOT modify the CSV file

**File Ownership:**
- `field-mappings-template.csv` = **USER-MAINTAINED** (source of truth)
- `field-mappings.md` = **AGENT-MAINTAINED** (documentation)

---

**Created**: 2025-01-16  
**Last Updated**: 2025-01-16  
**Maintained By**: AI Agents (synced from CSV)  
**CSV Owner**: Development Team

