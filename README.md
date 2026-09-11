# OpenAWF Specification

Agentic workflows are everywhere, but every tool represents them differently. Each harness and SDK defines its own: what a workflow is, how it is represented, how it is shared. Attempts at collaboration, like the Claude marketplace, stay bound to one tool. This absence of a standard holds back collaboration industry-wide, and within teams, where colleagues cannot readily share and collaborate easily on workflows they build.

The OpenAWF Specification (Open Agentic WorkFlow) defines a standard, tool-agnostic description for agentic workflows. A workflow is an FSM (finite-state machine) of tasks: the flow runs from a start task to a terminal one.

The standard defines an agentic workflow as a single, self-contained document, so anyone can share, render, version, and run it, independent of the tool that made it.

OpenAWF documents are represented in YAML or JSON.

## Documents per version

Each version ships three files:

| File | Role | Authority |
| --- | --- | --- |
| `versions/<version>.md` | The specification, in prose. | Normative. Source of truth. |
| `schemas/<version>/schema.yaml` | JSON Schema, hand-authored. | Structural validation only. |
| `schemas/<version>/schema.json` | JSON Schema, generated from `schema.yaml`. | Structural validation only. |

The Markdown is the source of truth. The JSON Schema validates structure; it cannot express every constraint in the specification. Where the two conflict, the specification wins.


## Design

OpenAWF defines every part of a workflow in one file. The tasks, their orchestration, and everything each task depends on are declared in the document itself.

Three principles follow from this:

- **Workflows are whole.** A workflow declares everything it needs; nothing is left to the environment.
- **Tasks are atomic, reusable units.** A task is defined once and usable across many workflows.
- **Tasks and workflows are versioned and signable.** Every task/workflow has an identity, so what an agent produced can be traced to the exact version that produced it.

## License

Apache 2.0. See [LICENSE](LICENSE).
