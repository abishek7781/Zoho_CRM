# ISF CRM implementation task tracker
Updated 30 October 2026 (IST). Organisation 60070586928.

## Active direction
User approved the role-workspace and automation restructuring plan and requested sequential execution. This queue supersedes the historical task order below. Existing verified configurations must be reused. A specification is never reported as deployed or tested configuration.

## Execution queue
| ID | Task | Completion evidence | Status |
|---|---|---|---|
| T01 | Finalise the 22-activity control matrix | All 22 activities have owner, prerequisites, evidence, optional paths, next task and notification policy | Complete: specification only |
| T02 | Map and align authoritative fields/layouts | Existing fields mapped; layout gaps repaired safely; remaining source/permission dependencies explicit | Baseline implemented: two existing fields added to Deal Pipeline and verified; accounting/permission checks remain in later tasks |
| T03 | Repair qualification, contact and sales gates | Missing/invalid contact, requirements, quote and order data blocked; controlled exceptions; WhatsApp consent separated | Draft re-saved and reopened: Discovery now gates on Mobile Number present OR Email Consent Verified=true; Mobile Number optional and Email Consent Verified mandatory; Quote Sent and Order Confirmation controls, acceptance checklist, Contract Value validation, existing handoff workflow and sender eligibility verified; not published; runtime checks blocked |
| T04 | Repair financial gates and MD approvals | Approved amount/version; verified receipt; partial payments; rejection/resubmission and no self-approval bypass | Implemented in CRM layout and unpublished Blueprint draft: Advance Receipt History subform (Receipt Amount, Receipt Date, Receipt Transaction ID, Receipt Payment Mode); Accounting Source Reference and Accounting Source Version are mandatory at Advance Payment Requested; Advance Payment Received retains mandatory receipt evidence/verifier gates; active function validation blocks Advance Received above Advance Amount; active payment approval now targets the named MD user Mungra Manendra rather than the broad MD role. Zoho still exposes no native requester-versus-approver exclusion, so the remaining residual control limitation is documented and the Blueprint remains unpublished. |
| T05 | Repair visit, preparation, execution and closure gates | Correct dates, readiness, evidence, conditional contract/sample paths and closure exceptions | Queued |
| T06 | Connect small action forms for all 22 activities | Reuse Kiosks/Wizards; preload same records; validate, write and bind each action; hide routing fields | Queued |
| T07 | Configure Sales workspace and My Work | Current-user owned work; enquiries, follow-ups, quotations and handoffs; no duplicate customer records | Queued |
| T08 | Configure Execution & Accounts workspace and My Work | Assigned visits, preparation, execution, receipts and handovers | Queued |
| T09 | Configure MD overview and approvals | Shared progress, blockers, approvals and totals; field permissions verified | Queued |
| T10 | Consolidate automation by business event | Each rule labelled Keep/Modify/Merge/Retire/Test-only; downstream dependencies and pending schedules checked; one sender/event | Queued |
| T11 | Configure internal reminders and customer notifications | Assigned-person notification, agreed escalation, cancellation on completion/reschedule; consent/template/dedup guards | Queued |
| T12 | Acceptance, controlled release and user guide | Positive/negative/role/repeat/failure cases pass; rollback recorded; three-role guide available | Queued |

Progress: T01 specification complete; T02 baseline field alignment implemented; T03 remains partially configured in an unpublished draft with the controlled email-route gate saved and persistence verified. T04 finance controls are implemented in the Deal Pipeline layout, the overpayment validation rule is active, and the request controls were saved and reopened in the unpublished Blueprint draft. The active payment approval now uses the verified named MD user Mungra Manendra; Zoho's native requester-exclusion control remains unavailable, and no runtime payment test or Blueprint publish was performed. T05–T12 remain queued. No percentage of live CRM implementation is implied. T06 contains 22 separately verified action forms.

## Implementation journal — 30 October continuation on this device

- Read the attached implementation tracker first and resumed the first unfinished task, T03. The attached wizard document was treated as procedural guidance; its guardrails remain subordinate to the user request and were preserved.
- Draft `1287721000004162041` was opened, saved as draft, reopened, and verified. Published Blueprint `1287721000002448077` was not changed and Publish/Republish was not pressed.
- Order Confirmation transition `1287721000004162049` now visibly contains the mandatory `Customer order acceptance` checklist with: (1) acceptance date, channel and evidence reference recorded in Negotiation Notes; and (2) agreed scope, quotation revision, price and terms match the acceptance. This checklist is saved and persisted on reopen.
- The same transition visibly contains mandatory Contract Value with validation `Contract Value >= 0.01` and alert `Enter the agreed order value greater than zero.` This validation is saved and persisted on reopen.
- Existing active workflow `Process Step → Order Confirmation` (`1287721000002144373`) was verified read-only. It sets `WA_Event` to `order_confirmation` and creates the existing `Verify customer order and execution handoff` task. No Blueprint task was added, avoiding a duplicate handoff.
- Discovery controlled-route draft change was implemented and persisted: eligibility is `Mobile Number is not empty OR Email Consent Verified is true`; During makes Mobile Number optional and Email Consent Verified mandatory. Requirement Notes and Contact Name remain mandatory. The Deal layout still has no email destination field, so actual email presence and exception reason remain human verification responsibilities; Zoho did not retain an attempted new checklist entry. Do not claim automatic email validation or publish until the route is runtime-tested and sender behavior is reconciled.
- WhatsApp sender eligibility was checked read-only: Business Messaging is active for India Sports Infra, associated phone `+917338858989`, available credits shown as `1`; the notification inventory contains the established Deal templates including quote sent, order confirmed, advance request/received, work started/completed, final payment and handover. This confirms channel/sender availability only, not runtime eligibility, consent, deduplication or delivery.
- No Deal was advanced/reset, no customer record was edited, no message was sent or resent, no trigger replay/debug was run, and the protected live router was not changed. TEST-DATA Deal `1287721000003658001` remains untouched.
- T03 status: controlled email-route gate saved and reopened; Quote Sent/Order Confirmation controls, existing handoff and sender eligibility verified; unpublished; runtime-tested = no; automatic email destination/exception evidence and sender exclusivity remain unverified. T03 is not complete or live.

