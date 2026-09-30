# Role Contract Stability Experiment v1

Status: frozen experimental protocol  
Date: 2026-09-30  
Stage: Cross-model robustness / variance reduction  
Purpose: test whether a lightweight presentation-role contract can reduce role drift and bad-tail variance on weaker models without suppressing the quality and diversity of stronger models.

---

## 1. Background

Stability testing on the same Original α prompt showed a clear difference between GPT-5.6 Sol and 豆包 Expert:

- GPT outputs varied visually but mostly remained inside the qualified solution space for a university social-practice defense cover.
- 豆包 Expert showed much larger variation in task role: some outputs behaved like presentation covers, while others drifted toward concept art, map visualization, spatial-model display, infographic, or design-portfolio work.

The problem therefore appears broader than “understanding 空间痕迹”.

Working hypothesis:

> A lightweight page-role contract may reduce role drift and catastrophic failures by reminding the model what this page is for, without specifying the final visual answer.

This experiment tests the hypothesis across repeated runs.

---

## 2. Research questions

1. Does Role Contract reduce role drift on 豆包 Expert?
2. Does Role Contract reduce output variance / bad-tail failures?
3. Does Role Contract preserve GPT-5.6 Sol quality-band consistency?
4. Does Role Contract preserve useful visual diversity rather than collapsing outputs into a generic university-defense template?
5. Can Role Contract become a candidate Baseline mechanism for cross-model robustness?

---

## 3. Existing baseline

Do not rerun Original α for this experiment.

Already collected:

- GPT-5.6 Sol Original α: 3 independent conversations × 2 images = 6 images
- 豆包 Expert Original α: 3 independent conversations × 2 images = 6 images

These serve as the control distribution.

---

## 4. New treatment condition

Run:

| Model | Condition | Independent conversations | Images per conversation | Total |
|---|---|---:|---:|---:|
| GPT-5.6 Sol | Original α + Role Contract | 3 | 2 | 6 |
| 豆包 Expert | Original α + Role Contract | 3 | 2 | 6 |

Total new images: 12.

Each conversation must be fresh.

Do not provide:
- GitHub / Skill;
- reference image;
- previous generated images;
- prior user feedback;
- information about which model performed better;
- any execution scaffold v1/v2.

---

## 5. Prompt

Use exactly this prompt on both models.

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

【Presentation Role Contract】

这是高校社会实践项目的现场答辩开场封面。

受众是现场评委。

这张页面的任务是：
- 建立项目识别；
- 完成开场定调；
- 让评委一眼读到项目标题，并感受到项目气质与核心方向；
- 为后续页面继续展开实践路线、证据、成果和方法留出空间。

这张页面不负责：
- 完整解释全部实践路线；
- 展示全部地点与事实；
- 承担信息总览页、宣传海报、展板、概念艺术作品或设计作品集页面的功能。

请保持封面应有的信息克制、明确视觉重心和投影环境下的可读性。

这段只定义页面角色与任务，不指定具体视觉风格、配色、字体、媒介或构图答案。
【Presentation Role Contract 结束】

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

## 6. Naming convention

### GPT
- G-RC-S1-1 / G-RC-S1-2
- G-RC-S2-1 / G-RC-S2-2
- G-RC-S3-1 / G-RC-S3-2

### 豆包 Expert
- D-RC-S1-1 / D-RC-S1-2
- D-RC-S2-1 / D-RC-S2-2
- D-RC-S3-1 / D-RC-S3-2

---

## 7. Evaluation dimensions

Do not evaluate only “which image is prettier”.

Compare the control distribution and treatment distribution on:

### A. Role stability
Does the output consistently behave like a university on-site defense cover?

### B. Semantic stability
Does “空间痕迹” remain a visual-organizing principle rather than collapsing into a random literal symbol?

### C. Quality-band consistency
How often does output fall below the usable threshold?

### D. Exploration breadth
Does visual diversity remain meaningful and task-compatible?

### E. Bad-tail rate
How many outputs are clearly:
- concept art;
- poster;
- infographic;
- portfolio work;
- information-summary page;
- or otherwise outside the cover role?

### F. Headroom preservation
On GPT, does the treatment preserve first-tier quality and visual individuality?

---

## 8. Desired distributional effect

The target is not identical outputs.

The target is:

> different visual solutions that all remain inside a qualified presentation-cover solution space.

For 豆包 Expert, success means:
- fewer role-drift failures;
- fewer “拉完了” outputs;
- more outputs in at least a usable-middle quality band.

For GPT, success means:
- no meaningful drop in quality;
- no collapse into a generic university-defense template;
- diversity remains.

---

## 9. Interpretation

### If 豆包 improves and GPT remains strong
Role Contract becomes a strong Baseline candidate.

### If 豆包 improves but GPT becomes generic
Role Contract may need lighter use for stronger models or delayed application.

### If 豆包 does not improve
Role drift may not be solvable through role framing alone.

### If both degrade
Reject the mechanism rather than adding more rules.

---

## 10. Current discipline

Do not modify Skill yet.

Do not create Role Contract v2 before this repeated test is complete.

Do not infer mechanism from one good or bad image.

Judge distribution shift, not isolated best-case samples.
