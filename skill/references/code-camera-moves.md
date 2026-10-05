# 运镜 20 种

## 1. 推镜（dolly in / push in）
- **传统定义**：摄影机沿镜头轴线向主体物理前移（不是变焦放大），有"穿过空间"的体感；情绪含义是逼近、真相浮现、内心被挤压出来，慢推等于凝视的加深。
- **AI提示词写法**：
  中文：`[推镜]深夜空街，阿棠黑风衣站在路灯下，看掌心旧怀表。镜头沿轴线缓慢前推，焦段不变，她比身后路灯放大得更快。终帧定格：怀表特写，拇指停在表盖上。`（可直接复制）
  English: `[slow push in] On an empty street at night, A-Tang in a black trench coat stands under a lamppost, studying an old pocket watch in her palm. The camera moves forward along its axis, focal length unchanged; she grows faster than the lamppost behind her. Final frame: close-up of the watch, her thumb resting on the lid.`（可直接复制）
- **免费档注意事项**：能用，是免费档最稳的运镜之一。必须写死幅度（"人物放大不超过 1.5 倍"）；别写 "zoom in"，模型会把推镜坍缩成中央裁剪。
- **反例**：`[推镜]阿棠很美，镜头电影感地推进`（不要这么写）——"很美""电影感"是空形容词，模型无所适从；且没写推什么、推多远、落在哪。

## 2. 拉镜（dolly out / pull back）
- **传统定义**：摄影机沿轴线后移，揭示更多环境；情绪含义是抽离、恍然大悟，"把人物还给世界"，拉镜结尾等于观众得以喘息。
- **AI提示词写法**：
  中文：`[拉镜]狭窄审讯室，老周坐铁椅上，双手交握抵着额头。镜头沿轴线缓慢后拉，画面边缘露出整间屋子：单面镜、墙上的钟。终帧定格：他缩在空荡房间中央的远景。`（可直接复制）
  English: `[slow pull back] In a cramped interrogation room, Lao Zhou sits on a metal chair, hands clasped against his forehead. The camera moves backward along its axis; the frame edges reveal the whole room: a one-way mirror, a clock on the wall. Final frame: wide shot of him shrunken at the center of the empty room.`（可直接复制）
- **免费档注意事项**：能用。4 秒只够"2–3 米体感"的拉开，别写"拉出整个城市"，空间跳变必糊。
- **反例**：`镜头zoom out，阿棠震惊地后退`（不要这么写）——zoom out 易被做成中央裁剪反向；且"震惊"是情绪词，应写成表情终点加身体动作。

## 3. 摇镜（pan）
- **传统定义**：机位固定不动，镜头水平旋转；情绪含义是扫视、寻找，"看"这个动作本身，慢摇等于审视。
- **AI提示词写法**：
  中文：`[摇镜]老周站在天台边缘，背对镜头。机位固定不动，镜头缓慢向右旋转，掠过远处楼群、江面上的船。终帧定格：停在他侧脸上，他转头，视线迎向画右。`（可直接复制）
  English: `[slow pan right] Lao Zhou stands at the rooftop edge, back to camera. The camera stays fixed and rotates slowly right, sweeping past distant towers and a boat on the river. Final frame: it settles on his profile as he turns his head, gaze meeting frame-right.`（可直接复制）
- **免费档注意事项**：能用。必须写"机位固定、只转镜头"，否则模型会做成横移；别写"镜头向左移动"，那是横移不是摇镜。
- **反例**：`镜头向左移动扫过城市`（不要这么写）——"移动"等于横移；且没写机位是否固定，模型大概率走错。

## 4. 横移（truck / slide）
- **传统定义**：摄影机整体沿平行线横向滑动（区别于摇镜的原地转头）；情绪含义是陪伴、并行，"我和你一起走"。
- **AI提示词写法**：
  中文：`[横移]雨夜老街，阿棠撑伞从画左走向画右。镜头与她平行，匀速向右横向滑动，近处屋檐掠过得比远处灯火快。终帧定格：她停在画面中央，伞尖一滴水正好落下。`（可直接复制）
  English: `[lateral truck right] On a rainy old street at night, A-Tang walks frame-left to frame-right under an umbrella. The camera slides right at her pace, parallel to her path; near eaves sweep past faster than distant lamps. Final frame: she stops at frame center, one drop falling from the umbrella tip.`（可直接复制）
- **免费档注意事项**：能用。必须写"与人物/墙面平行"，否则模型会转弯或做成摇镜。
- **反例**：`镜头跟着她横着走`（不要这么写）——"横着走"含糊（横移还是摇镜？），没写平行关系和速度，模型会转弯。