### T03 continuation — controlled email route saved, 30 October 2026
- Discovery transition `1287721000004162044` now shows Before criteria `Mobile Number is not empty OR Email Consent Verified is true`.
- Discovery During now shows Mobile Number as Optional and Email Consent Verified as Mandatory. Requirement Notes, Contact Name, Sport Type and Site Location remain Mandatory.
- Reopened draft `1287721000004162041` after saving and verified the criteria and During field states. Published Blueprint `1287721000002448077` remains unchanged; no publish action was taken.
- Attempted to attach a new `Email-only contact exception` checklist through the During > Checklists picker, but the entry did not persist after save/reopen. The saved control therefore relies on mandatory Requirement Notes plus the mandatory consent-verification field; no automatic email-address validation or separate exception-reason field is claimed.
- No Deal edits, transition executions, trigger replays, messages, or protected-router changes occurred. Runtime tests remain blocked pending reconciliation of the direct-send test orchestrator and sender/deduplication isolation.

### T04 continuation — financial request controls saved, 30 October 2026
- Draft `1287721000004162041`, `Move to Advance Requested` During, now has mandatory `Advance Amount` with validation `Advance Amount >= 0.01` and alert `Enter an advance amount greater than zero.` It also has mandatory `Advance Requested Date` and `Advance Due Date`.
- Root cause of the earlier save failure: Zoho's masked currency input did not accept the automation `fill()` replacement; the old value remained submitted. Keyboard replacement of the visible value to `0.01`, followed by `>=`, saved successfully.
- Draft was saved, reopened and verified. Published Blueprint `1287721000002448077` remains unchanged. No Deal edits, transition executions, payment changes, messages or trigger replays occurred.
- Existing active approval process `Deals - Payment Request Approval` (`1287721000003199220`) was verified read-only: trigger is Create or Edit on Deals; criterion is `Current Process Step IS Advance Payment Requested`; Stage 1 approvers are the MD role; final approval updates Advance Payment Approval Status; rejection updates Advance Payment Rejected Status. No duplicate approval process was created.
- The saved draft's `Move to Advance Received` transition (`1287721000004162051`) was then reached by panning the Blueprint canvas. Its During form now requires `Advance Payment Mode`, `Advance Transaction ID`, `Advance Received`, `Advance Payment Date` and `Advance Verified`. `Advance Received` has validation `Advance Received >= 0.01` with alert `Enter the received advance amount greater than zero.`
- Added Deal Pipeline field `Advance Receipt Verified By` as a required single-user field. The receipt transition now also requires `Advance Receipt Verified By` and the Associated Items relationship `Attachments` (mandatory). This makes the evidence attachment and verifier identity part of the saved transition form; `Advance Verified` remains the explicit confirmation gate.
- The draft was saved, reopened and the receipt fields, mandatory attachment relationship, verifier field and amount validation were verified after reopen. Published Blueprint `1287721000002448077` remains unchanged; no runtime transition was executed.
- Resolved finance-source and receipt-history blockers: the Deal Pipeline layout now contains `Advance Receipt History` with primary `Receipt Amount` plus `Receipt Date`, `Receipt Transaction ID` and `Receipt Payment Mode`; `Accounting Source Reference` and `Accounting Source Version` were added to the Commercials & Advance Payment section. The unpublished Blueprint draft's `Move to Advance Requested` During form now requires both accounting source fields. Layout save completed successfully and the draft was saved, reopened and verified after the new fields were added.
- Resolved overpayment handling: active Deal Pipeline validation rule for `Advance Received` uses function `Reject Advance Overpayment` (`rejectAdvanceOverpayment`) and returns an error when cumulative `Advance Received` exceeds `Advance Amount`. This is configuration-verified, not runtime-tested against the protected TEST-DATA Deal.
- Approval blocker mitigated: Users read-only verification showed `Mungra Manendra` has the `MD` role and is the active MD account. The existing approval Stage 1 was changed from `Role > MD > Anyone` to `User > Mungra Manendra`; Zoho displayed `Deals - Payment Request Approval updated successfully.` This removes broad-role ambiguity and was saved in the active approval process without touching any Deal.
- Residual control limitation: Zoho's approval editor still exposes no native requester-versus-approver exclusion. A named MD approver is safer and auditable, but it does not prove that an MD-owned Deal cannot be approved by that same MD. No unverified alternate approver or fail-open rule was introduced; runtime approval testing remains intentionally blocked.
- Working policy approved for continuation: Deal fields are the workflow gate populated from the approved quotation/invoice; accounting remains the reconciliation source; receipt evidence must include amount, date, mode, bank/transaction reference, proof attachment and verifier; MD approval is required and the requester/Deal Owner may not self-approve; `Advance Received` is cumulative for partial receipts; overpayments/mismatches route to MD as exceptions.
- The new subform and fields are structure/process controls, not a second finance ledger. Accounting remains the reconciliation source; the source reference/version identifies the approved accounting record. No receipt data, customer record, payment change, message, trigger replay or live-router change was created.

## Implementation journal — 29 October continuation

