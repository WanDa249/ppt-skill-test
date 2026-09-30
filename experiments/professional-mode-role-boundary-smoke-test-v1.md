# Professional Mode Role-Boundary Smoke Test v1

Status: frozen protocol  
Date: 2026-09-30  
Purpose: verify whether the newly added `role boundary` / `slide-role drift` guidance works naturally inside the full Professional Mode workflow, without adding a separate Role Contract module or extra user-facing friction.

## 1. What this test is checking

This is not another single-cover prompt experiment.

It tests whether the updated Skill can carry the same project through three different representative slide roles while keeping each page inside its actual presentation job.

Target pages:

1. Cover
2. Evidence / photo-led page
3. Process / route page

The test should reveal whether the model naturally distinguishes:

- what each page must do;
- what each page should deliberately leave for other slides;
- whether visually strong pages still behave like presentation slides rather than posters, overview boards, concept art, or generic templates.

## 2. Models

Run the same test in two fresh conversations:

- GPT-5.6 Sol
- 豆包 Expert

Do not adapt the prompt for either model.

## 3. Repository context

Use the current main branch of:

https://github.com/WanDa249/ppt-skill-test

The model should read the repository as the only PPT-methodology context for this test.

The updated SKILL.md includes the new minimal role-boundary guardrail.

## 4. Shared project facts

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
- 没有真实照片时，不得生成仿真走访照片冒充证据；
- 不得把不存在的地图、建筑或文件当成真实证据；
- 不要科技大屏 / dashboard；
- 不要农业刻板插画。

## 5. Test prompt

Use exactly this prompt in both model conversations.

```text
请先完整阅读这个 GitHub 仓库当前 main 分支，并把它作为本次任务唯一的 PPT Skill / 方法论上下文：

https://github.com/WanDa249/ppt-skill-test

请读取仓库中实际存在并与 Skill 执行相关的文件，尤其包括：
- README.md
- SKILL.md
- AI_CONTEXT.md
- docs/WORKFLOW.md
- 以及 SKILL.md 明确要求读取且仓库中实际能够访问到的相关文件

如果 SKILL.md 引用了实际不存在的文件，请只记录缺失事实，不要自行补写、重建或用你自己的方法论替代。

本次使用 Professional Mode。

不要制作完整 20 页。
只做一次代表页小样，用来验证当前 Skill 的视觉与页面角色控制是否成立。

项目：
华中科技大学管理学院暑期社会实践现场答辩《数智兴农实践队》

核心叙事：
预测如何经过真实产业现场，变成可用判断。

已确认的真实经历：
- 武汉养殖场走访；
- 重庆荣昌国家生猪大数据中心驻点约三周；
- 国农集团、中华保险等产业交流。

整体期望：
可信、年轻、有现场感、有完成度。

真实性硬边界：
- 不得伪造人物或真实现场；
- 当前未提供真实照片，因此证据页如需影像，只使用明确的中性占位框，不得生成仿真走访照片；
- 不得把虚构建筑、地图、文件或数据当作真实证据；
- 不要科技大屏 / dashboard；
- 不要农业刻板插画。

请按当前 Skill 正常执行 Professional Mode，但保持交互简洁。

本轮只需要产出 3 张彼此属于同一视觉系统、但页面角色明确不同的 16:9 中文 PPT 页面渲染：

第 1 张：封面
标题：数智兴农实践队
副标题：华中科技大学管理学院暑期社会实践答辩
页面作用：建立项目识别与开场定调。
不要在封面完整讲完实践路线、全部地点、全部事实或方法。

第 2 张：证据 / 照片页
标题：深入一线，理解数据如何进入真实决策
证据标签仅使用：
- 武汉养殖场
- 重庆荣昌国家生猪大数据中心
当前没有真实照片，因此请使用明确的中性影像占位框。
页面作用：让“我们确实进入一线并驻点学习”成为视觉核心。
不要把它做成宣传海报、路线总览或成果汇总页。

第 3 张：过程 / 路线页
标题：从一线走访到产业交流
只使用这些节点：
武汉 → 重庆荣昌 → 成都 → 乐山 → 北京
页面作用：解释实践行动如何逐步深入产业场景。
不要把它做成第二张封面，也不要把所有成果、证据和结论一起塞进来。

三张必须属于同一视觉系统，但不能机械重复同一种版式。

先完成必要的内部判断和 Visual Intent。
除非当前 Skill 明确要求用户决策，否则不要长篇解释过程，也不要先输出设计方案。
直接进入代表页渲染。
```

## 6. What to inspect

Do not score aesthetics first.

Inspect these dimensions:

### A. Role fit
- Cover behaves like a cover
- Evidence page behaves like evidence
- Route page behaves like process/route

### B. Role boundary
- Cover does not take over route/explanation work
- Evidence page does not turn into promotional poster or summary board
- Route page does not absorb all evidence/results

### C. Cross-page coherence
- Same visual system
- Different page roles remain visually distinct
- No mechanical template repetition

### D. Factual/documentary discipline
- No fake people / fake site photos
- No invented evidence passed off as real
- Placeholders remain visibly placeholders where necessary

### E. Professional-mode headroom
- Pages should still show meaningful visual exploration
- The new guardrail must not reduce the deck to a generic safe template

## 7. Success criterion

The change is promising if both models:

- keep all three pages inside their intended presentation roles;
- avoid obvious slide-role drift;
- preserve cross-page visual coherence;
- keep enough visual freedom that the result does not collapse into a generic template.

The goal is not identical output across models.

The goal is:

> different visual solutions that stay inside the correct presentation-role solution space.

## 8. Stop condition

Do not modify SKILL.md again based on one run.

If the smoke test exposes a repeatable failure, record it first and decide whether it belongs in:
- core Skill;
- experiment notes;
- or model/rendering limitations.

Do not add a new rule merely because one generated page is weak.
