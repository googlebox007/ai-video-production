# 模型方言 · 七模型对比与母语写法（卷三第一章）

> 截至 2026-10 快照。所有"某模型擅长/不擅长"的结论都带时间戳，大版本一更可能反转；标"待核实"的是没找到可靠公开来源、凭社区口碑暂列的，用时先小步实测。

**是什么（一句话）**：每个视频模型对提示词的"理解偏好"不同——同样的镜头意图，用 A 模型的语法写给 B 模型，效果打折甚至完全失效。这叫"模型方言"。

**怎么用**：开工前先查该模型的官方提示词指南（prompt guide），按它的母语写；跨模型迁移提示词时，只迁移"镜头意图"，语法重写。

## 1.0 七模型对比总表

| 模型 | 提示词方言（一句话） | 镜头语言偏好 | 最擅长 | 最拉胯 | 一致性手段 |
|---|---|---|---|---|---|
| **Kling**（快手，2.x/3.0） | 槽位式英文：`[景别] of [主体] [动作]，[环境]，[运镜]，[用光]，[风格]`；运镜用好莱坞动词（dolly push / whip-pan / crash zoom） | 好莱坞术语吃得最透；原生音频（对白加引号） | 复杂人体运动、物理真实感、长片段 | 文字渲染、高速动作糊、多人物手部错乱 | 真 negative prompt 字段；首尾帧；参考视频/运镜迁移 |
| **Veo**（Google，3/3.1） | 五段式：`[摄影] + [主体] + [动作] + [场景] + [风格氛围]`；官方摄影词汇表（dolly/tracking/crane/aerial/pan） | 电影摄影词汇理解最强，原生音频+对白口型 | 提示词服从度、电影感用光、原生音频/对白 | 手动精细控制弱、生成慢、贵 | 参考图；Flow 场景续接 |
| **Seedance**（字节，2.0/2.5） | 顺序流：`主体→动作→地点→运镜→用光→画面质感→声音`；2.5 支持 `@图片/@视频/@音频` 角色引用 + 时间戳 `[0:00-0:05]` | 多参考、分段式长镜头；中文提示词原生友好 | 多模态参考、视频改写/延长、超长模式（2.5 原生 30–180s） | 无 negative prompt 架构（否定词会被画出来）；seed 不保证复现 | 最多 30 图/10 视频/10 音频参考 |
| **MiniMax-Hailuo**（H3 Turbo，raphael 免费档用的就是它） | 括号运镜指令 `[推镜]` `[固定镜头]` 每段最多 2 个；**语言跟界面走**（国内 UI 全中文，国际版全英文，不混排） | 单张人像主体一致性、一拍完成的动作 | 人像一致性、短片段动作完成度 | 人脸"演太多"（表情夸张循环）；运动预算上限约 5 | subject reference 人物参考；identity string 文字锚 |
| **Wan**（阿里，2.1/2.2） | 长段落叙事式（100–150 词最佳），`Scene:/Camera:/Lighting:/Mood:` 分块；开源权重 | 电影感原生调色；复杂运动 | 复杂人体运动、物理交互、电影质感直出 | 中文界面为主；文字特效以中英为主 | 首尾帧控制；多图融合（第三方平台） |
| **Pika**（2.x） | 显式运镜命令（push-in/pull-out/pan/tilt/orbit）+ 运动强度 0.1–1.0；Modify Region（画区域+描述改法） | 风格化特效（Pikaffects）、快速迭代 | 风格化短片、产品"活照片"、区域改写 | 片段短；特效无区域遮罩（全图生效）；出片较"碰运气" | Add 4s 延长；seed 参数（网页版有） |
| **Runway**（Gen-4/Aleph） | 镜头语法：`<运镜>. <主体运动>. <环境+用光>. <时长+画幅>.`；图生视频只描述"什么在动" | 导演式精细控制 | 可控性、可预测性、商业短片 | 额度贵、生成慢；Aleph 改写按次计费 | Motion Brush（笔刷点哪哪动）；Aleph 上下文改写；Act-One/Two 表演驱动 |