### T02 saved production layout change
- Deal Pipeline layout 1287721000000594218: moved existing Quotation Reference from Unused Items into Commercials & Advance, before Quotation Sent Date. Moved existing Site Visit Appt Date into Site Survey & Drawings, beside legacy Site Visit Date.
- No new fields created. Both optional at layout level. Save and Close completed; Field Listing verified each now includes Deal Pipeline as well as its previous layouts.
- This does not sync the two visit date fields, change template mapping, or complete the separately named ISF Site Visit Date Sync action.
- Rollback: remove only these two fields from Deal Pipeline back to Unused Items; retain the underlying fields and their other layouts/data. No rollback performed.

### T03 saved unpublished Blueprint draft
- Published Blueprint remains 1287721000002448077. Saved draft is 1287721000004162041, shown with an asterisk in Blueprint list and a Published link in its editor. Publish/Republish was not pressed.
- Discovery draft transition 1287721000004162044: retained mandatory Requirement Notes; added mandatory Contact Name, Mobile Number, Sport Type and Site Location. These saved fields were reopened and verified. This is the normal phone path only; controlled email-only exception is not built, so do not publish as the complete contact policy.
- Quote Sent draft transition 1287721000004162046: retained mandatory Contact Name, Quotation Sent Date and Quotation Amount; added mandatory Quotation Reference; changed Whatsapp Number and WhatsApp Opt In from mandatory to optional. No consent value was selected or manufactured. Messaging eligibility must continue to be enforced separately by a verified sender path.
- Quotation Amount validation: >= 0.01; alert "Enter an approved quotation amount greater than zero." Saved, reopened and verified. An earlier attempt using > 0 did not persist; it was corrected before the final saved verification. Do not report the failed attempt as the final configuration.
- Order Confirmation: retained mandatory Negotiation Notes; added mandatory Contact Name, Contract Value, Scope Summary and Quotation Reference. Latest reopen verifies the mandatory customer-acceptance checklist (evidence plus scope/revision/price/terms) and Contract Value `>= 0.01` validation with the saved positive-value alert. Automatic evidence verification is not claimed.
- Existing active workflow `Process Step → Order Confirmation` supplies the `order_confirmation` router event and the existing `Verify customer order and execution handoff` task. No Blueprint duplicate was added. No transition was executed; no Deal was advanced/reset; no message, Flow test/debug, or trigger replay was run.
- Draft acceptance checks: persistence of field requirements/optional states, quotation criterion, acceptance checklist, and Contract Value criterion passed. Missing/invalid/valid record tests, roles, controlled email-only route, sender exclusivity and runtime behavior remain untested or blocked. T03 is not complete or live.
- Rollback before release: leave published version in place; discard/revert only the documented draft edits through the supported draft interface after checking for later user edits. Do not overwrite later work or delete the published process.

### Test dependency found during prior continuation
- Active TEST WA Hybrid Orchestrator now visibly contains Updated module entry, Fetch module entry, If else, Send template message, Update module entry and Create module entry nodes; its description still says the native CRM test rule sends the template. Direct-send parameters/condition branch and sender exclusivity remain unverified. Presence of the node is not proof of delivery or duplicate sends.
- No-send/no-replay/no-advance boundary remains in force while the test path is reconciled. Do not enable the old quote-test Flow or change the protected live router to compensate.
- No field named Exception was found in the Deal field-name search; this is not proof that no exception logic exists in other modules/functions.


## T01 — completed control matrix
Commercial Stage stays independent of operational activity. Six lifecycle groups are derived summaries. Optional and parallel work is tracked against the same Deal, with owned Tasks and verified completion evidence rather than one forced linear sequence.
Sales = Sales Executive. Ops = Project Execution & Accounts. MD = approval/exception decision maker.

