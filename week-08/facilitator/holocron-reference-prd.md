# Holocron — Reference PRD (Facilitator Answer Key)

> Facilitator-only — **do not hand to participants.** This is the real, fully-specified Holocron PRD (new format, revised 2026-05-19). It is **19 Capability Stories** plus cross-cutting concerns and appendices. Participants receive only `handouts/holocron-problem-brief.md` (business context, facts, stakeholders, constraints) and derive their own requirements from it.
>
> **Facilitator-only** — ships in the facilitator folder of every repo (public + instructor); the facilitator folder is the separation from participants. Do not hand it to quads.
>
> **How to use this:** as a comparison reference during Day 2–4 coaching and Friday review — **not** a grading rubric. A quad's PRD will differ from this and can still be excellent. What is worth checking against it:
> - Did they find the **governance / compliance** driver (legal review gates, audit evidence), not just the "editing is slow" driver?
> - Did they scope a **defensible slice** (the P1 Capability Stories), or try to specify all 19?
> - Do their non-functional requirements engage the real numbers (150+ countries, 20–30+ apps, 30–40 languages, ~500k strings, audit retention)?
> - Did they surface the genuinely **open questions** rather than inventing answers?
> - Did they treat **fallback behaviour, placeholder integrity, and audit immutability** as requirements? These are the most commonly missed.

---

Holocron String Management Service

| **Field** | **Value** |
|----|----|
| Spec Branch | N/A |
| Created | 2026-05-19 |
| Status | Draft |
| Input | Holocron Requirements Discussion — Chance & Anna · Holocron discussion — Nick Grant, Daniel Rowe & Anna · VPC Working Draft 2026-05-19 · Lean Business Case 2026-05-19 · Enterprise Epic Request Input |

## Problem Statement

UI text across the enterprise is managed in fragmented, often hardcoded patterns. Changing a single label can require a code deployment, engineering involvement, and a multi-day or multi-week turnaround. For a global company operating across 150+ countries with 20–30+ applications and 30–40 supported languages, this creates:

- Slow change cycles: what should be an hour of work takes days or weeks due to deployment dependencies

- Engineering bottleneck: content changes that require no technical judgment nonetheless consume engineering capacity

- Compliance and legal risk: strings can ship without legal review; audit evidence of review decisions is distributed and inconsistent

- Translation inconsistency: no single source of truth means translation quality and completeness vary across products and languages

- Tech debt accumulation: every new application built with hardcoded strings requires future retrofit when governance, translation, or platform standards tighten

## Solution Overview

Holocron is a centralized string management wherein content changes do not require code deployments to consuming applications. All text is authored and governed in one place service providing:

- Management Application — A web-based interface for content owners, legal/compliance reviewers, and administrators to create, edit, govern, and monitor strings

- Structured Delivery to Consuming Applications — A governed mechanism for consuming applications to retrieve strings by application and namespace without hardcoding

- Translation Exchange Workflow — Export and import capabilities for routing strings to and from translation services

- Governance Workflows — Approval routing, audit trail, version history, and alias-based cross-product governance

## Capability Stories

### Capability Story 1 — Core Access Roles (Priority: P1)

> **Persona:** Authenticated Employee, Content Owner, Holocron Administrator
>
> As a Holocron user, I need access to be enforced by role and scope so that all authenticated employees can view product content while product changes, review actions, and administrator capabilities remain limited to authorized users.
>
> **Independent Test (DRAFT):** *An authenticated employee with no assigned role can view and search any product's strings, translations, and history; a Content Owner can modify only products they own; and a Holocron Administrator can grant a Review Administrator privilege — each verified in isolation.*

#### Acceptance Scenarios

> **CS1-AS-001** — Given I am an authenticated employee, when I navigate to any product, then I can view and search its string content, translations, version history, review history, and audit history without a separately assigned role.
>
> **CS1-AS-002** — Given I am a Content Owner for a product, when I access that product, then I can perform the product and content-management actions authorized for Content Owners; when I access a product I do not own, then modification and configuration controls are unavailable.
>
> **CS1-AS-003** — Given I am a Holocron Administrator, when I appoint a Legal, Compliance, or Translation Review Administrator, then I can grant one or more of those administration privileges, and the appointed Review Administrator can appoint additional administrators only within the same authorized review domain or domains.
>
> **CS1-AS-004** — Given I am a Holocron Administrator, when I add an authenticated employee as a Content Owner for an existing product/application, then the employee receives Content Owner access to that product, existing ownership remains unchanged, and the assignment is recorded in the audit trail.
>
> **CS1-AS-005** — Given all Content Owners assigned to a product/application are inactive, when a user attempts to publish a string within that product scope, then the system blocks publication and identifies that an active Content Owner must be assigned before publication can proceed.

#### Functional Requirements

> **CS1-FR-001** — The system MUST integrate with the enterprise identity management system for authentication.
>
> **CS1-FR-002** — The system MUST support the following roles at minimum: Product Content Owner, Reviewer, Review Administrator, and Holocron Administrator. Authenticated employee access MUST provide view and search capabilities without requiring a separately assigned Read-Only role.
>
> **CS1-FR-003** — The system MUST allow authenticated employees to view and search all products and their string content while enforcing product-level permissions for creating, editing, publishing, retiring, restoring, ownership management, and product configuration.
>
> **CS1-FR-004** — Active Owner Publication Requirement: The system MUST identify products without an active Content Owner and MUST prevent strings within those product scopes from advancing to Published status until an active Content Owner is assigned.
>
> **CS1-FR-005** — The system MUST prevent users from modifying, configuring, or completing review actions outside the permissions granted by their product, review-type, and locale scope when applicable.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 2 — Set Up and Manage a Product/Application (Priority: P1)

> **Persona:** Content Owner
>
> As a Content Owner with access to Holocron, I need to create and manage a product/application workspace so that I can establish its namespace, ownership, and string-management scope without relying on a central administrator.
>
> **Independent Test (DRAFT):** *A Content Owner can create a product/application with a unique identifier, be assigned as its initial Content Owner, add and remove co-owners (never removing the last active one), configure target languages, and retire then restore the product — all observable within this story alone.*

#### Acceptance Scenarios

> **CS2-AS-001** — Given I am an authenticated Holocron user, when I create a product/application with the required information and a unique application identifier, then the system creates the product workspace, assigns me as its initial Content Owner, and records the creation in the audit trail.
>
> **CS2-AS-002** — Given I enter an application identifier that is already in use, when I attempt to create the product/application, then creation is blocked and the system informs me that the identifier must be unique.
>
> **CS2-AS-003** — Given a product/application has been created, when a string is created within that product workspace, then the application identifier is automatically used as the first segment of the string namespace.
>
> **CS2-AS-004** — Given I am a Content Owner for a product/application, when I add another authenticated Holocron user as a Content Owner, then that user receives Content Owner access to the product and the change is recorded in the audit trail.
>
> **CS2-AS-005** — Given a product/application has multiple Content Owners, when an existing Content Owner removes another owner, then the change is allowed only if at least one active Content Owner remains assigned.
>
> **CS2-AS-006** — Given a product/application has one or more active Content Owners, when a string is created or viewed within that product scope, then the string inherits the product’s current ownership without requiring a separate string-level owner assignment.
>
> **CS2-AS-007** — Given I am creating or managing a product/application, when I select one or more supported target languages and save the configuration, then those languages are associated with the product and become the available target languages for translation requests, translation imports, review, and locale-specific publication.
>
> **CS2-AS-008** — Given I am a Content Owner for a product/application, when I retire the product and confirm the impact, then the product and all strings within it transition to Retired, those strings are no longer delivered, affected alias owners are notified and asked to break their aliases, and the retirement is recorded in the audit trail.
>
> **CS2-AS-009** — Given a product/application is Retired, when I restore it, then the system follows the non-destructive rollback method by restoring the product as active and creating new Draft versions for its strings from the most recent versions that existed before retirement, while preserving all history and audit records.

#### Functional Requirements

> **CS2-FR-001** — Product/Application Creation: The system MUST allow any authenticated Holocron user to create a product/application workspace by providing the required product information and a unique application identifier.
>
> **CS2-FR-002** — Product Identifier Uniqueness: The system MUST enforce uniqueness of the application identifier and MUST prevent creation when the identifier is already in use.
>
> **CS2-FR-003** — Namespace Root: The system MUST use the application identifier as the first segment of every string namespace created within the product/application workspace.
>
> **CS2-FR-004** — Initial Product Ownership: The system MUST assign the product/application creator as an initial Content Owner when the workspace is created.
>
> **CS2-FR-005** — Product Owner Management: An existing Content Owner MUST be able to add or remove authenticated Holocron users as Content Owners for the product/application, but the system MUST prevent removal of the last active Content Owner.
>
> **CS2-FR-006** — Product Ownership Inheritance: Every product/application MUST have at least one active Content Owner before strings can be created, and all strings within the product scope MUST inherit the product’s current ownership without independent owner assignments by default.
>
> **CS2-FR-007** — Product Language Configuration: The system MUST allow an authorized Content Owner to add or remove one or more supported target languages for a product/application. US English MUST remain the authoritative source language and MUST NOT require target-language selection.
>
> **CS2-FR-008** — Product Language Workflow Scope: The product/application’s configured target languages MUST determine the locales available for translation requests, translation exports, imported translations, translation review, translation coverage, and locale-specific publication. Changes to configured target languages MUST be recorded in the audit trail.
>
> **CS2-FR-009** — Product Retirement and Restoration: The system MUST allow an authorized Content Owner to retire a product/application and all strings within it. Retirement MUST exclude those strings from delivery, preserve the product and string histories, identify active aliases to affected strings, and notify the alias owners to break the links. The system MUST allow restoration using a non-destructive rollback method that reactivates the product and creates new Draft string versions from the most recent versions that existed before retirement.
>
> **CS2-FR-010** — Product Configuration Audit Trail: The system MUST record product/application creation and Content Owner additions and removals, including the affected product, actor, and timestamp.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 3 — Create and Publish Strings (Priority: P1)

> **Persona:** Content Owner
>
> As a Content Owner, I need to create and publish strings with full version and audit history so that I can manage UI text for my product without filing engineering requests.
>
> **Why this priority:** This is the foundational capability. Without it, the system has no value for any downstream workflow.
>
> **Independent Test (DRAFT):** *A Content Owner can create a new string with a unique namespaced key and English content, see it saved as Draft v1, publish it after confirming the no-review warning, and confirm the published value and full audit trail — with no code deployment.*

#### Acceptance Scenarios

