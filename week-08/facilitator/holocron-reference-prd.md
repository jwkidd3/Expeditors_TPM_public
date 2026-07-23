# Holocron — Reference PRD (Facilitator Answer Key)

> Facilitator-only — **do not hand to participants.** This is the real, fully-specified Holocron PRD. Participants receive only `handouts/holocron-problem-brief.md` (business context, facts, stakeholders, constraints) and derive their own requirements from it.
>
> **How to use this:** as a comparison reference during Day 2–4 coaching and Friday review — not a grading rubric. A triad's PRD will differ from this and can still be excellent. What is worth checking against it:
> - Did they find the **governance/compliance** driver, not just the "editing is slow" driver?
> - Did they scope a defensible slice, or try to specify everything?
> - Did their non-functional requirements engage the real numbers (500k strings, 30–40 locales, 150+ countries, audit retention)?
> - Did they surface the genuinely open questions rather than inventing answers?
> - Did they treat **fallback behaviour, placeholder integrity, and audit immutability** as requirements, or miss them entirely? These are the most commonly missed.
>
> Source: the enterprise Holocron requirements consolidation (spec-kit format, `US#-FR-001` style). Note the house style differs from the course's 11-section PRD with Given/When/Then acceptance criteria — that difference is worth naming out loud if participants see this after Friday.

---

## Metadata
- Feature Branch: [001-string-management-service]
- Created: 2026-05-19
- Status: Draft
- Input: Holocron requirements discussions, VPC working draft, lean business case, and enterprise epic request inputs consolidated from docs/specify/PRD-Holocron-v1.md

## Problem Statement
UI text across the enterprise is currently managed in fragmented and frequently hardcoded patterns. Updating even simple copy often requires engineering intervention and a deployment cycle, turning minor text corrections into multi-day or multi-week work. This slows delivery, ties up engineering capacity, and prevents business teams from making timely content changes.

The current state also introduces compliance and governance risk. Compliance-sensitive strings can move through release processes without consistent legal review gates or centralized audit evidence. For a global footprint across 150+ countries, 20-30+ applications, and 30-40 languages, inconsistent translation processes and decentralized ownership lead to uneven quality and increased operational risk.

Holocron addresses this with a centralized, governed string management platform so content owners can create, review, and publish text without hardcoding or redeploying applications, while preserving traceability, ownership, and approval controls.

## Solution Overview
Holocron is a centralized string management service that separates UI content lifecycle management from application code deployment.

- Management Application - Authoring, editing, ownership, governance, and visibility for strings and translations.
- Structured Delivery Contract - Machine-consumable delivery of strings to consuming applications by product and namespace.
- Translation Exchange Workflow - Governed export and import process for translation providers.
- Governance and Audit - Version history, approvals, ownership controls, and immutable audit trail.

## User Stories

### User Story US1 - Create and Manage Strings (Priority: P1)
As a Content Owner, I need to create, edit, and organize strings with full version and audit history so that I can manage UI text without engineering tickets.

- Why this priority: Foundational capability required before all downstream workflows.
- Independent Test: A content owner can create and edit namespaced strings and view versioned history and audit records end-to-end.

#### Acceptance Scenarios
- US1-AS-001: Given authorized access to a product namespace, When a user creates a valid key and source string, Then version 1 is created and an audit entry is recorded.
- US1-AS-002: Given an existing string, When source text is edited, Then a new version is created and prior versions remain visible.
- US1-AS-003: Given a duplicate key in the same namespace, When submission is attempted, Then validation blocks creation.
- US1-AS-004: Given context notes and placeholders are provided, When the string is saved, Then context and placeholder metadata are persisted and displayed.

#### Functional Requirements
- US1-FR-001: System MUST support unique namespaced keys per product/application scope.
- US1-FR-002: System MUST persist en-US as authoritative source language.
- US1-FR-003: System MUST maintain immutable source version history and per-change audit entries.
- US1-FR-004: System MUST enforce key schema and immutability after creation.
- US1-FR-005: System MUST support source lifecycle states (Draft, In Review, Published, Retired) with audited transitions.
- US1-FR-006: System MUST warn and require acknowledgement when source edits invalidate published translation placeholder compatibility, and mark affected translations Outdated.
- US1-FR-007: System MUST support product grouping, tags, sortable/filterable table, and detail view.
- US1-FR-008: Source string minimum field contract MUST include key, source locale, source text, owner(s), lifecycle status, last modified by, and last modified at.

