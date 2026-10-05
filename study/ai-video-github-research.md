# AI 视频 / AI 电影制作：GitHub 实战经验挖掘报告

> 研究时间：2026-10-05。方法：`github search_repositories` + 全文抓取 README 与核心参考文档 + 公开网页搜索交叉验证。
> 深入阅读 8 个仓库（DirectorSKILL、higgsfield-ai-prompt-skill、higgsfield-seedance2-jineng、codeywood、emulsion、character-anchor-skill、awesome-seedance、apimage-skills），外加 3 个补充来源。
> 目标：回答"怎样把 AI 视频做专业"，并给出**可直接用于 raphael.app 免费档 MV 流程**的具体改造清单。

---

## 一、总览：专业派 vs 堆料派

所有高质量仓库的共识只有一句话：**专业 = 前期设计 + 一致性工程 + 失败分诊**，而不是"更好的形容词"。

| 维度 | 业余做法（我们上次 MV 的做法） | 专业做法（仓库共识） |
|---|---|---|
| 人物一致性 | 一段文字描述，每镜重写一遍 | 冻结的 identity string（逐字复制）+ 人物参考图 + 多角度参考集 |
| 运镜 | "slow push in" 一句话带过 | 几何级精确的运镜描述（dolly vs zoom 的物理区别）+ 每镜只许一个主运镜 |
| 轴线/方向 | 没管 | 180° 轴线、30° 规则、银幕方向写进分镜纪律，写进提示词 |
| 失败处理 | 感觉不好就重跑 | 编码失败手册 F1–F19 + 成本阶梯 L1–L7 + 三振规则 |
| 流程 | 文字分镜 → 直接生成 | 剧本 → 节拍 → 导演书 → 走位 → 分镜表 → 关键帧 → 视频提示词 → 声音 → 剪辑 → QC，每步有交付物 |

---

## 二、wuwangzhang1216/DirectorSKILL ★158 —— 最值得吃透的一个

链接：https://github.com/wuwangzhang1216/DirectorSKILL

一个 Claude Code skill，把剧本/一段话/一张关键帧变成完整制作方案：节拍表、导演书、走位、分镜表、关键帧提示词、视频动作提示词、声音方案、剪辑时间线、连贯性圣经、QC 修复环。核心观点：**大多数"电影感"提示词是形容词堆砌，模型不知道机位在哪、身体在做什么、动作终点在哪。**

### 2.1 Identity String 契约（解决"人物不一致"的标准答案）

- **定义**：一个 30–50 词的名词短语，完整重述人物，**逐字粘贴**进每一镜的关键帧提示词和视频提示词。**永不改写、永不缩写、永不"优化"**。写一次，之后只复制不重打（重打=改写=漂移）。
- **配方（按顺序）**：1–2 个人口学锚点（年龄写具体数字，不写"30多岁"）→ 2–3 个面部结构事实（下颌、眼距、眉、鼻、发际线——模型真正重建的是这些）→ **恰好 1 个可核查的独特标记**（左侧嘴角下方的痣、疤的长度、缺角的门牙——这是 QC 手柄，半秒钟就能看出漂没漂）→ 1 个发型规格（长度、剪裁、分缝/扎法、方向）→ 1 个服装锚点放最后（服装、颜色、材质、一个远距离可核查的细节）。
- **禁区**：情绪形容词（beautiful/mysterious）、机位镜头词（close-up/85mm——这些槽位提示词别处管）、明星类比（"像年轻时的梁朝伟"——每个模型解析都不同）、年龄区间、"和参考图保持一致"这种否定式记忆指令（模型没有记忆，绑定参考图是控制面，不是句子）。
- **示例**（46 词）：`MEI, 24, a Chinese woman with an oval face, thin straight eyebrows, a small mole below the left corner of her mouth, black hair cut blunt at the jaw and tucked behind her right ear, in an army-green cotton postal jacket with a red collar tab`
- **配套**：Continuity Bible 还规定了 wardrobe schema（服装分层：外/中/下/鞋/配饰，每层颜色+材质）、prop schema（道具描述+状态演进带）、location schema、**seed 与参考登记表**、**状态变更台账**（每镜状态最多推进一格，跳两格=观众觉得缺了一镜）。