| # | Activity / group | Action owner | Prerequisites and required evidence | Next work / notification | Exception / optional treatment |
|---|---|---|---|---|---|
| 1 | Lead Logged / Qualified opportunity | Sales | Qualified Lead; duplicate/customer match; Account/Contact; owner; usable contact route | Assigned Sales discovery task | Unqualified enquiries stay Leads; controlled email-only exception |
| 2 | Discussion & Brochure Sent / Qualified opportunity | Sales | Sport, courts/area, site, requirements; actual brochure sharing if performed | Next agreed Sales action | Brochure optional; reuse Lead requirements |
| 3 | Price Shared / Proposal & negotiation | Sales | Scope assumptions, amount, actual share evidence | Quote/follow-up task if needed | Preliminary pricing optional |
| 4 | Quote Sent / Proposal & negotiation | Sales | Approved Quote/revision, amount, date and actual sharing channel/evidence | One follow-up task | Email/manual sharing allowed without WhatsApp consent; messaging separately gated |
| 5 | Follow-up / Proposal & negotiation | Sales | Actual outcome; next agreed date where applicable | Replace/reschedule owned follow-up | Repeatable; close stale reminders; no automatic last-attempt inference |
| 6 | Office Visit / Meeting / Proposal & negotiation | Sales | Agreed date, location, meeting owner; outcome after visit | Meeting and outcome task | Optional; parallel with quotation |
| 7 | Order Confirmation / Order confirmed | Sales | Customer acceptance, agreed scope/value/terms, execution assignee | Ops handoff task; acknowledgement visible to Sales | Customer rejection/changes return to negotiation without invented acceptance |
| 8 | Advance Payment Requested / Order confirmed | Ops; MD where policy applies | Accepted order, correct amount/version, due date and required approval | Accounts collection task; eligible request message | Do not assume fixed 10000 is correct; preserve current rule until policy verified |
| 9 | Advance Payment Received / Order confirmed | Ops | Actual amount/date/reference/mode, verified receipt and verifier | Preparation task; eligible receipt notification | Partial/overpayment tracked; never infer receipt from approval |
| 10 | Site Visit Scheduled / purpose-dependent | Sales schedules; Ops attends | Agreed appointment, site/access, visit owner and purpose | One owned visit task/meeting | Pre-sale and post-order visits allowed; reschedule cancels stale work; named date-sync change remains separately gated |
| 11 | Schedule Shared / Project preparation | Ops | Agreed planned dates, execution owner, actual share evidence | Preparation tasks | Revised schedule invalidates stale reminders |
| 12 | Freebies / Samples Prepared / Project preparation | Ops | Promised sample list and readiness | Relevant delivery/design task | N/A with reason when not promised |
| 13 | Design Finalization / Project preparation | Ops | Approved drawing/revision and acceptance evidence | Work-order readiness check | Parallel preparation allowed; affected work waits for approval |
| 14 | Contract Signing / Project preparation | Sales to Ops | Contract Required evaluated; signed document and date when required | Work-order readiness check | N/A only where contract not required; signing remains human |
| 15 | Final Work Order / Project preparation | Ops; MD for exception | Authorised work order, approved scope/design/contract and financial readiness | Procurement/execution tasks | Recorded MD exception where permitted; no silent skip |
| 16 | Material Procurement / Project preparation | Ops | Approved requirement, material readiness/expected date, blockers | Readiness/start task | Partial availability remains visible; no automatic purchase |
| 17 | Project Started / Execution | Ops | Actual start date, assigned executor, work-order/site/material readiness | Progress task; eligible actual-start notification | Start-today template only on actual IST start day |
| 18 | Work In Progress / Execution | Ops | Progress, issues/blockers, next action/owner/due date | Update next owned work | Repeatable; do not resend start message |
| 19 | Project Completed / Execution | Ops | Completion date, inspection evidence, defects and acceptance status | Final billing/handover preparation | Blocking defects prevent unqualified completion; approved exceptions visible |
| 20 | Final Payment Requested / Handover & closure | Ops; MD where policy applies | Correct invoice/version, verified outstanding balance and approval | Accounts collection task | Disputed amounts route to MD; no payment demand from stale amount |
| 21 | Final Payment Received / Handover & closure | Ops | Receipt amount/date/reference, verifier and reconciled balance | Closure-readiness task | Partial/overpayment unresolved; never equate message success with receipt |
| 22 | Handover & Client Satisfaction / Handover & closure | Ops | Handover date/document, customer acceptance, outstanding-item/finance resolution or approved exception | Close resolved tasks; one optional feedback invitation | Feedback optional; no automatic high rating or forced financial closure |

Notification policy: notify assigned user on new responsibility; remind on due work; escalate only after agreed SLA. Customer messages require a verified event, eligible destination/consent/no-opt-out, complete template variables and one duplicate-protected sender. Business completion and message outcome are separate states.

## T02 — canonical data contract
| Data | Source / reuse | Current evidence and remaining action |
|---|---|---|
| Customer | Contact/Account; Lead until qualification | Existing conversion mapping retained; avoid duplicate customers |
| Commercial/project status | Deal Stage / Current Process Step / Lifecycle Summary | Separate commercial and operational progress |
| Action ownership | Task Owner and Related To Deal | Deal Owner remains commercial owner; do not repurpose customer identity fields |
| Phone | Mobile Number for primary call route; Whatsapp Number for eligible messaging destination | Both Phone fields currently listed on Deal Pipeline only; normalisation must preserve valid international numbers |
| Quote | Authoritative Quote/revision plus existing Quotation Amount, Quotation Sent Date, Quotation Reference | Amount/date on Deal Pipeline; Reference on Sales Workspace/Standard only: layout gap |
| Appointment | Existing Site Visit Appt Date (DateTime); legacy Site Visit Date (Date) used by template | DateTime listed on Sales Workspace/Standard only; Date on Deal Pipeline only: layout gap. Adding a field is separate from named ISF Site Visit Date Sync |
| Advance | Advance Amount / Advance Received / Advance Payment Date / Advance Transaction ID / Advance Verified / approval status | Existing fields reusable; verify payment policy and accounting source before enforcement |
| Final receipt | Final Payment Amount / Final Payment Verified plus accounting receipt | Receipt date/reference not established by the Final Payment field search; use authoritative accounting reference or verify reusable field |
| Execution | Execution Start Date / Execution Completion Date / Handover Date | Reuse rather than create duplicate dates |
| Message outcome | WhatsApp Send Log with correlated event/message IDs | Pending/Sent/Delivered/Failed/Unknown remain distinct; staff cannot self-certify delivery |

## Current live evidence from 29 October
- Active Deal Process Blueprint 1287721000002448077 last modified 28 October; Deals/Deal Pipeline/Current Process Step; Continuous.
- Discovery During: Requirement Notes only. Order Confirmation: Negotiation Notes only.
- Quote Sent During: mandatory Quotation Sent Date, Contact Name, Whatsapp Number, Quotation Amount, WhatsApp Opt In.
- Advance Requested During: mandatory Advance Amount with exact 10000 validation.
- Project Started and Final Payment Recieved During panels: no fields configured. This does not establish absence of upstream/other checks.
- Deal Pipeline creation: Contact Name and Whatsapp Number visually optional.
- Progressive disclosure keyed to commercial Stage; observed actions show sections, not per-activity mandatory evidence.
- Validation list: Advance Amount and Contract Value on Standard and Deal Pipeline; no separate phone/contact validation listed.
- Active TEST orchestration relay receives all Deal edits; downstream boundary unknown. Active quotation WhatsApp relay receives all Quote create/edit events; downstream readiness/dedup unknown.
- WA Guarded Quote Sent and Project Started are currently OFF; do not misreport as active duplicates.
- Active intake/SLA rules may overlap; action comparison required before retirement.
- Off legacy Attach Quote PDF variants and Generate Quote Products remain off.
- No production sender/router changed, no message sent, and no customer business record modified during the preceding review.

