# AI 视频专业制作工艺 · 学习笔记（第二版：全技能贯通）

> 针对《Against the Headwind》MV 六条批评的系统性补课。方法来源：higgsfield 官方 skill 库（prompt / camera / pipeline / shotlist-director / character-design / soul-id / music-video / moodboard / style）。
> GitHub 实战挖掘（subagent 进行中，结论回来后并入第三版）。

---

## 总纲：专业 AI 制作 = 传统影视流程 + AI 约束层

传统影视流程：剧本 → 资产设计（设定板）→ 分镜 → 拍摄 → 后期。
AI 制作流程多了两层：**资产锁定**（identity/consistency）和**镜头词典**（Global Style Prefix + @-glossary）。

任何一个镜头"从概念直接跳到提示词"，都是不专业。这是第一条铁律。

---

## 一、剧本（Master Script）—— 对应批评 1

higgsfield-pipeline Step 02：剧本是独立文档，包含：故事/概念、场次顺序、人物、视觉风格、摄影规则、场景、情绪基调、连续性规则、**绝不允许出现的东西**。

关键纪律：**剧本写"发生什么"，提示词写"AI 怎么画"，两份文档绝不混在一起**。

MV 版：逐句拆解歌词 → 叙事节拍 → 每节拍的情绪曲线 → 分幕 → 每幕的时长预算（tempo budget：各镜时长加起来必须精确等于总时长）。

---

## 二、角色设定（Character Bible）—— 对应批评 3、4

来源：higgsfield-character-design + soul-id。

**world-first**：先锁世界（六维：物理/社会/经济/意识形态/历史/感官），再铸造角色。世界是一套约束，决定角色不得不成为谁。

**九问角色表**（9-Question Character Sheet）：主题角色、外部目标、内部目标、心理需求（伤自己的缺陷）、道德需求（伤别人的缺陷）、创伤、闪光点、剪影（跨房间一眼能认出的轮廓）、矛盾。**含糊的答案是敌人——必须是"只有这个角色能答出来"的回答**。

**视觉 DNA + Forbidden List**：色盘+材质+光线+世界"不是什么"（比如"不是赛博朋克霓虹，是青橙史诗"）。**明确世界不是什么，比色盘更能防跑偏**。

**screen test**：角色设计好不等于能用，先试演（试妆式测试）再进场。

**一致性四件套**（技术层）：
1. 同一段人物描述**逐字复制**进每一条提示词，一个词都不能差。
2. 人脸 ID 系统（soul-id）：5–20 张照片训练 → 身份一致性模型。免费档没有时，用首帧参考图 + 固定种子。
3. 链深度上限：无缝续接链最多 2–3 节，之后必须**用最初的 canonical 参考图重新锚定**，或用 B-roll 空镜打断链条（防逐代劣化）。
4. 上一镜的视频作为连续性参考喂给下一镜：风格可以变，人物和故事靠"上一镜" carry。

铁律：**Hero Frame 不对，绝不动畫**——人物在静帧里崩了，修图，不修提示词。

---

## 三、资产设定板（Asset Sheets）—— 对应批评 3

来源：ad-asset-prep 模板 + shotlist-director @-glossary。

开拍前先做三套板子，**全部经用户确认**：

| 板子 | 内容 |
|---|---|
| 角色设定板 | 正面/侧面/背面/四分之三/顶视图；表情板；服装板（含破损/淋湿等状态变化）；灰底；面部锁定裁剪（face-lock crop）；极端比例加尺寸参照框 |
| 道具设定板 | 多角度（前/侧/背/四分之三/顶），材质拆解 |
| 场景设定板 | location plate，定死空间结构 |

方法：**generate-many → test-in-motion → lock-the-winner**（多刷几版、动态里试、锁定最优），而不是"第一版能用就上"。

每条资产起名进 **@-glossary**（如 `@traveler` `@satchel` `@storm_plain`），每条带**保真等级**：
- full-preserve：原样保留（如主角脸）
- partial-preserve：保留风格/结构，细节可变
- attribute-transfer：只取属性（如质感、配色）
- loose-guide：宽松参考

---

## 四、导演分镜表（Shotlist）—— 对应批评 2、6

来源：higgsfield-shotlist-director。这是整套方法的心脏：**一份可交付的导演分镜 HTML 文档，不是聊天里的零散提示词**。

三层结构：

