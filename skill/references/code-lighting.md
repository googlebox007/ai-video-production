# 灯光 10 种（每种写清"光源 + 落在什么表面上"，motivated lighting，不写情绪词）

## 36. 伦勃朗光（Rembrandt lighting）
- **传统定义**：主光在人物侧上方，鼻影与脸颊阴影连成一片，在暗侧脸颊上"困"出倒三角光斑；气质是有故事、有分量、亦正亦邪。
- **AI提示词写法**：
  中文：`[固定镜头]老周坐窗边椅子上，唯一的窗户在他左上方。光从窗口斜切进来，在他右侧脸颊困出一小块倒三角光斑，鼻影连着脸颊阴影。终帧定格：他抬起眼，三角光斑随他的脸动了一下。`（可直接复制）
  English: `[locked-off] Lao Zhou sits in a chair by the window, the only window high to his left. Light slants in, trapping a small inverted triangle of light on his right cheek, nose shadow joined to the cheek's shadow. Final frame: he lifts his eyes; the triangle shifts with his face.`（可直接复制）
- **免费档注意事项**：能用。布光词要写"光源在哪、落在脸上哪"，不要只写"伦勃朗光"四个字（中英都写最稳：Rembrandt lighting）。
- **反例**：`伦勃朗光，老周很有故事感`（不要这么写）——"有故事感"是情绪词；没写光源位置（左上方的窗），模型布光会乱。

## 37. 蝴蝶光（butterfly lighting / Paramount lighting）
- **传统定义**：主光正对人物、高高在上，鼻子正下方投出对称的蝴蝶形小影；气质是 glamour、精致、明星感。
- **AI提示词写法**：
  中文：`[固定镜头]化妆镜前，阿棠坐着，镜框上的灯带是唯一光源，从她正上方打下来。鼻子下方投出对称的小影，像蝴蝶，颧骨被照亮。终帧定格：她合上口红盖，镜子里她的眼睛看向镜头。`（可直接复制）
  English: `[locked-off] Before a dressing mirror, A-Tang sits; the bulb strip around the mirror is the only source, striking from directly above. A small symmetrical shadow like a butterfly falls under her nose, cheekbones lit. Final frame: she caps the lipstick; her eyes in the mirror meet the lens.`（可直接复制）
- **免费档注意事项**：能用。女性特写默认光，但会暴露法令纹，慎用于年长男性。
- **反例**：`蝴蝶光，阿棠很美`（不要这么写）——"很美"是空形容词；没写光源（镜框灯带）在正上方。

## 38. 分割光（split lighting）
- **传统定义**：主光在人物正侧面 90°，半边脸亮、半边脸黑，脸被"劈"成阴阳两半；气质是神秘、危险，"这个人有两副面孔"。
- **AI提示词写法**：
  中文：`[固定镜头]走廊尽头壁灯是唯一光源，在阿棠正左侧。她右半边脸沉在黑暗里，左半边脸被照亮，分界线劈过鼻梁。终帧定格：她缓缓转头，亮与暗在她脸上交换了位置。`（可直接复制）
  English: `[locked-off] The corridor's end sconce is the only source, at her exact left. Her right cheek sinks into darkness, her left lit, the dividing line splitting her nose bridge. Final frame: she slowly turns her head; light and dark trade places on her face.`（可直接复制）
- **免费档注意事项**：能用。硬光加分割光是 noir 标配，写"光源在正左侧 90°"模型执行得好。
- **反例**：`一半脸亮一半脸黑，气氛很悬疑`（不要这么写）——"悬疑"是情绪词；没写光源在哪一侧、多少度。

## 39. 轮廓光（rim light / back light）
- **传统定义**：光源在人物脑后，在头发和肩膀上勾一条亮边；功能只有一个：把人物从背景上"撕"下来。
- **AI提示词写法**：
  中文：`[固定镜头]天台上，老周背对镜头，城市灯火在他身后。轮廓光沿他肩膀和头发勾出一圈亮边，把他的剪影从夜色里撕出来。终帧定格：他抬起手，亮边跟着他的手臂动了一下。`（可直接复制）
  English: `[locked-off] On the rooftop, Lao Zhou stands back to camera, city lights behind him. Rim light traces a bright edge along his shoulders and hair, tearing his silhouette out of the night. Final frame: he raises a hand; the bright edge follows his arm.`（可直接复制）
- **免费档注意事项**：完全能用。轮廓光是"人物不贴背景"的保命灯，夜景人物必写。
- **反例**：`老周站在天台，背景很亮`（不要这么写）——"背景很亮"没写光在人物脑后勾亮边；且没写光源和人物的位置关系。

## 40. 剪影光（silhouette lighting）
- **传统定义**：人物正对强光源、机位在暗侧，人物全黑只留轮廓；光源必须入画或明确可感。
- **AI提示词写法**：
  中文：`[固定镜头]落日余晖从落地窗灌进来，阿棠站在窗前，整个人黑成剪影，只有发丝边缘透着金边。她举起怀表对着光看。终帧定格：她把怀表贴在心口，剪影的手臂弯成一个弧。`（可直接复制）
  English: `[locked-off] Sunset pours through the floor-to-ceiling window; A-Tang stands before it, black as a silhouette, only her hair's edge glowing gold. She holds the pocket watch up to the light. Final frame: she presses the watch to her chest, her silhouetted arm curving into an arc.`（可直接复制）
- **免费档注意事项**：完全能用。剪影等于看不清脸，是 AI 安全区；光源（落日/窗）必须写进画面。
- **反例**：`剪影，阿棠很忧伤`（不要这么写）——"忧伤"是情绪词；没写光源（落日从落地窗进来）。

