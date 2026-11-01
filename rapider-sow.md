<!-- Rapider Official App SOW & Specification | App #143: Building Information Modeling (BIM) Collaboration (building-information-modeling-bim-collaboration) | Domain: REA -->

# #143 Building Information Modeling (BIM) Collaboration (`building-information-modeling-bim-collaboration`) — Scope of Work (SOW)

- **App Number & Name:** `#143` — Building Information Modeling (BIM) Collaboration
- **App Key:** `building-information-modeling-bim-collaboration`
- **Rapider Suite / Domain Key:** `REA` (Real Estate, Facilities & Construction Suite)
- **Model Prefix:** `Rea*`
- **Representative Product:** Autodesk Construction Cloud (`BIM Collaborate Pro & Autodesk Docs / Forma`)
- **Top 6 Global Benchmarks:** Autodesk Construction Cloud (`P1`), Revizto (`P2`), Trimble Connect (`P3`), Bentley ProjectWise & iTwin (`P4`), Oracle Aconex (`P5`), IFS Cloud BIM & Asset Lifecycle (`P6`)
- **Companion Combined Feature Set:** [`../combined-features/143-building-information-modeling-bim-collaboration-features.md`](../combined-features/143-building-information-modeling-bim-collaboration-features.md)

---

## 1. Executive Outcome & Target Audience

**Executive Outcome:**  
`building-information-modeling-bim-collaboration` delivers an ISO 19650-compliant Common Data Environment (`CDE`) and OpenBIM 2D/3D design-coordination hub for Architects, Structural/MEP Engineers, BIM/VDC Managers, General Contractors, and Facility Owners. It governs model and drawing revision lifecycles (`ReaCdeContainer`, `ReaBimModel`, `ReaDrawingSheet`), formal cross-firm design transmittals (`ReaDesignPackageTransmittal`), multi-discipline federated 3D/2D viewing (`ReaFederatedModelView`), automated clash-detection matrices (`ReaClashTestRun`), `BCF 3.0`-compliant coordination issues (`ReaBimCoordinationIssue`), quantity extraction handoffs to `#148` (`construction-cost-estimation`), field RFI/punch escalations to `#142` (`construction-project-administration`), and `COBie` digital-twin commissioning into `#141` (`property-management`), `#146` (`space-planning-and-workplace-utilization`), and `assets`/`maintenance`.

**Why Pre-Construction BIM Coordination Matters Economically:**  
Resolving a structural-vs.-MEP duct penetration digitally during `S1 Coordination` costs `\$150.00`–`\$400.00` in modeling time, whereas discovering the same clash during jobsite installation triggers a `\$15,000.00+` field rework Change Order (`ReaChangeOrder` in `#142`) and critical-path schedule delay.

**SME Fast-Path vs. Enterprise Progressive Disclosure:**
- **SME Fast-Path:** Upload PDF plan sets and OpenBIM `.ifc` models into Rapider Drive-backed containers, auto-extract slip-sheeted 2D sheets (`A-101`, `M-201`), inspect federated 3D models in browser, drop markup pins, track `BCF 3.0` coordination issues on `<rapider-kanban>`, and escalate unresolved design conflicts to `#142` RFIs in one click.
- **Enterprise Depth:** Full ISO 19650 naming-convention Holding Area & suitability state gates (`WIP` -> `SHARED` -> `PUBLISHED` -> `ARCHIVED`), unalterable multi-party `Oracle Aconex`-style transmittals, automated discipline-vs.-discipline Clash Matrix (`Autodesk BIM Collaborate Pro`), `Revizto`-style 2D-on-3D hybrid sheet overlay & MCP/AI metadata queries, `Bentley iTwin` GUID version diffing + Watch Groups, and `COBie` equipment handover into `OpsOperationsAsset`.

**Target Personas:**
1. **BIM / VDC Manager:** Configures ISO 19650 naming templates, BEP/LOD checklists, federated coordination views, automated clash test matrices, and COBie handover readiness.
2. **Lead Architect / Structural / MEP Engineer:** Uploads discipline model drops, participates in `WIP -> SHARED -> PUBLISHED` review ballots, resolves assigned `BCF 3.0` clash issues, and syncs `.bcfzip` back to Revit/Navisworks/Tekla.
3. **GC Project Engineer / Field Superintendent:** Views current `PUBLISHED / A1` 2D sheets and 3D cutaways on tablet/mobile (`768px`/`390px`), compares sheet revisions, and escalates field-impacting clashes to `#142` `ReaConstructionRfi`s.
4. **Owner Digital Twin / Facilities Lead:** Audits COBie parameter completeness (`Manufacturer`, `SerialNumber`, `WarrantyDuration`) prior to commissioning assets into `assets` and `#141`.