## 1.1 Kling（快手）

**方言**：Kling 官方 2.x 指南推荐所有模型里**最明确的槽位顺序**：`[Shot type] of [subject] [action/movement], [environment/setting], [camera movement], [lighting/mood], [style/aesthetic]`。以及两条硬经验（来自社区 skill 总结）：①运镜用**摄影动词**不用泛泛的运动词——`dolly push`、`whip-pan`、`shoulder-cam drift`、`crash zoom`、`snap focus`，不要写 "moves / goes"；②Kling 有**真正的 negative prompt 字段**，这是它家独一份的干净画面的来源。

Kling 3.0 加了原生音频：对白写进引号并点名说话人+语气（`The soldier whispers in a low exhausted voice, "We are finally going home."`），支持中/英/日/韩/西语对白。还有"参考视频"能力：`Based on <<<video_1>>>, generate the next shot: ...`（续拍）、`Use <<<image_1>>> as the first frame and apply the camera movement from <<<video_1>>>`（运镜迁移）——相当于把"运镜"从文字描述升级成"视频示范"。

**最擅长**：复杂人体运动建模（社区技术审计给 prompt 服从度 9.5/10 三家最高）、长片段（可达 2 分钟级）、物理真实感。

**最拉胯**：画面里的文字容易错乱；高速+复杂动作叠加时糊；多人物近距离交互时手部/肢体错乱。待核实：3.0 的 Motion Control（表演驱动）对风格化角色的兼容边界。

**免费档做法**：raphael 免费档用的是 MiniMax 不是 Kling，Kling 方言**不直接适用**。但两条可迁移：①"运镜用摄影动词"是通用纪律，MiniMax 的中文括号指令本质也是"命名运镜"；②Kling 的"参考视频续拍"思路 = 我们的"末帧续接法"的升级版（视频级参考比文字描述更稳），免费档下用"上一段视频当下一段的参考"喂给图生视频/续接。

## 1.2 Veo（Google DeepMind，3 / 3.1）

**方言**：Google 官方 Veo 3.1 终极提示词指南（Google Cloud Blog）给的五段式：`[Cinematography] + [Subject] + [Action] + [Context] + [Style & Ambiance]`。其中 **[Cinematography] 是权重最高的槽位**，官方给了标准词汇：运镜 `dolly shot / tracking shot / crane shot / aerial view / slow pan / POV shot`，构图 `wide shot / close-up / extreme close-up / low angle / two-shot`，镜头 `shallow depth of field / wide-angle lens / macro lens / deep focus`。音频是 Veo 的杀手锏，官方写法：对白用引号（`A woman says, "We have to leave now."`）、音效写 `SFX: thunder cracks in the distance`、环境声 `Ambient noise: the quiet hum of a starship bridge`。3.1 支持**时间戳提示词**做单片段多镜头：`[00:00-00:02] Wide establishing... [00:02-00:05] Cut to medium tracking...`。负面提示词官方建议"说你不要什么的具体画面"而不是 "no X"（与 Seedance 的"禁否定词"不同，Veo 有 negative prompt 通道）。

**最擅长**：提示词服从度与电影词汇理解（社区横评"电影感用光和质感"三家最佳）、原生音频+对白口型同步、物理与光照连续性。

**最拉胯**：手动精细控制不如 Runway（没有 Motion Brush 这类像素级工具）；生成慢（5–15 分钟/条是常态）；按次计费贵，不适合"烧额度试错"。

**免费档做法**：Veo 免费档碰不到，但它的"**一镜只讲一个清楚的想法**"（官方：one clear idea per shot）和"运镜词汇用电影术语不用氛围词"是通用纪律，直接抄进 MiniMax 中文提示词：把"电影感"换成"35mm 镜头感、慢速推镜、浅景深"。Veo 的音频写法对免费档的意义在于**后期配音的台词本格式**：说话人+引号台词+语气，这套格式可以直接拿去做 TTS 配音的分轨脚本。

