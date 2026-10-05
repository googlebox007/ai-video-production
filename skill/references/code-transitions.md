# 转场 8 种（免费档转场一律剪辑时做，不许写进生成提示词）

## 51. 白闪（white flash / flash frame）
- **传统定义**：画面瞬间闪白再切到下一镜；情绪含义是能量标点、记忆闪回，"世界晃了一下"。
- **AI提示词写法**（剪辑时做，生成时只管两段的首尾帧）：
  中文：`本段：阿棠举起怀表对着光，终帧定格在怀表特写。// 下段：首帧是二十年前的老照片，怀表躺在襁褓边。// 剪辑点加3帧白闪。`（可直接复制）
  English: `This segment: A-Tang holds the pocket watch to the light, final frame on the watch close-up. // Next segment: first frame is an old photo from twenty years ago, the watch lying beside a swaddling cloth. // Add a 3-frame white flash at the cut.`（可直接复制）
- **免费档注意事项**：剪辑时做。白闪全片别超 5 次，超了变"遮瑕膏依赖"；生成提示词里写白闪等于浪费运镜预算。
- **反例**：`[白闪转场]阿棠穿越到二十年前`（不要这么写）——把转场写进生成提示词，模型会在 4 秒里硬做"闪白加穿越"两个动作，必糊；且"穿越"没写落点。

## 52. 黑场（fade to black）
- **传统定义**：画面渐隐到黑再渐显；情绪含义是时间流逝、段落结束，"一夜过去了"。
- **AI提示词写法**（剪辑时做，本段终帧收在"可黑场"的静帧上）：
  中文：`本段：老周吹灭蜡烛，终帧是彻底的黑暗，他坐着不动。// 剪辑：2秒黑场。// 下段首帧：天亮，同一间屋，窗帘透光。`（可直接复制）
  English: `This segment: Lao Zhou blows out the candle; final frame is total darkness, him sitting still. // Edit: 2 seconds of black. // Next segment first frame: morning, same room, light through the curtains.`（可直接复制）
- **免费档注意事项**：剪辑时做。黑场是最便宜的时间跳跃；别让模型"渐黑"（它渐不匀），剪辑里做 fade。
- **反例**：`[渐黑]老周睡着了，第二天`（不要这么写）——让模型做渐黑加过夜，4 秒塞两个时间动作；正确做法是终帧静止加剪辑黑场。

## 53. 出画入画（exit / entry cut）
- **传统定义**：人物出画→切→从另一边入画（新场景）；情绪含义是空间转换，"他去了别处"。
- **AI提示词写法**（剪辑时做，生成时两段各管一段：本段负责"右出画"，下段负责"左入画"）：
  中文：`本段：阿棠从画左走向画右，右出画，终帧是空巷。// 下段：首帧是火车站台空镜，她从画左入画，继续向右走。`（可直接复制）
  English: `This segment: A-Tang walks frame-left to frame-right, exiting right; final frame is the empty alley. // Next segment: first frame is an empty station platform; she enters frame-left, still walking right.`（可直接复制）
- **免费档注意事项**：剪辑时做。免费档最常用的转场，零成本；方向配对写死（右出→左入），见条目 50。
- **反例**：`阿棠走出画面，下一段她在火车站`（不要这么写）——没写出画方向和入画方向，剪辑时接不上。

## 54. 尺度匹配（scale match / match on scale）
- **传统定义**：前后两镜在"尺度/形状"上对上（如怀表特写→月亮），时空可跳很远，观众却觉得顺滑。
- **AI提示词写法**（剪辑时做：本段终帧定格在"可放大的细节"上，下段首帧从相似形状开始）：
  中文：`本段终帧：怀表表盘特写，指针停在十二点。// 下段首帧：满月特写，月面纹理像表盘。// 剪辑硬切，0.5秒内完成尺度跳跃。`（可直接复制）
  English: `This segment final frame: close-up of the watch dial, hands at twelve. // Next segment first frame: close-up of the full moon, its texture like the dial. // Hard cut, the scale jump landing within half a second.`（可直接复制）
- **免费档注意事项**：剪辑时做。Trillo《The Hardest Part》无限变焦就是尺度匹配的极致；免费档版每段只写"一次对上"，终态明确。
- **反例**：`怀表变成月亮，阿棠很惊讶`（不要这么写）——"变成"是模型最难的形变；正确做法是两段各拍一个特写，剪辑点硬切，变化由剪辑完成。