#### Success Criteria
- US1-SC-001: 95%+ of source string create/edit/find operations completed without developer assistance.
- US1-SC-002: 100% of mutating operations captured with actor and timestamp.

#### Non-Functional Requirements
- US1-NFR-001: Management application availability MUST be 99.5% or higher.

#### Edge Cases
- US1-EC-001: Concurrent edits require optimistic locking and explicit conflict handling.
- US1-EC-002: Retire operations must preserve history and expose dependent relationships before confirmation.

### User Story US2 - Add and Manage Language Variants (Priority: P1)
As a Content Owner or translator, I need to add and manage translations per language so targeted corrections can be made without full re-import.

- Why this priority: Required for translation lifecycle operations and post-import correction.
- Independent Test: A user can add/update a locale variant independently from source content and other locales.

#### Acceptance Scenarios
- US2-AS-001: Given a source string, When a supported locale is selected, Then translated content can be created and saved.
- US2-AS-002: Given an incorrect locale translation, When it is edited, Then a new locale-specific version is created.
- US2-AS-003: Given source changes after published translation, When update occurs, Then translation status becomes Outdated.

#### Functional Requirements
- US2-FR-001: System MUST support configurable language set with en-US source.
- US2-FR-002: System MUST store independent per-locale content and history.
- US2-FR-003: System MUST support translation lifecycle states and audited transitions.
- US2-FR-004: System MUST support Outdated transition when source changes post-publication.
- US2-FR-005: Translation minimum field contract MUST include locale, translated text, status, actor, updated timestamp, and source version reference.

#### Success Criteria
- US2-SC-001: Single-locale correction can be completed quickly by authorized users without engineering intervention.

#### Non-Functional Requirements
- US2-NFR-001: Localization architecture MUST support expansion to additional locales without code changes.

#### Edge Cases
- US2-EC-001: RTL content must be storable and deliverable without corruption.
- US2-EC-002: Pluralization and grammar policy requires ICU/CLDR-compatible handling in future phase.

### User Story US3 - Export Strings for Translation (Priority: P2)
As a Content Owner, I need to export strings in a governed format so translation services receive source text with required context and placeholders.

- Why this priority: Core integration point for translation workflow, planned post-MVP.
- Independent Test: User exports selected strings with complete metadata package in approved exchange format.

#### Acceptance Scenarios
- US3-AS-001: Given selected strings, When export is run, Then file includes key, source text, context, placeholders, and translation status.
- US3-AS-002: Given placeholders exist, When export is generated, Then placeholder syntax is preserved.
- US3-AS-003: Given subset selection, When export is run, Then only selected strings are included.

#### Functional Requirements
- US3-FR-001: System MUST support bulk export in approved governed format(s).
- US3-FR-002: System MUST include key metadata fields needed for translation quality.
- US3-FR-003: System MUST support subset export from search/table scope.
- US3-FR-004: System MUST update per-locale status to Exported after export event.

#### Success Criteria
- US3-SC-001: Export reliability and performance meet agreed operational targets for expected usage.

#### Non-Functional Requirements
- US3-NFR-001: Export pipeline MUST preserve schema integrity and placeholder fidelity.

#### Edge Cases
- US3-EC-001: Mixed-state selections must preserve accurate per-locale status in payload.
- US3-EC-002: Large export batches must remain operationally usable.

### User Story US4 - Import Translated Strings (Priority: P2)
As a Content Owner, I need to import translated files so locale content is linked to correct keys without manual re-entry.

- Why this priority: Completes translation round-trip workflow.
- Independent Test: Import validates rows before apply, rejects invalid rows with actionable errors, and updates valid rows atomically according to policy.