## 1.3 Seedance（字节跳动，2.0 / 2.5）

**方言**：社区 skill 总结的有效顺序是：`主体 → 动作 → 地点 → 运镜 → 用光 → 画面质感 → 声音`，只有前两项必填。官方基础模板：`<SUBJECT> <main action or event> in <scene and environment>. The image is <visual style>. The camera uses <shot size, position, movement or cutting>. Sound includes <dialogue, ambience, effects or music>.`

2.5 的核心差异是**多模态参考**：`@图片1` 管身份/服装、`@图片2` 管场景/光线、`@音频1` 管音色/语速，每个参考要写清"借什么、不借什么"（比如动作参考不能悄悄覆盖人物身份）。2.5 支持 4–30 秒标准生成、30–180 秒超长模式、视频延长（从 ≤30s 的源延长 ≤30s），参考上限约 30 图/10 视频/10 音频（以即梦界面实时为准）。**中文提示词原生友好**，这是 Seedance 对中文创作者最大的红利。

两条铁律：①**提示词正文不写否定词**——Seedance 没有 negative embedding 架构，"no jitter" 会被当成场景描述渲染出来，要用正向约束句（"Face stable. Limbs anatomically natural."）；②**注意力从左到右递减**，第一句权重最高；50–80 词三句话最佳，70 词稳定打败 200 词（词多=扩散，不是控制）。

**最擅长**：多参考一致性（图/视频/音频一起上）、视频改写与延长、中文语义理解、超长一镜到底。

**最拉胯**：否定词反噬；seed 参数"不保证复现"（Replicate 上的 Seedance 2.5 文档明确写了 Reproducibility is not guaranteed even when set）；多个参考图光线/风格打架时模型替你"和稀泥"。

**免费档做法**：raphael 免费档是 MiniMax 不是 Seedance，但三条可迁移：①"禁否定词、用正向约束句"是 MiniMax 同样适用的（MiniMax 也没有可靠的 negative 通道）；②"第一句权重最高"——把最重要的（主体+动作）放第一句；③中文提示词红利：MiniMax 国内 UI 同样中文友好，全中文提示词+括号运镜就是 Seedance 中文路线的 MiniMax 版。

## 1.4 MiniMax-Hailuo（H3 Turbo —— 免费档的本命模型）

**方言**（主要来源：DirectorSKILL 的 Hailuo 适配器 + 我们 MV 实测）：**括号运镜指令**如 `[推镜]` `[固定镜头]` `[环绕]`，比散文式运镜描述可靠，每段最多 2 个；**语言必须跟界面走**——raphael 国内 UI 就全中文写提示词（含术语），不要中英混排（中文人物描述放在英文提示词里绑定很弱）；**写表情终点不写情绪**（"ends on a small held half-smile" / "最终定格在一个克制的浅笑"，不写 "she looks happy" / "她很开心"）；运动预算上限约 5，两个括号运镜已花掉 1–2。

打法公式：`subject reference（人物参考）+ 运镜括号 + 动作 + 环境 + 终态`。典型失败是人脸"演太多"（表情夸张循环），修法就是"表情终点"写法。

**最擅长**：单张人像的主体一致性、一拍完成的短动作、括号运镜的执行。

**最拉胯**：长片段人物漂移（4 秒以上风险陡增——免费档 4 秒恰好是甜点）；夜景会被"美化"（阴影提亮、凭空加湿反光路面）；复杂多动作叠加必糊。

**免费档做法**：这就是本卷的"主场模型"，`free-tier-survival.md` 全部围绕它展开。这里先记三条铁律：①全中文提示词+括号运镜；②每段只讲一个动作+一个明确终态（F5 无终态是 MiniMax 头号杀手）；③夜景/雨景提示词里加压制句（"深黑阴影不提亮、路面干燥不反光"）。

## 1.5 Wan（阿里，2.1 / 2.2）

