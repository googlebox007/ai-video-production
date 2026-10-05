# 轴线 5 规则（每条写清"怎么编码进提示词让无状态模型遵守"）

## 46. 180°规则（180-degree rule）
- **传统定义**：两主体之间的假想轴线，机位永居轴线同一侧；一旦越轴，两人左右互换，观众瞬间迷失。
- **AI提示词写法**：
  中文：`[固定镜头]面馆里，阿棠坐画左，老周坐画右，桌子是两人之间的轴线。机位始终在桌子南侧：阿棠永远在画左看向画右，老周永远在画右看向画左。终帧定格：她放下筷子，他端起碗，两人视线在银幕上对上。`（可直接复制）
  English: `[locked-off] In the noodle shop, A-Tang sits frame-left, Lao Zhou frame-right, the table the axis between them. The camera stays on the table's south side: she is always frame-left looking frame-right, he always frame-right looking frame-left. Final frame: she sets down her chopsticks, he lifts his bowl, their gazes meeting on screen.`（可直接复制）
- **免费档注意事项**：无状态模型没有"上一镜机位"记忆，轴线必须逐镜写死（"A 永远在画左看向画右"），不能指望模型自己保持；这是 DirectorSKILL 验证过的铁律。
- **反例**：`两人在面馆吃饭，镜头来回切`（不要这么写）——没写轴线在哪一侧、谁在左谁在右，连续两镜必越轴，观众迷路。

## 47. 30°规则（30-degree rule）
- **传统定义**：相邻两镜拍同一主体，机位夹角至少 30° 或景别差两档，否则像"卡了一下"。
- **AI提示词写法**：
  中文：`第一镜[固定镜头]：老周在天台抽烟，中景，他在画面右侧。第二镜[固定镜头]：机位绕到他正前方45度，推近到特写，烟雾从他嘴角升起。终帧定格：特写里他把烟掐灭在栏杆上。`（可直接复制）
  English: `Shot one [locked-off]: Lao Zhou smoking on the rooftop, medium shot, frame-right. Shot two [locked-off]: the camera moves 45 degrees to his front, pushing to close-up, smoke curling from his lips. Final frame: in close-up he stubs the cigarette out on the railing.`（可直接复制）
- **免费档注意事项**：免费档 4 秒一段天然是"一镜"，30° 规则用在"相邻两段"的关系上：分镜表标注每镜机位角度，差不到 30° 就改景别（中景接特写）。
- **反例**：`老周抽烟，切近一点继续拍`（不要这么写）——"近一点"差不到两档景别，切出来像卡顿；且没写机位转了多少度。

## 48. 银幕方向锁定（screen direction lock）
- **传统定义**：人物在银幕上的行进方向全片锁定（如全程向右）；方向一乱，再稳的人物也像业余。
- **AI提示词写法**：
  中文：`[横移]戈壁公路上，老周从画左走向画右，右出画，镜头与他同速向右横移。下一镜：他在下一个路口从画左入画，继续向右走。终帧定格：他走到地平线，变成小点，仍在向右。`（可直接复制）
  English: `[lateral truck] On the desert highway, Lao Zhou walks frame-left to frame-right, exiting right, the camera trucking right at his pace. Next shot: he enters frame-left at the next crossing, still moving right. Final frame: he reaches the horizon, a small dot, still moving right.`（可直接复制）
- **免费档注意事项**：零成本、效果最大的一条。每镜提示词写"从画左走向画右，右出画"，分镜表单独列"方向"栏，开工前通读，不许无理由变向。
- **反例**：`老周在公路上走，有时向左有时向右`（不要这么写）——方向乱是业余片铁证；观众不会说"方向错了"，只会觉得"别扭"。

## 49. 视线匹配（eyeline match）
- **传统定义**：A 看向画右，切 B 时 B 必须看向画左，视线在银幕上"对上"；视线高度也要匹配。
- **AI提示词写法**：
  中文：`第一镜[固定镜头]：阿棠在楼下，看向画右，视线微微向上。第二镜[固定镜头]：老周在天台边缘，看向画左下方，视线与她对上。他举起手里的怀表晃了晃。终帧定格：她伸出手，像要接住什么。`（可直接复制）
  English: `Shot one [locked-off]: A-Tang below, looking frame-right, gaze tilted slightly up. Shot two [locked-off]: Lao Zhou at the rooftop edge, looking frame-left and down, his eyeline meeting hers. He raises the pocket watch and shakes it. Final frame: she extends her hand as if to catch something.`（可直接复制）
- **免费档注意事项**：视线是银幕上最强的"连线"。写清"谁看向哪边、视线向上还是向下"；坐着的人看站着的人必须是"抬头看"，高度错配是业余重灾区。
- **反例**：`阿棠看老周，老周看阿棠`（不要这么写）——没写画左画右、视线高低，模型可能让两人各看各的，对话变自言自语。

## 50. 出画入画配对（exit / entry pairing）
- **传统定义**：人物从画右出画，下一镜必须从画左入画（反之亦然）；观众的大脑自动缝合空间。
- **AI提示词写法**：
  中文：`第一镜[横移]：阿棠撑伞从画左走向画右，右出画，终帧是空巷，雨声不断。第二镜：首帧是火车站台空镜，0.5秒后她从画左入画，继续向右走。终帧定格：她走入一家亮灯的店，门帘晃动。`（可直接复制）
  English: `Shot one [lateral truck]: A-Tang walks frame-left to frame-right under her umbrella, exiting right; final frame is the empty alley, rain hissing on. Shot two: first frame is an empty station platform; after half a second she enters frame-left, still walking right. Final frame: she steps into a lit shop, the door curtain swaying.`（可直接复制）
- **免费档注意事项**：免费档伪一镜的核心零件。相邻段"右出→左入"加同向运镜，观众会脑补成一镜；转场型衔接优先，容错率最高。
- **反例**：`阿棠走出画面，切她进店`（不要这么写）——没写从哪边出、从哪边入，方向一反，观众瞬间迷路。