## 55. 动作匹配（match on action）
- **传统定义**：一个动作切成两镜，前镜拍前半、后镜接后半，剪辑点落在动作"进行中"。
- **AI提示词写法**（剪辑时做：本段终帧定在"动作中点"，下段首帧从"中点之后"开始）：
  中文：`本段：阿棠伸手推木门，终帧定格在手掌刚触到门板。// 下段：首帧是手掌已在门板上，门被推开一条缝，光涌进来。// 剪辑点落在"推"的进行中。`（可直接复制）
  English: `This segment: A-Tang reaches to push the wooden door; final frame freezes as her palm just touches the panel. // Next segment: first frame has her palm already on the panel, the door cracking open, light flooding in. // The cut lands mid-push.`（可直接复制）
- **免费档注意事项**：剪辑时做。人眼追踪运动时对"切"最不敏感，是最顺滑的接法；两段动作速度/方向必须一致，写死。
- **反例**：`阿棠开门，走进去`（不要这么写）——一段里塞"开门加走入"两个动作，且没写中点在哪，剪辑时找不到下刀处。

## 56. 声音桥（sound bridge / J cut / L cut）
- **传统定义**：声音跨过剪辑点，提前进入下个镜头（J cut）或滞后（L cut）；情绪含义是转场变软，两个时空叠在一起。
- **AI提示词写法**（剪辑/混音时做，生成时在分镜表"声音列"写清桥接关系）：
  中文：`本段：老周在雨中走，环境音是雨声加脚步声。// 下段首帧出现前，雨声里先混入火车站广播声（J cut：下个镜头的声音先出来）。// 剪辑：音频先切，画面晚6帧切。`（可直接复制）
  English: `This segment: Lao Zhou walks in the rain; ambience is rain plus footsteps. // Before the next shot's first frame, station announcements bleed into the rain (J cut: the next shot's sound arrives first). // Edit: cut audio first, picture 6 frames later.`（可直接复制）
- **免费档注意事项**：剪辑时做，零生成额度，是"最便宜的转场润滑剂"。分镜阶段就写声音列，否则剪辑时发现声画各玩各的。
- **反例**：`（分镜表声音列空白）后期随便配点音乐`（不要这么写）——声音没进前期规划，J cut/L cut 无从谈起；音乐盖住一切等于业余混音。

## 57. 空镜过渡（cutaway bridge）
- **传统定义**：在两个叙事镜之间插入一个空镜（风景/物件）；情绪含义是喘息、时间流逝，"世界还在转"。
- **AI提示词写法**（剪辑时做；空镜单独生成一段，纯文生，无需人物一致性）：
  中文：`空镜段：雨后巷口，一只猫跳上墙头，抖了抖水，跑了。固定机位4秒，无人物。// 剪辑：插在阿棠出画和她入画火车站之间，停留2秒。`（可直接复制）
  English: `Cutaway segment: after rain, a cat leaps onto a wall, shakes off water, and runs. Locked-off 4 seconds, no people. // Edit: place between A-Tang's exit and her station entry, holding 2 seconds.`（可直接复制）
- **免费档注意事项**：剪辑时做。空镜是免费档"万能润滑剂"：纯文生、无人物、零一致性压力，还能打断续接链（防漂移累积）。
- **反例**：`切个风景过渡一下`（不要这么写）——"风景"太空；空镜也要有具体内容（一只猫、抖水、跑了）和明确时长。

## 58. 叠化感（dissolve）
- **传统定义**：两镜叠影过渡；情绪含义是回忆、梦境、时间融化。
- **AI提示词写法**（剪辑时做；ffmpeg xfade 或剪辑软件叠化；注意 ffmpeg 8.1.2 的 xfade 吞帧，先拿 2 段做 POC）：
  中文：`本段终帧：阿棠脸部特写，她闭上眼睛。// 下段首帧：二十年前的她，同样闭眼的特写，同样构图。// 剪辑：12帧叠化，两张脸在叠影中"变成"彼此。`（可直接复制）
  English: `This segment final frame: close-up of A-Tang's eyes closing. // Next segment first frame: her twenty-years-younger self, same closed-eye close-up, same framing. // Edit: 12-frame dissolve, the two faces "becoming" each other in the overlap.`（可直接复制）
- **免费档注意事项**：剪辑时做。叠化前先做 POC（xfade 吞帧是我们的实战教训）；适合"同一构图、不同时间"的两镜，构图差太多叠出来是重影事故。
- **反例**：`两段叠化，阿棠回忆过去`（不要这么写）——"回忆过去"没写两镜的构图关系；且没做 POC 直接全量，xfade 吞帧哭都来不及。
