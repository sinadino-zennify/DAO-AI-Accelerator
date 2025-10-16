# {{PROJECT_NAME}} - Development Backlog

**Last Updated**: 2025-01-16  
**Project**: {{INTEGRATION_SOURCE}} Integration  
**Client**: {{CLIENT_NAME}}

---

## 🎯 Active Sprint

### In Progress
- [ ] **[DM-001]** Define data model and relationships
- [ ] **[MAP-001]** Complete field mappings in `field-mappings-template.csv`

### Up Next
- [ ] **[API-001]** Implement REST API endpoint for {{INTEGRATION_SOURCE}}
- [ ] **[ING-001]** Build data ingestion service

---

## 📋 Backlog

### Phase 1: Foundation (Data Model + API)

**Data Model**
- [ ] **[DM-001]** Define object relationships and ER diagram
- [ ] **[DM-002]** Create custom fields for external IDs
- [ ] **[DM-003]** Validate FSC object usage

**Mappings**
- [ ] **[MAP-001]** Complete field mappings CSV
- [ ] **[MAP-002]** Document special handling rules
- [ ] **[MAP-003]** Validate data types and formats

**API Integration**
- [ ] **[API-001]** Implement REST endpoint (`/dao/application`)
- [ ] **[API-002]** Build request payload DTOs
- [ ] **[API-003]** Build response structure
- [ ] **[API-004]** Add authentication and security

**Testing**
- [ ] **[SEC-001]** Implement CRUD/FLS checks
- [ ] **[SEC-002]** Add PII encryption
- [ ] **[SEC-003]** Test bulkification (200+ records)

---

## 📌 Completed

_Track completed items here_

---

## 🏷️ Work Item Prefixes

- **DM-** = Data Model (objects/fields/ER updates)
- **MAP-** = Mappings ({{INTEGRATION_SOURCE}}→SF field map & rules)
- **ING-** = Ingestion (parser, mapper, upsert services, tests)
- **API-** = API Development (REST endpoints, authentication, integration)
- **SEC-** = Security (FLS/CRUD, PII handling, permissions)
- **DOC-** = Documentation (ER/mappings/ADRs)

---

**Maintained By**: Development Team  
**Review Frequency**: Weekly