> **CS3-AS-001** — Given I am a Content Owner with access to my product namespace, When I create a new string with a valid namespaced key and English content, Then the string is automatically saved as a “Draft” with version 1, appears in my string table, and the creation is recorded in the audit trail with my user identity and a timestamp.
>
> **CS3-AS-002** — Given I attempt to create a string with a key that already exists in my product namespace, When I submit the form, Then creation is blocked and I receive a clear validation error indicating the key already exists.
>
> **CS3-AS-003** — Given I want to add context so translators and engineers understand how a string is used, When I populate the context notes field, Then the context is stored with the string and visible to anyone who views or exports it.
>
> **CS3-AS-004** — Given a new string contains placeholders such as {shipmentId} or {count}, when I save the string, then the system detects and stores the placeholder metadata and displays the placeholders visually in the editor.
>
> **CS3-AS-005** — Given I am a content owner and have a string in draft that does not require any reviews and has all the required fields, when I select the option to publish the string, I am presented with a warning message asking me to confirm publishing without review, and when I confirm, the string is saved as a published version with a full audit trail and is made available to consuming applications.
>
> **CS3-AS-006** — Given I am a content owner working within a specific product workspace, when I create a string, the product section of the namespace is entered as first segment of the namespace.
>
> **CS3-AS-007** — Given I am a Content Owner who is not working within a specific product context, when I create a string, then I must select the product from a list of products for which I am a Content Owner; the selected product serves as the first segment of the namespace.
>
> **CS3-AS-008** — Given I am creating an English source string for a product I own, when I add one or more review designations, then I can select Legal, Compliance, and/or Peer Review, and the saved source string displays those designations for later review submission.

#### Functional Requirements

> **CS3-FR-001** — The system MUST allow content owners to create string records with unique namespaced keys scoped to their product or application.
>
> **CS3-FR-002** — Each string MUST store US English (en-US) as the source language. US English is the authoritative source for all translations.
>
> **CS3-FR-003** String Context and Metadata Model: Each string MUST store and display optional context notes describing how and where the string is used
>
> **CS3-FR-004** — Placeholder Metadata and Validation: The system MUST detect, store, and visually display placeholder metadata for positional placeholders such as {0} and {1}, named placeholders such as {shipmentId} and {customerName}, plural-dependent text, choice-dependent text, and nested placeholder patterns that require a separate translation lookup. Placeholder syntax and metadata MUST be preserved in export and import exchange formats and made available to translation lifecycle processing. The system MUST validate source and translated content against the stored placeholder metadata and identify missing, added, altered, or malformed placeholders before save or import as applicable.
>
> **CS3-FR-005** — The system MUST automatically assign version 1 to newly created strings and increment the version number on each subsequent edit to the source content.
>
> **CS3-FR-006** — The system MUST enforce a namespaced key structure. Keys MUST follow a dotted hierarchy pattern (e.g., product.feature.element). The specific minimum and maximum segment count is a discovery decision to be confirmed before implementation. OPEN TOPIC
>
> **CS3-FR-007** — Newly created strings MUST enter Draft status by default. A string in Draft status is editable but is not delivered to consuming applications.
>
> **CS3-FR-008** — A Content Owner MAY submit a Draft source-string version for review. Submitting for review creates an independent review request and MUST NOT change the source string’s lifecycle status or lock the source string from editing.
>
> **CS3-FR-009** — The system MUST support publishing an eligible Draft source-string version. If publishing without a requested review, the system MUST display a clear confirmation warning before completing publication. The publish action is explicit, creates the Published version available to consuming applications, and is recorded in the audit trail.
>
> **CS3-FR-010** — String keys MUST be immutable once a string is created. If a key must change, a new string with the new key must be created; the original string may be aliased or retired. This prevents breaking changes in consuming applications that reference string keys.
>
> **CS3-FR-011** — The system MUST provide a detail view for strings, including full edit capability as permissions allow, version history, Context Notes, Screenshot Link, Screenshot Reference, Do Not Translate designation, placeholder metadata, and audit trail.
>
> **CS3-FR-012** — The system MUST support source-string lifecycle states including Draft, Published, and Retired. Each state transition MUST be recorded in the audit trail with the actor and timestamp. Review requests and outcomes MUST be tracked independently from the source-string lifecycle status.
>
> **CS3-FR-013** — Source-String Field Contract: To create a source string, the required user-entered fields MUST be the product/application, unless inherited from the current product workspace, a valid unique namespaced key, and US English source text. Context Notes, Screenshot Link, Screenshot Reference, Do Not Translate, and review designations MUST remain optional. Screenshot Link accepts an externally hosted screenshot URL; Screenshot Reference accepts an externally hosted asset ID. Do Not Translate is a whole-string flag indicating that the English source content must be preserved through translation workflows. The system MUST assign the source locale, inherited product ownership, lifecycle status, version, actor identity, and timestamps; these system-assigned values are part of the source-string record but are not required authoring fields.
>
> **CS3-FR-014** — Screenshot Context Fields: The system MUST provide optional Screenshot Link and Screenshot Reference fields for translation context. Screenshot Link MUST accept an externally hosted screenshot URL, and Screenshot Reference MUST accept an externally hosted asset ID. The system MUST record additions, changes, and removals of either field in the audit trail. In-system screenshot or binary storage remains out of scope.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 4 — Edit Strings (Priority: P1)

> **Persona:** Content Owner
>
> As a Content Owner, I need to edit strings with full version and audit history so that I can manage UI text for my product without filing engineering requests.
>
> **Why this priority:** This is the foundational capability. Without it, the system has no value for any downstream workflow.
>
> **Independent Test (DRAFT):** *A Content Owner can edit an existing string's English content, see a new draft version created with the prior version preserved, publish after the no-review warning, and retire then restore the string — with every change captured in the audit trail.*

#### Acceptance Scenarios

> **CS4-AS-001** — Given a string exists at version 1, When I edit the English content and save, Then a new version is automatically saved as draft, the previous version is preserved in history, and the audit trail records my change with my user identity and timestamp.
>
> **CS4-AS-002** — Given an edited string exists as a draft, when I select the option to publish the string, I am presented with a warning message asking me to confirm publishing without review, and when I confirm, the string is saved as a published version with a full audit trail and is made available to consuming applications.
>
> **CS4-AS-003** — Given I am editing a string within a product for which I am a Content Owner, when I add one or more new or existing tags or remove an assigned tag and save, then the string displays the updated tags, the tags are available for search and filtering, and the tag changes are recorded in the audit trail.
>
> **CS4-AS-004** — Given I am editing an English source string within a product I own, when I add or remove one or more review designations and save, then the string displays the updated Legal, Compliance, and/or Peer Review designations, and the change is recorded in the audit trail.
>
> **CS4-AS-005** — Given I am a Content Owner for a product and a string is Draft or Published, when I retire the string and confirm the action, then the String Lifecycle Status becomes Retired, the string is no longer delivered to consuming applications, and the retirement is recorded in the audit trail.
>
> **CS4-AS-006** — Given the string I am retiring is the canonical source for one or more active aliases, when I review the retirement impact and confirm retirement, then the system allows the retirement, shows me each affected alias and its Content Owners, notifies those owners that the canonical string is Retired, and asks them to break the alias.
>
> **CS4-AS-007** — Given a string is Retired, when I restore it, then the system follows the non-destructive rollback method by creating a new Draft version from the most recent version that existed before retirement, preserves all history, and records the restoration in the audit trail.

#### Functional Requirements

> **CS4-FR-001** — When a content owner edits source content in a way that removes or alters placeholders that exist in one or more currently Published translations, the system MUST warn the user, require explicit acknowledgement before saving, and automatically transition all affected translations to Outdated status. The system MUST NOT block the save outright — refining source content is a legitimate operation. Blocking is reserved for cases where the user has not acknowledged the downstream impact.
>
> **CS4-FR-002** — String Tag Management: The system MUST allow an authorized Content Owner to add new or existing tags to a string, remove assigned tags, display the current tags on the string detail view, make assigned tags available to search and filtering, and record tag additions and removals in the audit trail.
>
> **CS4-FR-003** — String Review Designation Management: The system MUST allow an authorized Content Owner to add or remove Legal, Compliance, and Peer Review designations on an English source string, display the current designations on string details, and record designation changes in the audit trail. Translation Review designations MUST be applied to a locale-specific translation rather than the English source string.
>
> **CS4-FR-004** — String Retirement and Restoration: The system MUST allow an authorized Content Owner to retire a Draft or Published string and MUST exclude Retired strings from delivery. The system MUST allow restoration by creating a new Draft version from the most recent version that existed before retirement, preserving prior versions and audit history.
>
> **CS4-FR-005** — Canonical Retirement Impact: Before retiring a canonical string, the system MUST display all active aliases and their current Content Owners. Retirement MUST remain allowed. After retirement, the system MUST notify each affected alias owner that the canonical string is Retired and direct them to break the alias. The retirement, affected aliases, notifications, actor, and timestamp MUST be recorded in the audit trail.

#### Success Criteria

> **CS4-SC-001** — Within 90 days of launch, at least 90% of source-string content changes are completed by Content Owners without engineering intervention, measured through recurring stakeholder survey.
>
> **CS4-SC-002** — For routine source-string edits (no schema/key changes), median published-to-live cycle time is 15 minutes or less, measured through recurring stakeholder survey.

#### Non-Functional Requirements

> **CS4-NFR-001** — The management application MUST maintain 99.99% or higher availability.

#### Edge Cases

> **CS4-EC-001** Concurrent edits: If two users edit the same string simultaneously, the system MUST apply optimistic locking and present a conflict resolution dialog showing both versions before allowing save.

### Capability Story 5 — View Version History and Audit Visibility (Priority: P1)

> **Persona:** Content Owner
>
> As a Content Owner, I need to view the full version history of a string so that I can understand what changed, by whom, and when.
>
> **Why this priority:** Version history is a foundational safety and governance mechanism for MVP.
>
> **Independent Test (DRAFT):** *After a string is edited several times, a Content Owner can open its version history and see every version in reverse-chronological order with content, actor, and timestamp, and filter the audit trail by actor, change type, language, and date.*

#### Acceptance Scenarios

> **CS5-AS-001** — Given a string has been edited multiple times, When I view the version history for that string, Then I see each version reverse-chronologically with its content, the actor who made the change, and the timestamp.
>
> **CS5-AS-002** — Given a string has been modified, When I view the string or translation details, Then I can see the most recent updates relevant to that string or translation on the same page.

#### Functional Requirements

> **CS5-FR-001** — The system MUST keep a permanent record of every change. Each record MUST include who made the change, when it was made, what type of change occurred, and the content before and after the change when applicable.
>
> **CS5-FR-002** — The system MUST maintain immutable version history for every string, preserving content, actor, and timestamp for every version.
>
> **CS5-FR-003** — The system MUST maintain independent version history per language translation, in addition to the English source version history, with a clear link between the translation version and the English source version.
>
> **CS5-FR-004** — The audit trail SHOULD use the common table filtering behavior defined in CS6 — Core Search and Filters, as applicable to audit records. At minimum, users MUST be able to filter by actor, change type, affected language, and date.
>
> **CS5-FR-005** — The audit trail MUST be displayed in reverse chronological order with the most recent updates at the top of the list.
>
> **CS5-FR-006** — Audit trail retention MUST comply with enterprise data retention policy. The specific retention period is a dependency to be confirmed with legal/compliance stakeholders.

