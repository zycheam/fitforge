# 用 Codex + 4 个 Skill 做网页 - 完整调用指南

> 生成时间: 2026-07-30
> 项目路径: D:\网页

---

## ✅ 安装状态确认

| Skill | 安装位置 | 状态 | 版本 |
|-------|---------|------|------|
| UI UX Pro Max | `.agents/skills/ui-ux-pro-max/` + 6个子技能 | ✅ | CLI 2.11.3 |
| Impeccable | `.agents/skills/impeccable/` + `.codex/hooks.json` | ✅ | 3.x |
| React Bits | `.codex/skills/react-bits/` | ✅ | 源码 |
| Karpathy 规范 | `.agents/skills/karpathy-guidelines/` + `CLAUDE.md` | ✅ | main |

| 依赖 | 版本 | 状态 |
|------|------|------|
| Node.js | v24.18.0 | ✅ |
| npm | 11.16.0 | ✅ |
| Python | 3.12.10 | ✅ |
| uipro CLI | 2.11.3 | ✅ |

---

## 一、在 Codex 中如何调用这些 Skill

所有 skill 已安装到 `.agents/skills/` 目录，Codex 会自动识别它们。
你只需在 Codex 对话框中用自然语言描述需求，skill 会自动生效。

### 1. UI UX Pro Max - 设计系统生成

**在 Codex 中这样说：**

```
"用 UI UX Pro Max 的 Soft UI Evolution 风格设计一个 SaaS 落地页"
"帮我生成一个电商网站的配色方案"
"查一下 health wellness 行业推荐的设计模式"
"给我推荐适合金融类 App 的 UI 风格"
```

**自动触发的子技能：**
- `banner-design` - Banner 设计
- `brand` - 品牌识别
- `design` - 综合设计
- `design-system` - 设计系统生成
- `slides` - 幻灯片设计
- `ui-styling` - UI 样式 (shadcn/ui)

**命令行直接调用：**
```powershell
# 搜索设计风格
python .agents\skills\ui-ux-pro-max\scripts\search.py "SaaS modern" --domain style

# 搜索配色方案
python .agents\skills\ui-ux-pro-max\scripts\search.py "healthcare" --domain colors

# 生成完整设计系统
python .agents\skills\ui-ux-pro-max\scripts\design_system.py --industry "fitness" --output json
```

---

### 2. Impeccable - 设计规范审计

**在 Codex 中这样说：**

```
"用 impeccable 审查这个页面的设计"
"/impeccable audit src/App.jsx"
"/impeccable critique 首页"
"/impeccable polish 产品页面"
"检查我的网页有没有设计反模式"
```

**23 个命令速查：**

| 命令 | 用途 | Codex 中的说法 |
|------|------|---------------|
| `craft` | 完整从设计到构建 | "用 impeccable craft 做这个页面" |
| `audit` | 技术质量检查 | "/impeccable audit src/" |
| `critique` | UX 设计审查 | "/impeccable critique Hero" |
| `polish` | 最终打磨 | "/impeccable polish" |
| `bolder` | 增强视觉冲击 | "让这个设计更大胆" |
| `quieter` | 降低视觉冲击 | "让这个设计更低调" |
| `animate` | 添加动效 | "/impeccable animate" |
| `colorize` | 色彩优化 | "/impeccable colorize" |
| `typeset` | 排版优化 | "/impeccable typeset" |
| `layout` | 布局优化 | "/impeccable layout" |
| `harden` | 错误处理/边界情况 | "/impeccable harden" |
| `clarify` | 文案优化 | "/impeccable clarify" |
| `delight` | 添加惊喜细节 | "/impeccable delight" |
| `overdrive` | 极致效果 | "/impeccable overdrive" |

---

### 3. React Bits - 动效组件

**在 Codex 中这样说：**

```
"用 react-bits 的 BlurText 组件做标题动画"
"给 Hero 区域加一个 react-bits 的浮动形状背景"
"把这个按钮改成 react-bits 的磁吸效果"
"在 Features 区域用 react-bits 的渐入动画"
```

**常用组件清单：**

**文本动画：**
- `BlurText` - 模糊渐入标题
- `SplitText` - 文字逐字分割动画
- `CountUp` - 数字滚动
- `Typewriter` - 打字机效果

**背景效果：**
- `AnimatedGradient` - 动态渐变背景
- `FloatingShapes` - 浮动几何形状
- `Particles` - 粒子效果
- `GridMotion` - 动态网格

**交互组件：**
- `MagneticButton` - 磁吸按钮
- `TiltedCard` - 倾斜卡片
- `SpotlightCard` - 聚光卡片
- `ParallaxSection` - 视差滚动

---

### 4. Karpathy 编码规范

**这是自动生效的，不需要手动调用。**

它会在 Codex 工作时自动遵循四大原则：
1. **先思考再编码** - Codex 会主动提问确认需求
2. **简单优先** - 不会过度设计
3. **精准修改** - 只改必要代码
4. **目标驱动** - 设置验证标准

**你只需正常对话，Karpathy 规范会自动优化 Codex 的行为。**

---

## 二、实战：从零建一个网页的完整流程

### 场景：做一个 "AI 写作助手" 的 SaaS 落地页

---

### 第一步：生成设计系统

**在 Codex 中说：**