## Boundaries and definition of done
Use existing production session. Do not edit synced sources/. No real customer Deal changes or duplicate records. Only TEST-DATA Deal 1287721000003658001 is the established business-record test boundary; do not advance/reset or replay/send without the specifically needed authorization. Existing protected live router remains unchanged until replacement testing passes. ISF Site Visit Date Sync retains its separate named approval requirement. General execution approval authorises ordinary reversible configuration work within these boundaries.

Each implementation records original state, exact delta, save/reopen evidence, positive/negative/role checks, pending-schedule treatment and rollback. Never label an enabled Kiosk complete based on its name or a draft description. No background execution or future completion is implied by this tracker.

---

# Historical evidence retained from 23 October
The following is preserved for provenance. Later live evidence above overrides historical status where inconsistent.

# ISF CRM simplification and WhatsApp implementation tracker

23 October 2026, IST. Production organisation 60070586928.

## Current result

Browser access restored in the existing Brave session. Production configuration inspected directly. No production configuration or business records changed in this session. No message sent, event replayed, Deal advanced/reset, or live router altered. This is an audit and implementation specification; it is not a release certificate.

The revised ten-task sequence supplied on 23 October supersedes the older wizard-first sequence. Historical context read in full: ISF_CRM_Wizard_Tasks_and_Prompts.md, version 2.

## Task ledger

| Task | Status | Dependencies / remaining evidence | Changes and rollback |
| --- | --- | --- | --- |
| 1. Audit configuration | In progress; findings below verified in UI | Complete conversion mappings, field permissions, sender exclusivity, native Wizard details and relevant transition rules | Read-only; no rollback required |
| 2. Map 22 activities | Specification prepared below; not implemented | Validate prerequisites against every existing transition and approval | No Blueprint/state changes |
| 3. Reuse fields and define three-role access | Existing profiles/users identified; access design prepared | Field permissions and least-privilege overview visibility must be verified before changes | No permission changes |
| 4. Organisation overview | Not built | Tasks 1–3; current Deals access is Private | No saved view or sharing change |
| 5. Three personal work queues | Not built | Tasks 1–4; inspect existing Workqueue before creating any duplicate queue | No task/queue changes |
| 6. Lead intake/conversion/sales actions | Not changed | Reuse existing enabled Inbound Lead Intake Wizard; verify conversion mappings | No record creation/conversion |
| 7. Operational and approval actions | Not built | Verified transition/approval rules and financial source | No finance or process changes |
| 8. Fourteen core WhatsApp event mappings | Inventory and proposed mapping below | Verify each sender, parameters and event evidence; six additional variants also exist | No template/notification changes |
| 9. Event wiring/logging/reminders | Blocked from enablement | Sender exclusivity, idempotency and outcome correlation unproven; no sends authorised | Live router untouched; test Flow remains OFF |
| 10. Role journey verification/release | Not performed | Prior tasks; tests must fit no-advance/no-reset/no-send boundary | Nothing enabled by this session |

## Verified configuration evidence

Evidence is the visible production UI inspected on 23 October 2026; no customer-record pages were opened. Customer task reminders surfaced automatically and were not investigated. Do not treat their incidental presence as authorised record inspection.

### Blueprint

- Deal Process Blueprint: 1287721000002448077; Deals; Deal Pipeline layout; Current Process Step; Continuous. List last modified 22 October.
- Editor offers Republish and Save as Draft. Neither pressed. Exited with Cancel.
- Move to Site Visit: Before = Record Owner, Add Criteria offered; During = mandatory Site Visit Date; After panel exposes actions but listed no configured action for this transition.
- Connected canvas contains the 22 states in the mapping below. Available but unconnected states include Advance Payment Pending MD Approval, Material Dispatched, Material Delivered, Handover Scheduled and Feedback Request. Their presence is not an implemented route.

### Roles, profiles and users

| Business role | Existing role / ID | Existing profile / ID | Active user |
| --- | --- | --- | --- |
| Sales Executive | Sales Admin / 1287721000000031154 | ISF Sales Rep - Restricted / 1287721000003573180 | PUSHPARAJ PUSHPARAJ |
| Project Execution & Accounts | Accounts and Project Engineer / 1287721000003199275 | ISF Accounts Project - Restricted / 1287721000003573432 | Test user 2 Accounts |
| MD | MD / 1287721000000031151 | Administrator / 1287721000000031157; user screen labels Super Admin | Mungra Manendra |

Additional existing roles: Project Engineer 1287721000000779001; Accounts 1287721000003199215. Additional profiles: Standard, Sales Admin, Engineer. Three active users shown. Do not rename roles merely to match user-facing labels.

Sales profile: Leads/Contacts/Deals/Tasks/Meetings/Calls/Quotes View/Create/Edit; Accounts View; Reports/Analytics View; Invoices and Purchase Orders disabled; Messages View/Reply; Convert enabled for Leads, Quotes, Sales Orders. View All Records, Modify All Records, Manage Automation and User Management disabled.

Accounts Project profile: Leads disabled; Contacts View; Accounts/Deals View/Edit; Tasks/Meetings/Calls View/Create/Edit; Quotes View; Sales Orders View/Edit; Purchase Orders View/Create/Edit; Invoices View/Edit; Messages disabled.

Both restricted profiles currently permit WhatsApp Send Logs View/Create/Edit/Delete. Sales also has import/export and several bulk tools scoped to Send Logs. Profile descriptions are not proof of effective restrictions. Proposed correction: reserve log mutation for the automation/admin identity; staff see only necessary read-only outcome information. Not applied.