#### Acceptance Scenarios
- US4-AS-001: Given a translation file, When uploaded, Then row-level validation and apply preview are shown.
- US4-AS-002: Given placeholder mismatch rows, When validated, Then invalid rows are flagged with clear errors.
- US4-AS-003: Given valid import, When apply runs, Then translations update and status changes to Imported with audit entries.

#### Functional Requirements
- US4-FR-001: System MUST support governed bulk import contract.
- US4-FR-002: System MUST perform pre-apply validation with row-level feedback.
- US4-FR-003: System MUST block commit when validation policy fails.
- US4-FR-004: System MUST validate placeholder integrity and nested interpolation contract.
- US4-FR-005: System MUST enforce schema, locale/key existence, and duplicate row handling.

#### Success Criteria
- US4-SC-001: Import of 1,000 rows completes with full validation in under 2 minutes.
- US4-SC-002: 100% of placeholder integrity violations are caught before writes.

#### Non-Functional Requirements
- US4-NFR-001: Import validation must be deterministic and auditable.

#### Edge Cases
- US4-EC-001: Partial failure policy must be explicit (block-all vs valid-row apply mode).
- US4-EC-002: Duplicate keys/locales in same batch must resolve predictably.

### User Story US5 - Legal and Compliance Approval Workflow (Priority: P2)
As a Content Owner, I need to route selected strings for legal/compliance review so approval decisions are auditable before publication.

- Why this priority: Foundational governance driver; depends on ownership model.
- Independent Test: Reviewer receives request, approves/rejects with comment, and publication gate enforces pending approvals.

#### Acceptance Scenarios
- US5-AS-001: Given designated review type, When submission occurs, Then configured reviewer(s) are notified.
- US5-AS-002: Given pending approval, When source changes, Then approval is invalidated for re-review.
- US5-AS-003: Given required approval pending, When publish is attempted, Then publish is blocked with clear reason.

#### Functional Requirements
- US5-FR-001: System MUST support optional/manual approval designation by type.
- US5-FR-002: System MUST route requests to configured reviewer contacts.
- US5-FR-003: Reviewers MUST approve/reject with optional comments in-app.
- US5-FR-004: Decisions MUST be audited with actor, timestamp, and decision metadata.
- US5-FR-005: Batch review submission and consolidated notifications MUST be supported.

#### Success Criteria
- US5-SC-001: Approval turnaround improves versus pre-Holocron baseline process.
- US5-SC-002: 100% of approval decisions are audit recorded.

#### Non-Functional Requirements
- US5-NFR-001: Approval gates must be enforceable and tamper-evident in audit records.

#### Edge Cases
- US5-EC-001: Source edits during pending review must invalidate prior pending/approved state per policy.
- US5-EC-002: Multi-string batch reviews must preserve per-string decision traceability.

### User Story US6 - Manage Shared Strings via Aliases (Priority: P2)
As a Content Owner, I need alias relationships across strings so shared terminology can be coordinated without forced inheritance.

- Why this priority: Enables cross-product reuse with controlled governance.
- Independent Test: Alias links are directional metadata, owners receive change notices, and explicit adopt/keep/remove actions are tracked.

#### Acceptance Scenarios
- US6-AS-001: Given semantically related strings, When alias link is created, Then directional relationship is stored.
- US6-AS-002: Given source content changes, When alias is affected, Then alias owner receives actionable notification.
- US6-AS-003: Given owner decision, When adopt/keep/remove is selected, Then decision is applied and audited.

#### Functional Requirements
- US6-FR-001: System MUST support directional alias metadata links.
- US6-FR-002: Alias MUST NOT imply automatic inheritance by default.
- US6-FR-003: System MUST notify alias owners on source changes.
- US6-FR-004: System MUST support explicit adopt, keep, or unlink decisions.
- US6-FR-005: System MUST prevent alias cycles and enforce traversal depth limits.
- US6-FR-006: System MUST support global namespace prefix for shared keys.

#### Success Criteria
- US6-SC-001: Alias relationships are manageable without developer intervention.
- US6-SC-002: No unintended cascading content changes occur from alias links.

#### Non-Functional Requirements
- US6-NFR-001: Alias traversal and dependency evaluation must remain bounded and performant.

