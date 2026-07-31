# Codex Skills 完整使用指南

> 本文档详细说明了 4 个 AI 编程技能的安装、配置和使用方法。
> 
> **下载位置**: D:\网页\.codex\skills\

---

## 📦 已下载的 Skills

| # | Skill 名称 | 目录 | 主要功能 |
|---|-----------|------|---------|
| 1 | **UI UX Pro Max** | .codex\skills\ui-ux-pro-max | 设计系统生成 |
| 2 | **Impeccable** | .codex\skills\impeccable | 设计规范审计 |
| 3 | **React Bits** | .codex\skills\react-bits | 动效组件库 |
| 4 | **Karpathy Skills** | .codex\skills\andrej-karpathy-skills | 编码规范 |

---

## 1️⃣ UI UX Pro Max - 设计系统生成

### 📁 本地路径
D:\网页\.codex\skills\ui-ux-pro-max

### 🎯 功能说明
- 161 个行业推理规则
- 84 种 UI 风格
- 192 种调色板
- 支持 React、Next.js、Vue、Laravel 等 22 种技术栈

### 📋 环境要求
- **Node.js**: 18+
- **Python**: 3.8+ (必需，用于设计系统搜索)
- **npm**: 7+

### 🔧 安装步骤

#### 步骤 1: 安装 CLI
`powershell
npm install -g ui-ux-pro-max-cli
`

#### 步骤 2: 验证 Python
`powershell
python --version
`
如果未安装，请从 https://python.org 下载

#### 步骤 3: 在 Codex 中配置
在 Codex 项目中运行：
`
/uipro init --ai codex
`

### 💡 使用示例

#### 生成设计系统
`
/uipro generate "SaaS landing page for a fitness app"
`

#### 查询设计模式
`
/uipro search "e-commerce" --domain style
`

#### 获取调色板
`
/uipro palette "modern" --count 5
`

### 📚 更多命令
- /uipro list - 查看所有可用风格
- /uipro templates - 查看模板列表
- /uipro help - 查看帮助

---

## 2️⃣ Impeccable - 设计规范审计

### 📁 本地路径
D:\网页\.codex\skills\impeccable

### 🎯 功能说明
- 23 个设计命令
- 60 个确定性检测规则
- AI 前端设计审计和改进
- 实时浏览器迭代

### 📋 环境要求
- **Node.js**: 18+
- **npm**: 7+
- **不需要 Python**

### 🔧 安装步骤

#### 步骤 1: 安装依赖
`powershell
cd .codex\skills\impeccable
npm install
`

#### 步骤 2: 全局安装 CLI (可选)
`powershell
npm install -g impeccable
`

#### 步骤 3: 配置 Codex 钩子
在 Codex 中运行：
`
/impeccable init
`

**重要**: 安装后需要在 Codex 中批准项目钩子（打开 /hooks）

### 💡 使用示例

#### 初始化项目
`
/impeccable init
`
会询问：
- 产品类型（brand/product）
- 品牌色调
- 设计风格

#### 设计审计
`
/impeccable audit src/components
`

#### 设计优化
`
/impeccable polish src/pages
`

#### 添加动效
`
/impeccable animate src/
`

#### 设计审查
`
/impeccable critique landing-page
`

### 📚 23 个命令速查表

| 命令 | 功能 |
|------|------|
| /impeccable craft | 完整的设计构建流程 |
| /impeccable audit | 技术质量检查 |
| /impeccable critique | UX 设计审查 |
| /impeccable polish | 最终优化 |
| /impeccable shape | UX/UI规划 |
| /impeccable bolder | 增强设计大胆度 |
| /impeccable quieter | 降低设计大胆度 |
| /impeccable animate | 添加动效 |
| /impeccable colorize | 添加色彩 |
| /impeccable typeset | 排版优化 |
| /impeccable layout | 布局优化 |
| /impeccable harden | 错误处理 |
| /impeccable clarify | 文案优化 |

