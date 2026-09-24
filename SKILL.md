---
name: ai-ppt-skill
description: Design high-quality presentations from complex materials by grounding claims in evidence, aligning the real communication goal, building a coherent communication logic, mapping it to slide-level jobs, and reviewing before delivery. Use when creating or substantially restructuring a presentation, defense deck, research presentation, project report, pitch, teaching deck, or when turning documents/data/images into slides. Do not use for a purely mechanical one-line edit unless that edit requires presentation-design judgment.
version: 0.6.0
---

# AI PPT Skill

Create presentations as communication systems, not as document summaries or template-filled pages.

The core sequence is:

```text
evidence → goal → communication logic → provisional slide roles → visual intent → references when useful → representative renders → visual lock → full visual draft → editable reconstruction → review
```

The sequence is a reasoning discipline, not a generic template workflow.

For substantive new presentations, especially judged/high-stakes decks or decks longer than roughly 8 slides, apply the decision gates described in this Skill before producing the full deck. Optional supporting references may exist, but this Skill should remain usable without external reference files. Do not bypass unresolved framing or visual-direction decisions.

Adapt depth to the task's complexity and stakes, not to the model identity.

## Core rules

### 1. Evidence before expression

Treat the user's materials as the primary evidence base.

For important claims, distinguish internally between:

- **fact** — directly supported by the user's material or a verified source;
- **interpretation** — a reasonable conclusion drawn from evidence;
- **hypothesis** — plausible but not established.

Never present an interpretation or hypothesis as a confirmed fact.

For externally added information:

- use it only when expansion is allowed and it materially improves the deck;
- verify important current or contested claims;
- keep external claims distinguishable from claims supplied by the user's materials.

If a claim cannot be supported, remove it, weaken it, or surface the uncertainty. Do not fill factual gaps with plausible prose.

### 2. Goal before design

Do not begin by choosing a template, page layout, color palette, or page-by-page outline.

First infer the communication goal from the task and materials:

- who the audience is;
- what they likely know, care about, or question;
- what the presentation is trying to accomplish;
- what the audience should understand, believe, decide, or remember afterward;
- which messages matter most;
- what constraints cannot be violated;
- **what success means in this specific setting** — for example, what judges, teachers, clients, executives, investors, or teammates are likely evaluating.

Before locking the central thesis, compare plausible framings against the audience, evidence, setting, and success criteria. Do not automatically choose the most intellectually interesting framing if it shifts attention away from what the presentation is actually being judged on.

Do not turn this into a long intake questionnaire. Infer what is safely inferable.

Ask the user only when missing information would materially change the result, such as:

- a major ambiguity in audience or purpose;
- a real trade-off between competing messages;
- conflicting source materials;
- an irreversible direction choice with no defensible default.

When asking, be concise: state the decision, give at most a few meaningful options, explain the trade-off, and recommend a default when evidence supports one.

### 3. Communication logic before slides

Do not force every presentation into a fixed story template.

Choose the logic that fits the task: research argument, analytical explanation, project report, decision support, teaching sequence, persuasive case, progress review, or another structure justified by the goal.

Internally establish:

- the central thesis or organizing idea;
- the audience's starting state and desired end state;
- the few cognitive shifts needed to move between them;
- the major narrative/argument units;
- why each unit follows the previous one;
- where emphasis belongs.

A chronology is not automatically a narrative. A list of sections is not automatically an argument.

If multiple communication logics are genuinely viable and the choice changes the deck materially, surface the alternatives briefly. Otherwise select the strongest evidence-supported route and continue.

### 4. Each slide must have a job

Only after the communication logic is coherent should it be mapped to slides.

For every slide, know internally:

- **job** — why this slide exists;
- **message** — the main thing the audience should take from it;
- **evidence/content** — what supports that message;
- **visual form** — the clearest way to express it;
- **connection** — why the next slide follows.

Prefer one dominant message per slide. This is a communication rule, not a ban on supporting detail.

Do not create slides merely to fill a requested count. If a fixed count exists, compress or expand meaningfully rather than padding.

Avoid orphan slides: if a slide does not advance the goal, provide necessary evidence, enable a transition, or satisfy an explicit requirement, remove or merge it.

### 5. Content determines visual form

Do not let the renderer or a favorite template determine the information architecture.

Choose the visual form based on what the slide needs to communicate:

- comparison → aligned comparison;
- change over time → timeline or trend;
- process → flow;
- hierarchy → layered structure;
- quantitative evidence → appropriate chart;
- spatial or field evidence → real photo/map/interface when available;
- key claim → strong focal composition;
- dense evidence → structured grouping rather than a decorative collage.

Prefer user-provided and real evidence assets over generated decoration when they exist.

Do not add imagery merely to make a slide look busy or "premium."

Visual consistency matters across the deck, but consistency does not require repeating the same layout.

### 6. Keep the interaction simple

Internal analysis may be detailed; user interaction should be short and decision-oriented.

Do not dump internal working notes, evidence maps, schemas, or long analysis reports by default.

Surface only what the user needs to:

