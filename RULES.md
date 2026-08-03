# FitForge 开发规则 & 踩坑记录

> 规则驱动开发：每完成一个任务后更新本文档，积累复利。上次更新：2026-07-31 19:30`n`n
---

## 1. 项目结构规则

| 规则 | 说明 |
|------|------|
| `index.html` 是唯一入口 | 纯 HTML/CSS/JS 单页应用，无构建步骤 |
| `exercises_data.js` 是数据源 | 格式 `window.EXERCISES = [...]`，由 `exercises_data.json` 生成 |
| `exercises_data.json` 是数据母版 | 编辑 .json → 运行脚本生成 .js |
| 所有中文字段后缀 `_cn` | `name_cn`、`instructions_cn`、`primaryMuscles_cn` |

## 2. 数据修改 SOP

```
1. 编辑 exercises_data.json（UTF-8 编码）
2. 运行生成脚本 → 生成 exercises_data.js
3. 用 PowerShell 字节流上传到 GitHub（避免编码损坏）:
   $bytes = [System.IO.File]::ReadAllBytes("路径")
   $content = [Convert]::ToBase64String($bytes)
```

## 3. 必踩过的坑

### 坑1：PowerShell 编码破坏中文
- **现象**: 用 `gh api` 上传文件后中文变成乱码
- **根因**: PowerShell `Get-Content` 和管道默认使用系统编码
- **解法**: 必须用 `[System.IO.File]::ReadAllBytes` + Base64 上传

### 坑2：Google Fonts CDN 被墙
- **现象**: 国内用户打开页面一直白屏
- **根因**: `fonts.googleapis.com` 在国内被 DNS 污染，`<link rel="stylesheet">` 阻塞渲染
- **解法**: `media="print" onload="this.media='all'"` + `<noscript>` 兜底 + 中文字体回退栈

### 坑3：`\b` 正则在中英文间失效
- **现象**: 替换英文词时，夹在中文字符间的英文匹配不到
- **根因**: `\b` 只在 `\w` 和 `\W` 之间匹配，中文是 `\W`，所以 `\benglish\b` 在 `中文english中文` 中不匹配
- **解法**: 用 `(?<![a-zA-Z])word(?![a-zA-Z])`

### 坑4：词对词翻译质量差
- **现象**: 机翻后语法破碎，`"keeping your back straight"` → `"保持你的背部伸直"`
- **根因**: dict-based 替换无法理解上下文
- **解法**: 先替换关键术语（肌肉名、动作名），剩余保持可读即可；不要追求完美翻译

### 坑5：Git push 在受限网络失败
- **现象**: `git push` HTTPS/SSH 都超时
- **解法**: 用 `gh api` REST 接口直接上传文件，绕过 git 协议

### 坑6：GitHub Pages 刷新后数据加载错误
- **现象**: 页面显示"数据加载失败"
- **根因**: `exercises_data.js` 编码损坏导致 `window.EXERCISES` 未定义或 JSON 解析失败
- **解法**: 确认 .js 文件以 `window.EXERCISES = [` 开头且 JSON 合法

### 坑7：分享链接打不开
- **现象**: 微信扫码或直接打开链接，页面空白
- **根因**: Google Fonts 阻塞 + 无本地字体回退
- **解法**: 参见坑2

## 4. 部署检查清单

- [ ] `exercises_data.js` 以 `window.EXERCISES = [` 开头
- [ ] `exercises_data.js` 中文字符未损坏（抽查前3条）
- [ ] `index.html` 字体加载为非阻塞模式
- [ ] 字体回退栈包含中文字体
- [ ] GitHub Pages 状态为 "built"
- [ ] 直接用浏览器打开 https://zycheam.github.io/fitforge/ 验证
- [ ] 测试分享功能：生成二维码 → 扫码 → 确认打开

## 5. Skill 环境速查

| Skill | 需要环境 | API Key | 适用场景 |
|-------|---------|---------|----------|
| UI UX Pro Max | Node 18+, Python 3.8+ | 无 | UI设计搜索、配色、排版 |
| Impeccable | Node 18+ | 无 | 设计审查、视觉打磨 |
| React Bits | Node 18+ (需React项目) | 无 | React动画组件（本项目不适用） |
| Karpathy Skills | 无 | 无 | 编码规范、减少常见错误（自动生效） |

## 6. Skill 在本项目中如何调用

由于本项目是纯 HTML 项目（无 React/Node 运行时），Skill 的调用方式是：