#### Edge Cases
- US6-EC-001: Circular alias relationship attempts must be blocked.
- US6-EC-002: Deep alias chains must enforce safe max-depth behavior.

### User Story US7A - View Version History and Audit Visibility (Priority: P1)
As a Content Owner, I need full historical visibility for strings so I can understand what changed, by whom, and when.

- Why this priority: Safety and governance foundation for MVP.
- Independent Test: User views complete source and locale histories with actor/timestamp details.

#### Acceptance Scenarios
- US7A-AS-001: Given multiple edits over time, When version history is opened, Then all versions and metadata are visible.

#### Functional Requirements
- US7A-FR-001: System MUST retain immutable source version history.
- US7A-FR-002: System MUST retain independent locale version history.
- US7A-FR-003: Audit retention MUST follow enterprise retention policy.

#### Success Criteria
- US7A-SC-001: Any prior version is retrievable in under 1 minute.

#### Non-Functional Requirements
- US7A-NFR-001: Historical data storage must support long-term retention and integrity.

#### Edge Cases
- US7A-EC-001: High-frequency edits must preserve complete and ordered event history.
- US7A-EC-002: Retired records must remain visible in history.

### User Story US7B - Rollback Capability (Priority: P3)
As a Content Owner, I need non-destructive rollback so prior content can be restored while preserving full auditability.

- Why this priority: Important operational safeguard but can follow core visibility features.
- Independent Test: Rollback creates a new version from prior content and records rollback provenance.

#### Acceptance Scenarios
- US7B-AS-001: Given selected prior version, When rollback is confirmed, Then a new current version is created using prior content.

#### Functional Requirements
- US7B-FR-001: System SHOULD support rollback by creating a new version only.
- US7B-FR-002: Rollback events SHOULD capture source version reference and actor metadata.

#### Success Criteria
- US7B-SC-001: Prior versions can be restored quickly via governed rollback workflow.

#### Non-Functional Requirements
- US7B-NFR-001: Rollback operations must never mutate historical records.

#### Edge Cases
- US7B-EC-001: Approval state behavior on rollback requires explicit governance decision.
- US7B-EC-002: Locale consistency on source rollback must be deterministic.

### User Story US8 - Deliver Strings to Consuming Applications (Priority: P1)
As an engineer, I need a reliable delivery mechanism for namespace-scoped strings so applications can render managed text without hardcoding.

- Why this priority: Required for managed content to be consumable by applications.
- Independent Test: Consumer retrieves namespace payload with metadata and fallback indicators for missing translations.

#### Acceptance Scenarios
- US8-AS-001: Given strings in namespace, When namespace request is made, Then structured payload returns key, value, locale, version, and fallback metadata.
- US8-AS-002: Given missing locale translation, When request is resolved, Then en-US fallback is returned with explicit indicator.
- US8-AS-003: Given key debugging need, When key lookup is performed in management UI, Then current value and recent changes are visible.

#### Functional Requirements
- US8-FR-001: System MUST provide machine-consumable retrieval by product and namespace.
- US8-FR-002: System MUST support single-request namespace-prefix retrieval.
- US8-FR-003: System MUST return fallback indicators when source fallback is applied.
- US8-FR-004: Delivery interface MUST require authentication.
- US8-FR-005: Management app MUST support key lookup for engineers without admin-only access.

#### Success Criteria
- US8-SC-001: Integrated consumers can remove hardcoded strings.
- US8-SC-002: Delivery mechanism handles peak load targets once finalized by architecture.

#### Non-Functional Requirements
- US8-NFR-001: Delivery availability MUST be 99.9% or higher.
- US8-NFR-002: Namespace retrieval latency MUST meet render-safe threshold (target to be finalized).

#### Edge Cases
- US8-EC-001: Fallback behavior across alias relationships requires explicit architecture decision.
- US8-EC-002: Large namespace payload handling must remain performant.

### User Story US9A - Core Search and Filters (Priority: P1)
As a management app user, I need core search/filter capability to find strings quickly at scale.

- Why this priority: Core usability requirement for large string inventories.
- Independent Test: User can find strings by key/content/tag and filter by core metadata fields.

