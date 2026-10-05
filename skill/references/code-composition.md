# 构图 15 种

## 21. 三分法（rule of thirds）
- **传统定义**：画面横竖各分三份，趣味中心放交叉点上；地平线放上三分之一等于压迫，放下三分之一等于开阔。
- **AI提示词写法**：
  中文：`[固定镜头]戈壁黄昏，老周牵骆驼走在画面下三分之一处，地平线压在下三分线上，天空占三分之二，云烧成暗红。终帧定格：他走到右侧交叉点，停住，回头望向来路。`（可直接复制）
  English: `[locked-off] At dusk in the Gobi, Lao Zhou leads a camel along the lower third, the horizon pressed on the lower third line, sky taking two thirds, clouds burning dark red. Final frame: he reaches the right intersection, stops, and looks back the way he came.`（可直接复制）
- **免费档注意事项**：完全能用，零成本的专业感。写"地平线在下三分之一"模型执行得不错。
- **反例**：`老周在沙漠里，构图很好`（不要这么写）——"构图很好"是空话；没写地平线位置、人物落点，模型随机摆。

## 22. 对称构图（symmetrical composition）
- **传统定义**：主体居中、左右镜像；情绪含义是仪式感、荒诞感，"被审视"。
- **AI提示词写法**：
  中文：`[固定镜头]深夜长走廊，阿棠站在正中央，左右两排房门完全对称，顶灯一字排开。她一动不动，只有影子在脚下。终帧定格：走廊尽头的门开了一条缝，她迈出第一步。`（可直接复制）
  English: `[locked-off] In a long corridor at night, A-Tang stands dead center, two rows of doors perfectly mirrored, ceiling lights in a straight line. She is motionless, only her shadow at her feet. Final frame: the far door cracks open; she takes her first step.`（可直接复制）
- **免费档注意事项**：完全能用。"左右镜像"指令明确，模型执行得好，是韦斯·安德森式质感的廉价来源。
- **反例**：`对称的走廊，阿棠很害怕`（不要这么写）——"害怕"是情绪词；且没写她站在哪、门在哪，模型可能把对称摆错地方。

## 23. 框架构图（frame within a frame）
- **传统定义**：用门、窗、洞口在画面里再套一个框；情绪含义是偷窥感、禁锢感，"被钉在环境里"。
- **AI提示词写法**：
  中文：`[固定镜头]透过半开的木门看进去，阿棠坐在窗边桌前写信，门框把她框在画面中央。她写一会儿，停笔望向窗外。终帧定格：她放下笔，信纸被风吹到地上。`（可直接复制）
  English: `[locked-off] Through a half-open wooden door, A-Tang sits writing a letter at a window-side table, the doorframe boxing her at frame center. She writes, pauses, looks out the window. Final frame: she sets down the pen; the letter blows off onto the floor.`（可直接复制）
- **免费档注意事项**：完全能用。框中框天然带纵深，配合"机位不动加纵深走位"，免费档一致性压力最小。
- **反例**：`阿棠在屋里写信`（不要这么写）——没写"透过门框看"，框中框的禁锢感全丢；且没写谁的视角。

## 24. 引导线（leading lines）
- **传统定义**：用画面里的线（路、走廊、栏杆）把眼睛引向主体。
- **AI提示词写法**：
  中文：`[固定镜头]雨夜高架桥，车灯拉出两条光带，直指远方桥头站着的老周。他撑黑伞，伞下一点暖光。终帧定格：一辆车驶过，车灯把他的影子甩向镜头。`（可直接复制）
  English: `[locked-off] On an elevated highway on a rainy night, headlights draw two ribbons of light pointing straight to Lao Zhou at the far bridgehead. He holds a black umbrella, a small warm glow beneath it. Final frame: a car passes, its headlights throwing his shadow toward the lens.`（可直接复制）