### 2.2 连贯性几何（越轴、30° 规则、银幕方向、视线匹配）

仓库明确指出：**视频模型不知道上一镜机位在哪**，所以每条规则都要给出"怎么编码进关键帧/提示词让无状态生成器遵守"。

- **180° 轴线**：把轴线写进 continuity bible 的逐场景字段（"axis: corridor runs camera-left to camera-right; ANNA always screen-left facing right"），**在关键帧里强制执行**——因为关键帧是管线唯一的记忆。每张关键帧提示词明确写画面位置和视线方向："Anna occupies the left third of frame, in three-quarter profile, looking off-screen to the right." 永不让模型自己决定人物朝哪看。
- **合法过轴的 5 种方式**（按打断程度排序）：人物移动重构轴线（免费）→ 运镜带过轴线 → 切轴线上的中性镜头再落到新一侧 → 切走再重建 → 广角重建（最钝）。
- **30° 规则**：相邻同主体镜头机位夹角至少 30°，或景别差两档，否则切出来像卡顿。AI 版写法：把新角度写成可见内容（"now from her other side, the window is behind her left shoulder instead of her right"），同时换景别。
- **银幕方向**：运动方向必须活过剪辑点。写法："she walks from frame-left toward frame-right, exiting right"。**不要写 "she walks away"**——模型会自己选方向。
- **视线匹配**：视线是向量，三要素——水平方向（A 看画右，B 的反打必须看画左）、高度（坐着的人看站着的人要抬头，高度错配是最常见的业余错误）、距离。拍不好就生成一个双人镜头再裁出两个单人，几何天然正确。
- **出画/入画**：右出画 → 下一镜必须左入画；朝向/背向镜头出画是中性重置。AI 拼接最便宜的接缝：明确要求上一段"she walks fully out of frame right, leaving the empty doorway"，下一段"frame starts empty, she enters from frame-left"。

### 2.3 镜头词汇表（解决"运镜业余"的标准答案）

- **dolly 和 zoom 不是一回事**，很多模型会坍缩成同一个中央裁剪。必须写几何变化：
  - 推镜："the camera moves forward through the space toward her; she grows faster than the wall behind her, which spreads out past the frame edges; the focal length does not change"（不要写 "zoom in"）
  - 横移："the camera slides left along a line parallel to the wall; foreground posts pass faster than the far wall"（不要写 "pan left"）
  - 摇镜："the camera stays in place and rotates left"（不要写 "moves left"）
  - 升降："the camera rises straight up about one metre, staying level"（不要写 "tilt up"）
- **One-dominant-move 规则**：一个生成片段只许一个主运镜，命名它并**点名禁止**其余的："Camera: one move only — a slow dolly in along the lens axis. The camera does not pan, tilt, zoom, orbit, roll, or shake."（禁止运镜名词是安全的，不会像禁止物体名词那样把东西召唤出来。）
- **速度限定词只做相对排序**：very slow < slow < steady < brisk < fast；brisk 以上人脸手部大概率劣化——要速度又要脸，就拆成两镜（身体快镜 + 脸慢镜）剪接。
- **用光写法**：永远写光源和它落在什么表面上，不写情绪。"a single gas-mantle lamp behind him throws a hard rim on his wet shoulders" 胜过 "moody backlight"。材质词比风格词管用（"wet asphalt" 自带镜面反射约束，"cinematic" 只返回平均值）。
- **夜景会被模型"美化"**（阴影提亮、统一白平衡、凭空加湿反光路面和雾气）：对策是正面压制——每个光源单独写颜色和方向（"sodium vapour from camera-left, cold mercury from camera-right, mixed colour temperatures, never balanced"）、写明地面状态（"dry pavement" / "matte asphalt, no standing water"）、给画面黑暗预算（哪部分允许看不清）。