#### Success Criteria

> **CS5-SC-001** — TBD — success criteria for CS5 will be defined after value outcomes and measurement approach are finalized.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 6 — Core Search and Filters (Priority: P1)

> **Persona:** Content Owner, Engineers
>
> As a user of the management application, I need core search and filtering across keys, English content, and core metadata so that I can find and manage content efficiently across thousands of strings.
>
> **Independent Test (DRAFT):** *A user can find a target string among thousands by searching a key, content, or metadata value; apply and combine filters within a product scope; clear them to restore the default view; and run a supported bulk action on a multi-select — all on its own.*

#### Acceptance Scenarios

> **CS6-AS-001** — Given a search term appears in a string key, English content, translated content, tag, product/application, namespace key, owner, String Lifecycle Status, Translation State, Review Status, Review Outcome, reviewer, creator, modifier, language/locale, version, or date, when I search using the full or partial value, then matching strings are returned.
>
> **CS6-AS-002** — Given search, filters, or sorting are applied, when I clear them, then the default view and result set is restored.
>
> **CS6-AS-003** — Given search or filter results are displayed, when I select multiple strings and initiate a supported bulk action—add or remove tags, request review, export, or publish—then the system applies the action only to selected strings for which I am authorized and that are eligible for the action. For bulk publish, the system first displays a preflight summary and excludes any string that requires an unresolved individual decision, including a Legal or Compliance override, peer-review confirmation, locale-specific translation publication choice, or active-owner assignment; the summary identifies each excluded string and the reason, and each completed action is recorded in the applicable history or audit trail.
>
> **CS6-AS-004** — Given I am viewing a product/application string table, when I apply one or more supported filters and sort the results, then only strings within that product/application scope that match all selected criteria are displayed in the selected order.
>
> **CS6-AS-005** — Given strings inherit ownership from their product/application, when I view string details or filter search results by owner, then the current product Content Owners are displayed and strings owned by the selected person are returned.
>
> **CS6-AS-006** — Given canonical strings are referenced by aliases, when I filter for reused canonical strings, then I see the matching canonical strings and the products and alias relationships that reference them.

#### Functional Requirements

> **CS6-FR-001** (MVP): The system MUST support global search across key, English content, translated content, tags, product/application, namespace key, owner, String Lifecycle Status, Translation State, Review Status, Review Outcome, reviewer, created by, modified by, language/locale, version, and date range.
>
> **CS6-FR-002** — The system MUST support filtering strings by product/application, string content including translated content, namespace key, owner, String Lifecycle Status, Translation State, Review Status, Review Outcome, reviewer, created by, modified by, language/locale, version, date range, and tags so that users can narrow results to the specific content they need to manage.
>
> **CS6-FR-003** — The system MUST provide a way to filter for all canonical strings (those that have aliases) and show all products and alias relationships referencing a those strings.
>
> **CS6-FR-004** — Bulk String Actions: The system MUST support multi-select and the following bulk actions on search and filter results: add or remove tags, request review, export, and publish. The system MUST apply an action only to selected strings for which the user is authorized and that are eligible for the action. Before bulk publish, the system MUST display a preflight summary and MUST exclude strings requiring an unresolved individual decision, including a Legal or Compliance override, peer-review confirmation, locale-specific translation publication choice, or active-owner assignment. The system MUST identify each excluded string and the reason for exclusion and record each completed action in the applicable history or audit trail.
>
> **CS6-FR-005** — The system MUST support organizing strings by product or application as the top-level grouping container.
>
> **CS6-FR-006** — The system MUST provide a sortable and filterable table view of strings within a product or application scope
>
> **CS6-FR-007** — Ownership Visibility and Filtering: The system MUST display inherited product/application ownership on string details and MUST allow users to search and filter strings by current product Content Owner.
>
> **CS6-FR-008** — The system MUST provide consistent search, filtering, sorting, filter-combination, filter-clearing, and result-selection behavior across applicable table views.

#### Success Criteria

> **CS6-SC-001** — Users can find the correct string in under 30 seconds for at least 80% of search attempts.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 7 — Deliver Strings to Consuming Applications (Priority: P1)

> **Persona:** Engineers (Consuming Application Teams)
>
> As an engineer on a consuming application team, I need a reliable, governed mechanism to retrieve strings by application and namespace so that my application renders the correct text without hardcoding.
>
> **Independent Test (DRAFT):** *An authenticated consuming application can request all strings for a namespace and receive only Published strings (key, content, language, version) with a fallback indicator when English is served, while an unauthenticated request is denied.*

#### Acceptance Scenarios

> **CS7-AS-001** — Given a namespace contains strings in multiple lifecycle states, when a consuming application requests all strings for that namespace, then the system returns only Published matching strings in a structured format including key, content, language, and version.
>
> **CS7-AS-002** — Given strings are requested for a locale, when the system responds, then it returns the content explicitly selected for publication for that locale—an approved or current translation, a previously published translation, or the English source fallback—and includes a clear fallback indicator when English source content is returned.
>
> **CS7-AS-003** — Given an engineer needs to debug unexpected UI text in their application, When they search for the string key in the management application, Then they can find the current content, version, and any recent edits without needing database access or administrative tools.
>
> **CS7-AS-004** — Given a consuming application requests strings without valid authentication, when the request is processed, then access is denied and no string content is returned.

#### Functional Requirements

> **CS7-FR-001** — The system MUST provide a machine-consumable delivery mechanism for consuming applications to retrieve strings by product and namespace key.
>
> **CS7-FR-002** — The delivery mechanism MUST support retrieval of all strings matching a namespace prefix in a single request, returning a structured collection of key-value pairs with metadata (language, version, fallback indicator).
>
> **CS7-FR-003** — Locale Publication Resolution: The delivery mechanism MUST return the content explicitly selected for publication for the requested locale. The selected content MAY be an approved or current translation, a previously published translation, or the English source fallback. When English source content is returned, the response MUST include a clear fallback indicator.
>
> **CS7-FR-004** (Could / For Technical Review): Delivery responses that include fallback content SHOULD provide explicit fallback metadata: resolved locale, fallback source, and fallback reason.
>
> **CS7-FR-005** (For Technical Review): The delivery mechanism MUST require authentication and deny the request if not properly authenticated and authorized.
>
> **CS7-FR-006** — Engineers MUST be able to look up any string key and its current content in the management application without requiring administrative or database access.
>
> **CS7-FR-007** — The delivery mechanism MUST return only Published strings and the locale content selected for publication and MUST exclude Draft, Retired, and other unpublished content.

#### Success Criteria

> **CS7-SC-001** — By Day 90 after CS7 go-live, at least 5 consuming applications are actively using Holocron string delivery (with at least 1 successful API call per week).
>
> **CS7-SC-002** — By Day 90 after CS7 go-live, at least 75% of surveyed engineers report a positive overall experience integrating and using Holocron string delivery in their consuming applications.

#### Non-Functional Requirements

> **CS7-NFR-001** — The string delivery mechanism MUST maintain 99.9% or higher availability.
>
> **CS7-NFR-002** — Response time for a namespace-scoped retrieval request MUST be within an acceptable threshold to avoid impacting application render performance. The specific target is an architecture decision to be set during design.

#### Edge Cases

> *None.*

### Capability Story 8 — Roll Back a Source String (Priority: P3)

> **Persona:** Content Owner
>
> As a Content Owner, I need to restore an English source string to a prior version through a non-destructive rollback flow so that I can correct source-content mistakes without losing audit history.
>
> **Why this priority:** Source rollback provides operational convenience and risk reduction after version history and audit visibility are available.
>
> **Independent Test (DRAFT):** *A Content Owner can select a prior source-string version, confirm the rollback, and see a new Draft version created from that content with all history preserved and the rollback recorded — independently of translation rollback.*

#### Acceptance Scenarios

> **CS8-AS-001** — Given I select a prior source-string version, when I confirm the rollback, then the system creates a new Draft version using the selected version’s content, preserves all existing history, and records the rollback in the audit trail.
>
> **CS8-AS-002** — Given the selected version previously received all required Legal or Compliance approvals, when it is restored, then those approvals remain associated with the restored content (along with their original approval date) and I may request a new review.
>
> **CS8-AS-003** — Given the selected version does not have all designated Legal or Compliance approvals, when it is restored and I attempt to publish it, then I must either complete the applicable approval workflow or explicitly override the unresolved review and provide an override reason before publication can proceed.

#### Functional Requirements

> **CS8-FR-001** — Non-Destructive Rollback: The system MUST allow an authorized Content Owner to restore any prior source-string version by creating a new Draft version with the selected version’s content. Existing versions and history MUST remain unchanged.
>
> **CS8-FR-002** — Rollback Audit Trail: The system MUST record the rollback action, including the selected prior version, newly created version, actor, and timestamp.
>
> **CS8-FR-003** — Prior Approval Preservation: When restored content previously received all required Legal or Compliance approvals, the system MUST preserve those approval records and their original dates with the restored content and prompt the user asking if they wish to request a new review.
>
> **CS8-FR-004** — Reapproval or Explicit Override: When restored content lacks a designated Legal or Compliance approval, the system MUST require the Content Owner either to complete the applicable approval workflow or explicitly override the unresolved review and provide a reason before publication. Any override MUST be recorded with the applicable review context, actor, and timestamp.

#### Success Criteria

> **CS8-SC-001** (Could): TBD — success criteria for CS8 will be defined after value outcomes and measurement approach are finalized.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 9 — Manage Shared Strings via Aliases (Priority: P2)

> **Persona:** Content Owner, Architects
>
> As a Content Owner, I need to relate strings across products using alias relationships so that shared terminology is coordinated without creating rigid dependencies that cause unintended cascading changes.
>
> **Independent Test (DRAFT):** *A Content Owner can create a one-directional alias to a published canonical string, be blocked from forming an alias chain, be notified when a newer canonical version publishes, and either adopt it or break the alias while retaining the adopted values.*

#### Acceptance Scenarios