- correct a misunderstanding;
- resolve an important ambiguity;
- choose between materially different directions;
- understand a meaningful risk;
- approve a consequential change when approval is necessary.

Otherwise continue proactively.

### 7. Preserve local changes

When revising an existing deck or a previously agreed plan, change only what the request requires unless a dependency makes broader changes necessary.

Preserve unaffected:

- facts;
- narrative decisions;
- slide order;
- visual system;
- approved assets;
- constraints.

If a requested change invalidates downstream decisions, update those dependencies explicitly instead of silently redesigning unrelated parts.

## Internal working state

Maintain enough working state to stay consistent, but do not require a fixed schema in v0.1. These states describe reasoning continuity only; they are not a required runtime, database schema, or state-machine implementation.

At minimum track:

### Material state
- source materials and their roles;
- confirmed facts and key data;
- useful visual assets;
- uncertainties and unsupported claims;
- evidence risks.

### Goal state
- audience;
- purpose;
- desired audience change;
- central message;
- priorities;
- constraints;
- important trade-offs.

### Communication-logic state
- central thesis/organizing idea;
- audience journey;
- major units;
- transitions;
- emphasis;
- rejected alternatives when they may become relevant later.

### Slide state
- slide sequence;
- per-slide job;
- message;
- supporting evidence;
- visual direction;
- dependencies.

### Review state
- factual risks;
- goal drift;
- logic gaps;
- duplicated or weak slides;
- visual/production issues;
- unresolved user decisions.

These are internal working states, not mandatory user-facing documents and not a requirement to build a separate runtime or state machine.

## Workflow

### Step 1 — Read the task and materials completely

Before proposing slides:

1. identify what files, images, data, prior decks, instructions, and constraints exist;
2. read the relevant material rather than relying on filenames or a partial sample;
3. identify which material is authoritative when sources conflict;
4. inventory useful existing visual assets;
5. note factual gaps and uncertainty.

If the user explicitly says a supplied document is authoritative, treat it as such unless the user asks for external correction or verification.

### Step 2 — Form the goal

Infer the goal state from the available evidence.

For judged/evaluated tasks, first determine what success in that setting actually means. If the materials support multiple substantially different central framings, follow Gate A in `references/workflow-gates.md` and stop for a concise user decision before proceeding.

Proceed automatically only when the direction is genuinely clear.

Ask one concise decision question only when a major unresolved ambiguity would produce substantially different decks.

A useful decision prompt contains:

- the issue;
- 2–3 real alternatives when applicable;
- the practical consequence of each;
- a recommended default if justified.

Do not ask for information that can be inferred from the material or safely decided later.

### Step 3 — Build the communication logic

Create the smallest coherent set of units needed to move the audience from its starting state to the intended outcome.

Check:

- Does the opening establish the right question or context?
- Does every major claim have evidence?
- Does each unit create a reason for the next?
- Is background proportionate to its value?
- Are the strongest facts placed where they change the audience's understanding?
- Is the conclusion earned by what came before?

Do not mechanically use "background → problem → solution → result" unless the task actually fits it.

### Step 4 — Build a provisional slide architecture and role inventory

Map the communication logic to a provisional slide architecture before visual-direction selection.

For each expected slide or slide family, determine its job, message, evidence, and likely role before writing final slide copy. At minimum, know which role families the visual system must support, such as cover, evidence/photo, process/route, data/chart, section/transition, comparison, team, or conclusion.

Do not freeze every page structure yet. Representative visual validation may reveal that some pages should be merged, split, or expressed differently.

Respect explicit duration and page-count constraints. If no count is given, choose a count appropriate to the material and speaking context instead of asking reflexively.

Titles should normally state the slide's point, not merely label its topic.

### Step 5 — Set the visual intent, test it on representative pages, then lock what works

For substantive new decks, follow Gate B in `references/workflow-gates.md`. This is mandatory unless the user has already supplied a detailed visual system that can be used without reinterpretation. Before visual exploration, also read:
- `references/visual-exploration.md`
- `references/visual-quality.md`
- `references/direction-library.md`
- `references/reference-index.md`

Keep this stage simple.

First form a concise **Visual Intent** from the audience, occasion, selected framing, content character, real assets, brand/context, and expected slide roles. Record only:
- what the presentation should feel like;
- the few constraints that must not be violated;
- the main visual behavior to aim for;
- obvious genres or treatments to avoid.

Use a small Reference Pack only when references are likely to improve direction control. References must reinforce the task's direction rather than redefine it. There is no required reference count.

If several fundamentally different visual directions are genuinely plausible and the choice would materially change the deck, show the user a small number of meaningful alternatives. If one direction is clearly appropriate, continue without manufacturing choices.

For visually important decks, when image generation is available, generate a small representative set before Visual Lock. Choose pages that expose the main visual risks, usually:
- the cover;
- one evidence/photo-led slide;
- one process/data/diagram slide when relevant.

Check the actual renders before judging polish. Verify that they fit the real audience and occasion, behave like presentation slides rather than an unrelated visual genre, remain coherent across page types, preserve factual/documentary constraints, and can plausibly be reconstructed as editable slides.

