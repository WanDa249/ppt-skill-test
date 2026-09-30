# Taste Discovery Experiment v1 — 空间痕迹 α vs 证据痕迹 β

Status: frozen experimental protocol  
Date: 2026-09-30  
Stage: Visual Exploration → Taste Discovery  
Purpose: test whether the user's positive reaction in the first A′/B/C round reflects a reproducible preference for **空间痕迹** or **证据痕迹**, rather than accidental features of individual images.

> This experiment does **not** test the current Skill, does **not** use a strong reference image, and does **not** modify SKILL.md.

---

## 1. Research question

The first blind review suggested two possible positive directions:

### α — 空间痕迹
Design grows from the spatial reality of practice:
- movement;
- route;
- geography;
- location;
- nodes;
- field-to-industry transitions;
- spatial relationships.

### β — 证据痕迹
Design grows from the evidence left by practice:
- real photos;
- notes;
- documents;
- screenshots;
- dates;
- records;
- maps;
- labels;
- data fragments;
- archival traces.

The question is:

> Does either direction consistently produce stronger user preference across different models, or were the earlier positive reactions accidental?

---

## 2. Experimental structure

Run the same experiment on two model/product surfaces:

| Model | α 空间痕迹 | β 证据痕迹 |
|---|---|---|
| 豆包 | 2 images | 2 images |
| GPT | 2 images | 2 images |

Total: **8 images**.

Use a fresh conversation for every model × direction cell:

1. 豆包-α
2. 豆包-β
3. GPT-α
4. GPT-β

Do not run α and β in the same conversation.

---

## 3. Shared project facts

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

Hard boundaries:
- 不得伪造人物或真实现场；
- 不要农业刻板插画；
- 不要科技大屏 / dashboard；
- 不使用上一轮任何生成图作为视觉参考；
- 不使用强视觉参考图；
- 不加载 AI-PPT-Skill。

Cover text:
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩

---

## 4. α Prompt — 空间痕迹

Use exactly this prompt on both models:

```text
请直接生成 2 张彼此独立、结构逻辑明显不同的 16:9 中文 PPT 封面候选。

不要先解释设计理念。
不要先定义配色或视觉风格。
不要自检。
不要输出文字方案。
直接生成页面。

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

本轮只探索一个方向：

“空间痕迹”。

设计感应当主要来自学生真实实践所形成的空间关系与行动轨迹，而不是额外套一个风格模板。

可以考虑但不要求全部出现：
- 路线；
- 地图；
- 地形；
- 定位；
- 节点；
- 城市与现场之间的移动；
- 从生产现场到数据中心、再到产业交流的空间关系。

重点不是做一张常规路线图，而是让“真实实践发生在不同地点、不断向产业深处移动”本身成为视觉组织逻辑。

两张必须是同一方向下的两种真正不同解法，不能只是换配色、换字体或移动元素。

硬边界：
- 不得伪造人物或真实现场；
- 不要农业刻板插画；
- 不要科技大屏 / dashboard；
- 不要标准商业流程图；
- 不使用任何上一轮生成图或参考图；
- 不要提前锁定某一种配色或字体风格。

封面文字：
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩

生成 2 张后停止，不要修改。
```

---

## 5. β Prompt — 证据痕迹

Use exactly this prompt on both models:

```text
请直接生成 2 张彼此独立、结构逻辑明显不同的 16:9 中文 PPT 封面候选。

不要先解释设计理念。
不要先定义配色或视觉风格。
不要自检。
不要输出文字方案。
直接生成页面。

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

本轮只探索一个方向：

“证据痕迹”。

设计感应当主要来自真实实践留下的材料、记录与证据如何被组织，而不是额外套一个手账模板或档案模板。

可以考虑但不要求全部出现：
- 真实照片的位置；
- 调研记录；
- 文档；
- 数据截图；
- 日期与编号；
- 地图碎片；
- 行程记录；
- 文件与批注；
- 实践证据之间的关系。

重要：
当前没有提供真实照片或真实材料，因此不得生成仿真的养殖场照片、人物照片、文件、票据或调研记录来冒充真实证据。
如页面需要真实证据，请使用明确的中性占位框或占位材料，并让“证据如何组织”成为设计重点。

重点不是做 scrapbook / 手账拼贴，而是测试“真实证据进入页面之后，能否自然形成有设计感的视觉系统”。

两张必须是同一方向下的两种真正不同解法，不能只是换配色、换字体或移动元素。

硬边界：
- 不得伪造人物或真实现场；
- 不得伪造真实证据；
- 不要农业刻板插画；
- 不要科技大屏 / dashboard；
- 不要泛化手账 / scrapbook 模板；
- 不使用任何上一轮生成图或参考图；
- 不要提前锁定某一种配色或字体风格。

封面文字：
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩

生成 2 张后停止，不要修改。
```

---

## 6. Controlled conditions

Keep fixed within each model:

- same model / product surface;
- same model settings if exposed;
- fresh conversation for α and β;
- same shared project facts;
- same image count: 2;
- same 16:9 output;
- no iterative correction;
- no reference image;
- no Skill;
- no previous generated images;
- no mention of which earlier images the user liked.

The only intended variable is:

> α spatial traces vs β evidence traces.

---

## 7. Why no reference image

The previous A′/B/C round suggested that strong references can act as a convergence mechanism and reduce exploration breadth.

This round is testing the **direction hypothesis itself**, so a strong visual reference would introduce unnecessary visual gravity and confound the result.

---

## 8. Why no Skill

This round is not asking whether the current Professional Mode works.

It asks:

> does the user actually prefer one of these two visual mechanisms?

Loading the Skill would reintroduce Visual Intent / narrative structuring as a second variable.

---

## 9. Evaluation

After all 8 images are collected:

1. hide model and direction labels;
2. shuffle into neutral IDs P1–P8;
3. show all 8 together in one contact sheet if possible;
4. collect spontaneous reaction first;
5. reveal direction/model only after the first judgement.

First-round reaction labels:

- **Strong** — “这张我真的愿意继续挖。”
- **Weak positive** — “还不够好，但这个方向有点对。”
- **Neutral** — “中规中矩。”
- **Negative** — “不对 / 模板感强 / 不像我要的。”

Also ask:

1. 哪几张最像这个项目？
2. 哪几张最有可能扩展成 20 页？
3. 哪几张有设计感但不是靠模板感？
4. 哪几张最像“真实实践留下来的东西”？
5. 哪几张只是某个偶然细节好看？

Do not calculate a weighted score.

---

## 10. Interpretation

### If α is preferred within both models
Evidence supports:

> the user has a reproducible preference for spatial-trace-driven organization.

### If β is preferred within both models
Evidence supports:

> the user has a reproducible preference for evidence-trace-driven organization.

### If α wins on one model and β on the other
Do not lock either direction.

Interpretation:

> preference may depend more on execution quality than on the abstract direction label.

Then inspect the specific visual behaviors that created the positive reaction.

### If neither direction produces a strong or weak-positive signal
Reject the hypothesis.

Do not force “空间痕迹 / 证据痕迹” into the Skill.

Return to broader visual exploration.

---

## 11. Success criterion

This experiment succeeds even if neither direction wins.

Success means we can distinguish:

- a real, reproducible taste signal;
- from an accidental reaction to a few first-round images.

---

## 12. Stop condition

Do not move to Visual Lock after this experiment.

If one direction is clearly stronger, the next stage should be:

> 2–3 same-family but structurally different continuations → user confirms “对，就是这一路” → only then introduce references for refinement.