## 41. 烛光暖源（candlelight practical）
- **传统定义**：画面内的蜡烛/油灯是唯一暖光源，光落在人物脸上，暖色、随烛火闪烁。
- **AI提示词写法**：
  中文：`[固定镜头]停电的老屋里，桌上三根蜡烛是唯一光源。暖黄的光落在老周脸上，随烛火轻轻晃动，墙上影子跟着摇。终帧定格：他吹灭一根蜡烛，烟升起来，光暗了一格。`（可直接复制）
  English: `[locked-off] In the blacked-out old house, three candles on the table are the only source. Warm yellow light falls on Lao Zhou's face, trembling with the flames, shadows swaying on the wall. Final frame: he blows one candle out; smoke rises, the light dropping a notch.`（可直接复制）
- **免费档注意事项**：能用。practical 灯具（蜡烛）必须入画，等于光源自证清白，否则观众潜意识报警"假"。
- **反例**：`暖光，老周在烛光里很温暖`（不要这么写）——"温暖"是情绪词；没写蜡烛在桌上、光落在脸上、烛火晃动。

## 42. 月光冷源（moonlight cold source）
- **传统定义**：月亮是唯一光源，冷蓝、高反差，光落在人物和地面上，影子又长又直。
- **AI提示词写法**：
  中文：`[固定镜头]院子里只有月光。冷蓝的光落在阿棠身上，把她的影子钉在青石板上，又长又直。她赤脚站在石板上。终帧定格：云遮住月亮，光灭一瞬又回来，她还在原地，深黑阴影不提亮。`（可直接复制）
  English: `[locked-off] Only moonlight in the courtyard. Cold blue light falls on A-Tang, pinning her long straight shadow to the stone slabs; she stands barefoot. Final frame: a cloud covers the moon, the light dies for a beat and returns; she hasn't moved, deep shadows never lifted.`（可直接复制）
- **免费档注意事项**：部分能用。MiniMax 爱把夜景"美化"（提亮阴影），必须加压制句"深黑阴影不提亮"。
- **反例**：`月光下阿棠很美，氛围拉满`（不要这么写）——"很美""氛围拉满"全是空词；没写光落在石板和她身上、影子多长。

## 43. 霓虹混合色温（neon mixed color temperature）
- **传统定义**：两种以上色温的光源同时存在（如红霓虹加青霓虹），分别落在人物两侧脸上。
- **AI提示词写法**：
  中文：`[固定镜头]雨夜巷口，左侧红色霓虹灯牌，右侧青色便利店灯箱。红光落在阿棠左脸，青光落在她右脸，鼻梁是分界线。终帧定格：她摘下帽子甩了甩头发，又戴回去，红蓝在她脸上重新拼好。`（可直接复制）
  English: `[locked-off] At a rainy alley mouth, a red neon sign left, a cyan convenience-store lightbox right. Red falls on A-Tang's left cheek, cyan on her right, her nose bridge the dividing line. Final frame: she takes off her cap, shakes her hair, pulls it back on; red and cyan reassemble on her face.`（可直接复制）
- **免费档注意事项**：能用。混合色温必须写清"哪个光源什么颜色、落在脸的哪一侧"，否则模型和成一团。
- **反例**：`霓虹灯下，阿棠很赛博朋克`（不要这么写）——"赛博朋克"是风格标签不是布光；没写红左青右、光源位置。

## 44. 顶光压迫（top light oppression）
- **传统定义**：光源在人物正上方，眼窝、鼻下投出深影（熊猫眼）；含义是审问、压迫，"无处藏身"。
- **AI提示词写法**：
  中文：`[固定镜头]审讯室顶灯直打下来，光源在老周正上方。他的眼窝和鼻子下方沉在深影里，只有额头和颧骨是亮的。终帧定格：他缓缓抬头，眼睛从阴影里露出来，看向镜头。`（可直接复制）
  English: `[locked-off] The interrogation room's ceiling lamp beats straight down, the source directly above Lao Zhou. His eye sockets and the underside of his nose sink into deep shadow; only forehead and cheekbones catch light. Final frame: he slowly lifts his head, eyes emerging from shadow toward the lens.`（可直接复制）
- **免费档注意事项**：能用。顶光熊猫眼是新手自查项，故意用时必须写"光源在正上方、眼窝深影"。
- **反例**：`顶光，老周很有压迫感`（不要这么写）——"压迫感"是情绪词；没写光源位置、阴影落在眼窝和鼻下。

## 45. 逆光剪影（backlit silhouette）
- **传统定义**：强光源在人物正后方、朝向镜头，人物全黑，边缘镶金边，眩光入画；与剪影光的区别是光源直对镜头。
- **AI提示词写法**：
  中文：`[固定镜头]清晨江边，太阳刚出水面，正对镜头。老周站在江堤上，整个人黑成剪影，身体边缘镶着一圈金边，镜头里有轻微眩光。终帧定格：他张开双臂，江风灌满他的外套，又放下手臂转身。`（可直接复制）
  English: `[locked-off] At dawn by the river, the sun just clears the water, facing the lens. Lao Zhou stands on the embankment, black as a silhouette, his outline rimmed in gold, a faint flare in the lens. Final frame: he spreads his arms, river wind filling his coat, then lowers them and turns.`（可直接复制）
- **免费档注意事项**：完全能用。逆光剪影藏脸加藏细节，是免费档人物镜头的万能安全牌。
- **反例**：`逆光，老周迎着朝阳很励志`（不要这么写）——"励志"是评价词；没写太阳正对镜头、人物全黑、金边、眩光。
