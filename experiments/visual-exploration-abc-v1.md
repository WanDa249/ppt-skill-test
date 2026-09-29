# Visual Exploration A′/B/C Experiment v1

Status: frozen experimental protocol  
Date: 2026-09-29  
Purpose: diagnose whether the current AI-PPT-Skill package suppresses visual exploration, whether a strong reference improves the visual ceiling, and whether the current full-slide generation chain shows an obvious capability ceiling.

> This experiment does **not** modify `SKILL.md`, `docs/WORKFLOW.md`, or the current visual workflow. The current Skill is the baseline under test.

## 1. Research questions

RQ1. Does the current Skill package produce weaker or more conservative visual exploration than a minimal-constraint prompt?

RQ2. Under the same minimal-constraint prompt, does one strong user-approved visual reference materially improve the quality or diversity of the generated directions?

RQ3. If all groups remain weak, is the current “model × full-slide image generation × prompt delivery” chain failing to produce a promising direction?

## 2. Groups

### Historical A — context only

Existing failed sample:

- warm paper background;
- dark green typography;
- ochre accent;
- editorial / publication-like composition;
- abstract “brush trace → dot” device.

Use only as historical context. Do **not** include it in the formal A′/B/C comparison.

### A′ — Current Skill Re-run

Use the current repository package as-is and run the task in Professional Mode.

Important:
- do not repair missing reference files before this run;
- do not inject the newer “Taste Discovery” hypothesis;
- do not rewrite Step 5;
- do not add extra prohibitions or self-check rules;
- use a fresh conversation.

Prompt:

```text
Use this repository as the only Skill context.

Run this task in Professional Mode.

Task:
Create exactly 3 genuinely different 16:9 Chinese cover-slide visual candidates for the same presentation.

Project:
华中科技大学管理学院暑期社会实践现场答辩《数智兴农实践队》

Core narrative:
预测如何经过真实产业现场，变成可用判断。

Confirmed real experiences:
- 武汉养殖场走访；
- 重庆荣昌国家生猪大数据中心驻点约三周；
- 国农集团、中华保险等产业交流。

Desired feeling:
可信、年轻、有现场感、有完成度。

Hard factual boundaries:
- 不得伪造人物或真实现场；
- 不要农业刻板插画；
- 不要科技大屏 / dashboard。

Cover text:
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩

Do not make the full deck. Stop after the 3 cover candidates.
```

### B — Minimal-Constraint Free Exploration

Do **not** load AI-PPT-Skill or any presentation-design rules beyond the prompt below.

Run in a fresh conversation.

Prompt B:

```text
请直接生成 3 张彼此独立、视觉逻辑真正不同的 16:9 中文 PPT 封面候选。不要先定义视觉风格，不要解释设计理念，不要自检，不要先输出文字方案。

项目：
华中科技大学管理学院暑期社会实践现场答辩《数智兴农实践队》

核心叙事：
预测如何经过真实产业现场，变成可用判断。

已确认的真实经历：
- 武汉养殖场走访；
- 重庆荣昌国家生猪大数据中心驻点约三周；
- 国农集团、中华保险等产业交流。

期望感受：
可信、年轻、有现场感、有完成度。

硬边界：
- 不得伪造人物或真实现场；
- 不要农业刻板插画；
- 不要科技大屏 / dashboard。

封面文字：
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩

请自由探索。3 张不能只是换配色、换字体或移动版式，而应当是视觉组织逻辑明显不同的 3 个方向。
```

### C — Minimal Free Exploration + Strong Reference

Everything must be identical to B except for the presence of **one user-approved strong reference image** and the single appended instruction below.

Use the exact Prompt B, then append only:

```text
你还收到 1 张参考图片。它只用于学习视觉张力、信息层级、空间关系、图文关系和完成度；不得复制其具体版式、文字、人物、品牌、场景或主题。
```

Do not add any further reference-analysis instructions.

## 3. Controlled conditions

For one model-level experiment, keep fixed:

- same model / product surface;
- same model settings if exposed;
- same date / session window as far as practical;
- fresh conversation for each group;
- same factual project input;
- same output target: 3 covers;
- same aspect ratio: 16:9;
- same language: Chinese;
- same cover text;
- same number of candidates;
- no iterative correction before first-round judging.

