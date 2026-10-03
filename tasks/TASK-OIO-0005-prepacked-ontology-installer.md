# TASK-OIO-0005 — Ship the prepacked OIO issue-log ontology and adopter installer

<!-- continuity:task {"acceptance":["A versioned, machine-readable OIO default ontology and readable Markdown map ship in this repository, limited to observational and operational issue-log filing; adopter extensions are namespaced and validated without redefining protected OIO concepts","A deterministic installer installs the pinned OIO default, adopter extension scaffold, local issue form, and triage into one explicitly selected target repository; it refuses ambiguous/outside targets and unmanaged conflicts, preserves adopter-owned data, and is safe to rerun","A disposable local Git repository can be adopted from scratch, checked using its installed OIO CLI, and reinstalled; assertions prove only the explicit target's documented OIO-owned paths changed","Automated tests cover ontology/schema validation, extensions, priority path parsing and ordering without floating point, installer path confinement, idempotence, preservation, and conflict refusal","OIO's own stack pins, CGM adapter, ACS/PCM instructions, and CI checks are reconciled with the current train proposal and pinned adoption contracts without writing to sibling repositories","All required local validators and tests pass; changes are tracked on this branch and delivered through the required reviewed PR, with GitHub task receipts and a verified merge"],"depends_on":[],"goal":"Define and ship a prepacked default issue-log ontology plus a safe, tested installer that lets adopter repositories extend OIO's observational and operational filing vocabulary without handing OIO authority over adopter-owned data","id":"OIO-0005","issue_url":"https://github.com/Pukujan/observational-issue-ops/issues/18","next_action":"Commit the validated OIO-only implementation, publish the synchronized checkpoint receipt, and open a reviewed PR; keep ACS runtime readiness explicitly unclaimed","owner":"owner/Pukujan","priority":"P5","protocol_version":"0.1.0-draft","schema":"project-continuity.task.v1","status":"active","why":"OIO's form and triage are published, but there is no installer or adoption harness; adopters cannot automatically receive the same definitions and extensions without manual copying, while OIO's own consumed stack has drifted from current certified integration contracts"} -->

- Status: active
- Owner: owner/Pukujan
- Priority: P5
- Depends on: none

## Goal

Ship an OIO-owned, prepacked issue-log ontology and a safe installer that adopters can run against an explicitly selected repository. The installer must give every adopter the same OIO core definitions while letting that adopter extend vocabulary and project priority concepts without replacing the core.

## Why

OIO currently publishes a form and triage workflow but no installer or disposable adopter test. Agents cannot reliably discover a single default ontology, and adopters have to copy and maintain intake behavior themselves. OIO's own manifest also lags the certified CGM version required by the current ACS hot-load contract.

## Scope and boundaries

- In scope: OIO's default ontology, record and extension schemas, installer, generated/adopter-local form and triage artifacts, tests using disposable local Git repositories, documentation and OIO's own stack-contract reconciliation.
- Ontology scope: observational and operational issue-log filing only. It does not define general implementation authorization, task/PR progression, deployment, or release policy.
- The target repository owns its issue history and extension. Installation or validation must not write anywhere except the explicitly selected target and only within documented OIO-managed paths. OIO, ACS, CGM, and PCM are protected repositories: agent issue submission or file writes require explicit human direction naming the repository and action.
- Out of scope: edits to PCM, ACS, CGM, Octo DB, ACS/CGM/PCM repositories, or any adopter repository; changes to other repositories' protection/settings; automatic network updates during installation.
- Canonical dependency facts from the audit: PCM 0.6.0 at `4e2385474b4af9249ca009cbdcb38c4498932475`; CGM 0.5.12 at `6831f91e165b62d719c05eb492f7375fa932b560`; ACS HOTLOAD 0.1.0 at source commit `3a381eba11c6262c702f5d696878c371342e859a`. The current train file has `status: proposed`; it is not final authority. OIO validates PCM and CGM but lacks ACS runtime artifacts and a passing hotload checker.
- Priority is represented as a project-scoped ontology concept and hierarchical string path, never a floating-point value. Roots 1–100 and deeper numeric subdivisions are supported without a fixed depth; a defined parent may be assigned directly.