---

## 2. In-Scope, Out-of-Scope & Suite Ownership Boundaries

### In Scope
- ISO 19650 CDE containers (`ReaCdeContainer`), filename validation Holding Area, suitability codes, `ReaDesignPackageTransmittal` audit logs, review ballots via Home `WorkItem`s, and BEP/LOD parameter checklists (`BIM-001`–`BIM-006`).
- 2D PDF plan splitting & title-block slip-sheeting (`ReaDrawingSheet`), 3D `IFC`/`glTF` federated coordination sets (`ReaFederatedModelView`), non-destructive 2D/3D markups, GUID version diffing (`Added`/`Modified`/`Removed`), 2D-to-3D anchor alignment, and `ReaModelWatchGroup` change alerts (`BIM-007`–`BIM-012`).
- Automated `ReaClashTestRun` tolerance rules, discipline Clash Matrix, grouped `ReaBimCoordinationIssue` tracking, native `BCF 3.0` import/export, auto-retest on new model publish, and 1-click escalation to `#142` `ReaConstructionRfi` / `ReaPunchListItem` (`BIM-013`–`BIM-018`).
- `IfcElement` QTO quantity export to `#148`, `IfcSpace` polygon/area export to `#141` & `#146`, `COBie` validation & `OpsOperationsAsset` commissioning (`ReaCobieHandoverBatch`), `plm` prefab component links, and grounded BIM AI copilots (`BIM-019`–`BIM-028`).

### Out of Scope
- Native desktop parametric CAD/BIM geometry authoring (performed in external desktop tools such as Revit, Archicad, Tekla, or Civil 3D and ingested as `IFC` / derivative `glTF` / `PDF`).
- Raw object blob storage infrastructure (delegated to Rapider Platform Files/Drive).
- Contractual RFI cost/change-order pricing, SOV progress pay apps, and lien waivers (owned by `#142` `construction-project-administration`).
- Unit-cost pricing libraries and subcontractor bid leveling (owned by `#148` `construction-cost-estimation`).

### Suite Ownership & Integration Contract Table

| Domain / App | Owns | Integration Contract with `building-information-modeling-bim-collaboration` |
| :--- | :--- | :--- |
| **`building-information-modeling-bim-collaboration` (`REA`)** | `ReaCdeContainer`, `ReaBimModel`, `ReaDrawingSheet`, `ReaFederatedModelView`, `ReaDesignPackageTransmittal`, `ReaClashTestRun`, `ReaBimCoordinationIssue`, `ReaModelWatchGroup`, `ReaCobieHandoverBatch` | Governs ISO 19650 CDE states, 2D/3D sheet/model versions, clash/BCF coordination, and COBie extraction. |
| **Rapider Platform Files / Drive** | Binary file blobs, signed upload/download URLs, virus scanning | Stores heavy `.ifc`, `.glb`/`.gltf`, `.pdf`, and `.bcfzip` files referenced by immutable `driveFileRef`s. |
| **`construction-project-administration` (`#142` — `REA`)** | `ReaConstructionJob`, `ReaConstructionRfi`, `ReaSubmittalItem`, `ReaPunchListItem` | `ReaBimCoordinationIssue` escalates to `ReaConstructionRfi` with embedded 3D viewpoint/sheet pin; `#142` pins resolve back to `ReaDrawingSheet`. |
| **`construction-cost-estimation` (`#148` — `REA`)** | `ReaCostEstimate`, `ReaTakeoffItem` | Consumes grouped `IfcElement` quantity payloads (`area`, `volume`, `length`, `count` by `ifcGuid`) for model-based QTO pricing. |
| **`property-management` (`#141`) & `space-planning` (`#146`)** | `ReaProperty`, `ReaUnit`, `ReaSpaceFloorPlan` | Consumes `IfcSpace` room polygons, floor levels, and BOMA/IPMS areas from `B1 As-Built` models. |
| **`assets`, `maintenance` & `plm` (`OPS`/`MFG` — Built)** | `OpsOperationsAsset`, `MfgMaintenanceWorkOrder`, `MfgProductRevision` | `ReaCobieHandoverBatch` commissions tagged building equipment (`ifcGuid`) into `OpsOperationsAsset` and links prefab modules to `MfgProductRevision`. |

---

## 3. Primary Web Pages & Sidebar Navigation Architecture (12 Pages)

All visible sidebar sections satisfy Rapider's **Minimum 3 Items per Section Rule** (`CDE & Drawings`: 3 items, `3D Coordination & Clashes`: 3 items, `Governance & Handover`: 3 items; 9 visible + 3 hidden detail/drawer routes = 12 total pages).