Default organisation access: Leads, Contacts, Accounts, Deals, Tasks, Meetings, Calls and WhatsApp Send Logs = Private. Sharing Rules tab shows the landing screen and Create Sharing Rule, with no rules listed. Views alone cannot create cross-owner visibility. Do not set Deals public as a shortcut.

### Reusable fields/layouts

Deals: Deal Pipeline layout 1287721000000594218 and Standard 1287721000000000173.

- Separate Stage and Current Process Step picklists both exist. Keep commercial Stage independent.
- Deal Next Action (Single Line), Deal Owner (Lookup), Stage Entered On (DateTime), Stage Age (Days) (Formula).
- Advance Amount, Advance Received (Currency); Advance Due Date, Advance Payment Date, Advance Requested Date (Date); Advance Payment Mode (Pick List); Advance Transaction ID (Single Line); Advance Verified (Boolean); Advance Payment Approval Status and Rejected Status (Pick List).
- Balance Due (Formula); Contract Value, Final Payment Amount (Currency); Final Payment Approval Status/Rejected Status (Pick List); Final Payment Verified (Boolean).
- Execution Start Date, Execution Completion Date, Expected Start Date, Handover Date, Follow-up Date (Date).
- Contract Required, Contract Signed, Feedback Submitted (Boolean); Agreement Date, Contract Sent Date, Contract Validity Date (Date); Layout Drawings and Site Photos (File Upload).
- Site Location, Site Details (Single Line); Site Study Notes and Site Visit Remarks (Multi Line).
- Site Visit Date = Date on Deal Pipeline. Site Visit Appt Date = DateTime on Standard only. Do not assume the latter is available in the live Blueprint layout. ISF Site Visit Date Sync remains separately approval-gated by exact name.
- Last WA Stage Sent exists on both layouts. Last WhatsApp Sent Time and Last WhatsApp Template were listed on Standard only.
- Search Project returned only Project Requirements on Standard; search Owner returned Deal Owner plus customer owner identity/address fields. No execution-user assignment field was established by those searches; inspect remaining fields before adding one.

Leads: Lead form 1287721000000452379 and Standard 1287721000000000167. Lead form layout contains customer identity, Mobile Number, Whatsapp Number, Email, Lead Source/Status/Owner, sport/site/courts/budget/Requirement Notes, follow-up/Next Action and technical automation section. Converted Account/Contact/Deal lookup fields exist. Conversion mapping inspection is separate; their existence alone does not prove mappings are correct.

### Kiosks and native Wizards

Important correction to prior handoff: the list shows 17 ISF Kiosks with checked status switches, plus `test` and ISF Work Progress explicitly labelled Draft. Schedule Visit detail offers Edit/Clone/Deactivate/Delete. Thus the 17 cannot be represented as unpublished merely because descriptions say draft.

Schedule Visit 1287721000003773613 displays Start → 1 - Appointment → 2 - Review appointment → End; no record/update/message node on its canvas. View Associations dialog shows Associate for Home Page, Setup Page, Custom Buttons, Record Detail View, Blueprint, Canvas, Mobile Canvas and Canvas Home View. No binding was shown there. No test run performed this session and no status changed.

| Kiosk | ID | List status observation |
| --- | --- | --- |
| ISF Schedule Visit | 1287721000003773613 | Checked switch; Deactivate menu verified |
| ISF New Enquiry | 1287721000003803179 | Checked switch |
| ISF Discovery | 1287721000003803751 | Checked switch |
| ISF Price Shared | 1287721000003804317 | Checked switch |
| ISF Quote Shared | 1287721000003804875 | Checked switch |
| ISF Follow Up | 1287721000003805433 | Checked switch |
| ISF Office Meeting | 1287721000003805991 | Checked switch |
| ISF Confirm Order | 1287721000003806549 | Checked switch |
| ISF Request Advance | 1287721000003807107 | Checked switch |
| ISF Verify Advance | 1287721000003807665 | Checked switch |
| ISF Share Schedule | 1287721000003808227 | Checked switch |
| ISF Samples Ready | 1287721000003808791 | Checked switch |
| ISF Approve Design | 1287721000003811351 | Checked switch |
| ISF Signed Contract | 1287721000003811909 | Checked switch |
| ISF Final Work Order | 1287721000003812467 | Checked switch |
| ISF Procurement | 1287721000003813027 | Checked switch |
| ISF Start Work | 1287721000003813591 | Checked switch |
| ISF Work Progress | 1287721000003742532 | Draft |

Native Wizards list: Inbound Lead Intake (Leads / Lead form; Administrator, Standard and three others; enabled; modified 16 October) and Quote Builder New (Quotes / Final Quote Layout; Administrator only; enabled; modified 23 October). No changes made to either. Inbound Lead Intake editor initially remained loading; its details still require verification.

### WhatsApp channel, rules and Flow

Business Messaging: WhatsApp for Business integrated and active. India Sports Infra sender +917338858989; new inbound sender records configured as Leads. Available Credits shown as 1; this is a UI observation, not a conclusion about provider capacity or pricing.

Process Step → Site Visit Scheduled, rule 1287721000002144410: ACTIVE; trigger Current Process Step modified to Site Visit Scheduled; condition Email Consent Verified selected. Four instant actions: set WA_Event site_visit_scheduled; Site Visit Scheduled - Client Email; task Confirm site visit and brief Project Engineer; meeting Client Meeting with Site Location merge. Saving a new stage action can invoke these existing effects; none invoked here.

WA Guarded - Site Visit Scheduled, rule 1287721000003186107: ACTIVE; same stage trigger; conditions WhatsApp Opt In selected, Whatsapp Number not empty, Deal Name does not contain TEST-DATA; action Deal - Site Visit WhatsApp. Test exclusion verified and unchanged.

