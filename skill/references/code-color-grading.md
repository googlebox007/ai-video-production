# 调色 4 种（免费档调色在剪辑时统一做，提示词里只写光质和色温倾向）

## 65. 青橙调（teal and orange）
- **传统定义**：阴影推向青、高光推向橙的互补色调；人脸（橙谱段）自动从背景（青）里弹出来，是 2000 年后好莱坞大片的默认皮肤。
- **调色词**：`teal and orange, 互补色分离，肤色保暖`；**适用题材**：动作 / 冒险 / 现代都市。
- **AI提示词写法**：
  中文：`[固定镜头]黄昏码头，老周站在集装箱之间。提示词只写光质：暖金色夕阳光从侧面打在他脸上，阴影偏青。终帧定格：他点燃一根烟，火光在他脸上跳了一下。// 调色（剪辑时）：阴影推青、高光推橙，肤色守住橙色线。`（可直接复制）
  English: `[locked-off] At the dusk dock, Lao Zhou stands between containers. Prompt carries only light quality: warm golden sunset raking his face from the side, shadows leaning teal. Final frame: he lights a cigarette, the flame flickering on his face. // Grade (in edit): shadows to teal, highlights to orange, skin tones held on the orange line.`（可直接复制）
- **免费档注意事项**：免费档调色一律剪辑时统一做（Resolve 免费版加统一 LUT），提示词里只写"暖金侧光、阴影偏青"的光质和色温倾向；全片调色词典写进 Global Style Prefix 逐字复用。
- **反例**：`teal-orange调色，阿棠很电影感`（不要这么写）——把调色词当风格咒语塞进生成提示词，且"电影感"是空词；调色是后期的事，提示词只管光质。

## 66. 冷调悬疑（cold thriller grade）
- **传统定义**：低饱和、冷蓝调、高对比、死黑；含义是不安、未知，"阴影里有东西"。
- **调色词**：`desaturated, cold blue, high contrast, crushed blacks`；**适用题材**：悬疑 / 惊悚 / 犯罪。
- **AI提示词写法**：
  中文：`[固定镜头]深夜地下车库，阿棠独自行走在两排车之间。提示词只写光质：顶灯冷白，车身反光偏蓝，阴影扎实不提亮。终帧定格：她停在一辆黑车前，车窗倒影里多了一个人影。// 调色（剪辑时）：降饱和、冷蓝、高对比、黑色压死。`（可直接复制）
  English: `[locked-off] In the underground garage at night, A-Tang walks alone between rows of cars. Prompt carries only light quality: cold-white overheads, bodywork reflections leaning blue, shadows kept solid and unlifted. Final frame: she stops at a black car; the window reflection holds one extra figure. // Grade (in edit): desaturate, cold blue, high contrast, crush the blacks.`（可直接复制）
- **免费档注意事项**：夜景加压制句"深黑阴影不提亮"防模型美化；冷调悬疑的"死黑"是剪辑时压出来的，不是生成时"调"出来的。
- **反例**：`冷色调，阿棠很害怕`（不要这么写）——"害怕"是情绪词；且把"冷色调"当生成咒语，正确做法是提示词写"顶灯冷白、阴影不提亮"，调色剪辑时做。

## 67. 暖调怀旧（warm nostalgic grade）
- **传统定义**：褪色的黑、暖高光、轻品红偏、光晕；含义是追忆，"一切都回不去了"。
- **AI提示词写法**：
  中文：`[固定镜头]1980年代的院子，年轻版阿棠在晾衣服。提示词只写光质：午后暖阳，柔光，白色衣物边缘有轻微光晕，蝉鸣声。终帧定格：她踮脚去够最高处的一件衬衫，衣摆扬起来。// 调色（剪辑时）：黑不压死、暖黄滤镜感、轻微褪色。`（可直接复制）
  English: `[locked-off] A 1980s courtyard, a young A-Tang hanging laundry. Prompt carries only light quality: warm afternoon sun, soft light, faint halation on the white clothes' edges, cicadas droning. Final frame: she stands on tiptoe for the highest shirt, its hem lifting. // Grade (in edit): lifted blacks, warm-yellow filter feel, slight fade.`（可直接复制）
- **免费档注意事项**：怀旧段落与现实段落用两套调色词典分区，观众没看懂剧情已经"感到"了时间差；调色统一先做"匹配"再做"风格化"，顺序不能反。
- **反例**：`怀旧滤镜，画面很温暖`（不要这么写）——"温暖"是感觉词；且滤镜是剪辑时套的，提示词里应写"午后暖阳、柔光、衣物边缘光晕"的光质。

## 68. 黑白高对比（black-and-white high contrast）
- **传统定义**：去色、高对比、硬调；含义是纪实、审判，"剥掉颜色只剩真相"。
- **调色词**：`black and white, high contrast, hard light, deep shadows`；**适用题材**：纪实 / 历史闪回 / 风格化短片。
- **AI提示词写法**：
  中文：`[固定镜头]审讯室，老周坐在顶灯下。提示词只写光质：硬顶光，眼窝深影，黑白。他的手在桌上，一动不动。终帧定格：他抬起眼，直视镜头。// 调色（剪辑时）：去色、拉高对比、阴影压死，高光保留皮肤质感。`（可直接复制）
  English: `[locked-off] The interrogation room, Lao Zhou under the ceiling lamp. Prompt carries only light quality: hard top light, deep eye sockets, black and white. His hands lie still on the table. Final frame: he lifts his eyes into the lens. // Grade (in edit): desaturate fully, push contrast, crush shadows, keep skin texture in the highlights.`（可直接复制）
- **免费档注意事项**：黑白是最省钱的"风格统一器"：各镜 baked-in 色偏再乱，去色后天然统一；但肤色层次靠光比，提示词必须写硬光。
- **反例**：`黑白滤镜，很有质感`（不要这么写）——"质感"是空词；黑白片的质感来自"硬顶光、眼窝深影"的高反差，提示词不写光，调色救不回来。
