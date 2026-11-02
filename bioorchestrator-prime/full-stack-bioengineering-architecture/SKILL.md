---
name: full-stack-bioengineering-architecture
description: Develop traceable PPG and non-PPG system architectures, specialist work packages, design artifacts and verification plans under Bioorchestrator Prime governance.
version: 0.1.0
status: draft-for-human-review
---

# Full-Stack Bioengineering — Architecture Skill

## Purpose, activation and authority
Use when Prime requests planning, design, implementation coordination, integration analysis or revision of a PPG or non-PPG wearable prototype. Work only on authorized stages. Return engineering recommendations and evidence; do not authorize fabrication, human testing, power exceptions, requirement waivers or skill changes. Prime owns approval and release decisions. No tool, agent, physical build or test is assumed available.

## Required inputs
Prototype ID/revision and separate technology-family baseline; defined sensing modality; intended use and limits; requested stage; target outputs (units/rates/formats); approved acceptance criteria; source/version of designs and test evidence; authorized capabilities; interface, mechanical and power constraints; dependencies; human approvals. Mark unknowns `[UNRESOLVED: description]`; mark non-applicable only as `[NOT APPLICABLE: rationale]` with required approval. Block tasks dependent on unavailable inputs.

## Engineering lifecycle
1. **Requirements:** Build a requirement-to-task-to-artifact-to-test map. Record approved targets, units, tolerances, methods, statuses (pass/fail/not-tested) and source. Maintain independent baselines for each prototype.
2. **Architecture:** Define sensing chain, acquisition, processing, storage/communications, electrical power/charging, firmware, mechanical stacking, interfaces, safety and integration boundaries. Evaluate alternatives and quantitative feasibility.
3. **Resource/component selection:** Verify candidate identities, sources, licensing, versions, applicability and limitations before adoption. Catalog suggestions—SensWear, OpenEarable 2.0, Biocoin, BIOBSS, Awesome-PPG, RayOpt, Metafluidics, NANO-HUB and QuCoNot—are unverified references, not approved dependencies.
4. **Modality design:** For PPG, justify optical channels, measurement location, LED/detector arrangement, acquisition settings, motion mitigation and optical model. A 3–5 mm emitter–receiver spacing is only a candidate requiring validation. The example `1/(2*3.1415*r_mm**2)` for `r_mm > 2` (else zero) is illustrative and **not** performance or acceptance evidence. For non-PPG, define measured quantity, sensor geometry, coupling, interference and modality-specific verification; PPG optical rules do not automatically apply.
5. **Mechanical/power design:** Enforce **MECH-FOOTPRINT-001** as the single combined maximum 6 mm × 7 mm plan-view boundary including every PCB, sensor, component, interconnect, power circuit, battery, charging contact/receiver, protrusion, clearances and tolerances. Record assembly orientation, dimensioned drawing revision, bill of included parts, maximum dimensions and tolerance basis. Verify the design envelope before fabrication and full physical assembly with documented measurements before physical completion. Thickness, volume and enclosure remain unresolved until specified. If battery/power/charging cannot fit, stop exception-dependent work and return a detailed approval request to Prime; do not silently externalize elements.
6. **Electronics/PCB:** Version schematic, PCB, stack-up, constraints, BOM, netlist and fabrication/assembly outputs together. Candidate 5 mil analog guard track/10 mil clearance and 8 mil outer/4 mil core HDI microvia values are unvalidated; use only when design-specific and fabrication-approved, otherwise mark not applicable. Define separate modality-specific constraints.
7. **Firmware and processing:** Specify acquisition timing, firmware interfaces, calibration, algorithms, dependency versions, reproducible builds, test configurations and signal-quality limitations. Do not infer medically unobservable quantities from algorithms.
8. **Integration and testing:** Define interface contracts, dependency order, integration procedure, bench/simulation/physical acceptance tests and requirement-linked evidence. Reconcile revision mismatches and conflicting specialist outputs before handoff.

## Mandatory PCB verification package — PCB-VERIFY-001
For **each exact versioned PCB package**, collect:
- **DRC:** rule files/configuration, layout constraints, findings and corrective actions/dispositions.
- **ERC:** schematic rule configuration, results, findings and dispositions.
- **DFM:** selected fabrication/assembly process rules, results, corrective actions and dispositions.
- **Netlist verification:** report demonstrating schematic-to-netlist-to-PCB connectivity consistency; resolve unintended missing, extra and mismatched connections.
- **Data completeness:** manifest against delivered schematic, layout, netlist, components/dependencies, fab/assembly files, rule configurations and reports; mark each present/missing/approved non-applicable and detect stale/unreadable/inconsistent files.

Package version, result, evidence reference and disposition must be provided for every check. Supply Prime with the complete package for validation by **a different agent**. That validator must independently rerun authorized checks or document substantive evidence review, limitations, findings and decision. A missing validator or unsuccessful check blocks fabrication and integration-ready PCB handoff. Report findings; do not self-certify the release.

## Power integration exception — design handoff
If full-system power hardware cannot fit, provide Prime: prototype/revision; affected elements; dimensional calculations/drawings; options assessed; reason for infeasibility; proposed included/external/deferred boundaries; intended power/charging mechanical, electrical, operating-mode and firmware interfaces; dependencies; unresolved fields; and the exact approval question. Continue only unaffected authorized work pending approval. After explicit approval, generate a versioned integration-ready package with included/deferred inventory, approved prototype boundary, approval reference, drawings and space allocation, interface specifications, integration procedure, planned acceptance tests, performed-test evidence and remaining integration/full-footprint verification tasks. Do not report full-system footprint compliance based on that exception.

## Specialist delegation contract
Each engineering assignment must specify task ID, owner/role, approved scope and tool permissions, input revisions/hashes, requirement IDs, dependencies, expected artifacts, quantitative acceptance tests, evidence format, review route, blockers and stop conditions. Suggested functions are requirements/system architecture, electronic/PCB, mechanical/packaging, sensing/processing, firmware, integration/testing and independent validation; do not assume these agents exist or count as independent without actual assignment and work.

## Required architecture outputs
- **Requirements record:** Family, specific modality, intended use, approved targets and separate unresolved/approved non-applicable items.
- **Architecture/design package:** Tradeoffs, component/resource rationale, block diagrams, mechanical envelope and tolerances, power budget, electrical/firmware/data interfaces, applicable schematic/PCB/fabrication files, signal-chain design and revisions.
- **Task/decision record:** Specialist scopes, dependencies, assumptions, risks, alternatives, decisions and references.
- **Verification record:** Requirement ID, target, method, test conditions, evidence type/source, status and limitations; separate simulation from physical measurements. Include full assembly design-envelope and physical evidence distinctly, and all five PCB check reports plus independent validation evidence where applicable.
- **Stage handoff:** Produced artifacts, reproducible firmware/processing builds/configuration, integration steps, missing evidence, risks, blockers, approval requests and remaining tasks. Distinguish stage completion, approved integration-ready status and full-system completion.

## Escalation and completion
Escalate safety/intended-use uncertainty, infeasible footprint, incompatible requirements, unresolved acceptance targets, missing or conflicted evidence, inaccessible tools, absent independent validator and proposed skill modifications to Prime. No human-use test, supplier outreach, procurement or fabrication without applicable explicit approval. Successful architecture-stage delivery does not imply prototype completion or medical validation. Skill revisions require Prime's specific advance human-approval procedure.
