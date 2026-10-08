# AI-PPT-Skill 对话交接与独立审查任务书

- 更新日期：2026-10-08
- 交接用途：新对话接手项目，**先独立审查当前 Skill 和最近一次依赖清理**；不立即生成 PPT、不继续扩建架构
- 仓库：<https://github.com/WanDa249/ppt-skill-test>
- 审查基线：`main`，在编写本文件之前的 HEAD 为 `e374330f4b7e63aa9b37d2b88b6369bb35f43f3c`
- 注意：本交接文件提交后 `main` 的 HEAD 会再次前进。**将上述 SHA 作为待审代码基线**；交接文档本身不计入 Skill 功能改动。
- 当前版本标记：`SKILL.md` 的 frontmatter 是 `version: 0.6.0`
- 状态：**最小依赖清理已合入，结构/文本检查已通过；独立审查、修改后实际执行验证尚未完成。**

## 一、项目定位和用户目标

这是一个面向不同 AI Agent 的**专业 PPT 设计流程 Skill**，而不是 PPT 应用、模板库、设计数据库或独立自动化平台。

它试图使 Agent 以可靠的证据与材料理解为基础，完成：
`材料理解 → 目标对齐 → 传播逻辑 → 页面任务 → Visual Intent → 可选参考 → 代表页渲染 → Visual Lock → 完整稿 → 可编辑重建 → 审查`。

用户最在意的不是单一案例偶然出一张好图，而是：

- **跨模型可用**：不同模型的能力不同，但尽量都不掉出正确的任务解空间；高能力模型仍保有审美和探索上限。
- **Professional Mode 真有专业价值**：提高探索、判断、表达和成品质量，而非 Baseline 加更多规则、更多确认和更多安全模板。
- **结构上守底线、视觉上保自由**：事实、页面角色、内容边界要可靠；视觉媒介、排版、色彩和风格不能被先验规则锁死。
- **小而美、验证优先**：不因为一张图不好就加一条规则；不为未来可能性提前造库/框架；风险、替代方案和非必要机制应主动指出。
- **真实证据优先**：不伪造走访照片、机构建筑、实证素材或未经确认的成果。需要影像而材料未给出时，明确使用中性占位。

### 两种模式的当前定位

`docs/WORKFLOW.md` 目前规定：

- Baseline Mode：方向清楚且可靠完成优先，完成必要决策与稳定交付。
- Professional Mode：高风险/评审/策略性或歧义大的演示，增加探索、方向比较、视觉验证和有价值的用户决策点。
- 原则：**Professional Mode improves decision quality, not system complexity.**

模式的具体执行边界仍值得独立审查，**不能把这段定位当成“已验证有效”**。

## 二、仓库中的权威材料与阅读顺序

建议新的审查 AI 先读：