> **CS9-AS-001** — Given I am creating a string, when its key or source text is similar to an existing canonical (non-alias) string, then the system suggests potential matches and allows me either to create a one-directional alias to a selected published canonical string or continue creating an independent string.
>
> **CS9-AS-002** Given I am creating or changing an alias, when I attempt to link it to a string that is already an alias, then the system prevents the alias chain and prompts me to link directly to the final canonical string instead.
>
> **CS9-AS-003** — Given I am managing an active alias string, when I attempt to update an inherited field, translation, or locale, then the system prevents the update and requires me either to remain fully linked or break the alias before making independent changes.
>
> **CS9-AS-004** — Given my alias is linked to a published canonical version, when a newer canonical version is published, then I am notified of the difference between my currently adopted version and the newer version and can choose either to adopt the newer version or break the alias while retain the values from my currently adopted version.
>
> **CS9-AS-005** — Given I choose to break the alias, when the change is saved, the alias relationship is removed and the adopted version’s content, metadata, and translations are stored as part of my string’s content.
>
> **CS9-AS-006** — Given a newer published canonical version is available, when I adopt it, then the alias inherits that complete canonical version, including its applicable metadata, translations, and translation review outcomes; partial or locale-specific adoption is not available; and the decision is recorded in the audit trail.
>
> **CS9-AS-007** Given my alias remains linked to its currently adopted canonical version, when a translation is added, revised, reviewed, or published for that same canonical version, then the alias inherits that translation lifecycle update, notifying the alias owner, but without requiring a new adoption decision.

#### Functional Requirements

> **CS9-FR-001** — The system MUST support alias relationships linking one string key to a published canonical string.
>
> **CS9-FR-002** — Alias relationships MUST be directional metadata (alias key → canonical_key). Bidirectional aliasing is not permitted.
>
> **CS9-FR-003** — Alias InheritanceThe system MUST allow an alias to inherit the source content, applicable metadata, translations, and translation review outcomes associated with its adopted canonical version.
>
> **CS9-FR-004** — Complete AdoptionThe system MUST apply adoption to the complete canonical version and MUST NOT support partial adoption, field-level overrides, locale-level exceptions, or independent translations while the alias remains active.
>
> **CS9-FR-005** — When a newer published canonical version becomes available, the system MUST notify alias owners and show the change from the currently adopted version.
>
> **CS9-FR-006** — The system MUST allow an alias owner either to adopt the newer canonical version or break the alias while retaining the currently adopted version.
>
> **CS9-FR-007** — Each decision MUST be recorded in the audit trail.
>
> **CS9-FR-008** — Break Alias Snapshot When an alias is broken, the system MUST enhance the string data to create an independent string by copying the source content, applicable metadata, and translations associated with the alias’s currently adopted canonical version.
>
> **CS9-FR-009** — The system MUST only allow one level of aliasing. A string may link to a canonical string, but it MUST NOT link to a string that is already an alias.
>
> **CS9-FR-010** If the selected canonical string already points to another string, the system MUST prompt the user to link directly to that final canonical string instead of creating an alias chain.
>
> **CS9-FR-011** — When creating a new string key, the system SHOULD proactively suggest potential canonical matches (based on key/text similarity and metadata) and offer a non-blocking option to link to an existing canonical string instead of creating a duplicate.
>
> **CS9-FR-012** — Alias Audit TrailThe system MUST record alias creation, canonical-version adoption, and alias removal, including the affected alias, canonical string, canonical version, actor, and timestamp.

#### Success Criteria

> **CS9-SC-001** — By the end of 45 days after CS9 go-live, at least 15% of identified cross-product terminology reuse cases are implemented through alias relationships.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 10 — Manage Reviewer Configuration (Priority: P2)

> **Persona:** Review Administrator, Product Content Owner
>
> As a Review Administrator, I need to manage Legal, Compliance, and Translation reviewer pools and eligibility within my authorized domains, and as a Product Content Owner, I need to configure product-scoped peer reviewers, so that review requests are routed to authorized people without relying on a generic administrator role.
>
> **Independent Test (DRAFT):** *A Review Administrator can define Legal/Compliance/Translation reviewer pools and locale eligibility, a Content Owner can configure product-scoped peer reviewers, and the system flags a product with no eligible reviewer — with no review yet requested.*

#### Acceptance Scenarios

> **CS10-AS-001** — Given I am setting up review administrators in Holocron, when I add a review administrator, then I can give them one or more review administration privileges: Legal, Compliance, or Translation.
>
> **CS10-AS-002** — Given I am defining a reviewer pool for my authorized area (Legal, Compliance, or Translation), when I add reviewers to that pool, then those reviewers become eligible for that type of review assignment.
>
> **CS10-AS-003** — Given I am configuring reviewers for a product, when I select one or more specific reviewers from the pool for Legal, Compliance, or Translation, then those reviewers become eligible for assignment within that product scope.
>
> **CS10-AS-004** — Given I am configuring reviewers for a product, when I select “any” rather than selecting specific reviewers from the pool for Legal, Compliance, or Translation, then any configured reviewer will be eligible for assignment to a string within the product. This is the default behavior.
>
> **CS10-AS-005** — Given I am defining reviewers for a review pool in translation or legal, when I add a reviewer to the pool, then I may also select one or more languages/locales this person is eligible to review for.
>
> **CS10-AS-006** — Given I am an authorized Translation Review Administrator, when I configure a product’s Japanese translation review by selecting a default Japanese language contact and assigning reviewers who are eligible for both that product and the Japanese locale, then the system determines eligibility using the review type, product scope, and locale; saves the language contact and eligible reviewers; and records each configuration change, the actor, and the timestamp in the audit trail.
>
> **CS10-AS-007** — Given a product requires a review for a specific review type and/or locale, when all configured reviewers are inactive or no eligible reviewer matches the product and/or locale, then the system flags the affected reviewer configuration for administrator review.
>
> **CS10-AS-008** — Given I am a Content Owner configuring peer review for my product, when I select one or more eligible associates as peer reviewers, then those associates become eligible to receive peer review requests for English source strings within that product.

#### Functional Requirements

> **CS10-FR-001** — Default Reviewer Eligibility: The system MUST support an “any eligible reviewer” configuration as the default for a review type when no product-specific reviewer restriction is set.
>
> **CS10-FR-002** — Language Contact Assignment: The system SHOULD support assigning a default language contact for a locale, who can receive review requests or coordinate reassignment for that language.
>
> **CS10-FR-003** — Locale-Based Translation Reviewer Eligibility: The system MUST allow translation reviewers to be configured as eligible for one or more languages/locales.
>
> **CS10-FR-004** — Product and Locale Reviewer Matching: For translation reviews, the system MUST determine eligible reviewers using review type, product/application scope, and language/locale.
>
> **CS10-FR-005** — Reviewer Configuration Audit Trail: The system MUST record reviewer configuration changes, including reviewer added, reviewer removed, scope changed, locale eligibility changed, actor, and timestamp.
>
> **CS10-FR-006** — Reviewer Eligibility: The system MUST determine eligible reviewers based on review type, product scope, and configured reviewer pool.
>
> **CS10-FR-007** — Reviewer Pool Definition: The system MUST allow authorized review administrators to create and maintain reviewer pools by review type, so an administrator may be authorized to manage Legal reviewers, Compliance reviewers, Translation reviewers, or a combination of these.
>
> **CS10-FR-008** — Specific Reviewer Restriction: The system MUST allow a product/application to restrict a review type to one or more named reviewers from the applicable reviewer pool.
>
> **CS10-FR-009** Product-Scoped Reviewer Configuration: The system MUST allow authorized review administrators to configure reviewer eligibility at global and, by when desired, the product/application scope.
>
> **CS10-FR-010** — Product-Scoped Peer Reviewer Configuration: The system MUST allow a Content Owner to configure one or more eligible peer reviewers for English source strings within their product scope.
>
> **CS10-FR-011** — Inactive Reviewer Detection: The system MUST detect when a configured reviewer’s user account is inactive or deactivated and flag affected reviewer configurations for administrator review.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 11 — Request and Manage Reviews (Priority: P1)

> **Persona:** Content Owner, Review Administrator
>
> As a Content Owner or Review Administrator, I need to request, assign, and manage reviews through a common workflow so that review requests are routed to authorized reviewers and their assignment, notifications, status, and history are managed consistently across review types.
>
> **Independent Test (DRAFT):** *A Content Owner can submit a designated string for review, have it auto-assigned when one reviewer is eligible or assign it to a specific reviewer or pool when several are, reassign a pending review, and see status move to Pending Review with every action audited.*

#### Acceptance Scenarios

> **CS11-AS-001** — Given a string or locale-specific translation has a review designation, when I submit that version for review, then the system creates a review request, determines the eligible reviewers based on the review type, product scope, and locale when applicable, changes the Review Status to Pending Review, records the action in the audit trail, and either automatically assigns the review when exactly one eligible reviewer exists or allows me to assign the review to a specific eligible reviewer or the eligible reviewer pool when multiple eligible reviewers exist.
>
> **CS11-AS-002** — Given multiple eligible reviewers exist for a review request, when I assign the review to the eligible reviewer pool, then the system stores the reviewer pool as the assignee, notifies the eligible reviewers, and sets the review status to Pending Review.
>
> **CS11-AS-003** — Given a pending review has been assigned to an eligible reviewer, when a Content Owner, Review Administrator, assigned reviewer, or eligible reviewer reassigns it to another active reviewer who is authorized for the same review type, product scope, and locale when applicable, then the new reviewer receives the assignment and a notification of the reassignment, the previous assignment is retained in history, and the reassignment is recorded in the audit trail with the initiating user and timestamp.
>
> **CS11-AS-004** — Given a product requires a review for a specific review type and/or locale, when no active reviewer is eligible for assignment based on the review type, product scope, and locale, then the system notifies the product content owner that no eligible reviewers are configured for that review.
>
> **CS11-AS-005** — Given a review is assigned to an eligible reviewer pool, when an eligible reviewer approves or rejects the review, then the review is automatically assigned to that reviewer, the review decision is recorded, and the assignment and action are captured in the audit trail.
>
> **CS11-AS-006** — Given a review is assigned to an eligible reviewer pool, when multiple eligible reviewers attempt to approve or reject the review at the same time, then the first successful review action assigns the review to that reviewer, and the remaining reviewers are informed that the review has already been completed or assigned.
>
> **CS11-AS-007** — Given I need to send multiple strings for review, when I select them and initiate batch review, then all selected strings are submitted in a single action and reviewers receive a consolidated notification for the strings.

#### Functional Requirements