1. **UI UX Pro Max**: 在 Codex 对话中描述需要的 UI 效果，Skill 会自动搜索设计数据库返回配色/排版/组件建议
2. **Impeccable**: 对现有 HTML 页面进行设计审查，用 `/impeccable critique index.html` 检查视觉问题
3. **Karpathy Guidelines**: 自动激活，编写代码时遵循最佳实践

**不需要在 HTML 中引入任何 Skill 的代码**，这些 Skill 是 AI 助手的内部工具。</think>

<｜DSML｜tool_calls>
<｜DSML｜invoke name="apply_patch_add_file">
<｜DSML｜parameter name="content" string="true"># FitForge 开发规则 & 踩坑记录

> 规则驱动开发：每完成一个任务后更新本文档。上次更新：2026-07-31 19:30`n`n
---

## 1. 项目结构

| 文件 | 角色 | 注意事项 |
|------|------|----------|
| `index.html` | 唯一入口，纯 HTML/CSS/JS | 直接部署到 GitHub Pages |
| `exercises_data.js` | 运行时数据源 | 格式 `window.EXERCISES = [...]` |
| `exercises_data.json` | 数据母版（UTF-8） | 编辑此文件 → 生成 .js |

---

## 2. 已踩过的坑

### 坑1: PowerShell 编码破坏中文
- **现象**: 上传文件后中文变乱码，"数据加载失败"
- **根因**: `Get-Content` 和管道默认使用系统编码
- **解法**: 用 `[System.IO.File]::ReadAllBytes` + Base64 上传

### 坑2: Google Fonts CDN 被墙
- **现象**: 国内用户打开页面白屏/卡死
- **根因**: `fonts.googleapis.com` DNS污染，`<link rel="stylesheet">` 阻塞渲染
- **解法**: `media="print" onload="this.media='all'"` + `<noscript>` 兜底

### 坑3: `\b` 正则在中英文间失效
- **现象**: 夹在中文字符间的英文词替换不掉
- **根因**: `\b` 只在 `\w` 和 `\W` 之间匹配，中文是 `\W`
- **解法**: 用 `(?<![a-zA-Z])word(?![a-zA-Z])`

### 坑4: 词对词翻译效果差
- **现象**: `"keeping your back straight"` → `"保持你的背部伸直"` (勉强可读)
- **解法**: 先替换关键术语（肌肉名、动作名），其他保持可读即可

### 坑5: Git push 在受限网络失败
- **现象**: HTTPS/SSH 都超时
- **解法**: 用 `gh api` REST 接口直接上传文件

---

## 3. 数据修改流程

```
编辑 exercises_data.json → 运行 clean_translations.py → 生成 exercises_data.js
→ [System.IO.File]::ReadAllBytes 上传到 GitHub
```

上传 PowerShell 模板:
```powershell
$bytes = [System.IO.File]::ReadAllBytes("D:\网页\文件名")
$content = [Convert]::ToBase64String($bytes)
$sha = (gh api repos/zycheam/fitforge/contents/文件名 --jq '.sha')
$body = @{message="commit信息"; content=$content; sha=$sha; branch="main"} | ConvertTo-Json -Compress
Invoke-RestMethod -Uri "https://api.github.com/repos/zycheam/fitforge/contents/文件名" -Method Put -Headers @{Authorization="Bearer $(gh auth token)"; Accept="application/vnd.github+json"} -Body $body
```

---

## 4. 部署检查清单

- [ ] `exercises_data.js` 以 `window.EXERCISES = [` 开头
- [ ] 中文字符正确显示（抽查前3条数据）
- [ ] 字体加载为非阻塞模式
- [ ] 字体回退栈包含 `'PingFang SC', 'Microsoft YaHei'`
- [ ] GitHub Pages 状态为 `"built"`：`gh api repos/zycheam/fitforge/pages`
- [ ] 浏览器直接打开 https://zycheam.github.io/fitforge/ 验证

---

## 5. Skill 环境速查

| Skill | 环境要求 | API Key | 本项目适用性 |
|-------|---------|---------|-------------|
| UI UX Pro Max | Node 18+, Python 3.8+ | 无 | 配色/排版/组件搜索 |
| Impeccable | Node 18+ | 无 | 设计审查、视觉打磨 |
| React Bits | Node 18+ (需React) | 无 | 不适用（本项目是纯HTML） |
| Karpathy Guidelines | 无 | 无 | 编码规范，自动生效 |

**调用方式**: 在 Codex 对话中描述需求，Skill 自动提供设计建议。不需要在 HTML 中引入任何 Skill 代码。

