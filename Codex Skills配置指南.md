# Codex Skills 配置指南

本文档整理了4个优秀Codex skills的GitHub仓库信息、安装方法和配置要求。

---

## 目录
1. [nextlevelbuilder/ui-ux-pro-max-skill](#1-nextlevelbuilderui-ux-pro-max-skill)
2. [pbakaus/impeccable](#2-pbakausimpeccable)
3. [DavidHDev/react-bits](#3-davidhdevreact-bits)
4. [multica-ai/andrej-karpathy-skills](#4-multica-aiandrej-karpathy-skills)

---

## 1. nextlevelbuilder/ui-ux-pro-max-skill

### 概述
UI UX Pro Max 是一个 AI skill,为构建多平台专业UI/UX设计提供智能支持。它包含161个行业特定的推理规则、84种UI风格、192个调色板和74种字体搭配。

**功能亮点:**
- 161个行业特定推理规则
- 84种UI风格(如玻璃拟态、新拟态、极简主义、布卢特利主义等)
- 192个产品类型调色板
- 74种字体搭配(Google Fonts导入)
- 25种图表类型推荐
- 22个技术栈支持(React、Next.js、Vue、Laravel、Three.js等)
- 设计系统生成器

**支持的框架/平台:**
- Web: HTML + Tailwind (默认)
- React: React, Next.js, shadcn/ui
- Vue: Vue, Nuxt.js, Nuxt UI
- Angular: Angular
- PHP: Laravel
- Desktop: JavaFX, WPF, WinUI 3等
- iOS: SwiftUI
- Android: Jetpack Compose
- Cross-platform: React Native, Flutter

### GitHub信息
- **仓库地址:** https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
- **描述:** An AI SKILL that provide design intelligence for building professional UI/UX multiple platforms
- **Python依赖:** Python 3.x (仅使用标准库,不进行网络调用)
- **许可证:** MIT License

### 安装方法

#### 方法1: Claude Marketplace 安装 (推荐)
```bash
/plugin marketplace add nextlevelbuilder/ui-ux-pro-max-skill
/plugin install ui-ux-pro-max@ui-ux-pro-max-skill
```

#### 方法2: CLI 安装 (推荐)
```bash
# 全局安装CLI
npm install -g ui-ux-pro-max-cli

# 定位到项目目录
cd /path/to/your/project

# 为不同的AI助手安装
uipro init --ai claude      # Claude Code
uipro init --ai cursor      # Cursor
uipro init --ai windsurf    # Windsurf
uipro init --ai antigravity # Antigravity
uipro init --ai codex       # Codex CLI
uipro init --ai copilot     # GitHub Copilot
# ... 更多支持的平台

# 全局安装(适用于所有项目)
uipro init --ai claude --global
uipro init --ai cursor --global
```

#### 方法3: 手动复制
```bash
cd your-project/
cp -r dist/agents/.agents your-project/
mkdir -p your-project/.codex
cp dist/codex/.codex/hooks.json your-project/.codex/hooks.json
```

### 其他可用命令
```bash
uipro versions              # 列出可用版本
uipro update                # 从已安装的CLI包刷新技能文件
uipro init --offline        # 兼容性标志;安装捆绑的模板
uipro uninstall             # 移除技能(自动检测平台)
uipro uninstall --ai claude # 移除特定平台
uipro uninstall --global    # 从全局安装中移除
```

### 环境要求
- Node.js (用于CLI安装)
- npm 或 yarn 包管理器
- Python 3.x (仅用于搜索脚本,使用标准库,不进行网络请求)

### Design System 命令 (高级)
```bash
# 生成设计系统(ASCII输出)
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "beauty spa wellness" --design-system -p "Serenity Spa"

# 生成Markdown输出
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "fintech banking" --design-system -f markdown

# 域特定搜索
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "glassmorphism" --domain style
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "elegant serif" --domain typography
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "dashboard" --domain chart

# 技术栈特定指导
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "form validation" --stack react
python3 .claude/skills/ui-ux-pro-max/scripts/search.py "responsive layout" --stack html-tailwind
```

### 使用示例
```
Build a landing page for my SaaS product
Create a dashboard for healthcare analytics
Design a portfolio website with dark mode
Make a mobile app UI for e-commerce
Build a fintech banking app with dark theme
```

---

## 2. pbakaus/impeccable

### 概述
Impeccable 为AI编码代理提供设计指导。它包含一个技能、23个命令、实时浏览器迭代,以及60个确定性检测规则,用于检测AI生成的前端设计。

**功能亮点:**
- 23个设计命令(`/impeccable`)
- 60个确定性检测规则
- 支持CI/CD集成
- 可选设计钩子(对文件编辑进行实时检测)
- 反模式检测(AI生成的通用设计模式)

**检测规则包括:**
- 边框、渐变色、弹性动画等AI常见模式
- 字体重复、颜色对比度、间距问题
- 性能问题、无障碍性检查
- 响应式设计问题

### GitHub信息
- **仓库地址:** https://github.com/pbakaus/impeccable
- **描述:** The design language that makes your AI harness better at design.
- **许可证:** Apache 2.0
- **官网:** https://impeccable.style

### 安装方法

#### 方法1: CLI 安装 (推荐)
```bash
# 从项目根目录运行
npx impeccable install

# 升级安装
npx impeccable update

# 仅安装特定平台(跳过交互式提示)
npx impeccable install --providers=claude,codex,cursor,grok --scope=project
```

#### 方法2: Git 子模块 (适合团队)
```bash
# 添加为子模块
git submodule add https://github.com/pbakaus/impeccable .impeccable

# 链接技能到你的框架目录
npx impeccable link --source=.impeccable --providers=claude,cursor

# 提交更改
git add .gitmodules .impeccable .claude .cursor
git commit -m "Add Impeccable skills"

# 更新子模块
git submodule update --remote .impeccable
npx impeccable link --source=.impeccable --providers=claude,cursor
```

#### 方法3: 插件安装

**Claude Code:**
```bash
/plugin marketplace add pbakaus/impeccable
```

**Grok Build:**
```bash
grok plugin install pbakaus/impeccable#plugin --trust
```

**其他平台:** 访问 https://impeccable.style 下载ZIP安装

**具体平台的复制命令:**

- **Cursor:** `cp -r dist/cursor/.cursor your-project/`
- **Claude Code (项目):** `cp -r dist/claude-code/.claude your-project/`
- **Claude Code (全局):** `cp -r dist/claude-code/.claude/* ~/.claude/`
- **OpenCode:** `cp -r dist/opencode/.opencode your-project/`
- **Gemini CLI:** `cp -r dist/gemini/.gemini your-project/`
- **Codex (项目):**
  ```bash
  cp -r dist/agents/.agents your-project/
  mkdir -p your-project/.codex
  cp dist/codex/.codex/hooks.json your-project/.codex/hooks.json
  ```
- **GitHub Copilot:** `cp -r dist/github/.github your-project/`
- **Trae (中国版):** `cp -r dist/trae/.trae-cn/skills/* ~/.trae-cn/skills/`
- **Trae (国际版):** `cp -r dist/trae/.trae/skills/* ~/.trae/skills/`
- **Rovo Dev:** `cp -r dist/rovo-dev/.rovodev your-project/`
- **Qoder:** `cp -r dist/qoder/.qoder your-project/`

### 23个可用命令

| 命令 | 功能 |
|------|------|
| `/impeccable craft` | 完整的形状-构建流程,带视觉迭代 |
| `/impeccable init` | 初始化:收集设计上下文,写PRODUCT.md和DESIGN.md |
| `/impeccable document` | 从现有项目代码生成根DESIGN.md |
| `/impeccable extract` | 将可重用组件和令牌提取到设计系统 |
| `/impeccable shape` | 在编写代码前规划UX/UI |
| `/impeccable critique` | UX设计评审 |
| `/impeccable audit` | 技术质量检查(无障碍性、性能、响应式) |
| `/impeccable polish` | 最终遍历,设计系统对齐,准备发布 |
| `/impeccable bolder` | 让 boring 的设计更 bold |
| `/impeccable quieter` | 让过于 bold 的设计更 quiet |
| `/impeccable distill` | 提取本质 |
| `/impeccable harden` | 错误处理、i18n、文本溢出、边缘情况 |
| `/impeccable onboard` | 首次运行的流程、空状态、激活路径 |
| `/impeccable animate` | 添加有意为之的动画 |
| `/impeccable colorize` | 引入战略性的颜色 |
| `/impeccable typeset` | 修复字体选择、层次、大小 |
| `/impeccable layout` | 修复布局、间距、视觉节奏 |
| `/impeccable delight` | 添加快乐的时刻 |
| `/impeccable overdrive` | 添加技术性的特效 |
| `/impeccable clarify` | 改进不清楚的UX文案 |
| `/impeccable adapt` | 为不同设备适配 |
| `/impeccable optimize` | 性能改进 |
| `/impeccable live` | 视觉变体模式:在浏览器中迭代元素 |

### CLI 检测工具
```bash
# 扫描目录
npx impeccable detect src/

# 扫描HTML文件
npx impeccable detect index.html

# 扫描URL
npx impeccable detect https://example.com

# CI友好的JSON输出
npx impeccable detect --json .

# 忽略项目配置的原始扫描
npx impeccable detect --no-config src/

# 列出检测忽略规则
npx impeccable ignores list

# 添加文件到忽略列表
npx impeccable ignores add-file "src/legacy/**"

# 添加值到忽略列表
npx impeccable ignores add-value overused-font Inter --reason "Brand font"
```

### 使用示例
```bash
/impeccable audit blog           # 审计博客主页+文章页面
/impeccable critique landing     # UX设计评审
/impeccable polish settings      # 发布前的最终清理
/impeccable harden checkout      # 添加错误处理+边缘情况
/impeccable live                 # 在浏览器中实时编辑元素
/impeccable pin audit            # 创建快捷命令 /audit
```

### 设计钩子配置

Codex用户需要在一个可选步骤:
1. 安装后或更新后,打开 `/hooks`
2. 批准项目钩子

钩子安装位置:
- `.codex/hooks.json`

### 忽略重要文件

创建或更新项目的`.gitignore`:
```gitignore
# impeccable-ignore-start
# 临时输出、运行时状态和个人覆盖。
# 未锚定: .impeccable 可能位于仓库根目录或嵌套工作区;
# 模式故意未锚定。

.impeccable/config.local.json
.impeccable/hook.cache.json
.impeccable/hook.pending.json
.impeccable/*.png
.impeccable/live/server.json
.impeccable/live/sessions/
.impeccable/live/previews/
.impeccable/live/annotations/
.impeccable/live/cache/
.impeccable/live/manual-edit-apply-transaction.json
.impeccable/live/manual-edit-events.jsonl
.impeccable/live/manual-edit-evidence/
.impeccable/live/pending-manual-edits.json
.impeccable/live/deferred-svelte-component-accepts.json
.impeccable/live/*.png
# impeccable-ignore-end
```

**需要保留的文件:**
- `.impeccable/config.json` (统一的共享配置)
- `.impeccable/live/config.json` (实时模式框架连线)
- `.impeccable/design.json` (共享设计规范)
- `.impeccable/critique/*.md` (评审报告)

### 反模式 - 避免事项
- 不要使用过于常见的字体 (Arial, Inter, 系统默认)
- 不要在彩色背景上使用灰色文本
- 不要使用纯黑/灰色 (始终有色调)
- 不要将所有内容包裹在卡片中或嵌套卡片
- 不要使用弹跳/弹性缓动 (感觉很过时)

### 支持的工具
- Cursor
- Claude Code
- GitHub Copilot
- Gemini CLI
- Codex CLI
- Grok Build
- OpenCode
- Pi
- Kiro
- Trae
- Rovo Dev
- Qoder
- Mistral Vibe

---

## 3. DavidHDev/react-bits

### 概述
React Bits 是最大的创意动画 React 组件库。它提供140+免费、可自定义的动画,适用于文本、背景和UI元素。

**功能亮点:**
- 140+ 个组件 (文本动画、UI元素、背景)
- 最小依赖 (轻量且可摇树消除)
- 完全可自定义 (通过props或直接编辑源代码)
- 4个变体/组件 (JS-CSS, JS-TW, TS-CSS, TS-TW)
- 复制粘贴就绪 (适配任何现代React项目)
- 支持shadcn CLI安装

** creative 工具:**
- Background Studio - 探索动画背景,自定义效果,导出为视频/图像/代码
- Shape Magic - 创建形状之间的圆角,导出为SVG,React代码或clip-path代码
- Texture Lab - 将20+效果(噪声、抖动、ASCII)应用于图像/视频,并高质量导出

### GitHub信息
- **仓库地址:** https://github.com/DavidHDev/react-bits
- **描述:** An open source collection of animated, interactive & fully customizable React components
- **许可证:** MIT + Commons Clause (个人和商业使用免费)

### 技术栈要求
- React 16.13+
- TypeScript (可选,推荐)
- Tailwind CSS (可选,推荐)

### 安装方法

#### 方法1: shadcn CLI (推荐)
```bash
# 通过shadcn添加一个组件
npx shadcn@latest add @react-bits/BlurText-TS-TW
```

#### 方法2: 手动复制
```bash
# 克隆仓库
git clone https://github.com/DavidHDev/react-bits.git
cd react-bits

# 安装依赖
npm install

# 入口文件中导入常用组件
import { BlurText } from './src/blur-text';
import { FloatingActionBtn } from './src/floating-action-btn';

// 其他天文选项...
```

### 使用示例
每个组件页面都包含复制就绪的CLI命令。访问 https://reactbits.dev/get-started/installation 查看完整文档。

### 官方移植
- Vue.js: [vue-bits.dev](https://vue-bits.dev/)
- Svelte: [sveltebits.xyz](https://sveltebits.xyz/)

### 组件分类
更多组件示例:
- 文本动画: BlurText, Cannon, Glitch, GradientText, Katakana, Rainbow, Scramble, ShimmerText, WriteIn 等
- UI 元素: FloatingActionBtn, MovingBorderBtn, Sidebar, StickyNote 等
- 背景: BlobBurst, BlobLandscape, Confetti, FloatingOrb, Galaxy 等

### 贡献
- 检查 [open issues](https://github.com/DavidHDev/react-bits/issues)
- 通过 [feature request template](https://github.com/DavidHDev/react-bits/issues/new?template=2-feature-request.yml) 提交请求
- 阅读 [contribution guide](https://github.com/DavidHDev/react-bits/blob/main/CONTRIBUTING.md)

---

## 4. multica-ai/andrej-karpathy-skills

### 概述
Karpathy Inspired Claude Code Guidelines 是一个单一的`CLAUDE.md`文件,用于改善Claude Code行为。它源于Andrej Karpathy对LLM编码陷阱的观察。

**四个核心原则:**

1. **Think Before Coding (编码前思考)**
   - 明确陈述假设
   - 在存在歧义时不默默选择解释
   - 在必要时反驳
   - 不清楚时停止并请求澄清

2. **Simplicity First (简单优先)**
   - 没有超出所请求的功能
   - 没有单一使用的代码抽象
   - 没有未请求的"灵活性"或"可配置性"
   - 不实现不可能场景的错误处理
   - 如果200行可以写成50行,重写它

3. **Surgical Changes (外科手术式更改)**
   - 只触碰你必要的更改
   - 只清理你自己造成的混乱
   - 匹配现有样式,即使你会做不同
   - 如果注意到不相关的死代码,提及它 - 不要删除它

4. **Goal-Driven Execution (目标驱动执行)**
   - 转换命令式任务为可验证的目标
   - 使用测试优先的方法
   - 为多步骤任务陈述简短计划

### GitHub信息
- **仓库地址:** https://github.com/multica-ai/andrej-karpathy-skills
- **描述:** A single CLAUDE.md file to improve Claude Code behavior, derived from Andrej Karpathy's observations on LLM coding pitfalls.
- **许可证:** MIT License
- **作者:** Forrest Chang

### 安装方法

#### 方法1: Claude Code 插件 (推荐)
```
/plugin marketplace add forrestchang/andrej-karpathy-skills
/plugin install andrej-karpathy-skills@karpathy-skills
```

#### 方法2: CLAUDE.md (项目级)

**新项目:**
```bash
curl -o CLAUDE.md https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md
```

**现有项目 (追加):**
```bash
echo "" >> CLAUDE.md
curl https://raw.githubusercontent.com/forrestchang/andrej-karpathy-skills/main/CLAUDE.md >> CLAUDE.md
```

### 与 Cursor 集成
此仓库包含提交的Cursor项目规则([`.cursor/rules/karpathy-guidelines.mdc`](.cursor/rules/karpathy-guidelines.mdc)),以便在Cursor中打开项目时应用相同的原则。

查看 **[CURSOR.md](CURSOR.md)** 了解如何设置、在其他项目中使用此规则,以及它与Claude Code的关系。

### 使用示例 vs 原则转换

| 转换前 | 转换后 |
|--------|--------|
| "Add validation" | "Write tests for invalid inputs, then make them pass" |
| "Fix the bug" | "Write a test that reproduces it, then make it pass" |
| "Refactor X" | "Ensure tests pass before and after" |

### 多步骤任务示例
```
1. [Setup database schema] → verify: [Schema tests pass]
2. [Create API endpoints] → verify: [API endpoints respond correctly]
3. [Implement frontend UI] → verify: [User can complete task]
```

### 自定义
这些原则旨在与项目特定说明合并。添加到现有的`CLAUDE.md`或创建新的。

例如,添加项目特定规则:
```markdown
## Project-Specific Guidelines

- Use TypeScript strict mode
- All API endpoints must have tests
- Follow the existing error handling patterns in `src/utils/errors.ts`
```

### 减少过度工程的测试
- 如果你是资深工程师会说这个过于复杂,简化它吗?

### 补充 Claude Code 使用的 Batched `write_to_file` 或 `apply_patch_batch` in parallel
Codex does not have a built-in batch `apply_patch` equivalent to the "Apply patches" in app prompts. However, users can implement a custom system. Meanwhile, Codex-inline `apply_patch` does support batch operations in a single call (akin to "Apply patches" in the app prompt).

### 补充 Codex: Hook vs. Skill difference (on top of the principles)
- Under Claude Code, Impeccable skill does not need a `.claude/settings.local.json` hook; the skill payload is both. It uses a single bookmarked `/impeccable` skill command.

Under Codex, Impeccable skill is a copy of that skill payload to `.agents/skills/impeccable/`. Its hook is written separately (to `.codex/hooks/impeccable.json` per the Impeccable README). The skill command flow is: tip or text-trigger the skill (e.g., `$impeccable`) followed by entering A. For other supported platforms, refer to the Impeccable README or docs.

### Tradeoff Note
这些原则倾向于**谨慎优于速度**。对于简单任务(简单的拼写错误更正、明显的单行代码),使用判断 - 并非每个更改都需要完整的严谨性。

目标是减少非平凡工作上的成本错误,而不是减慢简单任务。

---

## 综合对比

| Feature | UI UX Pro Max | Impeccable | React Bits | Karpathy Skills |
|---------|--------------|-----------|-----------|-----------------|
| 主要功能 | 设计系统生成 | AI设计审计/改进 | React组件库 | 打 CLLAUDE.md原则 |
| 编程语言优先 | 所有框架 | 设计指导 | React组件 | 语言指导(CLAUDE.md) |
| 组件库 | 无 | 无 | 140+动画组件 | 无 |
| 企业级特性 | 是(214行/注意) | 是(前端) | 否 | 是(LLM) |
| CI/CD支持 | 后续支持 无 | 是 | 否 | 是(在合适任务逻辑中) |
| 社区/生态 | 有 | 完善 | 活跃 | 有 |

**适用场景:**
- **UI UX Pro Max**: 需要完整、专业级设计系统生成,多平台支持
- **Impeccable**: 需要AI编码代理的设计审计、无障碍性和前院检测
- **React Bits**: 需要快速集成动画React组件,创意文本/背景效果
- **Karpathy Skills**: 需要减少过度工程、改善LLM编码质量的通用原则

---

## 推荐组合方案

### Web开发为主的项目
```
技术栈: React/Next.js + TypeScript + Tailwind

推荐: Karpathy Skills + Impeccable + React Bits + UI UX Pro Max
```

**使用流程:**
1. 使用Karpathy Skills确保代码质量不高复杂性
2. 使用Impeccable审计设计和前端问题
3. 使用React Bits快速添加动画组件
4. 使用UI UX Pro Max生成设计系统和样式指南

### 企业应用为主的项目
```
技术栈: 企业级框架(React/Angular/Laravel等)

推荐: Karpathy Skills + UI UX Pro Max + Impeccable
```

**使用流程:**
1. 使用Karpathy Skills确保代码质量和原则
2. 使用UI UX Pro Max创建企业级设计系统
3. 使用Impeccable验证无障碍性和性能

### 创意项目为主的项目
```
技术栈: React + 3D/WebGL

推荐: Karpathy Skills + React Bits + UI UX Pro Max
```

**使用流程:**
1. 使用Karpathy Skills保持原则
2. 使用React Bits添加创意动画
3. 使用UI UX Pro Max确保设计一致性

---

## 常见问题

### Q: 这些skills都可以在Codex CLI中使用吗?
A: 是的,所有4个skills都明确支持Codex CLI:
- UI UX Pro Max: `uipro init --ai codex`
- Impeccable: 通过手动复制或命令行安装即可
- React Bits: 作为React组件库直接使用
- Karpathy Skills: 添加到`CLAUDE.md`文件(守此规则)

### Q: 需要哪些模块化费用?
A: UI UX Pro Max需要Python3.10+用于search脚本;其他作用者使用Node.js/npm。

### Q: 性能?
A: UI UX Pro Max的性能取决于规模(支持横向扩展);Impeccable检测(60个确定性规则)使用性能开销最小(后遵循原则);其余为静态库。

### Q: 安全性?
A: 所有技能都作为本地文本资源使用。Impeccable设计钩子基于本地决策(无API密钥在检测/执行中)。

### Q: 可以同时使用多个skills吗?
A: 是的,Codex支持多个skills的作用。建议根据任务负载分配(如3个良好/1-2个最佳组合)。

### Q: 如何保持更新?
A: 定期查看GitHub仓库和发布:
- UI UX Pro Max: `npm install -g ui-ux-pro-max-cli@latest`
- Impeccable: `npx impeccable update`
- React Bits: 使用palette内的`npm update`
- Karpathy Skills: 从官方r同步CLAUDE.md

---

## 资源链接

- **UI UX Pro Max:**
  - GitHub: https://github.com/nextlevelbuilder/ui-ux-pro-max-skill
  - 官网: https://uupm.cc
  - 文档: 根目录中的README文件(包括中英文)

- **Impeccable:**
  - GitHub: https://github.com/pbakaus/impeccable
  - 官网: https://impeccable.style
  - 文档: 官网和README中的命令引用

- **React Bits:**
  - GitHub: https://github.com/DavidHDev/react-bits
  - 文档: https://reactbits.dev/
  - 快速开始: https://reactbits.dev/get-started/installation

- **Karpathy Skills:**
  - GitHub: https://github.com/multica-ai/andrej-karpathy-skills
  - Andrej Karpathy X推文: https://x.com/karpathy/status/2015883857489522876

---

## 附录: Codex-Claude Code需求对照
(来自Claude Code例如脚本的AGENTS.md结构和Agent行为说明)
- Agent决定了为Skills附带顺序/run次数上限;每个Scope可以/细粒度落地
- Codex指令(chunker run)传递给skills以确保Agent正确理解,diff/max_output_tokens/tty等关注
- 如果Agent拒绝垃圾/无关/sustained重用或有明确阻塞条件,应该.abort或.YN
- 渲染栈需与Claude Code一致(含最大tokens和驳回机制)

---

**最后更新:** 2026-07-29