## 5. 升降（crane up / crane down）
- **传统定义**：摄影机在摇臂上垂直升降；上升等于超脱、上帝视角、希望，下降等于下坠、渺小、命运压顶。
- **AI提示词写法**：
  中文：`[升镜]清晨菜市场，老周蹲在摊位前挑菜。镜头从他身后约一米高度笔直上升，保持水平，摊位、人流、整条街道依次入画。终帧定格：整条街道的俯视全景，他只是人群中的一个点。`（可直接复制）
  English: `[crane up] At a morning market, Lao Zhou crouches picking vegetables at a stall. The camera rises straight up from about one metre behind him, staying level, taking in the stall, the crowd, the whole street. Final frame: overhead wide of the entire street; he is one dot in the crowd.`（可直接复制）
- **免费档注意事项**：能用。升降幅度写死（"上升约一米"）；别写 "tilt up"，那是摇镜头上下转，不是机位升降。
- **反例**：`tilt up，阿棠从绝望中看到希望`（不要这么写）——tilt 是转镜头不是升降；"看到希望"是抽象情绪，没有可画的动作。

## 6. 环绕（orbit / arc shot）
- **传统定义**：摄影机以主体为圆心做圆弧运动；情绪含义是审视、眩晕、时间凝固，"世界围着他转/他被世界围观"。
- **AI提示词写法**：
  中文：`[环绕]废弃工厂中央，阿棠站在光柱里，仰头看顶棚破洞。镜头以她为圆心缓慢顺时针环绕约30度，她始终居中，铁架背景缓缓扫过。终帧定格：环绕停在她正侧面，光柱斜切过她的脸。`（可直接复制）
  English: `[slow orbit] In an abandoned factory, A-Tang stands in a shaft of light, head tilted toward a hole in the roof. The camera circles her slowly clockwise about 30 degrees; she stays centered, iron frames sweeping behind. Final frame: the orbit ends at her profile, the light shaft cutting diagonally across her face.`（可直接复制）
- **免费档注意事项**：部分能用，翻车率最高，慎用。4 秒只够约 30°，写 360° 必糊；必须写圆心、方向、角度。
- **反例**：`镜头360度旋转，阿棠很震惊`（不要这么写）——4 秒 360° 模型必糊；"震惊"是情绪词；且没写圆心和半径。

## 7. 跟拍（tracking / follow shot）
- **传统定义**：摄影机跟随人物移动（前跟/后跟/侧跟）；情绪含义是主观陪伴、紧迫感，"甩不掉"。
- **AI提示词写法**：
  中文：`[跟拍]老周在雨中快步穿过胡同，镜头跟在他身后半步，贴近他的肩膀。他拐过墙角时镜头同步转向，雨水打湿他的衣领。终帧定格：他冲出胡同口，停在路灯下，背影充满画面。`（可直接复制）
  English: `[follow from behind] Lao Zhou hurries through a rain-soaked alley, the camera half a step behind him, tight on his shoulders. It turns with him around the corner, rain darkening his collar. Final frame: he bursts out of the alley mouth and stops under a lamppost, his back filling the frame.`（可直接复制）
- **免费档注意事项**：能用。必须写清"前跟/后跟/侧跟"，不写模型随机选，连续两段必穿帮。
- **反例**：`镜头跟着老周走`（不要这么写）——没写前跟还是后跟、距离多远，模型随机选，续接必穿帮。

## 8. 手持呼吸感（handheld breathing）
- **传统定义**：极轻微的晃动，幅度小、频率缓，像人的呼吸；情绪含义是在场、亲密，"我就在他身边"。
- **AI提示词写法**：
  中文：`[固定机位+手持呼吸感]深夜厨房，阿棠坐桌边，双手捧热茶，蒸汽升起。镜头几乎不动，只有极轻微的起伏，像人在呼吸，幅度不超过一指宽。终帧定格：她把茶杯放回桌面，发出轻响。`（可直接复制）
  English: `[locked-off with handheld breathing] In a kitchen at night, A-Tang sits at the table, both hands around hot tea, steam rising. The camera barely moves, only a faint rise and fall like breathing, less than a finger's width. Final frame: she sets the cup back on the table with a soft clink.`（可直接复制）
- **免费档注意事项**：能用。必须写死幅度（"不超过一指宽"），不写幅度模型会做成过山车。
- **反例**：`手持拍摄，阿棠很悲伤`（不要这么写）——"手持"没写幅度，模型大概率给过山车；"悲伤"是情绪词。