#### Acceptance Scenarios
- US9A-AS-001: Given partial query, When search runs, Then matching strings are returned from MVP fields.
- US9A-AS-002: Given approval-status filter, When applied, Then results reflect only matching states.

#### Functional Requirements
- US9A-FR-001: System MUST support search by key, source content, and tags.
- US9A-FR-002: System MUST support filters for product/application, approval status, created by, and modified by.

#### Success Criteria
- US9A-SC-001: Any string in a 100,000+ corpus is discoverable in under 5 seconds.

#### Non-Functional Requirements
- US9A-NFR-001: Search index and query behavior must support sustained interactive usage.

#### Edge Cases
- US9A-EC-001: Large result sets require stable pagination and sort behavior.
- US9A-EC-002: Concurrent updates must not produce stale or inconsistent filter counts.

### User Story US9B - Where Used Lookup (Priority: P2)
As a user, I need where-used visibility for keys and aliases so I can assess impact before changes.

- Why this priority: Supports safe change management across reuse links.
- Independent Test: A selected key shows all referencing products and alias relationships.

#### Acceptance Scenarios
- US9B-AS-001: Given a selected key, When where-used is requested, Then all references are returned.

#### Functional Requirements
- US9B-FR-001: System MUST provide where-used lookup across products and aliases.

#### Success Criteria
- US9B-SC-001: Impact assessment can be completed from in-app where-used evidence.

#### Non-Functional Requirements
- US9B-NFR-001: Relationship traversal for where-used must remain bounded.

#### Edge Cases
- US9B-EC-001: Alias cycles or deep chains must not break where-used computation.
- US9B-EC-002: Deleted/retired references must be represented clearly.

### User Story US9C - Advanced Reuse and Bulk Search Tools (Priority: P3)
As a user, I need advanced search and bulk actions for large-scale operations.

- Why this priority: Efficiency enhancement after MVP search capabilities.
- Independent Test: User can multi-select search results and perform supported bulk operations.

#### Acceptance Scenarios
- US9C-AS-001: Given canonical search mode, When searching for reuse opportunities, Then canonical entries and direct actions are available.

#### Functional Requirements
- US9C-FR-001: Search SHOULD expand to translated content and context notes.
- US9C-FR-002: Filters SHOULD expand to locale, translation status, and version/date range.
- US9C-FR-003: Results SHOULD support multi-select and bulk operations.

#### Success Criteria
- US9C-SC-001: High-volume content maintenance effort is reduced for power users.

#### Non-Functional Requirements
- US9C-NFR-001: Bulk operation UX and processing must remain predictable at scale.

#### Edge Cases
- US9C-EC-001: Mixed-permission result sets must only allow authorized bulk actions.
- US9C-EC-002: Bulk failures must return actionable per-item error details.

### User Story US10A - Core Access Roles (Priority: P1)
As an administrator, I need core role and scope controls so users only operate within authorized product boundaries.

- Why this priority: Required for secure baseline operation.
- Independent Test: Role assignment controls editing capabilities and product-level visibility exactly as configured.

#### Acceptance Scenarios
- US10A-AS-001: Given role assignment by product, When user logs in, Then capabilities match role.
- US10A-AS-002: Given read-only role, When browsing product content, Then editing and approvals are disabled.

#### Functional Requirements
- US10A-FR-001: System MUST integrate with enterprise identity system.
- US10A-FR-002: System MUST support Product Content Owner and Read-Only roles in MVP.
- US10A-FR-003: System MUST enforce product-level data access restrictions.
- US10A-FR-004: Unauthorized users MUST NOT view/export/modify out-of-scope content.
- US10A-FR-005: Role model MUST be extensible for future roles.

#### Success Criteria
- US10A-SC-001: Access control violations for out-of-scope data are prevented by policy.

#### Non-Functional Requirements
- US10A-NFR-001: Authorization checks must be consistent and low-latency.

#### Edge Cases
- US10A-EC-001: Role changes should take effect predictably with bounded propagation delay.
- US10A-EC-002: Cross-product users must receive only authorized composite views.

### User Story US10B - Advanced Role Governance (Priority: P2)
As an organization at scale, we need additional governance roles to separate drafting, publishing, and review responsibilities.