1. [`SKILL.md`](../SKILL.md) — 主要执行规范；特别是 Step 2、Step 4、Step 5、Step 6、Step 7。
2. [`docs/WORKFLOW.md`](./WORKFLOW.md) — 流程和 Baseline / Professional 的定位。
3. [`AI_CONTEXT.md`](../AI_CONTEXT.md) — 项目阶段、边界和反过度建设原则。
4. [`README.md`](../README.md) — 对外定位。
5. [`docs/REFERENCE_DEPENDENCY_AUDIT_2026-10-08.md`](./REFERENCE_DEPENDENCY_AUDIT_2026-10-08.md) — 此次依赖审查的观点；**它是待审判断，不是不可质疑的结论**。
6. [本次最小清理 commit](https://github.com/WanDa249/ppt-skill-test/commit/e374330f4b7e63aa9b37d2b88b6369bb35f43f3c) — 必须看实际 diff，勿只依赖本交接。
7. 可选：[之前加入 role boundary 的 commit](https://github.com/WanDa249/ppt-skill-test/commit/a6090df38e9b13b99f07a0f059bece94c98084c8) — 检查是否保留、是否重复。

**请先从上述核心文件和 diff 做独立判断。** 只有出现需要核实的历史问题，才定向读取 `experiments/`；勿把里面的历史实验提示词当作当前 Skill 的执行规定。以下记录仅供回溯：

- [视觉探索 A′/B/C 阶段记录](../experiments/visual-exploration-stage-report-2026-09-30.md)
- [Taste Discovery α/β 实验协议](../experiments/taste-discovery-alpha-beta-v1.md)
- [Execution Scaffold v2 实验协议](../experiments/execution-scaffold-v2.md)
- [Role Contract 稳定性实验协议](../experiments/role-contract-stability-v1.md)
- [Professional Mode 三页 smoke test 协议](../experiments/professional-mode-role-boundary-smoke-test-v1.md)

**重要时效提示：** 早期 `experiments/` 文档的“待办”“Skill 尚未修改”等状态可能已经过时；2026-10-08 的当前 Git commit 和核心文件优先。旧审查文档里“当前缺失引用”的措辞描述的是**清理前快照**。

## 三、已发生的实际代码变更

### 1. 2026-09-30：最小 Role Boundary 增强

- commit：[`a6090df...`](https://github.com/WanDa249/ppt-skill-test/commit/a6090df38e9b13b99f07a0f059bece94c98084c8)
- 只修改 `SKILL.md`：
  - Core rules / 每页任务字段加入 `role boundary`；
  - Step 4 加入关键页面“负责什么、什么留给其他页”；
  - Step 5 增加 `slide-role drift` 检查；
  - Common failure modes 增加 `slide-role drift`。
- 未增加 Role Contract 模块、Gate、按模型分流或强制视觉模板。
- **状态：结构上很轻，逻辑有意义，但增益没有经过干净的旧版/新版对照证明。**

### 2. 2026-10-08：清理失效 references 依赖

- 审查文档 commit：[`e87c288...`](https://github.com/WanDa249/ppt-skill-test/commit/e87c288599806f5aaf5b94bcb4c397553843032d)
- 功能清理 commit：[`e374330...`](https://github.com/WanDa249/ppt-skill-test/commit/e374330f4b7e63aa9b37d2b88b6369bb35f43f3c)
- 原始问题：`SKILL.md` 宣称 Skill 可不依赖外部 reference 独立执行，却在 Step 2/5 把 5 个不存在的文件写成强制依赖：
  - `references/workflow-gates.md`
  - `references/visual-exploration.md`
  - `references/visual-quality.md`
  - `references/direction-library.md`
  - `references/reference-index.md`
- 实际操作：**没有补造这 5 个文件**；只改 `SKILL.md` 两处。
  - Step 2 的原外部 Gate A 引用改为内联条件：确有重大不同的中心叙事方向时，先暂停给用户做简短选择。
  - Step 5 的 Gate B / 强制预读段落改为：正式制作前根据下文条件解决视觉方向决策；已有可用的详细视觉系统则不强制重复选择。
  - 四个强制预读链接删除；其余 Visual Intent、可选 Reference Pack、代表页检查、Visual Lock、可编辑重建和 Step 7 审查保留。
- 修改前/后 `SKILL.md` 分别约 412 / 408 行；GitHub diff 只有两段。
- 已核实：`SKILL.md` 中无 `references/...` 残留链接；Gate A/B 仍在；可选 Reference Pack、role boundary、slide-role drift 仍在；此次未修改 `docs/WORKFLOW.md` 或 `AI_CONTEXT.md`。
- **尚未完成**：第三方独立审查；修改后的冷启动执行；在复杂真实任务中的价值验证。

### 需要独立审查者特别检查

清理外部依赖是否只是删除了 404，还是也意外削弱了重要的 Gate 行为？目前 Gate B 仍以“决策/分歧明显时比较备选”的文字表达，是否清晰到可由不同模型稳定执行？如果不清晰，**优先寻找更简短的语义修订，不先新增文件**。

## 四、实验历史：观察、解释与证据边界

本项目曾以“华中科技大学管理学院暑期社会实践现场答辩《数智兴农实践队》”为共同任务，测试 GPT-5.6 Sol、豆包不同模式的封面及三类代表页。

### A. 视觉方向 A′/B/C 和 Taste Discovery

- A′：依据当时 Skill 运行；B：较少限制的自由探索；C：B 加强参考图。
- 对多轮图像的用户反馈显示：高能力模型常能生成完成度较高的封面；强参考图可能提高风格一致性但缩小探索宽度；豆包曾多次出现“像设计作品却不像答辩封面”的角色漂移。
- 后续围绕“空间痕迹”“证据痕迹”做过 α/β、scaffold v1/v2、Original α 重复实验。
- **证据边界**：主观评价、生成模式差异、随机性和若干条件的来源标签混乱，不足以证明某一 prompt 技术有普遍因果效应。不能把“空间痕迹”固定成通用 PPT 风格规则。

### B. Original α vs 加入长篇 Role Contract

- 每个条件都曾收集 GPT、豆包各 3 次独立生成 × 2 张，用户观察到豆包加入 Role Contract 后更像封面，但相应样本也更集中在纸张/等高线/路线视觉。
- GPT 两组原本就较能维持封面角色；新增约束的边际收益不明确。
- **证据边界**：这是视觉样本趋势，非正式统计结论；长篇 Role Contract **没有被加入正式 Skill**，仅以更轻的 `role boundary` 吸收一部分思想。

### C. Professional Mode 三页 smoke test

任务要求：封面、证据/照片页、过程/路线页各一张，真实性边界明确，三页同一视觉系统但页型不同。

- GPT 实际送来的三张观察样本是“路线页、另一张路线页、封面”；没有看到按要求交付的证据页。封面视觉偏传统红色山水答辩风，路线页出现城市旅游地标式表达；这只能说明该次运行存在**必需页面覆盖失败、视觉/证据表达风险**，不能推断是 role boundary 造成。
- 豆包 Pro 三张分别对应封面、证据占位、路线，页型完整；豆包 Turbo 三张也覆盖这三类，但顺序为路线、证据、封面。二者都采用中性影像占位，观感与表达能力有所不同。
- 对比提示：强模型不保证执行绝对可靠；相对弱的模型通过整个 PPT 工作流也可能保住页型与事实边界。
- **重要实验效度问题**：
  - smoke-test prompt **本身明确写了每页不负责什么**，也就是把 treatment（role boundary 思想）泄漏到了任务输入；不能用这个试验证明那四处 Skill 修改有效。
  - 当时 `references/` 尚未清理；两次测试不等于现在新版本的完整验证。
  - 没有严格固定生产/渲染方式；不要把模型能力、渲染器能力和 Skill 文本效果混为一谈。
  - 以上仅为对话中用户交付图片的观察摘要；**图片文件不保证已经归档在 GitHub**。新对话若要逐张重新审美判断，需要用户提供相应图像，不能虚构图像证据。

### 目前可以说 / 不能说

**可以说：**
- 原 `references/` 强依赖确实不存在并与“Skill 可独立运行”的声明冲突。
- 此次代码变更消除了这些路径引用，至少在文本/结构层面让核心规范自包含。
- 页面角色漂移、任务完整性、虚构实证影像、过早视觉收敛是值得关心的质量风险。
- Skill 核心已有 Step 4/5/7 等机制，不应每次失败都新增一条硬规则。

**不能说：**
- 新版 Skill 已证明跨模型“稳定高质量”。
- role boundary 在严格因果意义上提高了生成质量。
- 增加更多风格禁令就一定可以提高 Professional Mode 的上限。
- GPT 与豆包在本轮样本的表现可以推广成总体模型排名。
- 删除五个引用就等于完整版 Professional Mode 已完成实证验证。

## 五、这次新对话真正要审查什么

请以**独立反对者/架构审查者**视角先判断，不要仅复述上述推荐结论。

### A. 功能是否被误删（最高优先级）

- `e374330...` 的实际 diff 是否仅删除坏依赖并内联了必要 Gate A/B？
- 清理后 Gate A/B 的**触发条件、暂停/继续条件、用户决策权、Visual Lock 前置要求**是否仍明确？
- 是否存在原强制引用承担了正文未覆盖的关键职责？注意原文件根本不存在，不能假设内容。
- 是否有看似删引用、实则改变交互强度或 Professional Mode 判断标准的问题？

### B. 可执行性与一致性

- Agent 冷启动仅凭 `README.md`、`SKILL.md`、`AI_CONTEXT.md`、`docs/WORKFLOW.md` 是否足以完成一次最小代表页任务？
- `docs/WORKFLOW.md` 与 `AI_CONTEXT.md` 的流程描述并非完全同文；这些差异是否实质影响执行？哪些只是摘要滞后？
- `SKILL.md` 中是否还有条件含混、重复或冲突，使不同模型走不同流程？
- Gate B 与可选参考图、Visual Intent、代表页验证、Visual Lock 的顺序是否能解释清楚？

### C. 是否值得保留、是否会使专业体验退化

- `role boundary` 是否在原 slide job 基础上提供了不同且必要的信息，还是只是在重复约束？
- 这四处改动是否足够轻？有没有重复、过度防御、限制视觉解法的隐患？
- 是否把 Baseline 错误理解为“最低审美下限”、Professional 错误理解为“更多步骤和审批”？
- 目前有没有证据支持新增第二套质量规范、方向库、参考索引或模型定制规则？若无，应明确否决。

### D. 实验结论的可信度

- 区分文本/结构检查、功能性 smoke test、主观视觉观察与因果实验。
- 不要以缺少 A/B 证据为由自动要求大规模重跑；先判断是否存在**必要且低成本**的下一步验证。
- 如果提议新的验证，要求明确被检验的机制、对照条件、是否会因测试 prompt 泄漏答案，以及停止条件。

## 六、新对话审查的交付格式

建议先交付一份**独立审查报告**，包含：

1. **明确总判定**：`KEEP / KEEP WITH MINOR FIX / REVISE / REVERT`；每个判定对应什么事实。
2. **阻断项（Blocking）**：如存在，必须指出准确位置、后果和最小修复；没有就明确“无”。
3. **必要改善（Necessary）**：每项解释为何已有文字不足以解决。
4. **可选改善（Optional）**：不混入必须修改。
5. **反对增加的内容（Reject/Defer）**：特别是任何额外 Gate、长篇 Prompt、设计模板/参考库。
6. **证据分级**：来自仓库正文、实际 diff、实验观测、推断分别标识。
7. **最小后续动作**：尽可能只做下一项必要的工作，避免重新进入无止境生成。

审查者可以与原助手意见相反；**无需为了体现创新或专业性强行找到改动项**。如果目前已足够合理，可以直接判定保持现状。

### 审查操作边界

- 这轮**先审查，不修改仓库，不提交、不推送、不生成 PPT**。
- 允许读取公开仓库和必要的公开最佳实践资料，但外部资料必须清楚标记，不能将其替代仓库事实。
- 如希望查看 `experiments/`，先完成核心文本的独立判断，再**按具体待核验问题定向读取**，避免历史预设污染独立审查。
- 不要因为 2026-09-30 的图片测试存在问题，就立即加一条通用禁止规则。
- 不要假设交接文档的结论一定正确；它是状态和待审问题的索引。

## 七、可直接发送到新对话的启动指令

> 我在继续审查一个 AI-PPT-Skill 项目，不是让你做 PPT。先阅读 GitHub 仓库 `WanDa249/ppt-skill-test` 中的 `docs/HANDOFF_20261008_AI_PPT_SKILL_REVIEW.md`，并以仓库中 `e374330f4b7e63aa9b37d2b88b6369bb35f43f3c` 为待审代码基线。
>
> 请按交接中的优先顺序，读取四个核心文件和 2026-10-08 依赖审查文件，**独立检查最近一次 Gate A/B 缺失依赖清理，以及之前的最小 role boundary 修改是否真的必要、准确、可执行**。
>
> 特别检查：是否误删关键流程、是否依旧存在逻辑断点、Professional Mode 是否被过度防御性规则压制、Baseline/Professional 是否保持“小而美”且不丢审美上限。
>
> 不要先看历史实验里的结论再替我下判断；只在必要时定向回查。请明确区分事实与推断，指出可以证实和不能证实的内容。
>
> 先提交 `KEEP / KEEP WITH MINOR FIX / REVISE / REVERT` 级别的审查报告及最小建议，不要直接修改仓库、生成 PPT、创建新机制或批量实验。允许质疑交接文档本身。

## 八、目前没有被授权执行的事情

- 继续改 `SKILL.md` / `docs/WORKFLOW.md`；
- 扩建 `references/` 为必读文件；
- 实施模型身份检测/动态路由；
- 自动开发视觉方向库、案例数据库或参考索引；
- 启动完整 20 页生成；
- 把某一套“空间痕迹”“纸张地形”“红色答辩”等个案视觉写为通用模板。

**交接到此为止。下一步应是独立审查，之后由用户决定是否接受建议并实施最小改动。**