## 7. 2026-07-31 新增踩坑

### 坑8: btoa/unescape 分享编码损坏中文
- **现象**: 分享链接中的 #share=... 参数含中文时，微信扫码打不开或乱码
- **根因**: toa(unescape(encodeURIComponent(json))) 使用废弃的 unescape API，部分浏览器/环境不支持
- **解法**: 改为 toa(encodeURIComponent(json).replace(/%([0-9A-F]{2})/g, (_,p)=>String.fromCharCode(parseInt(p,16))))

### 坑9: GitHub Pages 更新有延迟
- **现象**: 上传后 gh api 显示 content 已更新，但 https 页面仍是旧内容
- **根因**: GitHub Pages 需要 rebuild，通常 30-60 秒
- **解法**: 上传后等待 gh api repos/zycheam/fitforge/pages/builds --jq '.[0].status' 变为 uilt

### 经验: 翻译清洗的优先级策略
- 名称和标签 > 指令详情：exercise name 直接影响浏览页，instruction 只在详情弹窗展示
- 词对词替换无效时，改用肌肉名/动作名专用映射表 + 常见词组修复
- 连词 artifact（如 "beginningchapt"）源于原始机翻缺陷，词级别正则无法处理，但影响面小可接受
---

## 7. Impeccable 审计修复记录 (2026-07-31)

### 修复清单（按优先级）

**P0 — 阻断级**
- user-scalable=no + maximum-scale=1.0 → 移除，允许用户缩放页面
- CTA 按钮对比度：白色文字在 #F97316(橙)和 #22C55E(绿)上对比度均 < 3:1 → 改为 ar(--color-bg) (#0F172A)，对比度 ≥ 5.7:1

**P1 — 重要**
- 模态框：添加 ole="dialog"、ria-modal="true"、焦点管理(_prevFocus)、ESC 键关闭
- exercises_data.js 在 <head> 中同步阻塞 → 添加 defer 属性
- 触控目标 ilter-chip/muscle-chip 约 20px → 添加 min-height: 44px、padding: 10px 14px
- 缺少 prefers-reduced-motion → 添加 @media (prefers-reduced-motion: reduce) 规则
- 输入框缺 ria-label → 搜索框/分享框/训练计划输入框均添加

**P2 — 改进**
- SVG 图标缺 ria-hidden → 4 个装饰性 SVG 全部添加
- 禁用分页按钮 opacity:0.25 不可读 → 改为  .35 + color: var(--color-text-muted)
- 动态图片缺 width/height → 添加 width="480" height="360"

**P3 — 优化**
- 内联硬编码颜色 → #EF4444 改为 ar(--color-error)
- 字体回退栈已有中文 fallback，无需修改
- 移动端导航内联适配可用，无需修改

### 落地页修复
- dark-glow: 3 处彩色 box-shadow → 改为中性阴影
- CTA 按钮对比度同步修复

### 验证方法
\\\powershell
node .agents/skills/impeccable/scripts/detect.mjs --json
# 应返回 []（无检测到问题）
\\\

### 部署
git push origin master → GitHub Pages 自动部署 → https://zycheam.github.io/fitforge/
---

## 8. Impeccable Polish 记录 (2026-07-31)

### 修复清单

**index.html（主应用 — Operate 模式）**
- 	ransition: all → 替换为 6 个具体属性（background, color, transform, border-color, opacity）
- Toast box-shadow 绿色 glow → 中性 gba(0,0,0,0.5)
- Exercise card hover 橙色 glow → 中性 gba(0,0,0,0.3)
- 重复的 ESC 键盘处理器 → 移除底部冗余监听，保留一个
- 重复的 prefers-reduced-motion 块 → 合并为一个
- outline: none → 补充 :focus-visible 聚焦环（2px solid primary, offset 2px）

**fitforge-landing.html（落地页 — Persuade 模式）**
- 移除被禁 section-tag kickers（"核心功能"/"使用流程"/"定价方案"）
- 移除 section-tag CSS 定义
- 整合散落的 reveal 动画：只保留 hero + 前 4 张 feature card
- 移除装饰性 gradient orbs，替换为 subtle 椭圆渐变
- 添加 focus-visible 键盘导航环

### Craft Floor 合规检查
- 无 gradient text ✓
- 无 glass/blur 装饰 ✓
- 无硬偏移阴影 ✓
- 无 unicode/emoji 代替图标 ✓
- 深度阴影均为 offset+blur 中性色 ✓
- 无卡片嵌套 ✓
- 字体回退栈含中文 fallback ✓