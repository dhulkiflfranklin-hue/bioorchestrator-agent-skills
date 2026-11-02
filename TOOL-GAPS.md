# TrueForge tool inventory and integration gaps (2026-11-02)

Assessment source: uploaded `Master-Tools-Inventory.txt` (historical snapshots dated 2026-11-01) and provided TrueForge Agents screenshot. **No direct inspection of the user's localhost TrueForge environment was performed.** Screenshot showed saved agents with `no tools`; this does not prove no runtime tools exist, only that none appear assigned in the library.

## Previously demonstrated elsewhere; verify afresh in exact TrueForge runtime
- Docker Desktop/Engine and `bioengineering-http-mcp` on local 127.0.0.1:8765 `/mcp` were historically confirmed on user's Windows host. The endpoint requires authentication; never paste credentials into chat.
- Eight read-only HTTP MCP adapter tools reportedly worked historically: `inspect_file`, `list_project_directory`, `inspect_file_metadata`, `file_sha256`, `repository_status`, `repository_log`, `repository_commit`, `repository_file_history`.
- Filesystem MCP (read-only): `list_directory`, `read_file`, `file_metadata`, `calculate_sha256`. Git MCP (read-only): `git_status`, `git_log`, `git_show_commit`, `git_file_history`. Their upstream exposure to TrueForge must be verified.
- Python 3.12.3, NumPy and SciPy were detected in the prior MCP container; this does not establish access in TrueForge. Python execution MCP was intentionally excluded from the external adapter.

## Missing, unverified or restricted integrations
| Priority | Capability | Candidates | Status / next test |
|---|---|---|---|
| P0 | TrueForge-to-MCP gateway | existing authenticated HTTP adapter | Verify endpoint reachability, secrets storage, tool discovery, per-agent allow/deny and audit records |
| P0 | Saved-agent-to-saved-agent delegation | TrueForge dynamic subagents and/or supported routing | Unproven; run bounded named-route and denial tests |
| P0 | Tool identity and approval gateway | registered identity manager and agent-tool-policy.yaml | File referenced, current policy not inspected; deny forbidden writes/execution per identity |
| P0 | Requirement/artifact/evidence registries | registered YAML files | Existing registries reportedly placeholders; populate only through approved staging process |
| P1 | CAD | FreeCAD, CadQuery, OpenSCAD | Candidate; verify executable, licensing, version and dimension/STEP workflows |
| P1 | PCB/Electrical | KiCad/kicad-cli, ngspice | Candidate; verify ERC/DRC, fabrication outputs, model accuracy |
| P1 | DSP/physiology | MNE, NeuroKit2, WFDB, YASA, pyPPG, PyWavelets, scikit-learn | Candidate; verify import, data access, licenses and validation |
| P1 | Embedded | Zephyr, FreeRTOS, Renode, QEMU, CMake, Ninja, ARM GCC | Candidate; verify isolated build/simulation; no flashing without approval |
| P2 | Advanced modeling | Meep, QuTiP, pymatgen, ASE, CVXPY, CasADi, PyMC, SALib | Candidate; verify imports, benchmarks and value before install |
| P1 | Supplier qualification | manufacturer datasheets/RFQ workflow | Companies only shortlisted, none qualified; no outreach/purchases without approval |
| P1 | Reference datasets | PhysioNet, Sleep-EDF, SHHS, ISRUC, CAP, MIMIC, PPG-DaLiA | Access/license/privacy and population fit unverified |
| RESTRICTED | Python Execution MCP | list_approved_scripts, execute_approved_script | Do not expose until approval-backed enforcement is independently verified |

## Recommended least-privilege assignment
- Orchestrator: registered read-only file/git/registry tools; identity/approval lookups only if backed by enforced policy.
- DFM: read-only file/git and, after approval, sandboxed CAD/PCB verification; vendor research only without unsolicited contact.
- DSP and ElectroPhys: read-only project tools; approved offline signal/data computation and reference datasets after authorization.
- Embedded: read-only sources, approved isolated firmware build/test tools; no firmware flashing.
- Optics and QuantumNano: read-only sources, controlled numerical modeling/circuit simulation after authorization.
- No agent receives unrestricted shell, network, data export, write or purchasing tools by default.

## Acceptance evidence to collect
For each agent identity: tool list, server identity/version, permission policy version, successful allowed read, denied write/execution, authentication expiration test, audit log, reproducible versioned results. Confirm any dynamic sub-agent delegation is a real callable route, not inferred from a UI toggle.
