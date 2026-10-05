---
name: "ai_video_production"
description: "统一 AI 视频制作 skill：MV、AI 短片、AI 短剧全流程——剧本、角色圣经、设定板、分镜表、故事板、提示词编码（运镜/构图/灯光/轴线/转场/表演/调色 68 条）、模型选型、一致性工程、失败分诊、后期与交付。默认 raphael.app 免费档（480P/4s/0积分）优先，也覆盖付费模型。做视频、分镜、写提示词、导演、剧作任一需求都触发。"
---

# AI Video Production 统一视频制作

## 一句话定位
从一个想法到一条成片的完整 AI 视频制作流程：**前期设计 → 生成制作 → 后期交付**，默认免费档优先，专业纪律拉满。这是 `mv-free-pipeline`、`prompt-codebook`、`film-director`、`ai-video-pipeline` 四个 skill 的合并版——以后只用这一个。

## 主流程（线性，缺一步不许往下走）
完整版见 `references/00-workflow.md`。极简版：

1. **前期七件套**（全部经用户确认才开工）：
   - `pre-master-script.md` — 剧本（写"发生什么"，不写"AI 怎么画"）
   - `pre-character-bible.md` — 角色圣经 + identity string 契约（30–50 词，逐字复制）
   - `pre-asset-sheets.md` — 角色/道具/场景设定板（多角度，generate-many → test-in-motion → lock-the-winner）
   - `pre-style-glossary.md` — Global Style Prefix + @-资产术语表（全片锁一次，改一处全片生效）
   - `pre-shotlist.md` — 导演分镜表（`Style → Characters → Scene → CUT 1..N`，每镜一镜一卡）
   - `pre-storyboard.md` — 视觉故事板（静帧先行，用户逐张确认）
   - 节奏预算：各镜时长精确等于总时长；留一个 6–8s hero hold；单调审计（不许连续三镜同景别同运镜）
2. **制作**：关键帧（80% 规则，Hero Frame 不对绝不动画）→ 链式视频生成（4s 一段，Continuation 五规则，一次只跑一段，每段必 QC）→ Generation Ledger 记账
3. **后期**：粗剪 → 生成监督（只重刷坏镜）→ 精剪 → Picture Lock（锁画后不再生成）→ 调色（第一任务是统一相邻镜）→ 声音 → 交付验货

## 何时查哪份 reference（按阶段查，不要通读）

| 阶段 | 查什么 |
|---|---|
| 写剧本/定结构 | `story-structure.md`、`story-character.md`、`story-scene-dialogue.md`、`story-visual.md`、`story-adaptation.md`；MV 专项看 `story-mv-narrative.md` |
| 定调度/摄影/轴线 | `dir-mise-en-scene.md`、`dir-cinematography.md`、`dir-camera-movement.md`、`dir-axis-system.md`、`dir-montage.md` |
| 定灯光/色彩/声音/表演 | `dir-lighting.md`、`dir-color.md`、`dir-sound.md`、`dir-actors.md`；MV 语法 `dir-mv-grammar.md`；找灵感 `dir-cases.md` |
| 写提示词 | 先看 `code-micro-discipline.md`（微观纪律），再按需查 `code-camera-moves.md` / `code-composition.md` / `code-lighting.md` / `code-axis-rules.md` / `code-transitions.md` / `code-acting.md` / `code-color-grading.md` |
| 选模型/保一致 | `pipe-model-dialects.md`、`pipe-consistency.md`、`pipe-keyframe-to-video.md` |
| 预可视化/混合管线 | `pipe-previz.md`、`pipe-hybrid.md` |
| 出错了 | `pipe-failure-manual.md`（先走三问流程；同一镜失败 3 次就改设计，不许第 4 次重抽） |
| 后期 | `pipe-post.md`（调色先统一再风格化） |
| 免费档专用 | `free-raphael-tier.md`（档位实测）、`free-chain-generation.md`（链式法）、`free-ffmpeg-assembly.md`（拼装）、`free-shot-card.md`（一镜一卡）、`free-tier-survival.md`（生存指南） |

## 提示词微观纪律（每条必遵守）
1. 50–80 词，三句话：场景+人物 → 运镜+动作 → 终帧定格
2. 禁否定词：不写"不/别/没有"，写正向约束（"固定机位，纹丝不动"）
3. 禁空形容词："电影感""氛围拉满"删掉，情绪写成表情终点或身体动作
4. 不写 "fast" 写物理："0.5 秒转头""每秒一步"
5. 一镜一动作 + 明确终态（F5 检查：说不出一镜最后一帧是什么，提示词就不合格）
6. MCSLA 五层：Model · Camera · Subject · Look · Action，缺一不可
7. Identity/Motion 分离：身份描述和动作描述分两块写，混写=脸在中段融化
8. 同形异义动词自查：zoom≠dolly/push，pan≠truck，tilt≠crane

## 免费档铁律（raphael.app：480P/4s/MiniMax H3 Turbo/0积分/无种子控制/网页手工）
- 全中文提示词 + 括号运镜（每段 ≤2 个），不中英混排
- 一致性三锚：identity string（文字锚）+ 首帧参考图（图像锚）+ 4 秒短片段（时长锚）
- 续接链深度 ≤3 节，之后用 canonical 参考图重新锚定
- 转场、调色一律剪辑时做，不写进生成提示词
- 一次只跑一段生成；每次提交前确认队列状态
- 480P 放大到 1080P 偏软——这是免费的代价，交付时如实说明

## Operating Rules
1. 免费档优先；除非用户明确批准，不点付费模型，每次提交确认 "0 credits"。
2. 不逆向、不绕限、不刷接口——普通手工速度使用。
3. 不编造歌词；无 verified 歌词源不烧录字幕。
4. 不用静态图推拉+交叉淡化凑时长——只用真实生成的视频。
5. 状态汇报数字打头（n/N）；异常只说处理结果。
6. 锁画（Picture Lock）后不再生成新镜头。
7. 交付必附：文件路径、精确时长、分辨率/fps/编码、文件大小、可核验说明。