| # | Route | Page Title | Sidebar Section | Menu Visible | Key Components & UX |
| :---: | :--- | :--- | :--- | :---: | :--- |
| 1 | `cde-overview` | CDE & Coordination Hub | `CDE & Drawings` | `true` | KPI strip (Published Sheets, Active Federated Models, Open Critical Clashes, Holding Area Quarantine Count, COBie Readiness `%`), recent transmittals, `#activeFilterTagsBar`. |
| 2 | `bim-models` | BIM Models & CDE Containers | `CDE & Drawings` | `true` | `ReaBimModel` & `ReaCdeContainer` table (`findSWR`) filtered by ISO 19650 state (`WIP`, `SHARED`, `PUBLISHED`, `ARCHIVED`) and discipline; Holding Area quarantine banner & fix action. |
| 3 | `drawing-sheets` | 2D Drawing Sheets (Current Set) | `CDE & Drawings` | `true` | Slip-sheeted `ReaDrawingSheet` register (`A-101`, `S-201`, `M-301`) with discipline/level pills, revision badge, callout links, and side-by-side `vN vs vN-1` diff launcher. |
| 4 | `federated-viewer` | Federated 3D / 2D Explorer | `3D Coordination & Clashes` | `true` | Interactive `ReaFederatedModelView` canvas selector (discipline toggles, level sectioning, object `ifcGuid` property tree, laser measure, 2D-on-3D hybrid sheet overlay, Watch Group alerts). |
| 5 | `clash-matrix` | Clash Detection Matrix | `3D Coordination & Clashes` | `true` | Discipline-by-discipline `ReaClashTestRun` heatmap grid (`Arch`, `Struct`, `HVAC`, `Plumbing`, `Elec`, `Fire`), tolerance config, 1-click "Run Clash Check" & "Group into Issue". |
| 6 | `coordination-issues` | BIM Issues & BCF Board | `3D Coordination & Clashes` | `true` | Dual List + `<rapider-kanban>` of `ReaBimCoordinationIssue`s (`Open` -> `In Progress` -> `Ready for Review` -> `Resolved`), `.bcfzip` Import/Export, 1-click "Escalate to `#142` RFI". |
| 7 | `design-transmittals` | Design Packages & Transmittals | `Governance & Handover` | `true` | Immutable `ReaDesignPackageTransmittal` register + Review Ballot status (`S0`–`A1`/`B1`), recipient acknowledgment timestamps, Home `WorkItem` approval links. |
| 8 | `bep-lod-standards` | BEP, Naming & Watch Groups | `Governance & Handover` | `true` | Tabbed governance config: ISO 19650 naming rule builder, LOD/LOIN parameter audit scorecard, and `ReaModelWatchGroup` element-change subscriptions. |
| 9 | `cobie-qto-handover` | QTO Export & COBie Handover | `Governance & Handover` | `true` | `ReaCobieHandoverBatch` validator (missing serial/warranty checker), 1-click Commissioning Push to `assets` (`OpsOperationsAsset`) & `#141`/`#146`, plus QTO push to `#148`. |
| 10 | `sheet-model-detail` | Sheet / Model Revision Viewer | *(Hidden)* | `false` | Deep-link route (`#/sheet-model-detail?id=...`) with `Back` filter-state preservation, markup layer toggles, GUID `Added/Modified/Removed` diff table, and `projectChannelMessage` thread. |
| 11 | `clash-issue-detail` | BCF Coordination Issue 360 | *(Hidden)* | `false` | Deep-link route (`#/clash-issue-detail?id=...`) displaying saved `BCF 3.0` camera snapshot, clashing `ifcGuid` pair properties, linked `#142` `rfiNumber`, and resolution audit log. |
| 12 | `upload-transmittal-drawer` | Model Upload & Transmittal Drawer | *(Hidden)* | `false` | Sliding drawer validating ISO 19650 naming live, consultant contact `<rapider-phone-input>`, `try...catch...finally` button reset, auto-close on save/cancel, and SWR cache invalidation. |

---

## 4. Canonical Data Models (`Rea*` — 9 Models)