## 9. 手持纪实感（documentary handheld）
- **传统定义**：中等幅度、可控的晃动，像新闻现场；情绪含义是"这是真的、正在发生"。
- **AI提示词写法**：
  中文：`[手持纪实感]清晨拆迁现场，老周站在废墟前，攥着一纸通知。镜头在他身侧，晃动明显但可控，像记者在拍，跟着他的视线扫过断墙。终帧定格：他抬手指向画右的塔吊，手停在半空。`（可直接复制）
  English: `[documentary handheld] At a demolition site at dawn, Lao Zhou stands before rubble, clutching a notice. The camera stays at his side, shaking visibly but under control like a news crew, following his gaze across broken walls. Final frame: he raises a hand pointing frame-right at a tower crane, the hand frozen mid-air.`（可直接复制）
- **免费档注意事项**：能用。写"晃动明显但可控，像新闻现场"，禁用"剧烈"一词。
- **反例**：`shaky cam，老周很愤怒`（不要这么写）——shaky cam 无幅度约束等于过山车；"愤怒"是情绪词，应写成攥紧通知、指向的动作。

## 10. 手持失控感（chaotic handheld）
- **传统定义**：大幅抖动甚至失焦；情绪含义是混乱、恐慌、世界散架，一场戏只许用一次高潮。
- **AI提示词写法**：
  中文：`[手持失控感]暴雨夜车祸现场，阿棠举手机电筒在人群里挤，画面剧烈晃动，偶尔失焦。警灯红蓝交替扫过她的脸。终帧定格：她挤到警戒线前，电筒光柱定在一辆侧翻的车上。`（可直接复制）
  English: `[chaotic handheld] At a crash scene on a stormy night, A-Tang pushes through the crowd holding up her phone flashlight, the frame shaking hard, occasionally losing focus. Police lights sweep red and blue across her face. Final frame: she reaches the cordon, her flashlight beam locking onto an overturned car.`（可直接复制）
- **免费档注意事项**：部分能用，翻车率高。一场戏只许一次，慎用；全程手持晃等于没有强度，观众 5 分钟脱敏。
- **反例**：`全片手持晃，老周逃命`（不要这么写）——全程一个强度就是没有强度；且"逃命"没写具体动作（跑、挤、摔）。

## 11. 固定机位（locked-off）
- **传统定义**：相机锁死，一动不动；情绪含义是凝视、审判，"时间自己流过去"。
- **AI提示词写法**：
  中文：`[固定镜头]老宅堂屋，老周坐太师椅上一动不动，只有窗外光斑缓慢移动。镜头锁在三脚架上，纹丝不动。终帧定格：光斑移到他脸上，他缓缓闭上眼睛。`（可直接复制）
  English: `[locked-off] In the old house's main hall, Lao Zhou sits motionless in a hardwood chair; only patches of window light drift slowly. The camera is locked on a tripod, perfectly still. Final frame: a light patch reaches his face and he slowly closes his eyes.`（可直接复制）
- **免费档注意事项**：能用，是免费档最稳的运镜（建议约 40% 镜头用它）。"让环境动、机位不动"是最省预算的电影感；静止必须明说"纹丝不动"。
- **反例**：`（不写运镜）老周坐在屋里`（不要这么写）——不写运镜，模型默认可能加推镜或晃动；静止是需要声明的指令。

## 12. 移焦（rack focus / focus pull）
- **传统定义**：焦点在纵深方向上切换（前景转背景），构图不变；情绪含义是注意力的转移，"真相在另一层"。
- **AI提示词写法**：
  中文：`[固定镜头+移焦]雨夜窗前，阿棠的脸贴在玻璃上。起初焦点在她脸颊的水汽上，窗外街道模糊；焦点缓慢外移，对面楼下站着一个撑黑伞的人。终帧定格：黑伞的人清晰，她的脸虚成一片柔光，构图全程不变。`（可直接复制）
  English: `[locked-off with rack focus] At a rainy window at night, A-Tang's face presses against the glass. Focus starts on the condensation on her cheek, the street behind blurred; focus shifts slowly outward to a figure with a black umbrella across the street. Final frame: the umbrella figure sharp, her face dissolved into soft blur, framing unchanged throughout.`（可直接复制）
- **免费档注意事项**：部分能用。MiniMax 对焦段变化执行不稳定，必须写清"构图不变、只转焦点"。
- **反例**：`focus on her，阿棠发现有人跟踪`（不要这么写）——"focus on her"会被理解成"拍她"，不是移焦；且"发现"是心理活动，要写成"视线钉住"的动作。