### 2.4 失败手册 F1–F19 + 成本阶梯 + 三振规则（解决"瞎重跑"）

- **成本阶梯 L1–L7**（按"扔掉多少工作量"排序）：L1 改提示词 → L2 改参数（降时长/降运动强度/锁种子）→ L3 原样重抽（限 2 次，连续两次同一种失败=确定性失败，停手）→ L4 重做关键帧 → L4.5 视频转视频只修表面（光/色/构图）→ L5 **重排这镜**（更短、更近、更简单、拆分）→ L6 剪辑里修（0.5s 的修剪胜过第 4 次生成）→ L7 砍掉这镜。
- **三振规则**：同一镜设计失败 3 次，**改设计不改提示词**。7 种改法：缩短 40–50%、推近一档景别、简化到只剩一个动作、拆成两镜、首尾帧、替换（用反应镜头/空镜代替动作）、出画（让动作离开画面只拍结果）。
- **最有用的诊断经验**：
  - F1 人物漂移：主因是**时长**（错误随帧序号累积，与动静无关——静止片段也花光 identity 预算），其次是头部转动超 ~45°、锚图太小（人脸不足画面高度 15%）。修法：时长砍到 3–5s、关键帧推近到 MCU 让人脸占更多像素、把 identity 锚点写成名词重述。
  - F2 PPT 感：提示词在描述一张画而不是一个事件。修法：写三层运动（身体/衣发/环境，至少两层）+ 给身体一个重心转移 + 关键帧摆成"动作中"（手已抬起、脚已离地）。
  - F5 无终态：诊断第一问永远是"你能一句话说出这镜的最后一帧是什么吗"——说不出就是 F5，提示词本来就没有终点。
  - F7 跨镜断裂 / F19 物体消失：转场拆到剪辑点上，不要让一个片段同时包含"动作+转场"。
  - 连续两次原样重抽失败方式**相同**=确定性失败（改提示词/关键帧/计划）；失败方式**不同**=随机性，再抽一次合理。

### 2.5 Hailuo / MiniMax 适配器（直接对应 raphael.app 免费档！）

- MiniMax 强项：**单张人像的主体一致性**、一拍完成的动作、括号式运镜指令。
- 打法：subject reference（人物参考）+ 运镜括号 + 动作 + 环境 + 终态。**括号运镜指令**（如 `[Push in]` `[Static shot]`）比散文式运镜描述更可靠，每片段最多 2 个。
- **语言必须跟界面走**：国内 UI 用中文写提示词（含术语），国际版用英文，**不要混**——中文人物描述放在英文提示词里绑定很弱。括号运镜指令用对应文档的语言。
- 典型失败：人脸"演太多"，表情夸张循环。修法：**写表情终点不写情绪**——"ends on a small held half-smile"，不写 "she looks happy"。
- 运动预算上限 5；两个括号运镜指令已花掉 1–2。

---

## 三、OSideMedia/higgsfield-ai-prompt-skill ★684 —— Higgsfield 提示词体系

链接：https://github.com/OSideMedia/higgsfield-ai-prompt-skill

32 个子 skill，覆盖 Kling 3.0、Veo 3.1、Seedance 2.5/2.0、MiniMax Hailuo 等。最有价值的几条硬规则：

### 3.1 MCSLA 公式（每个视频提示词五层）

**Model · Camera · Subject · Look · Action**，五层缺一不可。以及硬纪律：平台词汇（运镜预设名、模型名、参数名）必须来自实测文件，**不许编**；长宽比是枚举值不是自由文本（2.35:1 是风格词，不是输出比例）。