```
"我需要做一个 AI 写作助手的 SaaS 落地页。用 UI UX Pro Max 帮我：
1. 推荐适合的设计风格和配色
2. 规划页面结构（Hero、Features、Testimonials、Pricing、CTA）
3. 推荐字体搭配"
```

Codex 会返回类似：

```json
{
  "style": "Soft UI Evolution",
  "colors": {
    "primary": "#6366F1",
    "secondary": "#8B5CF6",
    "accent": "#F59E0B",
    "background": "#FAFAFA",
    "text": "#1E1B4B"
  },
  "typography": {
    "heading": "Cal Sans",
    "body": "Inter"
  },
  "sections": ["Hero", "Features", "HowItWorks", "Testimonials", "Pricing", "CTA"]
}
```

---

### 第二步：创建项目结构

**在 Codex 中说：**

```
"用 React + Tailwind CSS + shadcn/ui 创建这个项目。

设计规范：
- 风格: Soft UI Evolution
- 主色: #6366F1
- 板块: Hero > Features(3个) > HowItWorks(3步) > Testimonials(3条) > Pricing(3档) > CTA

先做 Hero 板块和 Features 板块"
```

---

### 第三步：添加动效

**在 Codex 中说：**

```
"现在美化页面：

1. Hero 标题用 react-bits 的 BlurText 做渐入动画
2. 背景用 react-bits 的 AnimatedGradient 做动态渐变
3. Features 卡片用 react-bits 的 TiltedCard 做倾斜悬停效果
4. Pricing 用 react-bits 的 SpotlightCard 做聚光效果

全部使用 TypeScript + Tailwind CSS 变体"
```

---

### 第四步：设计审计和打磨

**在 Codex 中说：**

```
"用 impeccable 审查整个页面：

/impeccable audit src/components/Hero
/impeccable critique 整体布局和信息层级
/impeccable typeset 检查字体大小和行距

根据审查结果修复所有问题，然后：
/impeccable polish 最终打磨"
```

---

### 第五步：响应式和边界情况

**在 Codex 中说：**

```
"/impeccable harden 检查所有组件：
- 文本溢出处理
- 移动端适配
- 加载状态
- 空状态
- 错误边界"
```

---

## 三、日常开发中的常用组合

### 场景 1：快速做一个 Landing Page

```
"用 UI UX Pro Max 推荐 design 风格和配色，
然后用 react-bits 的组件做一个完整的 landing page，
最后用 impeccable 审查一遍"
```

### 场景 2：优化现有页面

```
"/impeccable audit src/pages
按审计结果逐个修复，
用 react-bits 替换生硬的动效"
```

### 场景 3：品牌视觉升级

```
"用 UI UX Pro Max 的 brand 技能做品牌审计，
推荐新的配色和字体方案，
应用到整个项目"
```

### 场景 4：做演示文稿

```
"用 UI UX Pro Max 的 slides 技能，
把项目特点做成 10 页演示文稿"
```

---

## 四、Skill 之间的协作关系

```
┌─────────────────────────────────────────────────┐
│                  你的需求                          │
└──────────┬──────────────────────────────────────┘
           │
     ┌─────▼─────┐
     │ Karpathy  │ ← 全程自动生效，规范 Codex 行为
     │  规范      │   先思考、简单、精准、目标驱动
     └─────┬─────┘
           │
     ┌─────▼─────┐
     │ UI UX Pro │ ← 第一步：生成设计系统
     │   Max     │   风格、配色、字体、板块结构
     └─────┬─────┘
           │
     ┌─────▼─────┐
     │ Codex 生成 │ ← 第二步：写代码
     │  HTML/CSS  │   根据设计系统生成页面
     └─────┬─────┘
           │
     ┌─────▼─────┐
     │ React Bits│ ← 第三步：添加动效
     │           │   文本动画、背景、交互效果
     └─────┬─────┘
           │
     ┌─────▼─────┐
     │Impeccable │ ← 第四步：审查打磨
     │           │   审计→修复→抛光→上线
     └───────────┘
```

---

## 五、关键要点

- **不需要 API Key**，全部免费
- **Karpathy 规范**自动生效，无需手动调用
- **UI UX Pro Max** 在设计阶段用，决定"做什么样的"
- **React Bits** 在实现阶段用，给页面"加动效"
- **Impeccable** 在审查阶段用，确保"做得好"
- 所有 skill 都可以直接用自然语言调用，不需要记住命令

---

## 六、常见问题

**Q: 怎么知道 skill 是否在生效？**
A: 当 Codex 开始按照 Karpathy 原则提问澄清、或按照设计系统生成代码、或在写完代码后自动做设计检查时，就证明 skill 在工作。

**Q: 可以只用一个 skill 吗？**
A: 可以。每个 skill 独立工作，按需使用。

**Q: React Bits 需要先 npm install 吗？**
A: 需要。在 React 项目中先装 shadcn，然后用 `npx shadcn@latest add` 添加组件。

**Q: 创建的不是 React 项目，能用吗？**
A: UI UX Pro Max、Impeccable、Karpathy 不限框架。React Bits 仅限 React。

**Q: 离线能用吗？**
A: UI UX Pro Max 的设计系统数据已本地化，可以离线查询。React Bits 和 Karpathy 完全离线。Impeccable 大部分功能离线。