## 13. 变焦（zoom in / zoom out）
- **传统定义**：焦段变化、机位不动的光学放大；与推镜的几何区别：推镜是"穿过空间"（人物比背景放大得快），变焦是"画面整体放大"（前后景同速放大）；情绪含义是偷窥、监视，"被盯上"。
- **AI提示词写法**：
  中文：`[变焦推进]天台对面楼顶，老周蹲在水箱后打电话。镜头机位不动，焦段缓慢拉长，画面整体放大，他周围楼群跟着一起变大，没有空间穿行感。终帧定格：他的脸充满画面，嘴唇在动，听不清说什么。`（可直接复制）
  English: `[slow zoom in] On the opposite rooftop, Lao Zhou crouches behind a water tank making a phone call. The camera does not move; focal length lengthens slowly, the whole frame magnifies, surrounding towers growing at the same rate, no sense of traveling through space. Final frame: his face fills the frame, lips moving, words inaudible.`（可直接复制）
- **免费档注意事项**：能用但慎用。想真推镜必须写几何区别（"人物比背景放大得快"），否则模型把 dolly 和 zoom 坍缩成同一个中央裁剪。
- **反例**：`zoom in，老周很紧张`（不要这么写）——zoom 和 dolly 混用，模型随机坍缩；"紧张"是情绪词，应写"他攥紧手机，指节发白"。

## 14. 甩镜（whip pan）
- **传统定义**：极快的摇镜，画面横向撕过；情绪含义是惊觉、转场，"世界被甩到另一边"。
- **AI提示词写法**：
  中文：`[甩镜]老周猛地转头看向画右，镜头随他视线极速向右甩过，画面横向撕成残影。终帧定格：残影散去，巷口的阿棠撑黑伞一动不动，她的脸清晰地钉在画面中央。`（可直接复制）
  English: `[whip pan] Lao Zhou snaps his head toward frame-right; the camera whips right with his gaze, the frame tearing sideways into motion streaks. Final frame: the streaks clear; at the alley mouth A-Tang stands motionless with her black umbrella, her face pinned sharp at frame center.`（可直接复制）
- **免费档注意事项**：部分能用。甩镜是藏剪辑点的利器（伪一镜），但 4 秒里只能甩一次，甩完必须给落点。
- **反例**：`快速摇镜头，老周很吃惊`（不要这么写）——"快速摇"没写甩的方向和落点；"吃惊"是情绪词，应写"他猛地转头"的动作。

## 15. 航拍感（aerial / drone feel）
- **传统定义**：高空俯视的运镜质感；情绪含义是渺小、命运感，"人在做，天在看"。
- **AI提示词写法**：
  中文：`[航拍感]戈壁滩上，一条公路笔直伸向地平线，老周开旧皮卡，车小如蚁。镜头从高空缓慢前移，公路、戈壁、远山依次铺开。终帧定格：皮卡驶入画面下方三分之一处，扬起一道长长尘烟。`（可直接复制）
  English: `[aerial feel] Over the Gobi, a highway runs straight to the horizon, Lao Zhou driving an old pickup, tiny as an ant. The camera glides forward from high above; highway, desert and distant mountains unfold. Final frame: the pickup enters the lower third, trailing a long plume of dust.`（可直接复制）
- **免费档注意事项**：能用。免费档没有真航拍参数，写"高空俯视、缓慢前移"即可；人物宜小，对 480P 不敏感。
- **反例**：`无人机航拍，风景很美`（不要这么写）——"风景很美"是空形容词；且没写高度、方向、画面里有什么。

## 16. 低角度跟拍（low-angle tracking）
- **传统定义**：机位低于人物、向上拍的跟拍；情绪含义是人物高大、有压迫感，观众在"仰望"。
- **AI提示词写法**：
  中文：`[低角度跟拍]雨夜地下通道，阿棠踩水洼大步向前。镜头贴近地面跟随，向上仰拍，她的身影高大，头顶的灯一盏盏掠过。终帧定格：她停在通道出口，剪影挡住外面的光。`（可直接复制）
  English: `[low-angle tracking] In an underground passage on a rainy night, A-Tang strides through puddles. The camera tracks near the ground, angled up; she looms large, overhead lamps sweeping past. Final frame: she stops at the passage exit, her silhouette blocking the outside light.`（可直接复制）
- **免费档注意事项**：能用。角度是"一句话定权力关系"最便宜的工具，写准"贴近地面、向上仰拍"。
- **反例**：`低角度，老周很威风`（不要这么写）——"威风"是评价词；且没写跟拍还是固定，机位一句话没交代。

