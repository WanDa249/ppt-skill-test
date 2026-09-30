# Execution Scaffold v2 — Style-Neutral Cross-Model Validation

Status: frozen experimental protocol  
Date: 2026-09-30  
Stage: Cross-model robustness validation  
Purpose: test whether a shorter, style-neutral execution scaffold can preserve the floor lift observed on 豆包 Expert while restoring style freedom on GPT-5.6 Sol.

---

## 1. Background

Previous scaffold v1 produced a promising but incomplete result:

- 豆包 Expert showed a clear floor-lift signal: at least one scaffolded output improved from near-unusable to roughly 80% of the user's perceived GPT level.
- GPT-5.6 Sol retained overall quality/headroom.
- However, GPT's visual language shifted from a looser ink/terrain feel toward a more modern architectural/scenario-composition style.

Interpretation:

> scaffold v1 likely helped translate the abstract intent into visual behavior, but it also unintentionally influenced visual medium/style.

Therefore v2 removes the scene-specific wording and keeps only the minimum semantic correction.

---

## 2. Research questions

1. Can v2 preserve the floor lift on 豆包 Expert?
2. Can v2 preserve GPT-5.6 Sol quality/headroom?
3. Can v2 reduce unintended style steering?
4. Can both models understand that “空间痕迹” is a spatial-relationship principle rather than a map/route icon recipe?

---

## 3. Experimental structure

Run exactly two fresh conversations:

| Model | Condition | Output |
|---|---|---|
| GPT-5.6 Sol | α + Scaffold v2 | 2 covers |
| 豆包 Expert | α + Scaffold v2 | 2 covers |

Do not rerun the existing baselines.

Compare against already collected:
- GPT original α ×2
- GPT scaffold v1 ×2
- 豆包 Expert original α ×2
- 豆包 Expert scaffold v1 ×2

---

## 4. Shared prompt

Use the same prompt on both models:

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

【Execution Scaffold v2】
“空间痕迹”不是地图、路线、定位点、等高线等视觉符号本身。

这些符号即使被拿掉，页面的空间关系与行动过程仍应成立。

请把这段说明只理解为“什么视觉关系必须成立”，不要把它理解成对视觉媒介、版式风格、配色、字体、摄影方式或插画方式的指定。
【Execution Scaffold v2 结束】

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

## 5. Controlled conditions

For both models:
- use a fresh conversation;
- no GitHub/Skill;
- no reference image;
- no previous images;
- no mention of prior results;
- no mention that one model performed better;
- same exact prompt;
- generate exactly 2 images;
- do not iterate after first output.

Only variable:
> model / generation chain.

---

## 6. Evaluation

After collecting 4 new images:

### A. Floor lift
Compare 豆包 Expert v2 against:
- 豆包 original α
- 豆包 scaffold v1

Question:
> Does v2 maintain or improve the quality gain seen in scaffold v1?

### B. Headroom preservation
Compare GPT v2 against:
- GPT original α
- GPT scaffold v1

Question:
> Does v2 remain around the user's first-tier quality level?

### C. Style freedom
Question:
> Does GPT regain broader stylistic freedom instead of being pushed toward one modern architectural/scenario-composition look?

### D. Portability
Question:
> Do both models express spatial relationship as the visual backbone, without mechanically reducing the concept to maps/routes/topographic lines?

---

## 7. Success criterion

Scaffold v2 is a stronger candidate than v1 only if:

1. 豆包 Expert maintains a clear floor-lift signal;
2. GPT remains near original first-tier quality;
3. visual style is less constrained than in v1;
4. outputs do not collapse into literal map/route symbolism.

No weighted score is required.

---

## 8. Interpretation

### If v2 succeeds
Candidate principle for future Baseline Mode:

> Execution scaffolds should clarify the required visual behavior while remaining neutral about visual medium, style, and final form.

Do not yet automate scaffold triggering.

### If v2 loses the 豆包 improvement
v1's more explicit wording may have been necessary for weaker-model execution.

Then investigate how to preserve semantic specificity without style steering.

### If GPT remains style-shifted
The problem may not be the specific wording but the act of supplying an execution scaffold itself.

Then do not make scaffolds globally mandatory.

### If both models degrade
Reject this scaffold approach for the current direction rather than adding more rules.