- **免费档注意事项**：完全能用。引导线写进场景描述（"两条光带指向他"）即可，模型吃得好。
- **反例**：`高架桥夜景，很有纵深感`（不要这么写）——"纵深感"是评价词；没写线是什么、指向谁，模型不会自动安排引导线。

## 25. 负空间（negative space）
- **传统定义**：主体只占一小块，大量留白；情绪含义是孤独、渺小、未知，留白处藏着"还没发生的事"。
- **AI提示词写法**：
  中文：`[固定镜头]巨大灰蓝天空占满画面，老周只是地平线上的小黑点，慢慢移动，风声呼啸。终帧定格：他停下来，小黑点静止在画面左下角，天空空得发疼。`（可直接复制）
  English: `[locked-off] A vast grey-blue sky fills the frame; Lao Zhou is only a small black dot on the horizon, moving slowly, wind howling. Final frame: he stops, the dot frozen at the lower-left corner, the sky achingly empty.`（可直接复制）
- **免费档注意事项**：完全能用。负空间人物小，对 480P 不敏感，是免费档的天然朋友。
- **反例**：`老周在空旷的地方，很孤独`（不要这么写）——"孤独"是情绪词；没写"天空占满画面、人物只是小点"的具体比例。

## 26. 前景遮挡（foreground occlusion）
- **传统定义**：用前景物体（树枝、栏杆、人群）半遮画面；情绪含义是偷窥感、层次感，"我们不该看"。
- **AI提示词写法**：
  中文：`[固定镜头]透过咖啡馆绿植叶片看进去，阿棠和老周坐在角落卡座里，叶片虚成前景暗绿。她把怀表推到他面前，他摇头。终帧定格：他把怀表推回去，她的手停在半空。`（可直接复制）
  English: `[locked-off] Through café plant leaves, A-Tang and Lao Zhou sit in a corner booth, the leaves dissolving into dark-green foreground blur. She slides the pocket watch toward him; he shakes his head. Final frame: he slides the watch back; her hand hangs mid-air.`（可直接复制）
- **免费档注意事项**：完全能用。前景虚化还能藏穿帮（挡住不稳的边缘），一举两得。
- **反例**：`咖啡馆里两个人谈话`（不要这么写）——没写前景遮挡，画面变白开水；且"谈话"没写具体动作（推怀表）。

## 27. 倒影构图（reflection composition）
- **传统定义**：用水面、玻璃、镜面构图，实景与倒影并置；情绪含义是双重性、虚实难辨，"另一个他"。
- **AI提示词写法**：
  中文：`[固定镜头]雨后广场，积水如镜。画面下半是阿棠的倒影，上半是她本人，她低头看着水里的自己。终帧定格：她蹲下来，指尖触到水面，倒影里的脸正好完整。`（可直接复制）
  English: `[locked-off] After rain, the plaza's puddles lie like mirrors. The lower half holds A-Tang's reflection, the upper half herself, looking down at the water. Final frame: she crouches, fingertip touching the water, the reflected face whole again.`（可直接复制）
- **免费档注意事项**：部分能用。模型做不好"倒影与本人严格对称"，写"积水如镜、下半倒影"即可，别要求像素级对称。
- **反例**：`阿棠站在水边，倒影很美`（不要这么写）——"很美"是空形容词；没写倒影占画面哪一半、发生了什么变化。

## 28. 剪影构图（silhouette）
- **传统定义**：主体全黑、只留轮廓；情绪含义是神秘、藏拙，"看不清反而更可怕/更美"。
- **AI提示词写法**：
  中文：`[固定镜头]日落时分山顶，老周和阿棠并肩站成两个黑色剪影，挡住半轮红日，风吹动衣角。终帧定格：阿棠抬起手，剪影的手臂指向太阳落下的方向。`（可直接复制）
  English: `[locked-off] On a mountaintop at sunset, Lao Zhou and A-Tang stand side by side as two black silhouettes against half a red sun, wind lifting their coat hems. Final frame: A-Tang raises her hand, the silhouetted arm pointing where the sun went down.`（可直接复制）