### 3.2 Identity vs. Motion 分离（铁律）

有角色引用时，提示词必须拆成两块：**Identity Block 只写静态描述**（脸、服装、体型、标记、配色），**Motion Block 只写时间性内容**（运镜、动作、速度、环境变化）。混在一起写会导致模型在处理运动时重读脸部描述 → 脸在中段融化。

### 3.3 Character Anchor Block（每镜十要素）

角色表是"搭建时"的，Anchor Block 是"拍摄时"的——每个出镜角色每镜写清：1 身份 2 画面位置（定性+百分比坐标）3 景深层 4 占画比 5 身体朝向 6 姿态 7 视线方向 8 接触点（靠着什么）9 状态锁（累/伤/湿透）10 表情。
**多状态角色要做多套表**（打斗受伤的五个阶段=五套角色表），靠提示词文字追踪状态必然在迭代中丢失——这是场记的纪律。

### 3.4 Seedance Continuation 五规则（我们的"末帧续接法"的专业版）

1. **末帧锚**：第一句写清上一段最后一帧的画面（姿态、画中位置、视线）。
2. **Identity 块逐字粘贴**，不改写不缩写。
3. 上一段只用一句话做"次级记忆"（"following her glance back"），不重述动作。
4. 新动作从上一段最后一帧的**下一帧**开始，无时间跳跃。
5. **不许重复动作**：上一段结尾是"她拔出武器"，续段写她拔出之后做什么，而不是再拔一次（重复=前一拍重播）。
- 跨段必须携带：身份、服装、环境（建筑/光质/调色/空气颗粒）、**情绪延续**（上一段结尾是紧绷的，续段开头身体上还得是紧绷的）。
- 扩展技巧：把已有片段作为 **video reference** 挂上，提示词以 **"The scene continues."** 开头，模型从片段结尾续写；前传用 "Show me what happens before"。

### 3.5 Seedance 提示词六槽公式 + 注意力模型

`[Camera movement] + [Subject] + [Action] + [Setting] + [Style] + [Lighting]` ——六槽是完备性清单（缺 3 个以上容易被过滤），但**注意力从左到右递减**：第一句权重最高。最佳实践：50–80 词，三句话——①主体+动作 ②运镜+风格 ③约束/正向锁。70 词的提示词稳定打败同结构 200 词版（词多=扩散，不是控制）。
- **杀死空形容词**：cinematic/epic/beautiful 不指向任何具体分布，要替换成窄指代——"cinematic lighting" → "golden-hour backlight, long shadows stretching forward"；"cinematic" → 具体导演技法或镜头规格。
- **"fast" 是最高降级词**：与复杂动作/运镜叠加时直接糊。写物理不写速度："feet striking hard, each stride at full extension" 而不是 "runs fast"。
- **Seedance 提示词正文里不写否定词**：没有 negative embedding 架构，"no jitter" 会被当成场景描述渲染出来。用正向约束句："Face stable. Limbs anatomically natural. Consistent lighting, no flicker."
- **同形异义陷阱**：动词发货前自查——这个词有没有第二种"长得不一样"的物理含义？（tearing=撕碎/流泪，draw=拉/画画/拔枪……）有就换成只有一种长相的说法。

### 3.6 参考角色模式

`@Image` / `@Video` / `@Audio` 显式角色引用；Seedance 句式如 `"[Image2] is in the interior of [Image1] where he is kept the style of [Image2], but the realism of [Image1] remains."`；时间码序列写法 `[0-4s]: ... [4-8s]: ...` 逐段升级镜头（见 awesome-seedance §1.5 的武士/宇航员/霓虹东京三例，含运镜+声音设计）。

---

## 四、beshuaxian/higgsfield-seedance2-jineng ★880 —— 音乐视频专项

链接：https://github.com/beshuaxian/higgsfield-seedance2-jineng

