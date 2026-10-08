# Reference Dependency Audit — 2026-10-08

Status: architecture review  
Scope: the five missing `references/` files currently named by `SKILL.md`  
Goal: decide which dependencies are truly necessary, which should become optional, and which should not exist.

## Executive decision

Do **not** recreate the five files as a mandatory reference bundle.

The current package contains an internal contradiction:

- `SKILL.md` states that supporting references are optional and that the Skill should remain usable without external reference files.
- Step 2 and Step 5 nevertheless refer to missing files as if they were required, including a mandatory Gate B dependency.

This creates brittle execution and unnecessary context loading.

Recommended architecture:

1. Keep **core control flow** in `SKILL.md`.
2. Use `references/` only for optional background/examples that improve a task when needed.
3. Do not create a design-direction library or reference index merely to satisfy old links.
4. Remove the five broken mandatory references from the core workflow before treating Professional Mode as complete.

This matches current Skill packaging guidance: `SKILL.md` should contain the main workflow; `references/` is optional supporting material loaded when needed, not a mandatory dependency for routine execution.

External cross-check:
- OpenAI Skills guide: keep main instructions in `SKILL.md`; use `references/` for background material and link to supporting files as needed.
  https://developers.openai.com/api/docs/guides/tools-skills
- OpenAI plugin skill guidance: supporting references are optional and should hold policies, schemas, examples, and background material; the workflow boundary should remain clear in `SKILL.md`.
  https://developers.openai.com/plugins/build/skills
- OpenAI skill architecture article: skills use progressive disclosure; supporting references should be read only when needed instead of bloating context up front.
  https://developers.openai.com/blog/skills-agents-sdk

---

## 1. `references/workflow-gates.md`

### Current use

`SKILL.md` uses it for:
- Gate A in Step 2 when multiple central framings are materially different.
- Gate B in Step 5 before visual exploration.

### Audit

This is **core control flow**, not background material.

The existing `SKILL.md` already describes most of the intended behavior:
- ask only when ambiguity materially changes the deck;
- surface meaningful alternatives;
- continue automatically when direction is clear;
- show visual alternatives only when multiple directions are genuinely plausible;
- validate representative pages before Visual Lock.

A mandatory external gate file therefore creates a fragile dependency without adding a distinct capability.

### Decision

**Do not recreate as a mandatory reference.**

Move/retain the minimum Gate A / Gate B behavior directly in `SKILL.md`.

If a future reference file exists, it should contain examples of gate decisions, not the gate definitions themselves.

### Recommended status

**CORE → inline, reference optional**

---

## 2. `references/visual-exploration.md`

### Current use

Step 5 says to read it before visual exploration.

### Audit

Visual exploration is a legitimate Professional Mode capability, but the project is still experimentally determining:
- how much exploration is useful;
- when references should enter;
- how Taste Discovery should work;
- how to preserve headroom across models;
- how to avoid reference gravity and premature convergence.

The current experiments show this mechanism is **not stable enough** to freeze into a mandatory reference document.

The core behavior already exists in `SKILL.md`:
- establish Visual Intent;
- compare genuinely different directions when needed;
- generate representative pages;
- inspect actual renders;
- delay Visual Lock until representative pages are good enough.

### Decision

**Do not create a mandatory visual-exploration reference yet.**

Keep ongoing mechanisms in `experiments/` until validated.

A future optional file may contain tested exploration patterns or examples, loaded only for Professional Mode when exploration is materially useful.

### Recommended status

**EXPERIMENTAL → no core dependency**

---

## 3. `references/visual-quality.md`

### Current use

Step 5 currently names it as a required pre-exploration read.

### Audit

Visual quality checks already appear in Step 5 and Step 7:
- audience/occasion fit;
- presentation-slide genre fit;
- coherence across page types;
- factual/documentary constraints;
- editability feasibility;
- density, hierarchy, alignment, cropping, chart legibility, image quality;
- avoidance of mechanical repetition.