- **免费档注意事项**：完全能用。剪影等于看不清脸，是 AI 安全区；"逆光加主体全黑"指令模型执行得很稳。
- **反例**：`剪影，老周和阿棠很浪漫`（不要这么写）——"浪漫"是情绪词；没写光源在哪（剪影必须写"挡住红日"这种光源）。

## 29. 顶视（top shot / bird's eye）
- **传统定义**：镜头垂直向下；情绪含义是上帝视角的极致，人物成棋子，命运感拉满。
- **AI提示词写法**：
  中文：`[固定镜头·顶视]镜头垂直向下：雨夜十字路口，阿棠撑黑伞站在斑马线中央，车流绕着她走，像棋盘。她仰起脸，雨点打在脸上。终帧定格：一辆车溅起水花，她的伞偏了一下，又扶正。`（可直接复制）
  English: `[locked-off top shot] The camera looks straight down: at a rainy intersection at night, A-Tang stands at the zebra crossing's center under a black umbrella, traffic flowing around her like a chessboard. She tilts her face up, rain hitting it. Final frame: a car splashes water; her umbrella tips, then rights itself.`（可直接复制）
- **免费档注意事项**：完全能用。顶视构图简单、人物小，对 480P 友好。
- **反例**：`俯视路口，场面很大`（不要这么写）——"场面很大"是空话；没写垂直向下、人物位置、发生了什么。

## 30. 低角度仰视（low angle）
- **传统定义**：镜头低于人物向上拍；情绪含义是人物高大、有权力，观众在"仰望"。
- **AI提示词写法**：
  中文：`[固定镜头·低角度]镜头贴近地面向上：老周站在台阶顶上，逆光，身影把天空切成两半。他一步一步走下来，每步踩得很实。终帧定格：他走到镜头前弯腰，脸第一次入画，直视镜头。`（可直接复制）
  English: `[locked-off low angle] The camera hugs the ground looking up: Lao Zhou stands atop the steps, backlit, his figure splitting the sky in two. He descends step by step, each footfall planted hard. Final frame: he reaches the lens and bends down, his face entering frame for the first time, looking straight into it.`（可直接复制）
- **免费档注意事项**：完全能用。角度词写准（low-angle/低角度），是"一句话定权力关系"最便宜的工具。
- **反例**：`仰拍老周，很有气势`（不要这么写）——"有气势"是评价词；没写机位多低、他在干什么（走下来）。

## 31. 荷兰角（Dutch angle / canted angle）
- **传统定义**：画面整体倾斜；情绪含义是世界"歪了"：不安、醉酒、秩序崩坏。
- **AI提示词写法**：
  中文：`[固定镜头·荷兰角]画面整体向右倾斜约15度：阿棠扶着酒吧吧台勉强站稳，酒杯倒在桌上，酒液往下淌。她伸手去抓酒杯，抓空了。终帧定格：她的手停在半空，酒液滴到地上。`（可直接复制）
  English: `[locked-off Dutch angle] The whole frame tilts right about 15 degrees: A-Tang grips a bar counter, barely steady, a tipped glass spilling liquor across the table. She reaches for the glass and misses. Final frame: her hand hangs mid-air, liquor dripping to the floor.`（可直接复制）
- **免费档注意事项**：能用。写清倾斜角度（"约 15 度"），别写"画面歪一点"。
- **反例**：`镜头歪着拍，阿棠喝醉了`（不要这么写）——"喝醉了"是状态不是画面；没写倾斜多少度、歪向哪边。