Deals_ZohoFlow_ISF WhatsApp Utility Router, rule 1287721000003665094: ACTIVE / Read Only; create-or-edit; all Deals; one webhook with the router name. Downstream router logic/exclusions were not established from this CRM relay screen. Do not claim the relay itself excludes TEST-DATA, and do not alter it.

Workflow inventory also shows active WA Guarded Quote Sent, Order Confirmation, Project Completed, Handover and Final Payment Requested; WA Guarded Project Started OFF; Advance Payment Approved WhatsApp ACTIVE. Active TEST WA Hybrid - Site Visit 1287721000003760183 and TEST WA Relay – Site Visit Request 1287721000003760201. Their complete conditions/actions still require inspection. Existing stage and SLA task rules are present; do not add duplicate reminders based on names alone.

Existing Flow `test_wa_hybrid_orchestrator_quote_sent`: OFF; created 22 October 11:06 AM; last saved displayed 11:11 AM. Summary description still refers to Site Visit, but actual condition is Deal Name contains TEST-DATA AND WA Send Trigger equals request_quote_sent AND WhatsApp Opt In is true AND Last WA Stage Sent does not contain quote_sent. Canvas: Updated module entry → If else → Update module entry → Create module entry. No Send Log lookup node shown. Summary reports zero task executions/no recent executions for last seven days. Last-stage string check does not establish an atomic duplicate claim or outcome correlation. No run/debug/save/enable performed.

## Proposed 22-activity mapping (Task 2 specification)

Existing state names below are verified; owners, prerequisites and completion rules are the proposed simplification, not verified live rules. No linear reordering or path removal has been applied. Sales = Sales Executive; Ops = Project Execution & Accounts.

| # | Existing activity | Lifecycle group | Action owner | Prerequisite / completion evidence | Optional or parallel treatment |
| --- | --- | --- | --- | --- | --- |
| 1 | Lead Logged | Qualified opportunity, legacy entry only | Sales | Lead qualified; duplicate resolution; existing customer linked at conversion | New unqualified enquiries remain Leads; do not create a Deal just to log intake |
| 2 | Discussion & Brochure Sent | Qualified opportunity | Sales | Requirements recorded once; brochure sharing evidenced if performed | Requirements can pre-exist in Lead; brochure optional |
| 3 | Price Shared | Proposal & negotiation | Sales | Scope assumptions and actual price-sharing evidence | Optional preliminary price; do not force before formal quotation |
| 4 | Quote Sent | Proposal & negotiation | Sales | Approved quote reference/revision; actual sharing evidence | Follow-up remains independent |
| 5 | Follow-up | Proposal & negotiation | Sales | Outcome; next due date only when needed | Repeatable action, not lifecycle regression |
| 6 | Office Visit / Meeting | Proposal & negotiation | Sales | Agreed date/owner; meeting outcome | Optional; parallel with quote/site clarification |
| 7 | Order Confirmation | Order confirmed | Sales | Customer acceptance and agreed scope/terms; operational handoff owner | Do not infer acceptance from a generic reply |
| 8 | Advance Payment Requested | Order confirmed | Ops; MD approval decision | Correct approved amount/version and order reference | Separate approval from request and customer message |
| 9 | Advance Payment Received | Order confirmed | Ops | Verified bank receipt, amount/date/reference/verifier | Partial payments and exceptions must remain visible |
| 10 | Site Visit Scheduled | Qualified opportunity or Project preparation, purpose-dependent | Sales schedules; Ops carries visit task | Agreed date, site access, assigned owner; reuse verified field mapping | Allow pre-sale survey and post-order visit without moving commercial Stage backwards |
| 11 | Schedule Shared | Project preparation | Ops | Agreed dates/owner and actual sharing | Coordinate with design, contract and material readiness |
| 12 | Freebies / Samples Prepared | Project preparation | Ops | Promised item list ready, or not applicable | Optional; parallel preparation |
| 13 | Design Finalization | Project preparation | Ops | Approved drawing/revision and evidence | Parallel with contract/finance when policy permits; required before affected work |
| 14 | Contract Signing | Project preparation | Sales hands to Ops | Existing signed document reference if Contract Required | Optional only where Contract Required is false; no automated signing |
| 15 | Final Work Order | Project preparation | Ops | Approved scope/design/contract references and authorised work order | Release gate for procurement/execution; preserve MD exceptions |
| 16 | Material Procurement | Project preparation | Ops | Approved requirement and readiness/expected date | Track status; do not place a purchase automatically |
| 17 | Project Started | Execution | Ops | Actual start and ready-to-start prerequisites | Started-today message only on actual local start day |
| 18 | Work In Progress | Execution | Ops | Progress, issues, next owned task/date | Repeatable; do not resend start notification |
| 19 | Project Completed | Execution | Ops | Inspection/completion evidence and no blocking unfinished items | Handover remains distinct |
| 20 | Final Payment Requested | Handover & closure | Ops | Approved invoice and verified balance; invoice sharing evidence | Exception route to MD for discrepancy |
| 21 | Final Payment Received | Handover & closure | Ops | Verified receipt/reference and reconciled balance | Partial/overpayment exceptions; no invented receipt template |
| 22 | Handover & Client Satisfaction | Handover & closure | Ops | Handover/acceptance evidence and approved exceptions | Feedback optional and separate from financial settlement |

The six lifecycle groups are a summary of shared Deal/project data. Commercial Stage remains commercial; Current Process Step remains the existing activity mechanism during migration. A single current-step field cannot itself represent all parallel activity completion. Use native owned Tasks associated with the same Deal, with independently verified completion gates. Do not make staff update duplicate status fields manually.

## Access and interface specification (not saved in CRM)