- Why this priority: Supports operational maturity after MVP.
- Independent Test: Advanced roles enforce policy boundaries for creation, review, and publish paths.

#### Acceptance Scenarios
- US10B-AS-001: Given a Draft Contributor, When they edit content, Then publish actions are not available.
- US10B-AS-002: Given a Legal/Compliance Reviewer, When review is requested, Then reviewer can issue decisions without content ownership rights.

#### Functional Requirements
- US10B-FR-001: System MUST support Draft Contributor role.
- US10B-FR-002: System MUST support Legal/Compliance Reviewer role.
- US10B-FR-003: System MUST support Administrator governance overrides under policy.
- US10B-FR-004: Translation Reviewer role MAY be supported if required.

#### Success Criteria
- US10B-SC-001: Governance separation of duties can be configured without schema changes.

#### Non-Functional Requirements
- US10B-NFR-001: Role expansion must remain backward compatible with MVP authorization model.

#### Edge Cases
- US10B-EC-001: Overlapping role assignments must resolve with deterministic precedence.
- US10B-EC-002: Governance override actions must be fully auditable.

### User Story US11A - String Ownership Core (Priority: P1)
As a Content Owner or Administrator, I need every string to have designated owner(s) at creation so accountability and routing always have a clear responsible party.

- Why this priority: Ownership is required for routing, escalation, and governance integrity.
- Independent Test: String cannot be saved without owner assignment; ownership can be maintained over lifecycle.

#### Acceptance Scenarios
- US11A-AS-001: Given string creation, When required fields are entered, Then at least one owner is mandatory.
- US11A-AS-002: Given owner deactivation, When publish is attempted, Then publish is blocked if no active owner remains.
- US11A-AS-003: Given ownership transfer, When reassignment is completed, Then audit trail records the change.

#### Functional Requirements
- US11A-FR-001: Every string MUST have one or more designated owners at creation.
- US11A-FR-002: Multiple owners MUST be supported.
- US11A-FR-003: Ownership must be visible and searchable.
- US11A-FR-004: Deactivated owners trigger reassignment controls and publish gating.
- US11A-FR-005: Reassignment MUST be available to owner(s) and administrators, with audit record.

#### Success Criteria
- US11A-SC-001: All active strings have at least one active owner at all times.

#### Non-Functional Requirements
- US11A-NFR-001: Ownership checks must be enforced consistently in publish workflow.

#### Edge Cases
- US11A-EC-001: Owner deactivation during in-flight review must preserve deterministic routing behavior.
- US11A-EC-002: Multi-owner edits require clear responsibility attribution and audit capture.

### User Story US11B - Additional Contribution Roles (Priority: P2)
As an organization, we need contributor roles beyond owners so drafting can be delegated while publish accountability remains controlled.

- Why this priority: Supports scaled operating model without weakening governance.
- Independent Test: Contributor can prepare changes but cannot publish unless policy permits.

#### Acceptance Scenarios
- US11B-AS-001: Given contributor role assignment, When user edits draft content, Then changes can be saved but publish remains restricted.

#### Functional Requirements
- US11B-FR-001: System MUST support governed draft/proposer-style contribution roles in future phase.

#### Success Criteria
- US11B-SC-001: Draft throughput increases without loss of ownership accountability.

#### Non-Functional Requirements
- US11B-NFR-001: Contributor role introduction must not alter existing owner/admin guarantees.

#### Edge Cases
- US11B-EC-001: Contributor and owner overlaps must be policy-safe and auditable.
- US11B-EC-002: Role revocation during active draft sessions must resolve safely.

## Cross-Cutting Concerns

### Key Entities
- String: Unique namespaced key, source text, context, placeholders, tags, status, owner(s), version history, audit entries.
- Translation: Locale-specific content, status, source version linkage, per-locale history.
- Product/Application: Top-level scope container for keys and access control.
- AliasRelationship: Directional link between keys with decision history.
- Approval: Review designation, status, reviewer decision metadata.
- User: Authenticated identity with product-scoped role assignments.
- AuditEntry: Immutable actor/timestamp operation records.