## 32. 浅景深隔离（shallow depth of field）
- **传统定义**：主体清晰、背景虚化；情绪含义是把人物从世界里"摘"出来，观众只能看他。
- **AI提示词写法**：
  中文：`[固定镜头·浅景深]菜市场人流虚成一片彩色雾气，只有老周的脸是清晰的。他捏着一颗西红柿凑到眼前看。终帧定格：他把西红柿放进袋子，嘴角动了一下，像笑了。`（可直接复制）
  English: `[locked-off, shallow depth of field] The market crowd dissolves into colored haze; only Lao Zhou's face is sharp. He holds a tomato up close, inspecting it. Final frame: he drops the tomato into his bag, the corner of his mouth twitching like a smile.`（可直接复制）
- **免费档注意事项**：能用。"背景虚化、主体清晰"模型吃得好，还能藏背景穿帮。
- **反例**：`背景虚化，老周买菜很开心`（不要这么写）——"很开心"是情绪词；没写虚化到什么程度、主体在干什么（捏西红柿看）。

## 33. 深焦全景（deep focus wide）
- **传统定义**：前景、中景、背景同时清晰；情绪含义是客观、史诗，"一个镜头讲三层故事"。
- **AI提示词写法**：
  中文：`[固定镜头·深焦]老宅院子：前景阿棠在井边打水，中景老周在廊下劈柴，背景远山和炊烟，三层同样清晰。终帧定格：阿棠提起水桶，水洒出来，老周抬头看了她一眼。`（可直接复制）
  English: `[locked-off, deep focus] In the old house's courtyard: foreground, A-Tang drawing water at the well; midground, Lao Zhou chopping firewood under the eaves; background, distant mountains and cooking smoke — all three planes sharp. Final frame: she lifts the bucket, water sloshing out; he glances up at her.`（可直接复制）
- **免费档注意事项**：能用。深焦加固定机位加纵深走位是侯孝贤式调度，免费档一致性压力最小。
- **反例**：`院子里大家都在干活，画面很丰富`（不要这么写）——"很丰富"是空话；没写三层分别是什么、谁在干什么。

## 34. 人物压边（edge framing）
- **传统定义**：人物被挤到画面边缘，大量空间留给"他看的东西"或"空无"；情绪含义是被排挤、渺小，未知压过来。
- **AI提示词写法**：
  中文：`[固定镜头]阿棠被挤在画面最左侧，只占五分之一，右侧大片黑暗里隐约是一扇半开的门。她盯着门，手指绞着衣角。终帧定格：门缝透出一线光，她往前迈了半步，又停住。`（可直接复制）
  English: `[locked-off] A-Tang is squeezed to the frame's far left, taking one fifth; the remaining darkness holds a half-open door. She stares at it, fingers twisting her sleeve. Final frame: a thread of light leaks through the crack; she takes half a step forward, then stops.`（可直接复制）
- **免费档注意事项**：完全能用。人物位置写百分比（"占五分之一""最左侧"），模型执行得好。
- **反例**：`阿棠站在画面边上，气氛很压抑`（不要这么写）——"压抑"是情绪词；没写她占多少、画面其余部分是什么。

## 35. 留白呼吸感（breathing room）
- **传统定义**：人物头顶/视线方向留出大量空位；情绪含义是喘息、思考，"还没说完"。
- **AI提示词写法**：
  中文：`[固定镜头]老周坐江边石头上，占据画面下方三分之一，头顶是巨大灰蓝天空。他望着江面，手里转着一枚硬币。终帧定格：他把硬币弹向空中，又接住，没有扔出去。`（可直接复制）
  English: `[locked-off] Lao Zhou sits on a riverbank rock, filling the lower third, a huge grey-blue sky above his head. He gazes at the water, rolling a coin in his fingers. Final frame: he flips the coin into the air, catches it, and does not throw it.`（可直接复制）
- **免费档注意事项**：完全能用。留白构图简单，写"头顶留大量天空"即可。
- **反例**：`老周在江边，画面很空`（不要这么写）——"很空"是感觉；没写人物占下方三分之一、头顶留天，模型可能把人物放中央。