> **CS11-FR-001** — Review Request Lifecycle: The system MUST support creating review requests with review type, assigned reviewer or reviewer pool, reviewed source-string or translation version, Review Status, Review Outcome, comments, notifications, and audit trail entries. Review Status MUST be Pending Review while the review is open and Completed after a decision is submitted. Review Outcome MUST be N/A while the review is open and Approved or Rejected after completion.
>
> **CS11-FR-002** — Reviewer Assignment: If exactly one eligible reviewer exists for the review type, product scope, and locale when applicable, the system MUST automatically assign that reviewer.
>
> **CS11-FR-003** — If multiple eligible reviewers exist, the system MUST allow the requester to assign the review either to a specific eligible reviewer or to the eligible reviewer pool.
>
> **CS11-FR-004** — Reviewer Pool Assignment: The system MUST support assigning a review request to an eligible reviewer pool. When assigned to a reviewer pool, the pool becomes the assignee and the system MUST notify all eligible reviewers within that pool.
>
> **CS11-FR-005** — No Eligible Reviewer Handling: If no eligible, active reviewer exists for a review configured for a product, the system MUST notify the user and identify the missing reviewer type, product/application, and locale when applicable.
>
> **CS11-FR-006** — Review Claiming: When a review request is assigned to a reviewer pool, the first eligible reviewer to approve or reject the review MUST automatically become the assigned reviewer for that review request.
>
> **CS11-FR-007** — When a review request is assigned to a reviewer pool and multiple eligible reviewers attempt to approve or reject the same review request simultaneously, the first successful review action MUST be accepted and the review assigned to that reviewer. Subsequent reviewers MUST be informed that the review has already been completed or assigned
>
> **CS11-FR-008** — The system MUST allow a Content Owner, Review Administrator, assigned reviewer, or eligible reviewer of an assigned reviewer pool to reassign a pending review to another authorized reviewer. The system MUST notify the newly assigned reviewer and record the reassignment in the audit trail.
>
> **CS11-FR-009** — Review Designation Types: The system MUST support Legal, Compliance, and Peer Review designations on English source strings and Translation Review designations on locale-specific translations.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 12 — Complete Review (Basic) (Priority: P1)

> **Persona:** Reviewer
>
> As a Reviewer, I need to complete assigned reviews through a common workflow so that I can approve or reject content with the required comments and maintain a consistent, auditable review decision across review types.
>
> **Independent Test (DRAFT):** *An assigned reviewer can open their queue, approve a request (comments optional) or reject it (comments required), see Review Status become Completed with the outcome recorded, and be blocked from acting on requests outside their eligibility.*

#### Acceptance Scenarios

> **CS12-AS-001** — Given I am an authorized reviewer assigned to a review request, when I approve the review, then the Review Status becomes Completed, the Review Outcome becomes Approved, my decision is recorded in the audit trail, and I may provide comments but comments are not required.
>
> **CS12-AS-002** — Given I am an authorized reviewer assigned to a review request, when I reject the review, then I must provide rejection comments before the decision can be submitted, the Review Status becomes Completed, the Review Outcome becomes Rejected, and the rejection comments and decision are recorded in the audit trail.
>
> **CS12-AS-003** — Given one or more review requests are assigned to me, when I view my review work queue, then I can see the assigned requests and open each request to approve or reject it according to the review decision rules.
>
> **CS12-AS-004** — Given a review request is tied to a specific English source-string version or locale-specific translation version, when the reviewed content changes, then the existing review request is invalidated and a new review request is created for the updated version using the same review type and standard assignment workflow; reviews for unchanged content or other locales remain valid.
>
> **CS12-AS-005** — Given a set of strings for a product that is not restricted to specific reviewers and I am authorized to review strings for any product, when I view the list of review requests for my review type, then I am eligible and allowed to approve, reject, or comment on a review request for those strings.
>
> **CS12-AS-006** — Given I am a reviewer and a product is restricted to specific reviewers, when I am not included in the product-level list of eligible reviewers, then I am not eligible or allowed to approve, reject, or comment on review requests for that product.

#### Functional Requirements

> **CS12-FR-001** — An approval decision MUST be recorded in the audit trail with: reviewer identity, decision (approved/rejected), comment if provided, and timestamp.
>
> **CS12-FR-002** — Review Decision Submission: The system MUST allow an authorized reviewer to approve or reject an assigned review request through the management application.
>
> **CS12-FR-003** — Review Decision Comments: The system MUST allow optional comments when a reviewer approves a review request and MUST require rejection comments before a reviewer can submit a rejection.
>
> **CS12-FR-004** — Review Version Invalidation: A review request MUST be tied to the specific English source-string version or locale-specific translation version reviewed. When that reviewed content changes, the system MUST invalidate the existing request and create a new request for the updated version using the same review type and standard assignment workflow. Reviews tied to unchanged content or other locales MUST remain valid.
>
> **CS12-FR-005** — Review Scope Authorization: The system MUST allow a reviewer to approve, reject, or comment on a review request only when the reviewer is eligible for that review based on the review type, product scope, configured reviewer restrictions, and locale when applicable. The system MUST prevent reviewers who do not meet those eligibility criteria from submitting review decisions or comments.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 13 — Peer Review Workflow (Priority: P3)

> **Persona:** Content Owner, Peer Reviewer
>
> As a Content Owner, I need to request peer review from another associate so that content can receive quality feedback without blocking publication.
>
> **Independent Test (DRAFT):** *A Content Owner can request peer review from multiple eligible associates, each receiving an independent request, and can still publish the string after confirming a warning while pending or rejected peer reviews remain visible in history.*

#### Acceptance Scenarios

> **CS13-AS-001** — Given peer reviewers are configured for my product, when I request peer review for an English source-string version and select one or more eligible peer reviewers, then the system creates a separate Pending Review request for each selected reviewer and notifies each reviewer of their assignment.
>
> **CS13-AS-002** — Given multiple peer reviewers have separate review requests for the same English source-string version, when one reviewer completes their review, then that decision is recorded independently and does not complete, assign, or change any other reviewer’s request.
>
> **CS13-AS-003** — Given one or more requested peer reviews are Pending or Rejected, when I attempt to publish the English source-string version, then the system displays a warning summarizing the peer review outcomes and allows me to publish after explicit confirmation; the peer review requests and decisions remain visible in review history and the audit trail.

#### Functional Requirements

> **CS13-FR-001** — Peer Review Request Assignment: The system MUST allow a Content Owner to request peer review for an English source-string version by selecting one or more peer reviewers who are eligible for the product.
>
> **CS13-FR-002** — Independent Peer Review Requests: The system MUST create a separate Pending Review request for each selected peer reviewer and notify each reviewer of their assignment. Selecting multiple peer reviewers MUST NOT create a reviewer-pool assignment and MUST NOT use pool claiming.
>
> **CS13-FR-003** — Independent Peer Review Decisions: Each peer review request MUST be completed and recorded independently. A decision on one peer review request MUST NOT complete, assign, or change another peer reviewer’s request for the same English source-string version.
>
> **CS13-FR-004** — Non-Blocking Peer Review Publication: Pending or Rejected peer reviews MUST NOT prevent publication. When one or more peer reviews are Pending or Rejected, the system MUST display a warning summarizing the peer review outcomes and require explicit confirmation before publication proceeds.
>
> **CS13-FR-005** — Peer Review History: Peer review requests and decisions MUST remain visible in review history and the audit trail after the English source-string version is published.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 14 — Legal and Compliance Approval Workflow (Priority: P2)

> **Persona:** Content Owner, Legal/Compliance Reviewers
>
> As a Content Owner, I need to designate strings for legal or compliance review and route them to the correct reviewers so that reviewed strings have an auditable approval record before they are Published.
>
> **Independent Test (DRAFT):** *With a Legal or Compliance designation pending or rejected, a Content Owner attempting to publish is required to cancel or explicitly override with a reason, and the override, reason, actor, and timestamp are recorded in the audit trail.*

#### Acceptance Scenarios

> **CS14-AS-001** — Given a string version has a Legal or Compliance review designation and the applicable review is Pending Review or has a Rejected outcome, when the Content Owner attempts to publish it, then the system displays the unresolved review details and requires the Content Owner to either cancel publication or explicitly override the review requirement and provide an override reason; when the Content Owner confirms the override, publication proceeds and the decision, reason, applicable review context, actor, and timestamp are recorded in the audit trail.

#### Functional Requirements

> **CS14-FR-001** — Legal and Compliance Review Override: Legal and Compliance review designations MUST be optional by default and apply only when explicitly added to a string. When the applicable review for the version being published is Pending Review or has a Rejected outcome, the system MUST require the Content Owner to cancel publication or explicitly override the review requirement and provide an override reason. The system MUST record the override decision, reason, applicable review request and outcome, actor, and timestamp in the audit trail.
>
> **CS14-FR-002** — Legal and Compliance reviewer configuration MUST be restricted to authorized administrators.

#### Success Criteria

> **CS14-SC-001** — At least 80% of designated legal/compliance reviews are completed within 5 business days.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 15 — Manage Translation Variants and Lifecycle (Priority: P1)

> **Persona:** Content Owner
>
> As a Content Owner, I need locale-specific translation variants to be stored, versioned, and tracked independently against the English source version so that I can understand translation freshness, lifecycle state, and language coverage across my product.
>
> **Why this priority:** The translation-variant data model and lifecycle provide the foundation used by export, import, translation review, publication, delivery, history, and rollback workflows.
>
> **Independent Test (DRAFT):** *For a product with configured target languages, a Content Owner can see one locale record per language with its Translation State, save an independently versioned translation linked to its source version, and see translations flip to Outdated when the English source is republished.*

#### Acceptance Scenarios

> **CS15-AS-001** — Given a product has one or more configured target languages and an English source string exists, when I view the string’s translation variants, then the system represents one locale-specific translation record for each configured target language and displays its Translation State.
>
> **CS15-AS-002** — Given a locale-specific translation is created or updated, when the translation version is saved, then it is versioned independently from the English source and other locale translations, linked to the applicable Source Version Reference, and preserved in translation history.
>
> **CS15-AS-003** — Given a Published translation is linked to an earlier English source version, when a newer English source version is published, then the system transitions that locale’s Translation State to Outdated without changing other locale translations.
>
> **CS15-AS-004** — Given a product has configured target languages, when I view translation coverage, then the system shows the number and percentage of strings in each Translation State by locale and identifies translations whose Source Version Reference does not match the latest English source version.

#### Functional Requirements

> **CS15-FR-001** — Translation Variant Model: The system MUST represent one locale-specific translation record per English source string and product-configured target language. US English (en-US) remains the authoritative source language and is not a translation variant.
>
> **CS15-FR-002** — Independent Translation Versioning: The system MUST store and version translations independently per locale per string, preserve all prior translation versions, and prevent a change to one locale from changing the English source or another locale.
>
> **CS15-FR-003** — Source Version Reference: Each translation version MUST record the exact English Source Version Reference from which it was produced so the system can determine translation freshness and support history and rollback.
>
> **CS15-FR-004** — Translation Lifecycle State Management: The system MUST track a Translation State per locale per string and support Not Translated, Awaiting Translation, Pending Review, Approved, Published, and Outdated in accordance with Appendix C — Translation and Review States and Appendix D — Translation State Matrix and Scenarios.
>
> **CS15-FR-005** — Translation Freshness: When a newer English source version is published, the system MUST transition each previously Published translation whose Source Version Reference no longer matches the latest source version to Outdated. Other locale translations MUST remain independently tracked.
>
> **CS15-FR-006** — Translation Coverage Reporting: The system MUST provide translation coverage reporting by product and configured target locale, including counts and percentages for Not Translated, Awaiting Translation, Pending Review, Approved, Published, and Outdated, and MUST identify translations whose Source Version Reference does not match the latest English source version.