15 个 skill，其中 `skills/10-music-video/SKILL.md` 是**音乐视频导演指南**，`01-cinematic` 带运镜百科。

- **2 秒钩子框架**：10+ 种开场抓注意力模式（MV 前 2 秒决定留存）。
- **节拍同步模板**（可直接套用）：按 VERSE / CHORUS / BRIDGE / FINAL CHORUS / OUTRO 分段，每段写能量等级、视觉焦点、3–5 个具体视觉点、"在 [时间点] 的 [节拍] 上做 [视觉动作]"、副歌的**重复策略**（"每 4 小节重复该视觉，加 [变化]"）、颜色/灯光切换点。
- **能量弧线匹配歌曲结构**：intro 低能量 → verse 铺陈 → chorus 峰值 → bridge 转折 → final chorus 爆发 → outro 收束；粒子/运动强度峰值对准 drop 点。
- 每个 skill 含 15–20+ 种运镜技术的**精确措辞**、灯光氛围方案、声音设计（环境音/拟音/音乐/静默）。

---

## 五、角色一致性：codeywood / character-anchor-skill / apimage-skills

### kaigani/codeywood ★32 —— 参考图管线的架构答案
链接：https://github.com/kaigani/codeywood

关键技术决策：**用 Google Nano Banana Pro 的参考图一致性（reference weight 0.85–0.95），不用 LoRA**。管线：`故事 → 角色/场景定义 → 参考图库 → 分镜图 → 视频`，每一阶段用上一阶段的**图**做参考输入，而不只是文字。skill 按阶段设质量门（v0.1 剧本圣经 → v0.2 参考图库 → v0.3 视频化）。

### xiaoweihu339-afk/character-anchor-skill ★3 —— 黄金参考画廊
链接：https://github.com/xiaoweihu339-afk/character-anchor-skill

把杂乱的角色素材沉淀成"黄金参考画廊"再用的工作流。硬性要求**四个黄金参考位**：`front-closeup`（正面特写）、`left-closeup`（左半脸）、`right-closeup`（右半脸）、`full-body-face-visible`（露脸全身）。参考不全时允许生成但必须警告漂移风险。核心：**角色锚点不只是脸**，体型、服装逻辑、气质是次级锚点。

### apimage-skills/character-consistency-video —— 两条金句
链接：https://github.com/apimageorg/apimage-skills/blob/HEAD/skills/character-consistency-video/SKILL.md

1. **参考集打败单张参考**：一张正脸只给模型一个视角，三四个角度才抓得住。
2. **描述情境和动作，永远不要重述主体**：参考图管身份，提示词再描述外貌会跟参考图打架导致漂移。（与 DirectorSKILL 的 identity string 是两条路线：有参考图时用这条，纯文字时用 identity string。）

### 网页交叉验证（dcaipulse / OpenArt / YouTube 教程共识）
- 身份测试五连拍：正面特写 → 3/4 身 → 侧脸 → 低角度全身 → 过肩，侧脸是最强试金石（鼻子/下巴/发际线最容易崩）。
- 角色表标准版式：两排——上排全身四视图（正/左/右/背），下排三张脸部特写；中性背景、统一布光、A-pose。
- 先锁定身份再换环境：每次只变一个变量（先换环境不换光，稳定了再动别的）。

---

## 六、预可视化：dennisonbertram/emulsion ★11

链接：https://github.com/dennisonbertram/emulsion

一个 Claude Code skill 自带 three.js 应用：用方块小人**搭 blocking**（走位+运镜关键帧），导出运镜/运动参考片段喂给视频模型。Agent 在应用里实时操作、用户可上手改。**这就是"分镜故事板"的动态版**：在烧生成额度之前，先把机位、走位、轴线、银幕方向用灰盒子验证一遍。

---

## 七、镜头语言速查（综合多源）