Only intended differences:

- A′ vs B: current Skill package vs minimal-constraint prompt;
- B vs C: no reference vs one strong user-approved reference.

## 4. Current-package dependency note

At protocol freeze time, the public test repository's `SKILL.md` requires these files during Step 5:

- `references/workflow-gates.md`
- `references/visual-exploration.md`
- `references/visual-quality.md`
- `references/direction-library.md`
- `references/reference-index.md`

They are currently unavailable in the test repository. Do not silently recreate them before A′. This is part of the current package state and must be logged as an execution defect.

Interpret A′ vs B accordingly:

> it tests the **current released package as experienced by a model**, not yet the isolated causal effect of one specific rule.

If B outperforms A′, run a second-stage ablation to locate the cause instead of immediately concluding that “all rules are bad.”

## 5. First-round evaluation

Do not let the generating model score or pass/fail its own images.

After collecting 9 images (A′1–3, B1–3, C1–3):

1. rename / shuffle them so the evaluator cannot see the group;
2. show all 9 under neutral IDs;
3. record spontaneous reactions first;
4. only then diagnose the reaction using the six dimensions below.

Dimensions:

1. 第一眼吸引力 — 有没有一张让人立刻觉得“这个有点意思”？
2. 方向差异 — 三张是否真的不同，而不是换配色？
3. 项目契合 — 是否能感受到学生进入真实产业现场？
4. 非模板感 — 换成无关项目后是否仍能原样成立？
5. 可扩展性 — 是否能自然发展成约 20 页？
6. 用户反馈响应潜力 — 是否存在值得进入下一轮 Taste Discovery 的方向？

Do not calculate a weighted total score in round 1.

Primary reaction labels:

- Strong signal: “这张有意思，我想继续看。”
- Weak positive: “还不好，但终于有一点感觉对了。”
- Negative: “还是模板 / 泛农业 / 奇怪 / 不像我要的。”

The first-round goal is not to select a final cover. It is to find whether any direction deserves further exploration.

## 6. Interpretation rules

### If B clearly produces more promising directions than A′

Evidence supports:

> the current Skill package is likely suppressing visual exploration.

Do not yet identify the specific cause. Run a second-stage ablation.

### If C clearly produces more promising directions than B

Evidence supports:

> a strong user-approved visual reference is an important visual-control lever.

Next investigate how to capture visual signals without template copying.

### If B and C are both weak

Do **not** conclude immediately that the base model is incapable.

Use the narrower statement:

> the current “model × full-slide image generation × prompt delivery” chain did not demonstrate sufficient visual exploration ability.

Then test whether the bottleneck is:
- the model;
- full-slide image generation;
- Chinese slide typography;
- prompt-to-image delivery;
- or whether image generation should be limited to local visual assets with editable reconstruction handling the slide.

## 7. Second round only after a promising candidate appears

Taste Discovery starts only after the evaluator identifies a candidate with at least a weak-positive signal.

Do not begin by changing colors, fonts, or alignment.

First infer what the evaluator actually responded to, such as:

- real-material presence;
- large-image behavior;
- asymmetry;
- image/text overlap;
- documentary feeling;
- motion / action;
- negative space;
- information density;
- departure from conventional PPT composition;
- title–evidence relationship.

Then generate exactly 2 same-family but structurally different continuations.

Visual Lock is not allowed until the evaluator explicitly confirms the direction.

## 8. Experiment log fields

Record for each run:

- group: A′ / B / C;
- model and product surface;
- date/time;
- fresh-context: yes/no;
- reference used: none / reference ID;
- output count;
- any tool or generation failure;
- any missing repository dependency;
- image IDs / filenames;
- blinded evaluation ID;
- first spontaneous reaction;
- six-dimension notes;
- whether it advances to Taste Discovery.

## 9. Stop conditions

Stop and diagnose instead of adding more rules when:

- a group fails to produce 3 usable candidates;
- A′ cannot execute because required Skill dependencies are missing;
- C cannot run with the exact same prompt as B plus one reference;
- the model changes or generation surface changes mid-comparison;
- the evaluator sees group labels before first reaction.

Do not add a D group in round 1. Add diagnostic groups only after A′/B/C reveal a specific unresolved cause.