## Human outcome

A project can install a pinned OIO release into a disposable or real target, receive the default observational/operational issue vocabulary and intake files automatically, add a validated project ontology overlay, and rerun or upgrade without overwriting project-owned data or touching another repository.

## Verification

Use deterministic unit and integration tests. Create a disposable local Git repository and compare its tracked/untracked paths before and after installation. Verify fresh installation, repeat installation, valid extension, invalid/colliding extension rejection, modified-managed-file conflict, and explicit-target confinement. Run OIO's PCM, CGM, stack-train consistency, YAML/JSON Schema, secret, and installer checks. GitHub test-repository changes are excluded unless separately authorized.

## Related records

- Leaf owning issue: [#18](https://github.com/Pukujan/observational-issue-ops/issues/18). Parent: [#17](https://github.com/Pukujan/observational-issue-ops/issues/17). Dependencies: none.
- Primary writer / branch / source issue revision / as-of status: Codex / `task/OIO-0005-default-ontology-installer` / owner direction in issue comments `5965428727` and `5965431511`, implementation scope on #18, and parent correction `5965756774` / active.
- PCM, ACS, and CGM adoption audit: read-only review completed on OIO revision `5efa7eb4004f984e1529067bfc4a66df815c11ed`; findings are recorded on the live issue.

## Checkpoint log

- 2026-10-03: task scoped on leaf issue #18 (parent #17) and branch created. Read-only audit confirmed PCM validation passes but GitHub review/admin enforcement is incomplete; CGM pin was behind the current train proposal and its required filename legend was missing; ACS was reference-only and lacks OIO-side runtime artifacts. Local changes now update CGM to 0.5.12 and add the filename legend, repair PCM worktree guidance, define and package the default ontology, add a fail-closed installer and triage review lanes, and test crash recovery/path confinement. Validation evidence and delivery status will be appended after completion.
- 2026-10-03: completed the OIO-only implementation and adoption audit. OIO pins PCM 0.6.0 and CGM 0.5.12; PCM continuity/preflight, the pinned CGM adapter validator, and release-train manifest checker pass. ACS HOTLOAD 0.1.0 remains a source reference only because OIO has no runtime assignments/leases/watchdog/claim flow and no passing ACS hotload check. The installer was exercised against a fresh disposable Git repository and its installed `--check` passed. All 33 unit tests pass, including path confinement/recovery, priority/scaffold behavior, and durable body-bound GitHub account attestation, revocation, same-second reapplication and cross-run reuse. YAML, JSON Schemas, Python compilation, secret scan and `git diff --check` pass. Sol's independent read-only review of PR #19 head `341d224` found no remaining concrete blocker. PR #19 is open and GitHub `gates` passed at that head; no sibling repositories were written. Awaiting human review and delivery decision.

### 2026-10-03 06:17:06 UTC — Codex

<!-- continuity:checkpoint {"agent":"Codex","blocked":[],"changed":["OIO installer, ontology, schemas, issue workflow/form, governance docs, CGM pin/legend, task/checkpoint, and tests."],"completed":["Built and validated the OIO-only prepacked observational/operational ontology, default 1\u2013100 project priority scaffold, confined adopter installer, issue form, triage, account-bound durable attestation, and PCM/CGM/ACS adoption documentation."],"decisions":["No writes to PCM, ACS, CGM, Octo DB, or adopter repositories. Human-origin queue rank is earned by mapped GitHub account attestation bound to issue event and exact body digest; edited body requires re-attestation."],"evidence":["33 unit tests passed; fresh disposable Git adopter installation and installed --check passed; continuity validate/preflight passed; CGM 0.5.12 adapter validator and stack-train manifest checker passed; YAML/JSON Schema/Python syntax/secret scan/diff checks passed. ACS HOTLOAD remains reference-only, not runtime-ready."],"next_action":"Open reviewed PR for OIO-0005, publish issue receipt and parent progression, then verify CI and review before delivery.","protocol_version":"0.1.0-draft","schema":"project-continuity.checkpoint.v1","task_id":"OIO-0005","timestamp":"2026-10-03T06:17:06Z"} -->
<!-- continuity:checkpoint-operation {"payload_sha256":"3badffb8caa1b5f75e43c9b213142435bde42939dd02a7948603aa45d7712f13","request_id":"068b6a7527814f70bbae4b135ebff8bf","schema":"project-continuity.checkpoint-operation.v1","task_id":"OIO-0005"} -->

Completed:
- Built and validated the OIO-only prepacked observational/operational ontology, default 1–100 project priority scaffold, confined adopter installer, issue form, triage, account-bound durable attestation, and PCM/CGM/ACS adoption documentation.

Evidence:
- 33 unit tests passed; fresh disposable Git adopter installation and installed --check passed; continuity validate/preflight passed; CGM 0.5.12 adapter validator and stack-train manifest checker passed; YAML/JSON Schema/Python syntax/secret scan/diff checks passed. ACS HOTLOAD remains reference-only, not runtime-ready.

Decisions:
- No writes to PCM, ACS, CGM, Octo DB, or adopter repositories. Human-origin queue rank is earned by mapped GitHub account attestation bound to issue event and exact body digest; edited body requires re-attestation.

Changed:
- OIO installer, ontology, schemas, issue workflow/form, governance docs, CGM pin/legend, task/checkpoint, and tests.

Blocked/uncertain:
- none

Next:
- Open reviewed PR for OIO-0005, publish issue receipt and parent progression, then verify CI and review before delivery.

### 2026-10-03 06:20:35 UTC — Codex

<!-- continuity:checkpoint {"agent":"Codex","blocked":[],"changed":["Synchronized CURRENT and OIO-0005 task projections with PR/check/review status."],"completed":["Published OIO-0005 PR #19 and verified its required gates pass at the tested source head; Sol completed a read-only review with no remaining concrete blocker."],"decisions":["Keep PR open for human review/delivery decision; no auto-merge or sibling-repository writes."],"evidence":["PR #19 gates passed at 341d224dbce98576a3a67f095b73288ec2e849a2; independent review by Sol of that exact PR head confirmed the prior authorization, revocation, event-ordering, and cross-run durability findings are resolved. All 33 tests and local validators passed."],"next_action":"Publish this checkpoint receipt to leaf #18 and parent #17, then await human direction on PR delivery.","protocol_version":"0.1.0-draft","schema":"project-continuity.checkpoint.v1","task_id":"OIO-0005","timestamp":"2026-10-03T06:20:35Z"} -->
<!-- continuity:checkpoint-operation {"payload_sha256":"27030055e6e7217478a0d9e657206480c4ca7fca29abe03eada968bdf97b1a4f","request_id":"ba17b7a4d00f474aab56782f7f6d7319","schema":"project-continuity.checkpoint-operation.v1","task_id":"OIO-0005"} -->

Completed:
- Published OIO-0005 PR #19 and verified its required gates pass at the tested source head; Sol completed a read-only review with no remaining concrete blocker.

Evidence:
- PR #19 gates passed at 341d224dbce98576a3a67f095b73288ec2e849a2; independent review by Sol of that exact PR head confirmed the prior authorization, revocation, event-ordering, and cross-run durability findings are resolved. All 33 tests and local validators passed.

Decisions:
- Keep PR open for human review/delivery decision; no auto-merge or sibling-repository writes.

Changed:
- Synchronized CURRENT and OIO-0005 task projections with PR/check/review status.

Blocked/uncertain:
- none

Next:
- Publish this checkpoint receipt to leaf #18 and parent #17, then await human direction on PR delivery.

## Handoff

Read PROJECT → CURRENT → this task → minimum relevant spec. Verify the live issue before resuming. Checkpoint before stopping.