## 17. 过肩推进（OTS push-in / over-the-shoulder push）
- **传统定义**：从人物肩后向前推进的镜头；情绪含义是逼近真相，"我们一起看过去"。
- **AI提示词写法**：
  中文：`[过肩推进]老周的肩膀占画面左侧前景，焦点越过他的肩头。镜头缓慢前推，穿过他的肩线，落在远处天台边缘的阿棠身上。终帧定格：阿棠的背影清晰，他的肩膀虚成前景暗角。`（可直接复制）
  English: `[OTS push-in] Lao Zhou's shoulder fills the left foreground, focus beyond it. The camera pushes slowly forward past his shoulder line, landing on A-Tang at the far rooftop edge. Final frame: her back sharp, his shoulder dissolved into a dark foreground blur.`（可直接复制）
- **免费档注意事项**：能用。过肩镜头天然带轴线信息（"谁在看谁"），是省台词的利器。
- **反例**：`从老周背后拍过去，他很担心阿棠`（不要这么写）——"担心"是情绪词；且没写推进、没写焦点变化，模型可能只给个静态背影。

## 18. 环绕半圈（180° arc）
- **传统定义**：环绕的受控版本，只走半圈；情绪含义是审视升级，"世界围着他转了半圈"。
- **AI提示词写法**：
  中文：`[环绕半圈]审讯室里，老周坐椅子上。镜头以他为圆心缓慢走半圈，从他的正面转到正侧面，灯光在他脸上从亮转暗。终帧定格：镜头停在他正侧面，半张脸沉在阴影里，他的手指停在桌面上。`（可直接复制）
  English: `[half-circle arc] In the interrogation room, Lao Zhou sits in the chair. The camera arcs a slow half-circle around him, from front to full profile; light slides from bright to dark across his face. Final frame: the camera rests at his profile, half his face sunk in shadow, his finger still on the table.`（可直接复制）
- **免费档注意事项**：部分能用。比整圈环绕稳，但必须写死"半圈、从正面到侧面"，否则模型走过头。
- **反例**：`镜头围着老周转，他在想事情`（不要这么写）——"转"没写角度和起止；"想事情"是心理活动，要写成"手指敲桌面"的动作。

## 19. 推近到特写（push to close-up）
- **传统定义**：从中景一路推到脸部特写；情绪含义是情绪升级，"观众无处可逃"。
- **AI提示词写法**：
  中文：`[推近到特写]天台上，阿棠背对镜头望江面。镜头从她背影中景缓慢推近，穿过肩线，停在脸部特写：一滴眼泪滑到嘴角，她抿住嘴。终帧定格：特写里她的眼睛看向画右，眼泪停在下巴上。`（可直接复制）
  English: `[push to close-up] On the rooftop, A-Tang faces the river, back to camera. The lens pushes slowly from a medium of her back, past her shoulder line, settling on a close-up: a tear slides to the corner of her mouth; she presses her lips together. Final frame: in close-up her eyes look frame-right, the tear resting on her chin.`（可直接复制）
- **免费档注意事项**：能用。情绪升级的标准件（中景→特写逐档推近），但终点必须是"表情终点"不是情绪词。
- **反例**：`推近，阿棠哭了`（不要这么写）——"哭了"是结果，模型会给夸张的哭脸；应写"眼泪滑到嘴角、抿住嘴"的物理终点。

## 20. 拉远 reveal（pull-back reveal）
- **传统定义**：从特写/中景拉开，揭示出乎意料的环境；情绪含义是恍然大悟、"原来如此"，人物被环境吞没。
- **AI提示词写法**：
  中文：`[拉远揭示]特写：阿棠的手紧攥一张车票，指节发白。镜头缓慢拉远，揭示她独坐在一节空无一人的绿皮车厢里，窗外是无边雪原。终帧定格：远景里她缩在座位一角，车票被风吹得翻飞。`（可直接复制）
  English: `[pull-back reveal] Close-up: A-Tang's hand grips a train ticket hard, knuckles white. The camera pulls back slowly, revealing her alone in an empty green train carriage, endless snowfields outside. Final frame: wide shot of her huddled in a corner seat, the ticket fluttering in the wind.`（可直接复制）
- **免费档注意事项**：能用。reveal 的冲击力来自"前后反差"，拉开前必须先给足特写的信息量。
- **反例**：`拉远，露出她在火车上`（不要这么写）——"露出"太平淡，没写从什么景别拉到什么景别；且"火车上"信息量不足，reveal 需要反差（空车厢加雪原）。