| 写清楚 | 业余写法 | 专业写法 |
|---|---|---|
| 推镜 | zoom in / push closer | the camera moves forward through the space toward her; she grows faster than the wall behind her; focal length unchanged |
| 拉镜 | zoom out | the camera moves backward, revealing more of the room at the frame edges |
| 横移 | pan left | the camera slides left parallel to the wall; foreground passes faster than the far wall |
| 摇镜 | moves left | the camera stays in place and rotates left |
| 升降 | tilt up / camera goes up | the camera rises straight up about one metre, staying level |
| 环绕 | rotate the camera | the camera circles her clockwise ~30°, keeping her centered; background sweeps |
| 手持跟拍 | shaky cam | handheld, level with his shoulders, drifting right with him; small natural instability, no whips |
| 移焦 | focus on her | focus shifts from the glass in foreground to her face; framing unchanged |
| 固定 | （不写） | the camera is locked on a tripod and does not move |
| 用光 | moody backlight | a single gas-mantle lamp behind him throws a hard rim on his wet shoulders |
| 速度 | fast | feet striking hard, each stride at full extension, arms pumping at 90 degrees |
| 表情 | she looks happy | ends on a small held half-smile |
| 方向 | she walks away | she walks from frame-left toward frame-right, exiting right |

**结构公式**（二选一，勿混用）：
- Seedance 六槽：`[运镜] + [主体] + [动作] + [场景] + [风格] + [用光]`，50–80 词。
- 通用五要素：Subject / Context / Action(一镜只许一个主动作) / Camera motion / Composition / Lighting & Ambiance。

---

## 八、可直接用于"零成本 raphael.app 免费档 MV"的改造清单

按投入产出比排序。raphael.app 免费档的现实约束：480P/4s/0 积分、MiniMax H3 Turbo、无种子控制（大概率）、网页手工操作、无 API。

### P0：不花钱、立即能用的（下次 MV 开工前必须做）

1. **Identity String 契约**（DirectorSKILL §2.1）：给主角写一条 30–50 词身份串，含 1 个可核查标记（痣/疤/缺牙），**逐字复制**进每一张关键帧和每一段视频提示词，不再每镜重写。这是免费档人物一致性唯一可靠的缰绳。
2. **中文写提示词**：raphael 国内 UI → 全中文提示词（含术语），不中英混排。MiniMax 括号运镜指令 `[推镜]` `[固定镜头]` 每段最多 2 个，比散文运镜可靠。
3. **Continuation 五规则**（§3.4）：续段提示词结构固定为——末帧锚（一句）+ identity 串逐字 + "接上一段XX之后"（一句）+ 新动作（不重复上一段动作）+ 环境/情绪延续。我们上次只做了"末帧续接"，缺了 identity 逐字粘贴和"不重复动作"两条。
4. **One-dominant-move**：每 4 秒一段只许一个主运镜，并点名禁止其余运镜。4 秒时长里塞"推+摇+环绕"=必糊。
5. **银幕方向锁死**：旅人全程向右（或向左），每段提示词写 "从画左走向画右，右出画"；出画/入画按"右出→左入"配对。这是免费档能做到的最便宜的"专业感"。
6. **三振规则**：同一镜失败 3 次就改设计（推近/缩短/简化/拆分/换反应镜头），不许第 4 次改词重抽。上次 S25 字幕烧录失败那种就属于该果断换方案的。

### P1：花时间不花钱，显著提升专业度

7. **四个黄金参考位**（character-anchor-skill）：主角先做正/左/右脸特写 + 露脸全身四张"定妆照"，raphael 的图生视频/首帧续接全从这四张出发，而不是每镜现想。
8. **Continuity Bible 轻量版**：一张表管全片——角色 identity 串、服装分层（颜色+材质）、轴线定义（"路在画面中横向，旅人永远画左向右"）、每镜状态台账（湿/干/伤一次只推进一格）。
9. **剧本 + 节拍先行**（beshuaxian MV 模板）：按 Verse/Chorus/Bridge/Outro 写能量等级和视觉钩子，副歌视觉每 4 小节重复+变奏，而不是 29 镜平均用力。
10. **视觉分镜故事板**：每镜一张关键帧小图拼成分镜板（emulsion 的灰盒思路的静态版），先给人过目再烧视频额度。
11. **夜景/雨景压制清单**：MiniMax 爱把夜景"美化"——每段夜景提示词加"深黑阴影不提亮、路面干燥不反光、混合色温不统一"，用正向句写。