### Cross-Cutting Non-Functional Requirements
- CC-NFR-001: Data in transit MUST be encrypted using enterprise-approved standards.
- CC-NFR-002: Data at rest MUST comply with enterprise encryption and classification requirements.
- CC-NFR-003: Structured logs, metrics, and traces MUST be emitted for observability.
- CC-NFR-004: Health/readiness endpoints MUST be provided for operations.
- CC-NFR-005: Architecture MUST support horizontal scaling and at least 500,000 strings.
- CC-NFR-006: Secrets MUST be managed in approved enterprise secret store only.
- CC-NFR-007: Containers MUST run as non-root from approved internal registries.
- CC-NFR-008: DR posture MUST define and validate RPO/RTO targets.
- CC-NFR-009: Delivery service MUST support per-consumer rate limiting and quotas.

### Cross-Cutting Edge Cases
- CC-EC-001: Full Unicode and bidirectional text must remain intact across storage and delivery.
- CC-EC-002: Alias and placeholder cycle detection must prevent runaway resolution.
- CC-EC-003: Concurrent multi-user edits must avoid silent overwrites.

## Assumptions
- ASMP-001: en-US is authoritative source for all translations. (Owner: Product)
- ASMP-002: No external AI translation automation is in scope for this version. (Owner: Product)
- ASMP-003: Translation provider and exchange format decisions will be finalized before import delivery. (Owner: Product + Stakeholders)
- ASMP-004: Enterprise identity services satisfy authentication and role mapping needs. (Owner: Infrastructure)
- ASMP-005: In-system binary/screenshot storage remains out of scope for this version. (Owner: Product/Architecture)

## Dependencies
- DEP-001: Enterprise identity management integration - Owner: Enterprise Infrastructure. Needed-by: MVP access control implementation. Risk if delayed: Cannot enforce scoped authorization.
- DEP-002: Translation service partner and format decision - Owner: Product + Stakeholders. Needed-by: Translation export/import delivery. Risk if delayed: Translation workflow blocked.
- DEP-003: Key schema and namespace governance decision - Owner: Architecture Team. Needed-by: Before production authoring starts. Risk if delayed: Rework and migration risk.
- DEP-004: Delivery mechanism architecture decision - Owner: Engineering Architecture. Needed-by: US8 build start. Risk if delayed: Consumer integration blocked.
- DEP-005: AKS namespace and database provisioning - Owner: Infrastructure. Needed-by: Environment readiness milestone. Risk if delayed: Delivery schedule slip.
- DEP-006: Audit retention policy confirmation - Owner: Legal/Compliance. Needed-by: Before production retention controls. Risk if delayed: Governance non-compliance.

## Clarifications
### Session 2026-05-19
- Q: Should legal/compliance approvals remain P1 or move behind ownership readiness? -> A: Moved to P2 pending validation because ownership is prerequisite for reliable routing.
- Q: Should rollback restore prior approval automatically? -> A: Decision pending (open question in source PRD).
- Q: Should alias fallback be used before en-US fallback in delivery? -> A: Decision pending architecture review.

## Out of Scope (Future Considerations)

### Deferred to Future Release
- AI-assisted translation automation: Not in scope for this version.
- Figma/design-system integration for key assignment: Future consideration.
- In-app access for external translation vendors: Exchange-file workflow only for current scope.
- Screenshot preview per locale and layout simulation: Future consideration.
- A/B testing and regional variants: Deferred.
- Component ripple/pin behavior for string propagation: Deferred.

### Not in Current Scope
- In-system binary asset storage for translation context.
- Public or unauthenticated access to string delivery contracts.
- Runtime behavior coupling to implementation-specific delivery mechanism details.

## Open Questions (From Source PRD)
- OQ-001: Final lifecycle states for source and translation content.
- OQ-002: Propagation SLA from publish to consumer availability.
- OQ-003: Alias-aware fallback behavior before en-US fallback.
- OQ-004: Peak RPS target for delivery mechanism.
- OQ-005: Alias hierarchy depth and governance rules.
- OQ-006: Approval behavior for rollback to previously approved vs non-approved versions.
- OQ-007: Optional review vs required review in publish workflow.