### ⚠️ 注意事项
- 首次使用必须运行 /impeccable init
- 钩子必须在 Codex 中批准才能自动运行
- 支持 --json 输出格式用于 CI/CD

---

## 3️⃣ React Bits - 动效组件库

### 📁 本地路径
D:\网页\.codex\skills\react-bits

### 🎯 功能说明
- 140+ 动画 React 组件
- 文本动画、UI 元素、背景效果
- 完全可定制
- 支持 shadcn/ui

### 📋 环境要求
- **Node.js**: 18+
- **React**: 18+
- **Tailwind CSS**: 推荐（可选）
- **TypeScript**: 可选

### 🔧 安装步骤

#### 方式 A: 使用 shadcn CLI（推荐）
`powershell
# 在你的 React 项目目录中
npx shadcn@latest add @react-bits/BlurText-TS-TW
`

#### 方式 B: 手动复制代码
1. 打开 D:\网页\.codex\skills\react-bits
2. 查看 src/components 目录
3. 复制需要的组件到你的项目

#### 方式 C: 使用 Codex 辅助
`
在 Codex 中：
"帮我从 react-bits 添加 BlurText 组件"
`

### 💡 使用示例

#### 安装文本动画组件
`powershell
npx shadcn@latest add @react-bits/BlurText-TS-TW
`

#### 在 React 中使用
`	sx
import { BlurText } from '@/components/ui/blur-text'

function Hero() {
  return (
    <BlurText 
      text="Welcome to our platform" 
      delay={0.1} 
    />
  )
}
`

### 📚 组件分类

#### 文本动画
- BlurText - 模糊渐入
- SplitText - 分割动画
- Typewriter - 打字机效果

#### 背景效果
- AnimatedGradient - 渐变动画
- FloatingShapes - 浮动形状
- GridPattern - 网格图案

#### UI 组件
- Accordion - 手风琴
- Card - 卡片动效
- Button - 按钮动效

### ⚠️ 注意事项
- 这是前端组件库，不是 Codex skill
- 需要在 React 项目中手动安装
- 推荐配合 Tailwind CSS 使用

---

## 4️⃣ Karpathy Skills - 编码规范

### 📁 本地路径
D:\网页\.codex\skills\andrej-karpathy-skills

### 🎯 功能说明
基于 Andrej Karpathy 的 4 大原则：
1. **Think Before Coding** - 编码前先思考
2. **Simplicity First** - 优先简单
3. **Surgical Changes** - 精准修改
4. **Goal-Driven Execution** - 目标驱动

### 📋 环境要求
- **不需要任何运行时**
- 纯文本配置文件

### 🔧 安装步骤

#### 方式 A: 作为 Codex skill（推荐）
在 Codex 中运行：
`
npx skills add .codex\skills\andrej-karpathy-skills
`

#### 方式 B: 复制到项目根目录
`powershell
Copy-Item ".codex\skills\andrej-karpathy-skills\CLAUDE.md" . -Force
`

#### 方式 C: 合并到现有 CLAUDE.md
`powershell
Get-Content ".codex\skills\andrej-karpathy-skills\CLAUDE.md" | Add-Content -Path "CLAUDE.md"
`

### 💡 使用方法

这个 skill 会在你每次与 Codex 交互时自动生效，无需手动调用。

#### 它会帮你：
- ✅ 在编码前提出澄清问题
- ✅ 避免过度设计
- ✅ 只修改必要的代码
- ✅ 设定可验证的成功标准

#### 示例对话

**你**: "添加用户登录功能"

**Codex (使用 Karpathy 原则)**:
`
在开始之前，我需要确认几个问题：

1. 使用什么认证方式？(JWT, OAuth, Session?)
2. 需要支持哪些登录方式？(邮箱、手机号、第三方?)
3. 有现成的用户表结构吗？

我的建议：
- 先用最简单的 JWT + 邮箱登录
- 如果需求不明确，可以先实现 MVP 版本

请确认以上问题，或者让我按 MVP 方案开始实现？
`

### 📚 四大原则详解

