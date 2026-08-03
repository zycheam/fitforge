# AGENTS.md - 项目Agent行为规范

## 语言要求

- **必须使用中文进行所有回复和交互**，包括解释、说明、错误信息等。
- 项目中的代码（变量名、函数名、类名等）可以使用英文，但**所有注释必须使用中文**。

## 代码注释规范

- 每个文件顶部应有中文注释说明文件用途
- 每个函数/方法应有中文注释说明功能、参数、返回值
- 复杂逻辑段落应有中文注释解释思路
- 注释风格保持简洁清晰，避免冗余

## 工作流程

- 每次新建任务前，先阅读 `复利与踩坑日志.md` 了解历史经验和可复用方法
- 处理问题时优先参考日志中记录的解决方案
- 每次任务完成后，必须及时更新 `复利与踩坑日志.md`：记录新踩的坑、发现的可复用方法、或值得总结的经验

## 通用原则

- 保持代码整洁，遵循项目已有的代码风格
- 优先使用简单直接的解决方案，避免过度设计
- 修改代码前先理解现有逻辑，避免引入不必要的变更
- **每次创建网页都必须运用以下4个Skill**

────────────────────────────────────────────

## 本项目4个核心Skill速查

### 1. UI UX Pro Max — 设计智能搜索引擎

| 项目 | 内容 |
|------|------|
| **位置** | `.agents\skills\ui-ux-pro-max` / `.codex\skills\ui-ux-pro-max` |
| **GitHub** | https://github.com/nextlevelbuilder/ui-ux-pro-max-skill |
| **环境** | Python 3.x（仅标准库，无pip依赖） |
| **API Key** | 不需要 |
| **网络** | 纯本地搜索，不需要外网 |
| **用途** | 配色方案、字体搭配、UI风格推荐、设计系统生成、UX最佳实践 |
| **数据规模** | 67种UI风格 / 161套配色 / 57种字体 / 99条UX指南 / 161条推理规则 |

**调用方式**：
```bash
# 生成设计系统（最常用）
python3 .agents/skills/ui-ux-pro-max/scripts/search.py "fitness gym SaaS" --design-system -p "FitForge"

# 按领域搜索
python3 .agents/skills/ui-ux-pro-max/scripts/search.py "dark mode vibrant" --domain style
python3 .agents/skills/ui-ux-pro-max/scripts/search.py "fitness health" --domain color
python3 .agents/skills/ui-ux-pro-max/scripts/search.py "sport modern" --domain typography
```

**在对话中触发**：描述设计需求，Skill自动激活。例如："帮我设计一个健身SaaS的暗色主题落地页"

---

### 2. Impeccable — 设计审查与打磨

| 项目 | 内容 |
|------|------|
| **位置** | `.agents\skills\impeccable` / `.codex\skills\impeccable` |
| **GitHub** | https://github.com/nextlevelbuilder/impeccable |
| **环境** | Node.js 18+（依赖已安装在 `.codex\skills\impeccable\node_modules`） |
| **API Key** | 不需要 |
| **网络** | 不需要外网 |
| **用途** | 设计审查(critique)、视觉打磨(polish)、可访问性审计、动画增强、色彩优化 |

**核心命令**：
| 命令 | 功能 |
|------|------|
| `critique [target]` | UX设计审查，启发式评分 |
| `polish [target]` | 交付前最终质量打磨 |
| `audit [target]` | 技术质量检查（可访问性/性能/响应式） |
| `bolder [target]` | 强化保守设计，增加视觉冲击力 |
| `animate [target]` | 添加有意义的动画 |
| `colorize [target]` | 为单色调UI添加策略性色彩 |
| `typeset [target]` | 改进排版层级和字体 |
| `layout [target]` | 修复间距、节奏和视觉层级 |
| `adapt [target]` | 适配不同设备和屏幕尺寸 |

**初始化**：
```bash
node .agents/skills/impeccable/scripts/context.mjs --target index.html
```

**在对话中触发**：使用 `/impeccable critique index.html` 或描述"帮我检查这个页面的设计问题"

---

### 3. React Bits — 动画React组件库

| 项目 | 内容 |
|------|------|
| **位置** | `.codex\skills\react-bits` |
| **GitHub** | https://github.com/DavidHDev/react-bits |
| **环境** | Node.js 18+，需要React项目 |
| **API Key** | 不需要 |
| **网络** | 不需要外网 |
| **用途** | 140+动画组件：文字动画、背景动画、UI组件 |
| **⚠️ 注意** | 本项目是纯HTML，React Bits **不适用**。仅在迁移到React框架后才使用 |

---

### 4. Karpathy Guidelines — 编码行为规范

| 项目 | 内容 |
|------|------|
| **位置** | `.agents\skills\karpathy-guidelines` |
| **GitHub** | https://github.com/andrej-karpathy/skills |
| **环境** | 无依赖（纯规则） |
| **API Key** | 不需要 |
| **网络** | 不需要外网 |
| **用途** | 减少LLM编码常见错误：先思考再编码、简单优先、手术式修改、目标驱动 |

**核心原则**：
1. **先思考再编码** — 陈述假设，不确定就问
2. **简单优先** — 最少代码解决问题，不过度设计
3. **手术式修改** — 只改必须改的，不动周围代码
4. **目标驱动** — 定义可验证的成功标准，循环直到通过

**自动生效**：每次编码任务自动适用，无需显式调用。

────────────────────────────────────────────

## 环境速查

| 项目 | 版本 |
|------|------|
| Node.js | v24.18.0 |
| Python | 3.12.10 |
| 项目类型 | 纯HTML/CSS/JS（无框架） |
| 数据库 | free-exercise-db（873条练习，已汉化） |
| 部署 | GitHub Pages: https://zycheam.github.io/fitforge/ |

## 每次创建网页的Skill调用流程

1. **UI UX Pro Max** → 生成设计系统（配色/字体/风格）
2. **Impeccable** → 审查和打磨设计质量
3. **Karpathy Guidelines** → 自动约束代码质量
4. **React Bits** → 跳过（纯HTML项目不适用）

### 典型对话触发方式

```
"用 UI UX Pro Max 帮我选一套健身类配色方案"
"用 Impeccable 对 landing page 做设计审查"
"帮我把这个按钮做得更有质感" → 自动触发Impeccable polish
```
