# 前期 4：Global Style Prefix + @-资产术语表

## 做什么
全片只锁一次的"视觉宪法"，逐字拼进每一条提示词。**改一处，全片生效**——这是"编辑一次，全局传播"纪律。

## 标准

### Global Style Prefix（示例，按项目改）
```
16:9, photorealistic, teal-and-ember color grade, 35mm film grain,
motivated practical lighting, shallow depth of field on close-ups,
locked-off tripod unless specified, 24fps cinematic motion, no text, no logo
```
包含：画幅、光线 doctrine、色彩比、镜头/快门倾向、表演尺度、物理真实度、构图倾向、帧率、全局否定（no text/no logo 等）。

### @-资产术语表
人物/道具/场景各起一个短名，提示词里用 `@名` 引用，不用每次重写描述：
```
@laozhou  → identity string 全文（full-preserve：原样保留）
@satchel  → 黄色帆布挎包，深棕色皮带扣（partial-preserve）
@storm_plain → 荒原，黑色碎石，远处电塔剪影（loose-guide：宽松参考）
```
每条带**保真等级**：
- full-preserve：原样保留（主角脸）
- partial-preserve：保留风格/结构，细节可变
- attribute-transfer：只取属性（质感、配色）
- loose-guide：宽松参考（大场景氛围）

## 检查项
- [ ] Prefix 写好了，50 词以内，读一遍没有自相矛盾
- [ ] 每个出场资产都有 @名 + 保真等级
- [ ] 主角是 full-preserve，且 identity string 已逐字贴进术语表
- [ ] 全片第一条提示词已验证：Prefix + @引用拼进去，模型听得懂
