# Contributors

**Project:** Codebase-Wide Version Migration & Refactoring Agent (MRA)
**Problem statement:** CAIML_Nimrita_Koul_3_PS_209
**Guide:** Dr Nimrita Koul, Center for Artificial Intelligence & Machine Learning
**Institution:** School of CSE, REVA University

## Team

| Name | SRN | GitHub | Workstream | Owns |
|---|---|---|---|---|
| Srinivas R C | R23EA121 | [@srinivas-rc0408](https://github.com/srinivas-rc0408) | **A.** Core engine and integration, PR review | `src/mra/graph.py`, `src/mra/nodes/`, `src/mra/recovery/`, `src/mra/sandbox/`, `src/mra/models/`, `src/mra/report/`, `src/mra/verdict.py` |
| Verril Vaz | R23EN179 | [@Verril-hash](https://github.com/Verril-hash) | **B.** Static analysis and call-graph mapping, PR review | `src/mra/analysis/` |
| Adithya Naik | R23EF014 | [@mradinax](https://github.com/mradinax) | **C.** Pluggable migration specs and SQLAlchemy 1.4 to 2.0 | `src/mra/specs/`, `src/mra/codemods/sqlalchemy/`, SQLAlchemy corpus tasks |
| Prajwal Ragavendra Hawaldar | R23EF183 | [@prajwal-tech07](https://github.com/prajwal-tech07) | **D.** Second migration family (Python 3.8 to 3.12 removals) and live LLM model comparison | `src/mra/codemods/py312/`, its corpus tasks, `runs/benchmark/live/` |
| Prabanjan R | R23EF181 | [@prabanjan-ux](https://github.com/prabanjan-ux) | **E.** Benchmark scale (real-repository Tier B tasks, synthetic task generator) and results dashboard | `corpus/tierB/`, `corpus/generated/`, `src/mra/benchmark/`, `dashboard/` |

Folder ownership is enforced for review by [`.github/CODEOWNERS`](.github/CODEOWNERS).
Srinivas and Verril review every pull request; the owner of a touched folder is
asked as well.

## Origin of the code base

The agent's core, versions 0.1 to 0.3, was built by **Srinivas R C** between
20 September and 6 October 2026: the `MAP -> PLAN -> EDIT -> TEST -> CORRECT`
LangGraph state machine, the Docker verification sandbox, the recovery loop,
the Tier-A and edge-case corpora, the benchmark harness and the paper draft.
Its history is preserved in full in this repository.

From version 0.4 the work is a team effort. Each workstream below extends the
core to close a limitation stated in `docs/paper/paper.md` section 9.

## Workstreams

| | Workstream | Closes paper limitation |
|---|---|---|
| A | Keep the pipeline coherent, integrate and review the other workstreams, run the final benchmark | |
| B | Function-level call graph, impact set, multi-pattern symbol resolution, Python 2 fallback parser, independent completeness oracle | 6 (unmigrated patterns), 7 (recovery away from call sites) |
| C | A migration-spec format so a migration is a plug-in; SQLAlchemy 1.4 to 2.0 codemods, including call-site argument changes | 1 (one migration family), 2 (arity changes) |
| D | Python 3.8 to 3.12 removals (`distutils`, `imp`, `asyncore`, unittest aliases); comparison of several live models | 1 (one migration family), 4 (live-model arms) |
| E | Tier-B tasks from real migration pull requests, a generator for synthetic tasks, a dashboard for run results | 3 (no real repositories) |

## How we work

* Branch from `main` as `<name>/<topic>`, for example `verril/callgraph`.
* Every change reaches `main` through a pull request with **two approvals**;
  nobody, including admins, can push to `main` directly.
* Merge with **Squash and merge** or **Rebase and merge** (linear history).
* Before asking for review, pass the done-gate in `CLAUDE.md`:
  `ruff format --check .`, `ruff check .` and `pytest -q`.
* Commit your own work from your own account, so the contribution graph is
  accurate.