### P2：需要新工具/额度，列入考察

12. **Nano Banana Pro 参考图管线**（codeywood）：Agnes 已有免费图生图能力，可试验"参考图库 → 分镜图 → 视频"的参考图路线，替代纯文字。
13. **emulsion 预可视化**：复杂运镜先用灰盒搭一遍，导出参考再喂模型。
14. **DirectorSKILL 本地安装**：`git clone https://github.com/wuwangzhang1216/DirectorSKILL.git ~/.claude/skills/cinematic-director`，作为以后所有视频项目的导演手册（MIT 协议）。higgsfield-ai-prompt-skill 同理可装（但注意它的 Higgsfield 预设名是平台专属，raphael 上只借方法论不借名词）。

### 明确不适用的

- Soul ID / LoRA / 种子锁定：raphael 免费档没有这些控制面，用 identity string + 参考图 + 短片段（4s 天然抗漂移）代替。
- Seedance 时间码长提示词：免费档 4 秒一段，用不上多时间戳；但"一镜一个主动作+终态"的纪律通用。

---

## 九、仓库索引（按推荐度）

| 仓库 | 星数 | 一句话 | 链接 |
|---|---|---|---|
| DirectorSKILL | 158 | AI 电影导演 skill：identity 契约、轴线几何、F1–F19 失败手册、MiniMax 适配器 | https://github.com/wuwangzhang1216/DirectorSKILL |
| higgsfield-ai-prompt-skill | 684 | MCSLA、Identity/Motion 分离、Continuation 五规则、角色锚点块 | https://github.com/OSideMedia/higgsfield-ai-prompt-skill |
| higgsfield-seedance2-jineng | 880 | 15 个 Seedance 技能，含音乐视频导演指南（节拍同步模板） | https://github.com/beshuaxian/higgsfield-seedance2-jineng |
| awesome-seedance | 2601 | Seedance 提示词库：时间码序列、参考角色句式 | https://github.com/ZeroLu/awesome-seedance |
| codeywood | 32 | 参考图管线架构（Nano Banana Pro 权重 0.85–0.95，不用 LoRA） | https://github.com/kaigani/codeywood |
| emulsion | 11 | three.js 灰盒 blocking，导出运镜参考喂视频模型 | https://github.com/dennisonbertram/emulsion |
| character-anchor-skill | 3 | 黄金参考画廊：正/左/右脸+全身四个参考位 | https://github.com/xiaoweihu339-afk/character-anchor-skill |
| apimage-skills | — | 参考集>单张；描述情境动作、不重述主体 | https://github.com/apimageorg/apimage-skills |
| higgsfield-ai-prompt-skill 的 Seedance 子 skill | — | 六槽公式、50–80 词注意力模型、fast 降级词、同形异义陷阱 | 见上（同一仓库 skills/higgsfield-seedance/SKILL.md） |

---

## 十、一句话结论

用户批评的六条（没剧本、没分镜提示词、没设定板、人物场景不一致、运镜用光业余、没故事板），GitHub 上都有现成解法，且**大部分不花钱**：identity string 契约解决 4，镜头几何词汇表解决 5，Continuation 五规则+成本阶梯解决"瞎重跑"，剧本→节拍→导演书→分镜表→关键帧的 13 步管线解决 1/2/3/6。免费档的真正瓶颈从来不是"没花钱"，是**前期设计没做到位就开跑**。