#### Success Criteria

> **CS15-SC-001** — Within 90 days of CS15 going live, at least 80% of active languages achieve and maintain at least 90% current translation coverage for required strings (where current means the translation source-version reference matches the latest source-string version).
>
> **CS15-SC-002** — Within 90 days of CS15 going live, at least 80% of translation records entering Pending Review are promoted to Published within 5 business days.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 16 — Export Strings for Translation (Priority: P2)

> **Persona:** Content Owner, Translation Services
>
> As a Content Owner, I need to export strings in a structured exchange format so that I can provide them to translation services to produce translations.
>
> **Independent Test (DRAFT):** *A Content Owner can select a subset of strings, choose and order the export fields (including Screenshot Link/Reference), and generate a file containing only those fields in that order with placeholder syntax preserved and the target locales moved to Awaiting Translation.*

#### Acceptance Scenarios

> **CS16-AS-001** — Given I have selected a set of strings for translation, when I configure the export, then the system allows me to select the available fields to include and arrange them in the desired order; when I initiate export, the generated file contains only the selected fields in that order. Screenshot Link and Screenshot Reference are available for selection and are included when selected even when a string has no value for the optional field.
>
> **CS16-AS-002** — Given I export strings that contain placeholders, Then the exported file preserves placeholder syntax so translators can see and respect placeholder position within each string.
>
> **CS16-AS-003** — Given I select a subset of strings from my table view, When I click export, Then only the selected strings are included in the export file.
>
> **CS16-AS-004** — Given the selected strings include strings that are aliased to other canonical strings, when I export that string set, I have a choice to include or exclude aliased-strings.

#### Functional Requirements

> **CS16-FR-001** — The system MUST support bulk export of strings in one or more governed structured file formats suitable and best practice for translation exchange.
>
> **CS16-FR-002** — String Context and Metadata Exchange Contract: Context Notes, Screenshot Link, Screenshot Reference, Do Not Translate, and placeholder metadata MUST be available for selection in translation exports and consistently represented in export and import exchange formats. Optional fields selected for export MUST be included in the exported schema even when a string has no value for that field.
>
> **CS16-FR-003** — Translation Export Field Contract: The system MUST make the following fields available for export selection: key, English source content, Source Version Reference, Context Notes, Screenshot Link, Screenshot Reference, placeholder metadata, Do Not Translate designation, applicable translation rejection comments, target locale, current translated content when available, Translation Version, and Translation State. The generated file MUST include only the fields selected by the user and MUST preserve the user-defined field order. A selected optional field MUST be represented for every exported string even when its value is blank.
>
> **CS16-FR-004** — The system MUST support exporting a user-selected subset of strings, not only full-product exports.
>
> **CS16-FR-005** — When a string is exported, the system MUST allow the user to specify that the export is intended for translation; when selected, the Translation State for each target locale MUST transition to Awaiting Translation.
>
> **CS16-FR-006** — Product-Language Export Scope: The system MUST support export of all or selected strings in a product for all target languages configured for that product or for one or more selected configured target languages. The system MUST NOT allow a translation request for a locale that is not configured for the product.
>
> **CS16-FR-007** The system must support including or excluding in the exported file alias strings that inherit data from another string.
>
> **CS16-FR-008** The system must support displaying recently exported files (up to 90 days) so that they can be redownloaded without being regenerated.

#### Success Criteria

> **CS16-SC-001** — Translation exchange batches pass contract validation on first attempt for the intended consumer profile (including required fields and approved format rules for both outbound export and inbound import compatibility checks) at \>=80% by Day 30 and \>=90% by Day 90 after CS16 go-live.
>
> **CS16-SC-002** — Contract-mismatch rework rate is \<=20% by Day 30 and \<=10% by Day 90 after CS16 go-live (where rework is any re-export/re-submission required due to missing required fields, schema mismatch, or unsupported format).
>
> **CS16-SC-003** — Translation workflow consumers report that (a) exported packages include the information they need in a consumable format and (b) returned translation files are accepted in the format they submit, measured through recurring consumer survey, at \>=75% by Day 30 and \>=85% by Day 90 after CS16 go-live.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 17 — Import Translated Strings (Priority: P2)

> **Persona:** Content Owner, Translation Services
>
> As a Content Owner, I need to import a translated file provided by a translation service so that translations are loaded into the system and linked to the correct strings without manual re-entry.
>
> **Why this priority:** Import is the return path from translation services.
>
> **Independent Test (DRAFT):** *A Content Owner can upload a translated file, see a row-by-row validation preview identifying creates vs. new versions, errors, and warnings, apply the valid rows so each locale moves to Pending Review linked to its source version, and resolve any Do-Not-Translate conflict explicitly.*

#### Acceptance Scenarios

> **CS17-AS-001** — Given I have received a translated file from a translation service, When I upload the file through the import interface, Then the system validates the file row by row before applying any changes, and displays a preview of what will be created or updated, including any validation errors.
>
> **CS17-AS-002** — Given an import file includes Screenshot Link or Screenshot Reference values, when the file is validated and applied, then the system validates those values, associates them with the corresponding source string, includes the resulting changes in the import preview, and records any applied changes in the audit trail.
>
> **CS17-AS-003** — Given the import file contains translations that already exist in the system, when validation completes, then the preview clearly identifies which translations will be created and which will result in new versions of existing translations.
>
> **CS17-AS-004** — Given the import file contains invalid rows or warnings, when validation completes, then the preview identifies each affected row and explains the issue; invalid rows are excluded from apply, and I may apply the valid rows, cancel the import, or explicitly override warnings and proceed with the warned rows.
>
> **CS17-AS-005** — Given a valid import is applied, then each string's translation content is updated for the relevant locale, the Translation State transitions to Pending Review, each change is captured in the audit trail including the translation source, and the translation version is linked to the applicable Source Version Reference.
>
> **CS17-AS-006** Given a translation already exists for a language, when I import updated translated content for that language, then the system creates a new translation version, preserves prior versions in history, and records the source-string version associated with the imported translation.
>
> **CS17-AS-007** Given a translation import was produced from an older English source version, when I import the file after the English source has changed, then the system warns me that the import was based on an outdated source version and identifies the affected strings.
>
> **CS17-AS-008** — Given an imported translation row targets a source string marked Do Not Translate, when validation identifies the conflict, then the system warns the Content Owner and requires an explicit choice to either keep the Do Not Translate designation and exclude the row from import, or override the designation and apply the translation; the selected action, actor, and timestamp are recorded in the audit trail.

#### Functional Requirements

> **CS17-FR-001** — The system MUST support bulk import of translated strings using the same exchange format(s) as export (see CS16-FR-001).
>
> **CS17-FR-002** — The system MUST validate the import file before applying any changes, performing row-level validation and returning actionable error descriptions for each failing row.
>
> **CS17-FR-003** — Translation Import Field Contract: Each imported translation row MUST include the string key, target locale, translated text, and Source Version Reference. The import contract MUST support Context Notes, Screenshot Link, Screenshot Reference, Do Not Translate designations, placeholder metadata, and applicable translation rejection comments. The system MUST validate required values, field formats, and protected Do Not Translate content before applying the row.
>
> **CS17-FR-004** — Product-Language Import Validation: The system MUST validate that each imported target locale is configured for the applicable product/application. A row for an unconfigured locale MUST be treated as invalid and excluded from apply.
>
> **CS17-FR-005** — Imported Screenshot Context: The import exchange contract MUST support Screenshot Link and Screenshot Reference values. The system MUST validate each value according to its field type, display proposed additions or changes in the import preview, associate accepted values with the corresponding source string, and record applied changes in the audit trail.
>
> **CS17-FR-006** — Import Error and Warning Handling: The system MUST exclude invalid rows from apply, return actionable row-level error details, and allow the user to apply valid rows or cancel the import. Rows with warnings MAY be applied only after the user explicitly acknowledges and overrides the warnings; the override and affected rows MUST be recorded in the audit trail.
>
> **CS17-FR-007** — On successful import of a translation, the system MUST transition the affected locale's Translation State to Pending Review, record the import in the audit trail with the translation source, and link the translation version to the applicable Source Version Reference.
>
> **CS17-FR-008** — The system MUST validate placeholder integrity on import: if an imported translation is missing required placeholders or uses placeholder syntax inconsistent with stored metadata, or does not support special handling or double interpolation, the row MUST be flagged as invalid.
>
> **CS17-FR-009** — During validation, the system MUST determine whether each imported translation row will create a new translation record or create a new version of an existing translation and MUST present that classification in the import preview.
>
> **CS17-FR-010** When an import updates an existing translation, the system MUST create a new translation version, preserve all prior versions, and maintain the source-string version reference associated with each translation version.
>
> **CS17-FR-011** Before applying an import, the system MUST provide a preview identifying:

- rows to be created

- rows that will create new translation versions

- validation errors

- warnings

- affected languages

> **CS17-FR-012** — Do Not Translate Import Decision: During import validation, the system MUST identify any translation row targeting a source string marked Do Not Translate and present a whole-row warning to the Content Owner. The system MUST require the Content Owner to choose either to retain the Do Not Translate designation and exclude the row, or to override the designation and apply the translation. The system MUST record the choice, affected string and locale, actor, and timestamp in the audit trail.
>
> **CS17-FR-013** For each imported translation version, the system MUST record the translation source, import batch, actor, timestamp, and resulting translation version in the audit trail.

#### Success Criteria

> **CS17-SC-001** — First-pass import acceptance rate (batches accepted without contract/schema correction re-upload) is \>=80% by Day 30 and \>=90% by Day 90 after CS17 go-live.

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 18 — Translation Review Workflow (Priority: P2)

> **Persona:** Content Owner, Translation Reviewer
>
> As a Content Owner, I need translated content reviewed before publication so that translations meet quality, locale, and business expectations.
>
> **Independent Test (DRAFT):** *A translation reviewer can view a Pending-Review translation with its English source and context, approve it to Approved (eligible for publication) or reject it with required comments, and the Content Owner can resolve an unresolved-review publish by choosing the previous translation, the English fallback, or the current content.*

#### Acceptance Scenarios