#### 1. Think Before Coding
- 明确假设
- 提出澄清问题
- 展示多种方案
- 在不确定时停止

#### 2. Simplicity First
- 只实现请求的功能
- 不创建不必要的抽象
- 避免"未来可能用到"的代码
- 如果 200 行能简化到 50 行，就重写

#### 3. Surgical Changes
- 只修改必要的代码
- 不"优化"相邻代码
- 保持现有代码风格
- 不删除未请求的"死代码"

#### 4. Goal-Driven Execution
- 定义明确的成功标准
- 编写测试驱动
- 多轮验证直到通过
- 将指令转化为可验证的目标

---

## 🚀 完整工作流程示例

### 场景：创建一个现代化的 SaaS 落地页

#### 步骤 1: 使用 UI UX Pro Max 生成设计系统
`
/uipro generate "Modern SaaS landing page for AI productivity tool"
`

#### 步骤 2: 初始化 Impeccable 设计规范
`
/impeccable init
# 选择：product > tech/SaaS > blue/purple tones
`

#### 步骤 3: 让 Codex 生成页面结构
`
"使用 React + Tailwind 创建落地页结构，
包括 Hero、Features、Testimonials、CTA 板块"
`

#### 步骤 4: 使用 React Bits 添加动效
`
"为 Hero 板块添加 BlurText 动画，
为 Features 添加浮动卡片效果"
`

#### 步骤 5: 使用 Impeccable 审计和优化
`
/impeccable audit src/pages/landing
/impeccable polish src/pages/landing
`

#### 步骤 6: Karpathy 原则全程指导
- 在每一步 Codex 都会主动提问确认
- 避免过度设计
- 保持代码简洁
- 验证每个步骤

---

## 🔍 常见问题 FAQ

### Q1: Python 必须安装吗？
**A**: 只有 UI UX Pro Max 需要 Python。其他 3 个不需要。

### Q2: 需要 API Key 吗？
**A**: 不需要！所有 4 个 skill 都是完全免费的。

### Q3: 可以离线使用吗？
**A**: 
- UI UX Pro Max: 部分功能需要网络
- Impeccable: 可以离线
- React Bits: 完全离线
- Karpathy: 完全离线

### Q4: 如何在 Codex 中启用这些 skill？
**A**: 
`
# 在 Codex 中
npx skills add .codex\skills\ui-ux-pro-max
npx skills add .codex\skills\impeccable
npx skills add .codex\skills\andrej-karpathy-skills
`

### Q5: React Bits 是 Codex skill 吗？
**A**: 不是，它是前端组件库，需要在 React 项目中手动安装组件。

### Q6: 如何更新 skill？
**A**: 
`powershell
# 重新下载最新版本
Remove-Item ".codex\skills\skill-name" -Recurse
# 然后重新下载
`

---

## 📝 快速命令速查

### 环境检查
`powershell
node --version
npm --version
python --version
`

### Skill 安装
`powershell
npm install -g ui-ux-pro-max-cli
npm install -g impeccable
`

### Codex 命令
`
/uipro generate "你的需求"
/impeccable init
/impeccable audit src/
/impeccable polish src/
`

### React Bits 安装
`powershell
npx shadcn@latest add @react-bits/BlurText-TS-TW
`

---

## 🎯 推荐组合

| 项目类型 | 推荐组合 |
|---------|---------|
| **SaaS 落地页** | UI UX Pro Max + Impeccable + React Bits |
| **管理后台** | Impeccable + Karpathy |
| **个人博客** | Karpathy + React Bits |
| **企业官网** | UI UX Pro Max + Impeccable + React Bits |
| **快速原型** | Karpathy + UI UX Pro Max |

---

## 📚 更多资源

- **UI UX Pro Max**: https://uupm.cc
- **Impeccable**: https://impeccable.style
- **React Bits**: https://reactbits.dev
- **Karpathy**: https://github.com/multica-ai/andrej-karpathy-skills

---

**文档生成时间**: 2026-07-29  
**Skills 版本**: 最新 main 分支