Only after the representative pages are good enough should the model establish **Visual Lock**: a concise record of the design decisions that must remain stable across the deck.

Use real images, charts, diagrams, screenshots, maps, and other evidence where they improve understanding.

For documentary/evidence assets, preserve the original content. Do not use generative recreation, scene extension, face alteration, object insertion/removal, or synthetic lookalikes as substitutes for supplied real evidence. If a generative tool cannot preserve an asset faithfully, use a placeholder frame and composite the unchanged original later with a non-generative tool.

When the user requests a local visual change after Visual Lock, preserve unrelated decisions. Reopen the overall visual direction only when the user clearly rejects it or the content change makes it invalid.

### Step 6 — Produce without surrendering the design

This Skill owns presentation reasoning and the locked visual direction, but not a specific rendering technology.

Use the host's available presentation/PPTX/HTML-slide capability when one exists. The renderer is an implementation layer, not a second presentation designer.

Before handing work to a renderer or another presentation Skill, pass it the locked:
- communication goal;
- slide architecture;
- per-slide job/message/evidence;
- selected visual direction/style brief;
- asset priorities;
- explicit constraints.

A downstream renderer must not silently replace the narrative, visual direction, page hierarchy, or evidence policy. If it cannot honor the locked brief, change renderer or surface the limitation instead of accepting a generic template route.

Do not let the mere presence of an installed presentation Skill decide the production approach.

For visually important decks, prefer a **visual-first, editable-second** workflow:
1. verify the selected direction on representative rendered/image previews;
2. produce the full visual draft;
3. review the full-deck overview for consistency, rhythm, density, and weak pages;
4. then produce or reconstruct the editable deliverable.

When an editable slide format is requested, preserve editability for text, charts, and simple graphics where practical.

If no renderer is available:

- do not pretend a PPT/PPTX was created;
- deliver a renderer-ready slide architecture and production brief instead;
- clearly state the missing production capability.

When production uses source files or code, fix issues in the source and regenerate rather than manually patching only the final artifact.

### Step 7 — Review adversarially before delivery

Review the deck or production plan against the task, not against generic aesthetics.

#### Evidence review
- Are important factual claims traceable?
- Did any unsupported achievement, number, attribution, or conclusion appear?
- Are external facts verified where necessary?

#### Goal review
- Does the deck serve the actual audience and purpose?
- Did the presentation drift into summarizing the source material?
- Are the highest-priority messages receiving the most attention?

#### Logic review
- Can the audience follow why each major unit follows the previous one?
- Are there chronological dumps, information dumps, repeated messages, or premature conclusions?
- Does the ending follow from the evidence?

#### Slide review
- Does every slide have a clear job?
- Is the title aligned with the page's actual point?
- Is any slide overloaded or so empty that it fails to make a complete point?
- Are transitions and section boundaries clear?

#### Visual review
- Does the visual form help comprehension?
- Are real assets used when they are better evidence than decoration?
- Is the deck visually coherent without becoming mechanically repetitive?
- Are text density, hierarchy, alignment, cropping, chart legibility, and image quality acceptable?

#### Constraint review
- Page count, duration, branding, required sections, logos, navigation, page marks, language, aspect ratio, file format, and other explicit constraints must be respected.

When rendering tools allow visual inspection, inspect the rendered result and correct visible failures before delivery.

## Common failure modes

Actively avoid:

- **document-summary deck** — every source section becomes a slide;
- **chronological dump** — events are listed in order without a communication thesis;
- **template-first design** — layout determines content;
- **forced storytelling** — a generic story arc is imposed on analytical or technical material;
- **unsupported claim** — plausible wording outruns the evidence;
- **questionnaire interaction** — the user is asked to fill fields the AI could infer;
- **approval fatigue** — the user is asked to confirm routine steps;
- **equal-weight deck** — every fact receives similar space regardless of importance;
- **page-count padding** — weak slides exist only to hit a number;
- **orphan slide** — a page has content but no role in the argument;
- **decorative visual** — imagery adds atmosphere but not understanding;
- **renderer-driven compromise** — content logic is distorted because a tool prefers a layout;
- **renderer takeover** — a downstream presentation Skill silently replaces the locked narrative or visual system with its own default workflow;
- **style-by-default** — the first available theme is used without visual exploration on a high-stakes deck;
- **evaluation-context drift** — the thesis is coherent but optimized for the wrong success criterion or presentation setting;
- **global rewrite for local edit** — a small requested change unnecessarily disrupts the rest of the deck.

## Completion standard

A task is ready to deliver only when:

1. the key claims are evidence-grounded;
2. the communication goal is clear;
3. the deck has a coherent logic rather than a list of sections;
4. every slide has a defensible role;
5. the visual direction serves the content;
6. explicit user constraints are satisfied;
7. important unresolved uncertainty is surfaced;
8. the produced artifact, when one is generated, has been reviewed in its rendered form where tooling allows.

Do not expose internal reasoning or working-state detail unless the user explicitly asks for the design rationale or diagnostic trace.