| Model Name | Key Fields & Types | Relationships & External Refs | Invariants & Lifecycle |
| :--- | :--- | :--- | :--- |
| **`ReaCdeContainer`** | `code` (`String`), `name` (`String`), `isoNamingPattern` (`String`), `defaultSuitability` (`String`), `lodStandard` (`LOD_200`, `LOD_300`, `LOD_350`, `LOD_400`, `LOD_500`), `status` (`ACTIVE`, `ARCHIVED`), `version` (`Integer`) | `jobId` -> `ReaConstructionJob` (`#142`, nullable), `propertyId` -> `ReaProperty` (`#141`, nullable) | Enforces regex/token naming validation on every child model/sheet upload; non-matching files land in `quarantineStatus = HOLDING_AREA`. |
| **`ReaBimModel`** | `modelCode` (`String`), `fileName` (`String`), `discipline` (`ARCH`, `STRUCT`, `MEP_HVAC`, `MEP_ELEC`, `MEP_PLUMB`, `FIRE`, `CIVIL`), `format` (`IFC_2X3`, `IFC_4_3`, `GLTF_DERIVATIVE`, `POINT_CLOUD`), `revisionNumber` (`Integer`), `cdeState` (`HOLDING_AREA`, `WIP`, `SHARED`, `PUBLISHED`, `ARCHIVED`), `suitabilityCode` (`S0`..`S4`, `A1`, `B1`), `elementCount` (`Integer`), `diffSummary` (`Object`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer`, `sourceDriveFileRef` -> Rapider Drive, `webStreamFileRef` -> Rapider Drive, `uploadedByRef` -> `HrEmployee` / `CrmContact` | Promoting `WIP -> SHARED` or `SHARED -> PUBLISHED` requires passing naming validation and (when configured) an approved Home `WorkItem` ballot; `PUBLISHED` revisions are immutable. |
| **`ReaDrawingSheet`** | `sheetNumber` (`String`, e.g., `A-101`), `sheetTitle` (`String`), `discipline` (`String`), `levelCode` (`String`), `revisionCode` (`String`), `revisionNumber` (`Integer`), `issueDate` (`Date`), `cdeState` (`WIP`, `SHARED`, `PUBLISHED`, `SUPERSEDED`), `anchorCalibration2d3d` (`Object`), `markups` (`Object[]`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer`, `sourceModelId` -> `ReaBimModel` (nullable), `pdfDriveFileRef` -> Rapider Drive | Uploading a new `PUBLISHED` sheet with identical `(containerId, sheetNumber)` atomically transitions the prior `PUBLISHED` revision to `SUPERSEDED` while migrating active open issue pins. |
| **`ReaFederatedModelView`** | `name` (`String`), `zoneOrLevelFilter` (`String`), `includedModelIds` (`UUID[]`), `savedViewpoints` (`Object[]`: camera eye/target/up, clipping planes), `isDefaultCoordinationSet` (`Boolean`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer` | Only `SHARED` or `PUBLISHED` `ReaBimModel`s may be included in cross-discipline `isDefaultCoordinationSet = true` views (`WIP` models remain private to the authoring discipline). |
| **`ReaDesignPackageTransmittal`** | `transmittalNumber` (`String`), `packageTitle` (`String`), `purpose` (`FOR_COORDINATION`, `FOR_REVIEW`, `FOR_TENDER`, `FOR_CONSTRUCTION`, `AS_BUILT_HANDOVER`), `suitabilityCode` (`String`), `modelIds` (`UUID[]`), `sheetIds` (`UUID[]`), `recipientAcks` (`Object[]`), `issuedAt` (`DateTime`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer`, `senderAccountRef` -> `CrmAccount`, `recipientContactRefs[]` -> `CrmContact`, `reviewWorkItemId` -> Home `WorkItem` | Strictly append-only immutable once `issuedAt` is set (`Oracle Aconex` non-repudiation invariant). |
| **`ReaClashTestRun`** | `testCode` (`String`), `name` (`String`), `leftDisciplineOrSet` (`String`), `rightDisciplineOrSet` (`String`), `clashType` (`HARD`, `CLEARANCE`, `DUPLICATE`), `toleranceMm` (`Decimal128`), `rawClashCount` (`Integer`), `groupedIssueCount` (`Integer`), `resolvedCount` (`Integer`), `executedAt` (`DateTime`), `status` (`QUEUED`, `COMPLETED`, `FAILED`), `version` (`Integer`) | `federatedViewId` -> `ReaFederatedModelView` | `toleranceMm >= 0`; deterministic `ifcGuid` pair hashing ensures repeated test runs recognize existing open/ignored clashes rather than creating duplicates. |
| **`ReaBimCoordinationIssue`** | `issueNumber` (`String`, e.g., `BIM-0108`), `bcfTopicGuid` (`UUID`), `title` (`String`), `issueType` (`CLASH`, `DESIGN_DEFECT`, `CODE_CLEARANCE`, `MISSING_INFO`, `CONSTRUCTABILITY`), `priority` (`CRITICAL`, `HIGH`, `MEDIUM`, `LOW`), `clashingIfcGuids` (`String[]`), `bcfViewpoint` (`Object`), `dueDate` (`Date`), `ignoredJustification` (`String`), `status` (`OPEN`, `IN_PROGRESS`, `READY_FOR_REVIEW`, `RESOLVED`, `APPROVED_IGNORED`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer`, `clashTestRunId` -> `ReaClashTestRun` (nullable), `sheetId` -> `ReaDrawingSheet` (nullable), `assigneeContactRef` -> `CrmContact` / `HrEmployee`, `escalatedRfiId` -> `ReaConstructionRfi` (`#142`, nullable) | Setting `status = APPROVED_IGNORED` requires non-empty `ignoredJustification` by BIM Manager; preserves lossless `bcfTopicGuid` for round-trip `.bcfzip` sync. |
| **`ReaModelWatchGroup`** | `name` (`String`), `watchedDiscipline` (`String`), `ifcEntityTypes` (`String[]`, e.g., `["IfcBeam", "IfcColumn", "IfcSlabOpening"]`), `watchedGuids` (`String[]`), `subscriberRefs` (`UUID[]`), `lastTriggeredRevision` (`Integer`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer` | Emits change digest notifications whenever a newly `SHARED`/`PUBLISHED` model modifies watched `ifcGuid` geometry or fire/structural parameters. |
| **`ReaCobieHandoverBatch`** | `batchCode` (`String`), `completenessPct` (`Decimal128`), `facilitySpacesCount` (`Integer`), `maintainableAssetsCount` (`Integer`), `missingAttributeWarnings` (`Object[]`), `status` (`VALIDATING`, `DEFICIENT`, `READY_FOR_HANDOVER`, `COMMISSIONED`), `commissionedAt` (`DateTime`), `version` (`Integer`) | `containerId` -> `ReaCdeContainer`, `asBuiltModelIds` (`UUID[]`), `targetPropertyId` -> `ReaProperty` (`#141`), `createdAssetRefs[]` -> `OpsOperationsAsset` | Cannot transition to `COMMISSIONED` while mandatory COBie fields (`AssetIdentifier`, `Space`, `ComponentType`, `WarrantyStart`) have `CRITICAL` deficiencies unless waived via Owner `WorkItem`. |

---

## 5. Core End-to-End User Journeys (6 Journeys)

### Journey 1: ISO 19650 Model Upload, Holding Area Fix & `SHARED` Package Promotion
1. Structural Engineer opens `bim-models` -> `upload-transmittal-drawer` and uploads `Struct_Level3.ifc`. Because it violates the container's ISO 19650 pattern (`PRJ14-STR-ZZ-03-M3-S-0001.ifc`), it is placed in `HOLDING_AREA` and Grounded AI Title-Block & Naming Inspector suggests the exact compliant code.
2. Engineer accepts the rename and submits a `PromoteCdeState(WIP -> SHARED)` request (`suitabilityCode = S1`), generating a Home `WorkItem` for the Structural Lead.
3. Upon approval, the model enters `SHARED`, triggers `ReaModelWatchGroup` alerts to the HVAC Lead (`3 modified IfcBeam penetrations on Level 3`), and emits an immutable `ReaDesignPackageTransmittal`.

### Journey 2: Automated Multi-Discipline Clash Matrix -> BCF 3.0 Issue -> Revit Round-Trip
1. BIM Manager opens `clash-matrix`, selects `Structural Steel (v4)` vs. `MEP_HVAC Ducts (v6)` (`HARD` clash, `toleranceMm = 10.0`), and clicks **Run Clash Check**.
2. Engine identifies 19 raw intersections along Corridor 3B and groups them into `BIM-0108 — Supply Trunk Duct Clashes with W18x35 Girder` (`CRITICAL`) with a saved `BCF 3.0` 3D camera viewpoint.
3. MEP Coordinator exports `.bcfzip` from `coordination-issues`, adjusts the duct elevation in Revit, uploads `MEP_HVAC (v7)` (`BCF` status `READY_FOR_REVIEW`), and automated clash re-verification confirms `0 mm` interference so BIM Manager closes `BIM-0108`.

### Journey 3: Escalating an Unresolvable Design Clash to a Contractual `#142` RFI
1. During coordination on `federated-viewer`, `BIM-0114` reveals insufficient ceiling plenum height to clear both gravity storm piping and structural framing—requiring an architectural ceiling drop.
2. BIM Manager clicks **Escalate to Construction RFI**, invoking `EscalateClashToRfi` which creates `RFI-0028` inside `#142` (`construction-project-administration`) pre-populated with the `BCF` snapshot, sheet `A-302` pin coordinates, and clashing `ifcGuid` metadata. When the Architect answers and locks `RFI-0028` in `#142`, the status reflects live on `clash-issue-detail`.

### Journey 4: 2D PDF Plan Slip-Sheeting & Red/Blue Revision Overlay in the Field
1. Document Controller uploads a 42-page `Issued for Construction (A1)` PDF set on `drawing-sheets`. Title-block parser splits all 42 sheets, matching `A-101` (`Rev 3`) onto `A-101` (`Rev 2`), marking `Rev 2` `SUPERSEDED` while carrying forward 3 active field pins.
2. On a jobsite tablet (`768px`), the Superintendent opens `sheet-model-detail` for `A-101` and toggles `Compare v3 vs v2`, inspecting relocated partition walls in red/blue overlay before framing begins.

### Journey 5: Model QTO Export to `#148` & `B1 As-Built` COBie Handover to `assets` & `#141`/`#146`
1. During pre-construction on `cobie-qto-handover`, Estimator exports grouped `IfcSlab`, `IfcWall`, and `IfcDoor` quantities to `#148` (`construction-cost-estimation`) for assembly pricing.
2. At project closeout, Facilities Lead runs `ValidateAndCommissionCobie` on `B1 As-Built` models (`98.5%` parameter completeness), pushing 84 tagged HVAC/electrical/fire components (with preserved `ifcGuid`s) into `assets` (`OpsOperationsAsset`) and exporting `IfcSpace` room polygons into `#141` (`ReaUnit`) and `#146` (`ReaSpaceFloorPlan`).

### Journey 6: Click-Through Navigation & Filter State Restoration
1. On `coordination-issues`, user filters `Priority: "CRITICAL"` and `Discipline: "MEP_HVAC"`, confirming `#activeFilterTagsBar` renders dismissible chips and `[Clear all]`. Clicking `BIM-0108` opens `#/clash-issue-detail?id=...` cleanly, and clicking `Back` restores the exact filtered `<rapider-kanban>` / table view.

---

## 6. Consolidated Feature Priorities & Work Packages (`P0`, `P1`, `P2`)

### `P0` Foundation Work Packages (11 Capabilities)
- **WP-P0-1 — ISO 19650 CDE, Naming Quarantine & Versioning (`BIM-001`–`BIM-003`):** `ReaCdeContainer`, `HOLDING_AREA` naming enforcement, and immutable `ReaBimModel` / `ReaDrawingSheet` version lineage (`cde-overview`, `bim-models`, `upload-transmittal-drawer`).
- **WP-P0-2 — 2D Slip-Sheeting, Federated 3D Viewer & Markups (`BIM-007`–`BIM-009`):** `ReaDrawingSheet` title-block extraction, `ReaFederatedModelView` discipline/section explorer, and non-destructive markups (`drawing-sheets`, `federated-viewer`, `sheet-model-detail`).
- **WP-P0-3 — Clash Matrix, BCF 3.0 Issues, `#142` Escalation & COBie Validation (`BIM-013`–`BIM-016`, `BIM-020`):** `ReaClashTestRun` matrix, `ReaBimCoordinationIssue` `<rapider-kanban>` + `.bcfzip` I/O, 1-click `#142` RFI escalation, and `ReaCobieHandoverBatch` validator (`clash-matrix`, `coordination-issues`, `clash-issue-detail`, `cobie-qto-handover`).

### `P1` Scale & Enterprise Work Packages (10 Capabilities)
- **WP-P1-1 — Formal Transmittals, Review Ballots & BEP/LOD Governance (`BIM-004`–`BIM-006`):** Immutable `ReaDesignPackageTransmittal`s, Home `WorkItem` suitability ballots, and LOD/LOIN parameter audits (`design-transmittals`, `bep-lod-standards`).
- **WP-P1-2 — 2D/3D GUID Diffing, Hybrid Overlay & Auto Clash Re-Verification (`BIM-010`, `BIM-011`, `BIM-017`, `BIM-018`):** `vN vs vN-1` `ifcGuid` diffing, 2D-to-3D anchor calibration, auto-retest on publish, and coordination meeting runner.
- **WP-P1-3 — Cross-Suite QTO, `IfcSpace` & EAM Asset Commissioning (`BIM-019`, `BIM-021`, `BIM-022`):** Quantity push to `#148`, `IfcSpace` sync to `#141`/`#146`, and `OpsOperationsAsset` COBie commissioning.

### `P2` Adjacent & Grounded AI Work Packages (7 Capabilities)
- **WP-P2-1 — Watch Groups, Prefab PLM Links & Coordination Health Scorecard (`BIM-012`, `BIM-023`, `BIM-028`):** `ReaModelWatchGroup` alerts, `plm` `MfgProductRevision` modular links, and MTTR/compliance analytics.
- **WP-P2-2 — Grounded BIM & CDE AI Copilots (`BIM-024`–`BIM-027`):** AI title-block/ISO-naming helper, natural-language `ifcGuid`/COBie query assistant, clash cluster prioritizer, and drawing-vs.-submittal consistency checker.

---

## 7. Roles, Permissions & Field-Level Governance

| Role | Permitted Actions | Restricted / Field-Level Boundaries |
| :--- | :--- | :--- |
| **BIM / VDC Manager** | Configures `ReaCdeContainer` ISO 19650 standards, manages `ReaFederatedModelView`s, runs `ReaClashTestRun`s, approves `WIP -> SHARED -> PUBLISHED` `WorkItem`s, authorizes `APPROVED_IGNORED` clashes. | Cannot alter historical `issuedAt` `ReaDesignPackageTransmittal` records or overwrite `PUBLISHED` binaries. |
| **Discipline Lead (Arch / Struct / MEP)** | Uploads/manages own discipline `WIP` models & sheets, submits `SHARED` packages, resolves assigned `ReaBimCoordinationIssue`s, exports/imports `.bcfzip`. | Zero visibility into another firm's private `WIP` folder (`SHARED` and `PUBLISHED` only, per ISO 19650 managed-trust standard). |
| **GC Project Engineer / Field Super** | Views `PUBLISHED` Current Set drawings/models, adds field markups, escalates clashes/issues to `#142` RFIs & punch items. | Cannot promote design suitability codes (`S0`–`A1`) or delete discipline design models. |
| **Document Controller** | Manages `HOLDING_AREA` naming remediation, slip-sheets PDF drawing packages, issues `ReaDesignPackageTransmittal`s, tracks recipient acknowledgments. | Cannot waive structural/MEP engineering clash sign-offs (`APPROVED_IGNORED`). |
| **Owner / Facilities Twin Lead** | Reviews `PUBLISHED` / `B1 As-Built` deliverables, audits `ReaCobieHandoverBatch` completeness, executes `OpsOperationsAsset` commissioning. | Read-only on pre-shared design `WIP` iterations. |

---

## 8. Technical APIs, Guarded Commands, Events & `requiredWorkflows`

### Guarded Domain Commands
Every command requires `{ idempotencyKey, correlationId, expectedVersion }`:
1. `IngestAndValidateCdeDeliverable({ containerId, driveFileRef, fileName, discipline, metadata })` — Checks ISO 19650 naming regex; places into `WIP` or quarantines into `HOLDING_AREA`.
2. `PromoteCdeState({ deliverableType, deliverableId, targetState, suitabilityCode, approvalWorkItemId })` — Enforces `WIP -> SHARED -> PUBLISHED` state machine and slip-sheets prior `PUBLISHED` sheets to `SUPERSEDED`.
3. `IssueDesignPackageTransmittal({ containerId, purpose, suitabilityCode, modelIds[], sheetIds[], recipientContactRefs[] })` — Writes immutable transmittal and dispatches notifications.
4. `RunClashDetectionMatrix({ federatedViewId, leftSet, rightSet, clashType, toleranceMm })` — Executes deterministic `ifcGuid` pair intersection check and updates existing `ReaBimCoordinationIssue` regressions.
5. `EscalateClashToRfi({ coordinationIssueId, jobId, assigneeRef, dueDate })` — Creates linked `ReaConstructionRfi` in `#142` with `BCF` viewpoint payload.
6. `CommissionCobieBatch({ cobieBatchId, targetPropertyId, approvalWorkItemId })` — Creates/updates `OpsOperationsAsset` records (`assets`) and `ReaUnit`/`ReaSpaceFloorPlan` space geometry (`#141`/`#146`).

### Domain Events Published & Consumed (Kafka)
- **Published:** `rea.bim_model.shared`, `rea.bim_model.published`, `rea.drawing_sheet.superseded`, `rea.transmittal.issued`, `rea.bim_clash.escalated`, `rea.qto_quantities.exported`, `rea.cobie_handover.commissioned`.
- **Consumed:** `rea.rfi.answered` & `rea.submittal.stamped` (from `#142` to update linked BIM issue status & spec checks), `ops.asset.updated` (from `assets` for twin lifecycle sync).

### `requiredWorkflows` (in `app.manifest.json`)
- `wf-rea-bim-derivative-and-sheet-splitter`: Asynchronous worker extracting PDF sheet title blocks and generating streaming `glTF` + `IfcElement` property indexes upon upload.
- `wf-rea-auto-clash-and-watch-notifier`: Runs automated clash re-verification and `ReaModelWatchGroup` diff digests whenever a discipline package promotes to `SHARED`.
- `wf-rea-cde-review-ballot-sla`: Routes and escalates multi-reviewer ISO 19650 suitability ballots in Home `WorkItem`s.

### Grounded Rapider AI Contract
AI assistants (`BIM-024`–`BIM-027`) respect ISO 19650 folder isolation (never indexing another firm's private `WIP` models), cite exact `sheetNumber`s and `ifcGuid`s, and NEVER auto-approve suitability promotions (`A1 Authorized for Construction`) or mark structural/life-safety clashes `APPROVED_IGNORED` without human BIM Manager sign-off.

---

## 9. Security, Privacy, Compliance & Non-Functional Requirements

- **ISO 19650 Information Security (Part 5 — ISO 19650-5):** Supports security-minded asset/facility protection (e.g., restricting critical infrastructure vaults, data-center power rooms, hospital security layouts) via container- and discipline-level ACLs, signed short-lived Rapider Drive streaming URLs, and strictly isolated `WIP` authoring spaces.
- **Contractual Non-Repudiation:** Issued `ReaDesignPackageTransmittal`s, `PUBLISHED` drawing/model revisions, and recipient download acknowledgments are append-only immutable for professional-liability defense (`10+ years`).
- **Performance & Viewport Responsiveness:** Streams chunked `glTF` / 2D vector tiles smoothly on desktop (`1440px`), jobsite iPad/tablets (`768px`), and mobile (`390px` Current Set sheet & BCF issue viewer); WCAG 2.2 AA compliant with `#ffffff !important` button text contrast.

---

## 10. Deterministic Acceptance Criteria (14 Testable Criteria)

1. **Sidebar Section 3+ Item Compliance:** `CDE & Drawings` (3 items), `3D Coordination & Clashes` (3 items), and `Governance & Handover` (3 items) each contain `>= 3` visible menu items; `sheet-model-detail`, `clash-issue-detail`, and `upload-transmittal-drawer` set `displayOnMenu: false`.
2. **ISO 19650 Naming Quarantine Invariant:** Uploading a file that violates `ReaCdeContainer.isoNamingPattern` automatically sets `cdeState = HOLDING_AREA` and blocks promotion to `SHARED` or `PUBLISHED` until renamed or waived via Home `WorkItem`.
3. **Strict `WIP` Privacy Isolation:** Querying `ReaBimModel` or `ReaFederatedModelView` as Discipline `MEP` never returns `WIP`-state models owned by Discipline `ARCH` (`403` on direct ID access).
4. **Automatic Sheet Slip-Sheeting:** Promoting `A-101` (`revisionNumber = 3`) to `PUBLISHED` atomically transitions `A-101` (`revisionNumber = 2`) to `SUPERSEDED` and carries open `ReaBimCoordinationIssue` sheet pins forward.
5. **Immutable Transmittals & Published Revisions:** Attempting `edit` or `delete` on an issued `ReaDesignPackageTransmittal` or `PUBLISHED` `ReaBimModel` rejects deterministically with `409 IMMUTABLE_CDE_RECORD`.
6. **Lossless BCF 3.0 Round-Trip:** Importing a `.bcfzip` topic and re-exporting it preserves `bcfTopicGuid`, camera position/clipping planes, and `clashingIfcGuids` without data loss.
7. **Justified Clash Ignore Rule:** Transitioning a `ReaBimCoordinationIssue` to `APPROVED_IGNORED` with an empty `ignoredJustification` fails deterministically with `422 JUSTIFICATION_REQUIRED`.
8. **1-Click `#142` RFI Escalation:** Executing `EscalateClashToRfi` creates a linked `ReaConstructionRfi` in `#142` carrying the sheet/viewpoint reference and prevents duplicate RFI creation on idempotent retry.
9. **COBie Commissioning Gate:** `CommissionCobieBatch` blocks transition to `COMMISSIONED` if mandatory COBie fields contain unresolved `CRITICAL` deficiencies (unless accompanied by an approved Owner `WorkItem`), and upon success creates canonical `OpsOperationsAsset` records in `assets`.
10. **SWR Reads & Active Filter Tags:** Every list/kanban page uses `findSWR`/`countSWR` with zero manual `isDeleted` `where` clauses, filters `item.isDeleted !== true` in memory, and displays `#activeFilterTagsBar` with escaped chips and `[Clear all]`.
11. **Table Actions & Real Click-Through Navigation:** Zero standalone "View" buttons in `Actions`; clicking `sheetNumber`, `modelCode`, or `issueNumber` navigates cleanly to detail pages without `<base href>` 404 diversion, and `Back` restores filter state.
12. **Custom Elements & Drawer Lifecycle:** Uses `<rapider-kanban>` on `coordination-issues` and `<rapider-phone-input>` in `upload-transmittal-drawer`; drawers reset buttons in `finally` and auto-close on save/cancel.
13. **Zero `projectId` Field:** No `Rea*` model defines `projectId`; workspace multi-tenancy is enforced automatically by host context.
14. **Theme & Contrast Compliance:** All 12 pages pass dark/light `validate_theme` checks with `#ffffff !important` on primary/danger buttons and zero `window.alert`/`confirm`/`prompt`.