1. **Global Style Prefix（全局风格前缀）**：全片只锁一次——画幅、光线 doctrine、色彩比、镜头/快门、表演尺度、物理、构图、帧率。逐字拼进每一条提示词。**改一处，全片生效**。这是"编辑一次，全局传播"纪律。
2. **@-资产术语表**：人物/道具/场景各一起名，带保真等级。
3. **每镜提示词**：固定格式 `Style → Characters → Scene → CUT 1..N`，每条英文（模型吃英文），**每镜只讲 1 个主要动作**。每镜还要写：时长预算、**Off-screen 行**（人物从哪侧出画、最后状态——保证下一镜合法重入）、**银幕左右位置**、视线方向。

**MCSLA 公式**（每条视频提示词五层，缺一不可）：
- M = Model（用哪个模型）
- C = Camera（运镜+镜头）
- S = Subject（主体+资产@名）
- L = Look（风格+调色）
- A = Action（动作，只讲一个）

两道全片级检查：
- **节奏预算（tempo budget）**：各镜时长精确等于总时长；留一个 6–8s 的 **hero hold** 给高光时刻（music-video skill 特别强调：不要全片平均切碎）。
- **单调审计**：通读"景别+运镜"列，不允许连续三镜同景别同运镜。

---

## 五、摄影指导语言（Camera Language）—— 对应批评 5

来源：higgsfield-camera + higgsfield-prompt-skill。

### 运镜 = 情绪，不是装饰

相机是主角的**情绪替身**（camera as emotional double）：
- 愤怒/失控 → 呼吸感手持抖动（handheld breathing）
- 平静/坦然 → 顺滑呼吸感
- 悲伤/下沉 → 慢速下沉（slow sink）
- 震惊 → 静止 + 极慢推近
- 情绪崩溃 → 慢慢拉远，"给人物留空间"

**运镜错配情绪是 AI 味最重的破绽**。每个运镜必须回答：它在替人物表达什么情绪？

### 一镜一运镜

单镜只指定**一个主运镜**。复合运镜要写清时间分段（如"0–3s 跟摇，4–8s 推近"）。

**微运镜要写死距离+时间**（如"7 秒内只拉 10–15cm"）——不写死，模型会演过头，把"呼吸感"做成"过山车"。

### 镜头按用途选（配焦段+光圈）

| 用途 | 焦段 | 光圈 |
|---|---|---|
| 情绪特写 | 85/100mm | F1.4 |
| 对白双人 | 50mm | F2.0–2.8 |
| 全景 establishing | 35mm | F4–5.6 |
| 特写/插入 | 必须写"焦点锁定，无拉风箱" | — |

### 轴线纪律（用户点的"越轴"）

- 银幕方向锁死：人物从左往右走，下一镜不能反过来。
- 180° 规则：轴线两侧不许跳，除非有中性镜/切动作过渡。
- 有人物离场必须记 Off-screen 行（从哪侧出、最后状态），保证下一镜从正确一侧进。
- 相邻镜尽量用**重复锚动作**做 match cut（切动作不断）。
- 2 人以上或有关键道具/复杂机位的戏，先画**俯视走位图**（top-down schema），走位用绝对距离写进提示词（"A 距 B 2 米"），不让模型自己脑补空间关系。

### 用光

每镜写明光源、光质、光位（motivated practical light：光要有来源——灯笼、黎明、闪电）。三幕光比（夜/风暴/黎明）先定死再生成。

### 风格层（moodboard / style skill）

- 用**参考图集合**（20+ 张同风格）做 style layer，比文字描述更稳。
- 全片调色词典：每个情绪一个调色词条（如 cold thriller = "teal and orange, desaturated, high contrast"），写进 Global Style Prefix。

---

## 六、故事板（Visual Storyboard）—— 对应批评 6

来源：higgsfield-pipeline Step 03（Popcorn）。

**Popcorn 阶段：先出全片关键帧（静帧故事板），用户逐张确认，再进视频**。静帧便宜，视频贵。这是成本纪律，也是审阅纪律。

故事板每张要能看出：景别、机位、人物位置、光位、情绪。不是"好看的图"，是"能拍的图"。

---

## 七、生成纪律（Generation Discipline）

来源：higgsfield-pipeline Steps 05–08。

