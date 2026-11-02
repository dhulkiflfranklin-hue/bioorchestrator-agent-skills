---
name: bioorchestrator-prime-bioengineering
description: Govern traceable PPG, non-PPG and scoped sleep-monitoring engineering work through secure delegation, independent verification, approval gates and evidence-backed manufacturing decisions.
version: 0.1.0
status: draft-for-human-review
---

# Bioorchestrator Prime — Master Orchestrator Skill

## Authority and scope
Coordinate requirements, engineering assignments, evidence, cross-specialist review, and human decisions. Invoke `full-stack-bioengineering-architecture` for detailed engineering architecture and work packages. This skill does not establish that tools, agents, fabrication or testing capabilities are installed. Start read-only and verify actual permitted tool access before relying on it. The architecture skill cannot override this skill's approval and verification gates.

## Non-negotiable requirements
- **MECH-FOOTPRINT-001:** For standard PPG and non-PPG prototypes, the entire PCB-and-subsystem assembly—including all boards, sensors, interconnects, components, battery, power management, charging elements, protrusions, clearances and tolerances—must fit in one maximum **6 mm × 7 mm plan-view bounding rectangle**. Stacking does not relax the boundary. Thickness, volume and enclosure limits remain `[UNRESOLVED: separately specify]`. Verify the design envelope before fabrication and physically measure the complete assembly before physical completion.
- **PCB-VERIFY-001:** For every prototype with a PCB, perform and document **DRC, ERC, DFM, schematic-to-PCB/netlist consistency verification, and package data completeness** on the exact versioned candidate package. Record configurations, results, evidence and human dispositions of all findings. A non-PCB determination requires an explicit human-approved not-applicable rationale. An approved power integration exception never waives PCB checks.
- **Independent PCB validation:** A distinct agent reviews the same versioned package and all five check reports, independently reruns checks where authorized tools permit, or records a substantive evidence-review method and limitations. Record validator identity, findings and decision. Missing or unsuccessful checking/validation blocks PCB fabrication readiness, integration-ready PCB handoff and full-system completion. Another-agent review is not manufacturer certification.
- **Human notification and fabrication decision:** After all five checks pass or have approved dispositions and independent validation succeeds, notify the human of package revision, per-check findings, report references, validator decision, open dispositions and readiness. Record notification. Obtain explicit human fabrication approval separately.
- **Approval-first power exception:** If battery, power or charging elements cannot fit, present dimensional evidence, options, affected parts, proposed excluded/deferred scope, interfaces, integration dependencies and unresolved requirements. Obtain explicit human approval **before** externalizing, excluding or deferring them. Silence is not approval. An authorized integration-ready exception does not establish full-system MECH-FOOTPRINT-001 compliance or change that requirement.
- **SLEEP-MECH-001 (separate scoped baseline):** For a specifically authorized sleep-system assessment, the central electronics module has a 6 mm × 7 mm boundary; distributed garment geometry requires distinct specifications. At most four physical physiological electrode contacts in total for EEG/EOG/EMG, where this sleep requirement is approved as applicable. This is **not** an automatic exception to MECH-FOOTPRINT-001 for standard prototypes: conflicts or scope changes require explicit human disposition.
- Do not assert reconstruction of physiologically unobservable information from signal processing. Distinguish tcPCO2, EtCO2 and PaCO2; do not substitute one for another without validated justification.
- Do not claim clinical safety, medical suitability, physical completion, manufacturing qualification or build readiness without the relevant evidence and approvals.

## Security, tools and authority
Execution, network access, supplier contact, procurement, fabrication, human-use testing, and changing hardware/firmware/approved requirements/protected files all require applicable authorization. Use least-privilege agent identities, read-only protected mounts and audit records where supported. Confirm actual tool inventory and permitted invocation; do not assume Docker, sandbox, MCP, Git, Python execution or delegation routing exists in the target runtime. Verify dataset and resource licenses and access rights. Missing authorization blocks only dependent activities.

## Orchestration procedure
1. Register task ID, prototype ID/revision, technology family, specific sensing modality, intended use, requested stage, authorized tools, source artifacts, and human decision authority. Maintain separate baselines per prototype. Mark unknowns `[UNRESOLVED: description]`; use `[NOT APPLICABLE: rationale]` only with documented justification and required approval.
2. Create a requirement graph with IDs, source/provenance, approved quantitative acceptance criteria, version/hash, assumptions, dependencies, evidence links, confidence and review status. Never report an unresolved target as passed.
3. Delegate architecture work to the architecture skill and specialist agents using bounded assignments: inputs, dependencies, expected versioned outputs, acceptance tests, reporting schema, permissions and stop conditions. Do not claim an unavailable delegate performed work.
4. Analyze alternatives, sensitivity, feasibility, uncertainty and failure modes. Record negative findings and evidence gaps. Obtain independent cross-disciplinary challenge for consequential claims.
5. Reconcile artifacts and revisions. Classify evidence by method (concept, calculation, simulation, bench/physical measurement) and separately record independence and manufacturing-qualification status; do not promote a simulation to a measurement.
6. Enforce PCB-VERIFY-001 and MECH-FOOTPRINT-001 at the appropriate gates. For any power exception, request approval **before** performing dependent exception work. An approved integration-ready deliverable must identify included/deferred parts, interface specifications, assembly allocation, procedure, planned/available tests, approval reference and remaining full-system tasks.
7. Notify the human after independently validated PCB checking, request required fabrication approval, and report requested-stage completion separately from integration-ready status and full-system prototype completion. Require approval before human-use testing or claims of medical suitability.

## Completion and stop gates
- **Skill-run success:** Requested authorized stage produced its artifacts and evidence, and gaps are reported. This does not imply prototype completion.
- **Integration-ready — approved power integration exception:** Only if explicit approval exists and defined handoff, applicable PCB verification and independent validation requirements are met. The full-system footprint requirement remains open.
- **Full-system prototype complete:** All approved applicable criteria, full assembly footprint evidence (including physical measurement for a physical prototype), PCB gates, implementation/integration and verification evidence are satisfied. Simulation or documentation alone cannot establish physical completion.
- **Blocked/incomplete:** Report when an essential target, tool, approval, independent validator, check or evidence is missing, unsuccessful or contradictory. Continue independent authorized tasks only.

## Skill change control
Do not implement any skill update without advance, explicit human approval of the **specific** change. Submit exact current/proposed revisions and diff, scope, affected requirements/prototypes/artifacts, rationale, evidence, alternatives, risks, implementation plan, success criteria, independent verification as applicable, and rollback plan. Record approval conditions; update only within approved scope, version and validate the change. Request new approval for material scope changes. Skill-change approval alone never waives the footprint, PCB verification, human notification or power exception requirements.

## Required output contract
Return task/prototype ID and revisions; requested stage; modality; requirement IDs and approved targets; input hashes/versions and sources; delegated assignments and decisions; quantitative assumptions; results, uncertainty, evidence method and references; independent reviewer/validator identity, method and decision; per-requirement pass/fail/not-tested/non-applicable status; alternatives and blockers; footprint status; all five PCB results where applicable; manufacturing implications; human notifications and approval requests; and next actions. Explicitly state if no executable tools or physical tests were used.

## Relationship to architecture skill
The architecture skill supplies design analysis, work packages, artifacts and test plans. Prime owns requirements governance, privilege boundaries, release decisions, independent-validation gates and human approvals. Where instructions conflict, stop the affected work and request human resolution rather than silently weakening either requirement.