Recreating a second mandatory checklist would duplicate the core review logic and increase instruction volume.

The recent smoke test also shows that quality failures can come from model/renderer execution, not from a missing generic checklist.

### Decision

**Do not recreate as a mandatory reference.**

If later needed, a visual-quality reference should be an optional illustrated diagnostic guide or examples library, not another set of rules every run must read.

### Recommended status

**DUPLICATIVE → remove core dependency**

---

## 4. `references/direction-library.md`

### Current use

Step 5 currently names it as a required read before visual exploration.

### Audit

This file has the highest architectural risk.

A mandatory direction library can push the Skill toward:
- template-first design;
- repeated style categories;
- lowest-common-denominator outputs;
- reference anchoring;
- a growing design knowledge base.

Those directions conflict with existing project principles:
- content determines visual form;
- do not use a favorite template to determine information architecture;
- avoid large design knowledge bases without evidence;
- Professional Mode should improve decision quality rather than system complexity.

Recent experiments also show that strong visual anchors can create reference gravity and reduce exploration breadth.

### Decision

**Do not create this file as a core dependency.**

If the project later builds a small set of validated visual examples, treat them as optional assets/examples for inspiration, not a taxonomy the model must choose from.

### Recommended status

**REJECT AS CORE**

---

## 5. `references/reference-index.md`

### Current use

Step 5 currently names it as a required read.

### Audit

The Skill already states:
- Reference Pack is optional;
- references should reinforce rather than redefine the direction;
- there is no required reference count.

A mandatory reference index presupposes a maintained reference library. The current project does not need one to execute the workflow.

It would also introduce maintenance cost and could make the system increasingly retrieval-centric even though the project has explicitly avoided becoming a design database/RAG platform.

### Decision

**Do not create this file now.**

If a real curated asset/reference collection emerges later, its index should belong to that optional asset layer rather than the core Skill execution path.

### Recommended status

**NOT NEEDED NOW**

---

## Resulting minimal architecture

### Keep in `SKILL.md`

Core:
- evidence discipline;
- audience/purpose/success criteria;
- communication logic;
- slide jobs and role boundaries;
- concise Gate A decision behavior;
- Visual Intent;
- concise Gate B decision behavior;
- representative render validation;
- Visual Lock;
- production handoff;
- adversarial review.

### Keep outside core

`experiments/`:
- Taste Discovery;
- Execution Scaffold;
- cross-model robustness experiments;
- role-contract experiments;
- reference-gravity experiments.

Potential future optional `references/`:
- examples of good/bad gate decisions;
- tested visual exploration examples;
- illustrated visual diagnostics;
- narrowly scoped domain/brand guidance when actually available.

### Do not build now

- mandatory direction library;
- mandatory reference index;
- model-specific rule library;
- generic style taxonomy;
- a second visual-quality ruleset.

---

## Proposed minimal code change

Do not add five files.

Instead, make a small cleanup in `SKILL.md`:

1. Replace the Step 2 external Gate A reference with an inline rule already substantially present in the surrounding paragraph.
2. Replace the Step 5 mandatory Gate B/reference-file preamble with a short inline decision rule.
3. Remove the four mandatory pre-read links from Step 5.
4. Preserve the existing optional Reference Pack behavior.
5. Keep the recent `role boundary` additions unchanged.

Expected effect:
- repository becomes internally consistent;
- cold-start agents stop encountering 404 dependencies;
- Professional Mode remains self-contained;
- context stays smaller;
- experimental mechanisms do not leak into the stable core;
- future supporting references can still be added through progressive disclosure when evidence justifies them.

## Decision threshold

This cleanup is justified now because it removes broken dependencies and resolves a direct contradiction in the current package. It does **not** add a new mechanism.

Do not add new `references/` content until a validated need cannot be satisfied cleanly inside the current core workflow.