> **CS18-AS-001** — Given translated content enters Pending Review status, when a reviewer is assigned, then the reviewer can view the translated content, English source content, locale, Source Version Reference, Context Notes, Screenshot Link, Screenshot Reference, and placeholder metadata.
>
> **CS18-AS-002** — Given I am an authorized reviewer assigned to a translation review, when I approve the review, then the review outcome is recorded as Approved, the translation moves from Pending Review to Approved, and the translation becomes eligible for publication.
>
> **CS18-AS-003** — Given a locale-specific translation is in Pending Review and review is not required, when the Content Owner approves the translation directly, then the system records the Content Owner as the decision maker, sets the Translation State to Approved, makes the translation eligible for publication, and records the action and timestamp in the audit trail.
>
> **CS18-AS-004** — Given I am an authorized reviewer assigned to a translation review, when I reject the review, then I must provide rejection comments before submitting the decision, the review outcome is recorded as Rejected, the translation remains in Pending Review, and the Content Owner is notified.
>
> **CS18-AS-005** — Given a translation review was rejected, when the Content Owner updates the translation based on the rejection comments, then the system creates a new draft translation version associated with the applicable English source version, keeps the translation in Pending Review, and creates a new review request according to the standard review workflow.
>
> **CS18-AS-006** — Given a locale-specific translation is in Pending Review and its latest review is pending or Rejected, when the Content Owner attempts to publish the string, then the system requires the Content Owner to explicitly choose to cancel the publication, or, for that locale whether use the previously published translation, use the English source fallback, or publish the current translation; no option is selected by default; and when publication is completed, the system uses the selected content and records the selection, applicable review context, actor, and timestamp in the audit trail.

#### Functional Requirements

> **CS18-FR-001** — Translation Review Context: The system MUST present the locale-specific translation version under review together with its English source text, locale, Context Notes, Screenshot Link, Screenshot Reference, placeholder metadata, and associated Source Version Reference.
>
> **CS18-FR-002** — Translation Review Approval: When an authorized reviewer approves a translation review, the system MUST record the review outcome as Approved, transition the translation from Pending Review to Approved, and make that translation version eligible for publication without an unresolved-review warning.
>
> **CS18-FR-003** — Content Owner Direct Translation Approval: When review is not required for a locale-specific translation, the system MUST allow the authorized Content Owner to approve the translation directly. The system MUST record the Content Owner as the decision maker, transition the Translation State from Pending Review to Approved, make the translation eligible for publication, and record the action and timestamp in the audit trail.
>
> **CS18-FR-004** — Translation Review Rejection: When an authorized reviewer rejects a translation review, the system MUST require rejection comments before the decision can be submitted, record the review outcome as Rejected, retain the translation in Pending Review, and notify the Content Owner.
>
> **CS18-FR-005** — Translation Review Rejection Comments: It MUST be clear to the user that the rejection comments should include the reason for rejection and an optional suggested correction.
>
> **CS18-FR-006** — Translation Revision After Rejected Review: When the Content Owner updates a translation following a rejected review, the system MUST create a new draft translation version associated with the applicable English source-string version, retain the translation state as Pending Review, preserve the rejected review in history, and create a new review request using the Generic Review Workflow.
>
> **CS18-FR-007** — Unresolved Translation Review Publication Choice: When the Content Owner attempts to publish a string for a locale whose translation is in Pending Review and whose latest review is pending or Rejected, the system MUST require the Content Owner to explicitly choose whether to cancel the string publication, or, for that locale, to use the previously published translation, the English source fallback, or the current translation.
>
> **CS18-FR-008** — Translation Publication Choice Audit Trail: When publication proceeds for a locale with a pending or Rejected translation review, the system MUST use the Content Owner’s selected content and record the selected option, applicable translation version and review context, actor, and timestamp in the audit trail.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

### Capability Story 19 — Roll Back Translated Strings (Priority: P3)

> **Persona:** Content Owner
>
> As a Content Owner, I need to restore translations associated with a prior English source-string version so that I can recover valid locale content without losing independent translation history.
>
> **Why this priority:** Translation rollback depends on source rollback, independent translation version history, and Source Version References.
>
> **Independent Test (DRAFT):** *When a source string is rolled back, the most recent translation linked to that source version is restored per language into new Pending-Review versions, and the Content Owner is offered the translations that would not be restored to choose which, if any, to retain.*

#### Acceptance Scenarios

> **CS19-AS-001** — Given translations are linked to the selected source-string version, when the source rollback is completed, then the most recent translation version linked to that source version is restored for each language.
>
> **CS19-AS-002** — Given the target rollback has fewer translations than the current string, when I initiate the translated-string rollback, then I am presented with the translations that would not be restored and may select which, if any, to retain.

#### Functional Requirements

> **CS19-FR-001** — Translation Restoration: When a source version is restored, the system MUST create a new translation version from the most recent translation version linked to that source version for each language, preserve all prior translation history, and link each restored translation version to the newly created Draft source version.
>
> **CS19-FR-002** — Restored Translation State: Each restored translation version MUST enter Pending Review unless no translation review is required, in which case the Content Owner may approve it directly through the translation review workflow.
>
> **CS19-FR-003** — Translation Retention Choice: Before translated-string rollback, the system MUST identify translations that exist on the current source version but not the selected source version and allow the Content Owner to choose which, if any, to retain. A retained translation MUST be copied into a new translation version linked to the newly created Draft source version and MUST enter Pending Review.

#### Success Criteria

> *None.*

#### Non-Functional Requirements

> *None.*

#### Edge Cases

> *None.*

## Cross-Cutting Concerns

### Key Entities

| **Entity** | **Definition and Key Relationships** |
|----|----|
| Product/Application | A configurable workspace identified by a unique application identifier that forms the namespace root. It has one or more Content Owners, configured target languages, lifecycle status, and audit history. |
| Source String | The US English content record within a product/application, identified by an immutable namespaced key. It inherits product ownership and includes lifecycle status, tags, context fields, placeholder metadata, a whole-string Do Not Translate flag, and source-level review designations. |
| Source String Version | An immutable version of a Source String containing the English content and associated versioned metadata. Reviews, translations, publication, retirement restoration, and rollback reference a specific source version. |
| Translation Variant | The locale-specific translation record associated with one Source String and one product-configured target language. It maintains its current Translation State and current Translation Version. |
| Translation Version | An immutable version of translated content for one locale. It records the Translation Version, Source Version Reference, translation source or import batch, actor, timestamp, and independent history. |
| Review Designation | A designation indicating that a source-string or locale-specific translation version may be submitted for a particular review type. Legal, Compliance, and Peer Review apply to English source strings; Translation Review applies to locale-specific translations. |
| Review Request | An independent request tied to a specific Source String Version or Translation Version. It records review type, Review Status, Review Outcome, reviewer or reviewer pool, comments, notifications, audit history, and any invalidated or replacement request relationship. |
| Reviewer Pool | A managed set of reviewers eligible for a review type, with product and locale restrictions where applicable. A review request may be assigned to an individual reviewer or an eligible pool. |
| Publication Selection | The content explicitly selected for delivery for a source string and locale. It may reference an approved or current translation, a previously published translation, or the English source fallback and records the actor, timestamp, and applicable review context. |
| Translation Exchange Batch | An export or import transaction containing selected strings, configured target locales, selected fields and order, file format, validation results, warnings or overrides, actor, timestamps, and retained file history. |
| Alias Relationship | A directional relationship from an alias string to a published canonical string and adopted canonical version. It records status, owner notifications, adoption decisions, and audit history. |

### Cross-Cutting Non-Functional Requirements

> **CC-NFR-001** — All data in transit MUST be encrypted using current enterprise-approved transport security standards.
>
> **CC-NFR-002** — Data at rest encryption MUST comply with enterprise data classification policy for the Internal classification level.
>
> **CC-NFR-003** — All system operations MUST emit structured observability signals (logs, metrics, traces) compatible with the enterprise observability platform.
>
> **CC-NFR-004** — Health and readiness endpoints MUST be provided for operational monitoring.
>
> **CC-NFR-005** — The system MUST support horizontal scalability to handle growth in consuming applications and string volume without architectural changes.
>
> **CC-NFR-006** — The system MUST support a target scale of at least 500,000 strings.
>
> **CC-NFR-007** — Secrets and credentials MUST be managed through the enterprise secrets management system and MUST NOT be hardcoded in any configuration or source artifact.
>
> **CC-NFR-008** — Container images MUST run as non-root users and MUST be sourced from approved internal registries.
>
> **CC-NFR-009** — The system MUST define and meet recovery point objective (RPO) and recovery time objective (RTO) targets aligned with enterprise standards for an Internal-classified service. As the single source of truth for UI text across 20+ consuming applications, Holocron’s disaster recovery posture must be explicitly designed, documented, and tested. Specific RPO/RTO targets to be confirmed with infrastructure and legal/compliance stakeholders before delivery.
>
> **CC-NFR-010** — The string delivery mechanism MUST support per-consumer rate limiting and quota controls to prevent any single consuming application from degrading service for others — including accidental high-volume polling, misconfigured retry loops, or runaway cache misses.

### Cross-Cutting Edge Cases

> **CC-EC-001** Unicode and character encoding (For Technical Review): All string content MUST support full Unicode. Special characters, multi-byte sequences, and bidirectional text MUST be stored and delivered without corruption.
>
> **CC-EC-002** Alias loops and limits (For Technical Review): The system MUST stop aliases from pointing in a circle and MUST keep the alias limit to one link. A string can point to a canonical string, but it cannot point to another alias. If the chosen canonical string already points to a different string, the system must ask the user to link to that final canonical string instead.
>
> **CC-EC-003** Concurrent multi-user edits (For Technical Review): Optimistic locking MUST prevent silent overwrites when two users edit the same string simultaneously.

## Assumptions

> **ASMP-001** US English (en-US) is the authoritative source language for all strings. Translations are derived from US English and versioned independently.
>
> **ASMP-002** No external AI translation automation is in scope for this requirements version. Translation is performed by humans (internal or external). AI-assisted translation is a future capability to be specified separately.
>
> **ASMP-003** Translation service integration (provider selection, exchange file format confirmation) is a discovery item to be resolved with translation stakeholders before the import workflow (CS17) is designed for delivery.
>
> **ASMP-004** The enterprise identity management system supports the authentication model required for role-based access.
>
> **ASMP-005** No image or binary asset storage is within scope for this requirements version. Non-text references (e.g., image pointers, alt text strings) are string values like any other and are in scope.
>
> **ASMP-006** Adoption by consuming application teams — auditing existing hardcoded strings and migrating to Holocron — is a program-level effort outside the scope of these requirements but must be accounted for in the delivery plan. Both Nick Grant and Dan Rowe noted that adoption effort will equal or exceed build effort.

## Dependencies