1. **Generation Ledger**：每一次生成（采用/废弃/报错）记一笔，算出 takes-per-kept，为后续项目定预算。
2. **80% 规则**：只修坏掉的部分，不动好的 80%；每个修好的坑变成一条新的 negative rule。
3. **连续性参考链**：Pipeline E——上一镜的视频作为下一镜的连续性参考。
4. **Picture Lock**：粗剪 → 生成监督（declared 窗口内重刷坏镜）→ 精剪 → 锁画。**锁画后不再生成**（否则调色和声音永远开不了工）。
5. **调色的第一任务是统一**：各镜自带 baked-in 调子，调色的首要工作是把相邻镜统一成"同一部片子"，其次才是风格化。
6. **Picture Lock 后原则上不再生成新镜头**。

---

## 八、对比：旧流程缺了什么

| 专业流程 | 旧 MV 流程 | 缺失 |
|---|---|---|
| Master Script（剧本） | 只有镜头表 | ❌ |
| 九问角色表 + 视觉 DNA + Forbidden List | 只有文字角色描述 | ❌ |
| 角色/道具/场景设定板（多角度） | 无 | ❌ |
| Global Style Prefix + @-glossary | 每镜独立提示词 | ❌ |
| Off-screen 行 + 银幕方向台账 | 无 | ❌ |
| 一镜一运镜 + 运镜情绪映射 | 运镜随意 | ❌ |
| 静帧故事板先行确认 | 直接进视频 | ❌ |
| Generation Ledger | 无 | ❌ |
| Picture Lock 纪律 | 无 | ❌ |

---

## 九、GitHub 实战挖掘结论（2026-10-05，报告全文：`~/workspace/study/ai-video-github-research.md`）

深入读了 8 个仓库 + 3 个补充来源。核心共识：**专业 = 前期设计 + 一致性工程 + 失败分诊**，不是"更好的形容词"。

### 1. Identity String 契约（DirectorSKILL）——人物一致性的标准答案

一条 30–50 词的名词短语，**逐字粘贴**进每一镜，不改写、不缩写、不"优化"。配方（按顺序）：
1. 1–2 个人口学锚点（年龄写具体数字）
2. 2–3 个面部结构事实（下颌、眼距、眉、鼻、发际线——模型真正重建的是这些）
3. **恰好 1 个可核查的独特标记**（痣/疤/缺牙——QC 手柄，半秒看出漂没漂）
4. 1 个发型规格
5. 1 个服装锚点放最后（远距离可核查的细节）

禁区：情绪形容词、机位词、明星类比、年龄区间、"和参考图保持一致"这类否定式记忆指令。

配套：Continuity Bible——服装分层（外/中/下/鞋/配饰，每层颜色+材质）、道具状态演进带、seed 与参考登记表、**状态变更台账**（每镜状态最多推进一格，跳两格=观众觉得缺了一镜）。

### 2. Identity vs. Motion 分离（铁律，higgsfield-ai-prompt-skill）

提示词拆两块：Identity Block 只写静态描述，Motion Block 只写时间性内容。混写=脸在中段融化。

### 3. Continuation 五规则（末帧续接法的专业版）

1. 第一句写清上一段最后一帧的画面（姿态、画中位置、视线）
2. Identity 块逐字粘贴
3. 上一段只用一句话做"次级记忆"，不重述动作
4. 新动作从上一段最后一帧的**下一帧**开始，无时间跳跃
5. **不许重复动作**：续段写上一段动作之后的事，而不是再做一次

跨段必须携带：身份、服装、环境（建筑/光质/调色/空气颗粒）、**情绪延续**。

### 4. 失败手册 F1–F19 + 成本阶梯 L1–L7 + 三振规则

成本阶梯（按"扔掉多少工作量"排序）：L1 改提示词 → L2 改参数 → L3 原样重抽（限 2 次，同一种失败连续两次=确定性失败，停手）→ L4 重做关键帧 → L5 **重排这镜**（更短、更近、更简单、拆分）→ L6 剪辑里修 → L7 砍掉这镜。

**三振规则**：同一镜失败 3 次，改设计不改提示词（缩短 40–50%、推近一档、简化到一个动作、拆两镜、换反应镜头、让动作出画只拍结果）。

关键诊断经验：
- F1 人物漂移：主因是**时长**（错误随帧序号累积，静止片段也花光 identity 预算），其次是头部转动超 ~45°、锚图人脸不足画面 15%。修法：时长砍到 3–5s、关键帧推近到 MCU、identity 锚点名词重述。
- F2 PPT 感：提示词在描述一张画而不是一个事件。修法：写三层运动（身体/衣发/环境至少两层）+ 给身体一个重心转移 + 关键帧摆成"动作中"。
- F5 无终态：诊断第一问永远是"你能一句话说出这镜最后一帧是什么吗"——说不出就是 F5。
- 连续两次原样重抽失败方式**相同**=确定性失败（改计划）；**不同**=随机性，再抽一次合理。