**方言**：Wan 吃**长段落叙事式提示词**，100–150 词最佳（与 Seedance 的"70 词打败 200 词"相反，这是方言差异的典型例子）。社区 skill 建议用 `Scene: / Camera: / Lighting: / Mood:` 分块写结构化描述，走"讲清楚一个完整段落"路线而不是关键词堆砌。Wan 2.1 开源权重（通义万相），ComfyUI/本地部署生态成熟；多语言文字特效（中英文字渲染是强项，别的模型多半拉胯）。

**最擅长**：复杂运动（花滑、游泳、跳水这类连贯身体运动是官方演示的招牌）、物理交互真实感、电影质感直出（不怎么调提示词就有 film look）、VBench 长期霸榜。

**最拉胯**：官方站中文界面为主，英文提示词支持"缓解但不根除"语言门槛；长片段的细节一致性仍是开放问题。待核实：2.2/2.5 在视频一致性控制面的具体参数。

**免费档做法**：Wan 的"结构化分块"写法（Scene/Camera/Lighting/Mood）可以借来做**提示词模板**，但词数要砍到 MiniMax 能消化的 50–80 字中文。Wan 开源是一条后路：如果以后要自建本地管线（ComfyUI + Wan 开源权重），prompt 资产可以平移。

## 1.6 Pika（2.x）

**方言**：显式运镜命令词：`push-in`（推近）、`pull-out`（拉远）、`pan left/right`、`tilt up/down`、`orbit`（环绕），配**运动强度 0.1–1.0**（0.3–0.5 subtle polished，0.7–1.0 energetic）。**Modify Region** 是 Pika 的独门武器：生成完视频后，用笔刷涂出要改的区域，写一句话描述改成什么，只有涂抹区重算——等于"视频版局部重绘"，修穿帮（多一根手指、背景乱入）不用整段重跑。**Pikaffects**（膨胀/融化/爆炸等特效）是全图生效的，没有区域遮罩，只适合风格化夸张内容。`Add 4s` 可以在已有视频上追加 4 秒延长。

**最擅长**：风格化特效短片、产品"活照片"（静物图转动效）、区域改写修穿帮、迭代快。

**最拉胯**：片段短（4–10 秒级）；出片随机性大（"碰运气"属性重）；Pikaffects 没有区域控制，不适合写实叙事。

**免费档做法**：Pika 的 Modify Region 思路值得记：**修局部不重跑整段**。免费档下没有这个按钮，但等价手工做法是——穿帮镜头不整段重抽，而是**改分镜设计**：推近一档（穿帮部位出画）、换反应镜头、剪掉坏帧。这是三振规则在免费档的落地形态之一。

## 1.7 Runway（Gen-4 / Aleph）

**方言**：社区总结的 Runway 镜头语法是 `<camera move>. <subject motion>. <environment + lighting>. <duration + aspect>.`——**运镜和主体运动分开写**，混在一起模型会懵。图生视频（image-to-video）的铁律：**只描述"什么在动"**，不要重述画面里已有的东西（"she slowly turns her head to the left, hair drifting slightly"，不要写 "a woman in a red jacket..."——夹克画面里已经有了，重述会压制运动幅度）。官方示例的语域是"短、plain、motion-first"。提示词硬上限 1000 字符。官方明确：**否定式措辞可能产生反效果**，约束要正向表达并点名"什么保持不动"（`Locked camera. The camera remains still.` 而不是 `no camera movement`）。

工具层是 Runway 真正的护城河：**Motion Brush**（笔刷涂哪里、哪里动，还能设方向和强度——区域运动控制的标杆）、**Director Mode**（推/拉/摇/移的滑杆式运镜）、**Act-One/Two**（手机录一段表演，迁移到角色脸上/身上——表情驱动）、**Aleph**（视频内改写：笔刷涂背景+一句话，换场景/换光/换角度，**不重跑整段**）。