- Organisation overview: shared project/opportunity summary using the same Deal IDs; show commercial Stage, lifecycle summary, Current Process Step, responsible owner, next action/due date and exceptions. Keep unqualified Leads out. Verify field visibility before sharing; customer identity documents and finance detail must not be exposed just because an overview is requested.
- My Work: native Tasks assigned to current user, open status; sections due/overdue, waiting and approvals where supported. Related To points to the authoritative Deal/Lead. Reuse existing Workqueue if it meets these conditions. Task owner is action responsibility; Deal Owner remains commercial responsibility.
- Sales: assigned Lead qualification/conversion, discovery, quotes, negotiation and order handoff. Reuse restricted Sales profile and existing intake Wizard.
- Ops: execution and verified finance updates for handed-off projects; use existing restricted Accounts Project profile. MD decisions remain separate from Ops verification.
- MD: approvals, exceptions, overdue work and derived totals; no second manual financial total store.
- Cross-owner overview visibility is not yet configured. Prepare the narrowest read-only sharing/summary alternative after checking field permissions. A material expansion of sensitive CRM access requires action-time confirmation under the browser policy, even though implementation work is generally authorised. No confirmation is requested for read-only inspection or ordinary drafts.

## Fourteen core template event map (inventory verified; wiring not verified)

All 14 below appear Approved in CRM and use the existing sender. Lead merge fields must stay on Leads. Actual template content governs required evidence. No customer sends authorised.

| Template | Module | Business event / eligibility evidence |
| --- | --- | --- |
| isf_lead_not_reached | Leads | Actual unsuccessful call; ask preferred time; no automatic last-attempt inference |
| isf_lead_callback_confirm | Leads | Customer-agreed callback time saved; correct Preferred Time to Call merge |
| isf_lead_last_attempt | Leads | Verified final outreach policy threshold; pause calls after final attempt |
| isf_brochure_share | Leads | Requested/discussed brochure actually available; correct sport/media |
| isf_requirement_confirm | Leads | Discussion captured sport/courts/site and customer confirmation requested |
| isf_deal_quote_sent | Deals | Approved quotation actually shared, reference/revision retained |
| isf_deal_site_visit | Deals | Agreed appointment; correct Site Visit Date; named sync approval unresolved |
| isf_deal_order_confirmed | Deals | Customer order acceptance evidenced |
| isf_deal_advance_request | Deals | Current amount approved under existing authoritative process |
| isf_deal_advance_received | Deals | Actual receipt verified by Accounts |
| isf_deal_work_started | Deals | Actual work starts today in IST; readiness gates passed |
| isf_deal_work_completed | Deals | Work completion verified; handover next |
| isf_deal_final_payment | Deals | Invoice/balance checked and final payment request authorised |
| isf_deal_handover_feedback | Deals | Eligible handover completed; one feedback invitation |

Six additional approved templates: isf_lead_welcome_brochure_v1, isf_lead_welcome_v4, isf_lead_afterhours_v2, isf_lead_welcome_v3, isf_lead_welcome_afterhours, isf_lead_welcome_v2. The Notifications inventory contains 17 actions, including three welcome actions. Do not enable all welcome variants or assume 20 templates mean 20 business events.

## Event wiring acceptance and rollback

For each event separately: verify sender inventory; record event evidence/version; atomic unique claim before invoking the single sender; preserve Pending/Accepted/Sent/Delivered/Failed/Unknown distinctions using actual provider evidence; correlate request/log/message IDs; do not retry unknown outcomes. Completion/rescheduling must cancel stale reminders and next tasks must be deduplicated against existing workflow tasks. A Last WA Stage Sent string alone is insufficient proof of these properties.

Do not switch on this Flow or disable a production sender to compensate for missing evidence. Each later change must record the original state, exact delta, verification, and reversal before activation. Existing router remains untouched. No business-state test requiring Deal progression is allowed under current boundaries.

## Resume boundaries

### Additional audit evidence

Lead Conversion Mapping for Lead form explicitly maps Account = Standard, Contact = Standard, Deal = Deal Pipeline. Verified rows: Budget → Deal Budget; Follow-up Date → Deal Follow-up Date; Email → Contact Email; Lead Source → Contact Lead Source and Deal Lead Source; Mobile Number → Deal Mobile Number, with Contact and Account None; Next Action → Deal Next Action; Number of Courts → Deal Number of Courts; Other Sport type → Deal Other Sport Type; Preferred Time to Call → Deal Preferred Time to Call; Requirement Notes → Deal Requirement Notes; Site Location → Deal Site Location; Sport Type → Deal Sport Type; Whatsapp Number → Account Phone, Contact Phone and Deal Whatsapp Number; WhatsApp Opt In → Deal WhatsApp Opt In. Company / Organization and Contact Person Role are None across targets. Lead Owner also shows None in the mapping table; actual ownership behavior still needs separate verification. No mapping saved, no conversion performed. Existing-customer matching and required Account Name behavior cannot be certified by this field table alone.

TEST WA Hybrid - Site Visit 1287721000003760183: ACTIVE; WA Send Trigger modified to site_visit_scheduled, repeated whenever modified; Deal Name starts with TEST-DATA, opt-in selected, number not empty. Actions: TEST WA Trigger Reset - Sent field update and Deal - Site Visit WhatsApp notification. Its criteria are name-prefix based, not exact Deal ID. Do not invoke it under the current no-send/no-replay boundary. The field-update label does not establish provider acceptance, sending or delivery; action order and provider callback correlation remain unverified.

Only TEST-DATA Deal 1287721000003658001 is authorised for business-record inspection/testing; do not advance/reset it. No other customer records, no new duplicate customers, no WhatsApp sends/resends or trigger replay. ISF Site Visit Date Sync requires separate explicit approval by that exact name. Synced sources/ remain read-only.

