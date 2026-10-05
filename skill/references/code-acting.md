# 表演指导 6 种（每条给"错写 vs 对写"对照）

## 59. 写表情终点，不写情绪（expression endpoint, not emotion）
- **传统定义**：只写"表情最终停在什么物理状态"，不写"她是什么情绪"；情绪词是结果导演，模型只能挤眉弄眼。
- **AI提示词写法**：
  错写：`阿棠很悲伤地看着怀表`
  对写中文：`[固定镜头]阿棠低头看掌心怀表，视线不动。她的嘴角绷住，下唇被咬出一道白印。终帧定格：她闭上眼睛，把怀表攥进手心，指节发白。`（可直接复制）
  对写 English: `[locked-off] A-Tang looks down at the pocket watch in her palm, gaze unmoving. The corners of her mouth lock; her lower lip bitten to a white line. Final frame: she closes her eyes and crushes the watch into her fist, knuckles white.`（可直接复制）
- **免费档注意事项**：MiniMax 头号病就是人脸"演太多"（表情夸张循环），表情终点写法是特效药；终点必须是可画出来的物理事实。
- **反例**：`阿棠悲伤、愤怒、又释然`（不要这么写）——4 秒三种情绪等于表情抽搐；一镜只许一个表情终点。

## 60. 动词式动作（action verbs, not adjectives）
- **传统定义**：用"她对他做动作"的及物动词写表演，不用形容词；"她攥紧包带，指节发白"而不是"她很紧张"。
- **AI提示词写法**：
  错写：`老周很紧张地等电话`
  对写中文：`[固定镜头]老周坐桌边，手机扣在桌面上。他攥紧裤缝，指节发白，眼睛钉在手机上。终帧定格：手机震了一下，他猛地抓起，又放下，把手机翻过去屏幕朝下。`（可直接复制）
  对写 English: `[locked-off] Lao Zhou sits at the table, phone face-down. He grips his trouser seam, knuckles white, eyes nailed to the phone. Final frame: it buzzes; he snatches it up, sets it back down, and flips it over, screen down.`（可直接复制）
- **免费档注意事项**：动词是身体的指令，形容词是脸的指令；模型和真人演员一样，听得懂动词、听不懂形容词。
- **反例**：`老周焦虑不安`（不要这么写）——"焦虑不安"没有身体可执行的动作；改成"攥紧裤缝、眼睛钉在手机上"。

## 61. 视线方向（eyeline direction）
- **传统定义**：不给情绪指令，给"看哪"的指令；人的情绪跟着注意力走，盯着杯子说分手比"演愧疚"真十倍。
- **AI提示词写法**：
  错写：`阿棠愧疚地看着老周`
  对写中文：`[固定镜头]阿棠坐老周对面，眼睛始终看着他手里的茶杯，不看他的脸。蒸汽升起，模糊她的视线。终帧定格：她伸手拿杯子，碰到他的手指，缩回来，视线落在桌面上。`（可直接复制）
  对写 English: `[locked-off] A-Tang sits across from Lao Zhou, eyes fixed on the teacup in his hands, never on his face. Steam rises, blurring her view. Final frame: she reaches for the cup, brushes his fingers, pulls back, gaze dropping to the tabletop.`（可直接复制）
- **免费档注意事项**：视线方向是"侧门"：情绪正门推不开时，从注意力进去；写"看杯子不看脸"比写"愧疚"可靠十倍。
- **反例**：`阿棠心虚地低下头`（不要这么写）——"心虚"是心理词；改成"眼睛盯着茶杯、不看他的脸"的视点指令。

## 62. 呼吸节奏（breathing rhythm）
- **传统定义**：用呼吸的可见变化写情绪转折：屏住、急促、长叹；呼吸是身体最诚实的节拍器。
- **AI提示词写法**：
  错写：`老周听到消息后很震惊`
  对写中文：`[固定镜头]老周举着电话听着。他的呼吸停住了，胸口不再起伏，持续两秒。然后他长长呼出一口气，肩膀塌下来。终帧定格：他把电话从耳边拿开，拇指悬在挂断键上。`（可直接复制）
  English: `[locked-off] Lao Zhou holds the phone, listening. His breathing stops, chest still, for two full seconds. Then he exhales long, shoulders collapsing. Final frame: he pulls the phone from his ear, thumb hovering over the end-call button.`（可直接复制）
- **免费档注意事项**：呼吸变化是小动作，运动预算花得少，MiniMax 执行得稳；比大喊大叫可靠得多。
- **反例**：`老周倒吸一口凉气，瞪大眼睛`（不要这么写）——"瞪大眼睛"易夸张；不如写"呼吸停住两秒、肩膀塌下来"的完整呼吸线。

## 63. 重心转移（weight shift）
- **传统定义**：用身体重心的移动写心理变化：前倾等于进攻/渴望，后退等于防御/拒绝，瘫坐等于放弃。
- **AI提示词写法**：
  错写：`阿棠下定决心要走`
  对写中文：`[固定镜头]阿棠站在门口，手搭在门把上。她的重心先前倾，门被推开一条缝；然后重心退回来，门又合上。终帧定格：她松开门把，后退一步靠在墙上，滑坐在地上抱住膝盖。`（可直接复制）
  English: `[locked-off] A-Tang stands at the door, hand on the knob. Her weight tips forward; the door cracks open. Then her weight pulls back; the door swings shut. Final frame: she releases the knob, steps back against the wall, and slides to the floor hugging her knees.`（可直接复制）
- **免费档注意事项**：重心转移是全身动作，幅度大、模型看得懂；"犹豫"的最佳视觉翻译就是"重心前倾又退回"。
- **反例**：`阿棠犹豫不决`（不要这么写）——"犹豫"是心理词；改成"重心前倾推开门缝、又退回来"的身体版本。

## 64. 微表情（micro-expression）
- **传统定义**：0.5 秒级的面部小动作：嘴角抽动、眼皮跳、鼻翼翕动；是情绪泄露的瞬间，不是情绪本身。
- **AI提示词写法**：
  错写：`老周强忍怒火`
  对写中文：`[固定镜头·特写]老周脸部特写。他听着电话那头，左眼眼皮跳了一下，嘴角向下一扯，又被他抿住。终帧定格：他挂断电话，脸上恢复平静，只有左手还在抖。`（可直接复制）
  English: `[locked-off close-up] Close-up of Lao Zhou's face. Listening to the voice on the phone, his left eyelid twitches; the corner of his mouth drags down, then he presses his lips shut. Final frame: he ends the call, face calm again, only his left hand still trembling.`（可直接复制）
- **免费档注意事项**：微表情要配特写（脸部像素够大模型才画得准）；"强忍"类词一律翻译成"嘴角一扯又抿住"的物理过程。
- **反例**：`老周面无表情，但内心愤怒`（不要这么写）——"内心愤怒"拍不出来；微表情的写法是"眼皮跳一下、嘴角一扯又抿住"，让观众自己读出愤怒。