| **ID** | **Dependency** | **Blocks** | **Owner** |
|----|----|----|----|
| DEP-001 | Enterprise identity management system | CS1, CS1-FR-001 | Enterprise infrastructure |
| DEP-002 | Translation service partner selection | CS17, CS16-FR-001 (format decision) — BLOCKING: export cannot be delivered without this decision | Anna Woods + stakeholders |
| DEP-003 | Architecture decision: namespaced key model and segment depth | CS3-FR-006 (cannot change after strings are entered) | Architecture team |
| DEP-004 | Architecture decision: string delivery mechanism design | CS7, CS7-FR-001–005 | Nick Grant + engineering |
| DEP-005 | RTL language scope decision | HLC-FR-017 \[unresolved — no matching requirement found in source\] | Architecture + product stakeholders |
| DEP-006 | AKS namespace and database provisioning | Delivery | Infrastructure |
| DEP-007 | MDM/RDM coordination | Alias governance model | Anna Woods + MDM/RDM team |
| DEP-008 | Legal/compliance: audit trail retention period | CS5-FR-006 | Legal/Compliance |

## Clarifications

*None recorded. (Source contained only the empty Clarifications template.)*

## Out of Scope / Future Considerations

| **Item** | **Notes** |
|----|----|
| AI-assisted translation automation | Future capability. Chance Kennedy described a "Translate" button with AI first-cut and human review as a desired future direction. Not in scope for this requirements version. |
| Figma / design system integration | Chance Kennedy flagged this as aspirational: mapping string keys to Figma design components for automatic key assignment. Future consideration requiring engagement with the GUIDE team (Chris Wells, Nick Grant, Tommy Ngo, James McQueen). |
| Screenshot preview per language | Nick Grant raised this as a future idea: previewing how UI layout shifts per language to help teams account for text expansion and RTL implications. |
| In-system access for external translation vendors | External vendors interact via export/import exchange only. No in-system vendor login is in scope. |
| A/B testing and regional string variants | Deferred to a future phase. |
| Component string ripple/pin behavior | Deferred to a future phase. |
| Review via emailed link (approver UX) | Planned future capability referenced in CS12-FR-002. Not in scope for initial delivery. |
| MDM/RDM operating model ownership | Post-POC ownership transition is a program-level decision; not a product requirement. |

## Appendices

### Appendix A — Supported Languages

Carlos Vega and Julia Holz each have an initial pass at languages to be supported. This list is not final but is meant to be a starting point. The “Julia Type” is for if the translation is for SPM or Training or meant for both:

| **Language** | **Julia Type** | **Carlos** | **Result** | **Special Handling / Key Considerations** |
|----|----|----|----|----|
| Arabic | SPM | No | Julia only | RTL (right-to-left). UI mirroring, alignment, navigation flow, icon direction, mixed LTR/RTL content. |
| Chinese Simplified | Both | Yes (Chinese) | Both | No spaces between words, different line wrapping, locale distinction from Traditional Chinese. |
| Chinese Traditional | Both | Yes (Chinese) | Both | No spaces between words, different line wrapping, locale distinction from Simplified Chinese. |
| Czech | SPM | Yes | Both | Complex pluralization, grammatical cases, variable word lengths. |
| Danish | SPM | Yes | Both | Primarily text expansion/contraction testing. |
| Dutch | Both | Yes | Both | Text expansion can be significant compared to English. |
| English | Both | Yes | Both | Baseline language. |
| Finnish | SPM | Yes | Both | Extremely long compound words can cause UI expansion issues. |
| French (Canadian) | SPM | Yes (French) | Both | Locale-specific terminology; text expansion. |
| French (France) | Both | Yes (French) | Both | Locale-specific terminology; text expansion. |
| German | Both | Yes | Both | Very long compound words can break layouts. |
| Greek | — | Yes | Carlos only | Uses Greek alphabet; verify fonts and character rendering. |
| Hungarian | — | Yes | Carlos only | Complex grammar, cases, and pluralization rules. |
| Indonesian | SPM | No | Julia only | Generally low technical risk. |
| Italian | SPM | Yes | Both | Moderate text expansion. |
| Japanese | Both | Yes | Both | Multiple writing systems (Kanji, Hiragana, Katakana); line wrapping and font rendering. |
| Cambodian (Khmer) | — | Yes | Carlos only | Complex script; font support and text rendering should be validated. |
| Korean | Both | Yes | Both | Hangul script; different typography and wrapping behavior. |
| Latvian | SPM | No | Julia only | Complex grammatical cases and inflections. |
| Lithuanian | SPM | Yes | Both | Complex grammatical cases and inflections. |
| Norwegian | SPM | Yes | Both | Low technical risk. |
| Polish | SPM | Yes | Both | Complex pluralization and grammatical cases. |
| Portuguese (Brazilian) | Both | Yes (Portuguese) | Both | Locale-specific terminology and formatting. |
| Portuguese (Portugal) | SPM | Yes (Portuguese) | Both | Locale-specific terminology and formatting. |
| Romanian | SPM | Yes | Both | Moderate pluralization complexity. |
| Slovenian | — | Yes | Carlos only | Complex plural rules and grammatical cases. |
| Spanish (LATAM) | Both | Yes (Spanish) | Both | Locale-specific terminology and formatting. |
| Spanish (Spain) | SPM | Yes (Spanish) | Both | Locale-specific terminology and formatting. |
| Swedish | SPM | Yes | Both | Low technical risk. |
| Thai | SPM | Yes | Both | Word wrapping can be difficult because spaces are not always used between words. |
| Turkish | Both | No | Julia only | Special casing rules for dotted/dotless "I"; avoid assumptions in upper/lowercase transformations. |
| Vietnamese | SPM | Yes | Both | Extensive use of diacritics; validate fonts and rendering. |

Note: AI has recommended using industry-standard libraries and practices by leveraging ICU and CLDR

### Appendix B — Role Permissions

| **Role** | **Scope** | **Core Permissions** |
|----|----|----|
| Authenticated Employee | Holocron | View and search all products, strings, translations, version history, review history, and audit history. |
| Content Owner | Assigned product/application | Create, manage, retire, and restore a product/application; manage Content Owners; create, edit, publish, retire, and restore strings; manage string metadata and review designations; manage translations; request reviews; and configure product-scoped peer reviewers. |
| Reviewer | Review type, product, and locale when applicable | View and complete only review requests for which the reviewer is eligible and authorized. |
| Review Administrator | Assigned Legal, Compliance, and/or Translation review domain | Maintain reviewer pools, reviewer eligibility, product and locale restrictions, and additional Review Administrators only within the assigned review domain or domains. |
| Holocron Administrator | Holocron | Grant or remove Legal, Compliance, and Translation Review Administrator privileges and add Content Owners to products/applications. |

### Appendix C — Translation and Review States

| **Field** | **Possible Values** |
|----|----|
| Translation State | Not Translated · Awaiting Translation · Pending Review · Approved · Published · Outdated |
| Reviewer | N/A · (User Name) |
| Review Status | Pending Review · Completed · Invalidated |
| Review Outcome | N/A · Approved · Rejected |

### Appendix D — Translation State Matrix and Scenarios

<table style="width:100%;">
<colgroup>
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
<col style="width: 16%" />
</colgroup>
<thead>
<tr>
<th><strong>Scenario</strong></th>
<th><strong>Translation State</strong></th>
<th><strong>Reviewer</strong></th>
<th><strong>Review Outcome</strong></th>
<th><p><strong>Owner</strong></p>
<p><strong>(For context)</strong></p></th>
<th><p><strong>Next Action</strong></p>
<p><strong>(For context)</strong></p></th>
</tr>
</thead>
<tbody>
<tr>
<td>New language never translated</td>
<td>Not Translated</td>
<td>N/A</td>
<td>N/A</td>
<td>Content Owner</td>
<td>Request/export translation</td>
</tr>
<tr>
<td>Translation exported to vendor</td>
<td>Awaiting Translation</td>
<td>N/A</td>
<td>N/A</td>
<td>Vendor</td>
<td>Translate</td>
</tr>
<tr>
<td>Vendor returns translation</td>
<td>Pending Review</td>
<td>N/A</td>
<td>N/A</td>
<td>Content Owner</td>
<td>Assign reviewer or approve directly</td>
</tr>
<tr>
<td>Content Owner assigns reviewer</td>
<td>Pending Review</td>
<td>Maria Garcia</td>
<td>N/A</td>
<td>Reviewer</td>
<td>Review translation</td>
</tr>
<tr>
<td>Reviewer reviewing</td>
<td>Pending Review</td>
<td>Maria Garcia</td>
<td>N/A</td>
<td>Reviewer</td>
<td>Complete review</td>
</tr>
<tr>
<td>Reviewer rejects translation</td>
<td>Pending Review</td>
<td>Maria Garcia</td>
<td>Rejected</td>
<td>TPM</td>
<td>Review the required rejection comments and decide whether to update the translation or request retranslation</td>
</tr>
<tr>
<td>TPM updates translation after rejected review</td>
<td>Pending Review</td>
<td>N/A</td>
<td>N/A</td>
<td>Reviewer</td>
<td>Create a new draft translation version and submit a new review request</td>
</tr>
<tr>
<td>TPM requests retranslation after rejected review</td>
<td>Awaiting Translation</td>
<td>N/A</td>
<td>N/A</td>
<td>Vendor</td>
<td>Re-translate using the rejection comments</td>
</tr>
<tr>
<td>Reviewer approves translation</td>
<td>Approved</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>TPM</td>
<td>Publish</td>
</tr>
<tr>
<td>TPM approves directly (review not required)</td>
<td>Approved</td>
<td>TPM</td>
<td>Approved</td>
<td>TPM</td>
<td>Publish</td>
</tr>
<tr>
<td>Approved but intentionally held</td>
<td>Approved</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>TPM</td>
<td>Publish when ready</td>
</tr>
<tr>
<td>Translation published</td>
<td>Published</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>None</td>
<td>Monitor</td>
</tr>
<tr>
<td>English changes after publication</td>
<td>Outdated</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>TPM</td>
<td>Obtain updated translation</td>
</tr>
<tr>
<td>Translation typo fix imported</td>
<td>Pending Review</td>
<td>N/A</td>
<td>N/A</td>
<td>TPM</td>
<td>Assign reviewer</td>
</tr>
<tr>
<td>Translation typo fix approved</td>
<td>Approved</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>TPM</td>
<td>Publish revision</td>
</tr>
<tr>
<td>Translation typo fix published</td>
<td>Published</td>
<td>Maria Garcia</td>
<td>Approved</td>
<td>None</td>
<td>Monitor</td>
</tr>
</tbody>
</table>

### Appendix F – Export file options

The approved format strategy (single canonical format vs approved format set, such as XLIFF and/or versioned JSON) is a discovery decision to be confirmed with translation service stakeholders before delivery.