### 5. MiniMax 适配器（直接对应 raphael.app 免费档）

- 括号运镜指令 `[推镜]` `[固定镜头]` 比散文运镜可靠，每片段最多 2 个。
- **语言必须跟界面走**：国内 UI 全中文提示词，国际版英文，不要混——中文人物描述放在英文提示词里绑定很弱。
- 写表情终点不写情绪："ends on a small held half-smile"，不写 "she looks happy"。
- 运动预算上限 5。

### 6. 提示词微观纪律

- 50–80 词最佳，三句话：①主体+动作 ②运镜+风格 ③约束/正向锁。70 词稳定打败 200 词。
- 杀死空形容词：cinematic/epic/beautiful 换成窄指代（"golden-hour backlight, long shadows stretching forward"）。
- **"fast" 是最高降级词**：写物理不写速度（"feet striking hard, each stride at full extension"）。
- 提示词正文不写否定词（"no jitter" 会被渲染出来），用正向约束句："Face stable. Limbs anatomically natural."
- 同形异义陷阱：tearing=撕碎/流泪，draw=拉/画画/拔枪——换只有一种长相的说法。
- 参考集打败单张参考；描述情境和动作，永不重述主体（有参考图时）。

### 7. 轴线几何的 AI 编码版

- 180° 轴线：写进 continuity bible 逐场景字段，**在关键帧里强制执行**——关键帧是管线唯一的记忆。每张关键帧提示词写清画面位置和视线方向，永不让模型自己决定人物朝哪看。
- 合法过轴 5 种方式：人物移动重构轴线（免费）→ 运镜带过 → 切轴线中性镜头 → 切走重建 → 广角重建（最钝）。
- 30° 规则：相邻同主体镜头机位夹角至少 30° 或景别差两档，否则像卡顿。
- 视线是向量：水平方向、高度（坐看站要抬头，高度错配是最常见的业余错误）、距离。
- 出画/入画配对：右出画 → 下一镜左入画。最便宜的接缝：上一段"she walks fully out of frame right"，下一段"frame starts empty, she enters from frame-left"。

### 8. 可直接用于 raphael.app 免费档的改造清单（P0/P1/P2）

**P0（不花钱，下次开工前必须做）**：identity string 契约、全中文提示词+括号运镜、Continuation 五规则、one-dominant-move、银幕方向锁死（"从画左走向画右，右出画"）、三振规则。

**P1（花时间不花钱）**：四个黄金参考位（正/左/右脸+露脸全身）、Continuity Bible 轻量版、按 Verse/Chorus/Bridge 写节拍视觉模板（副歌每 4 小节重复+变奏）、视觉分镜故事板、夜景压制清单（"深黑阴影不提亮、路面干燥不反光"）。

**P2（新工具/额度）**：Nano Banana 参考图管线试验、emulsion 灰盒预可视化、DirectorSKILL 本地安装（MIT，可装，等用户决定）。

**明确不适用的**：Soul ID / LoRA / 种子锁定（免费档没有控制面，用 identity string + 参考图 + 4s 短片段代替）；Seedance 时间码长提示词（4 秒一段用不上）。

### 仓库索引

| 仓库 | 星数 | 一句话 |
|---|---|---|
| wuwangzhang1216/DirectorSKILL | 158 | AI 电影导演 skill：identity 契约、轴线几何、F1–F19 失败手册、MiniMax 适配器 |
| OSideMedia/higgsfield-ai-prompt-skill | 684 | MCSLA、Identity/Motion 分离、Continuation 五规则、角色锚点块 |
| beshuaxian/higgsfield-seedance2-jineng | 880 | 15 个 Seedance 技能，含音乐视频导演指南（节拍同步模板） |
| ZeroLu/awesome-seedance | 2601 | Seedance 提示词库：时间码序列、参考角色句式 |
| kaigani/codeywood | 32 | 参考图管线架构（Nano Banana Pro 权重 0.85–0.95，不用 LoRA） |
| dennisonbertram/emulsion | 11 | three.js 灰盒 blocking，导出运镜参考喂视频模型 |
| xiaoweihu339-afk/character-anchor-skill | 3 | 黄金参考画廊：正/左/右脸+全身四个参考位 |
| apimageorg/apimage-skills | — | 参考集>单张；描述情境动作、不重述主体 |