**最擅长**：可控性与可预测性（商业短片、产品片、多元素复杂调度）；Aleph 的"改写不重生成"是省额度的范式创新。

**最拉胯**：贵（Aleph 改写按次计费，预算要单列）；生成慢；免费额度只够尝味道。

**免费档做法**：Runway 碰不起，但三条方法论免费：①"图生视频只写变化"是通用铁律——我们的续接提示词里不要重述首帧已有的内容；②"点名什么保持不动"的正向约束句式，MiniMax 同样吃；③Aleph 的"**转场拆到剪辑点上**"思想：不要让一个 4 秒片段同时承担"动作+转场"两件事（这正是 F7 跨镜断裂的病根）。

## 1.8 各模型一句话方言示例（同一镜头，七种母语）

同一镜头意图——"黄昏街道，老周从画左走向画右，镜头缓慢推近"——七个模型的母语写法对照：

| 模型 | 写法 |
|---|---|
| Kling | `Medium shot of an elderly man in a gray Zhongshan suit walking from frame-left to frame-right on a dusk street, slow dolly push in, warm low-key lighting, cinematic realism`（槽位顺序+摄影动词） |
| Veo | Cinematography: slow dolly-in, medium shot. Subject: elderly Chinese man, gray suit. Action: walks frame-left to frame-right. Context: empty dusk street, long shadows. Style: cinematic, warm highlights. Audio: distant traffic, footsteps on pavement.（五段式+音频行） |
| Seedance | 老周在黄昏的空旷街道上从画左走向画右。画面是写实电影感。镜头用中景缓慢推近。声音包括远处车流和脚步声。（主体→动作→地点→运镜→用光→质感→声音） |
| MiniMax | `[推镜]老周，左眉有竖疤，深灰色中山装，在黄昏空旷街道上从画左走向画右，右出画，最终定格在他迈出最后一步的瞬间`（括号运镜+identity 要素+动作+终态） |
| Wan | Scene: 黄昏时分空无一人的老街道，暖调低光，影子拉得很长。Camera: 中景，缓慢推近。Lighting: 低角度暖光，轮廓光。Mood: 孤独而坚定。老周穿深灰色中山装，从画左走向画右。（分块叙事式） |
| Pika | `elderly man walking right across a dusk street, slow push-in, motion strength 0.4`（显式运镜命令+强度） |
| Runway | `Slow push in over 4 seconds. Subject motion: elderly man in gray suit walks from frame-left to frame-right, coat hem swaying. Environment: empty dusk street, warm low-key light, long shadows. Duration: 4s, 16:9.`（运镜.主体运动.环境.时长） |

> 看出规律了吗：**镜头意图相同，槽位顺序、用词、详略完全不同**。跨模型抄提示词，抄的是意图，不是句子。

## 1.9 一句话：方言差异的本质

> 模型方言差异的本质是**各家训练数据的标注习惯不同**：Kling 的标注员用好莱坞术语，Veo 的用电影摄影词汇，Seedance 的用中文短视频语料，MiniMax 的被中文 UI 语料调教过。所以"翻译提示词"不是中英互译，是**按目标模型的标注习惯重写**。永远不要假设 A 模型的"咒语"在 B 模型上有效。

**本节免费档做法汇总**：主场是 MiniMax-Hailuo——全中文提示词 + 括号运镜（每段 ≤2 个）+ 一个动作 + 明确终态 + 表情写终点。其他六家的方言里，**只借方法论**（Kling 的摄影动词、Veo 的"一镜一个想法"、Seedance 的禁否定词、Runway 的"只写变化"、Pika 的"修局部不重跑"），**不借具体咒语**。

**本节坑/上限**：①所有"最擅长/最拉胯"都是截至 2026-10 的快照，大版本一更就可能反转，关键结论动手前先用 1–2 条小步验证；②不要把"社区口碑"当"官方文档"，标了"待核实"的就是还没找到硬来源的；③方言只解决"模型听不听得懂"，不解决"人物一致性"——那是 `consistency.md` 的事。
