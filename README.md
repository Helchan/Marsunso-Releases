# Marsunso - 书签快捷搜索插件

<div align="center">

[![Version](https://img.shields.io/badge/version-1.1.5-blue.svg)](https://github.com/Helchan/Marsunso-Release.git)
[![License](https://img.shields.io/badge/license-Apache%202.0-blue.svg)](LICENSE)
[![Chrome](https://img.shields.io/badge/chrome-88%2B-brightgreen.svg)](https://www.google.com/chrome/)

一个提升浏览器书签访问效率的 Chrome 扩展程序，通过快捷键快速搜索和访问书签，让书签管理如同 macOS Spotlight 一般流畅便捷。

[功能特性](#功能特性) • [安装方法](#安装方法) • [使用指南](#使用指南) • [技术架构](#技术架构) • [开发说明](#开发说明) • [贡献指南](#贡献指南)

</div>

---

## 项目简介

Marsunso 是一个轻量级的 Chrome 书签快捷搜索插件，旨在解决传统书签管理的效率问题。通过类似 macOS Spotlight 的交互体验，用户可以快速搜索、导航和访问书签，无需在书签栏中逐层点击。

### 核心优势

- **极速访问**：`Ctrl+K` / `Command+K` 一键唤起，无需鼠标操作
- **智能搜索**：支持书签名称、URL、拼音匹配，多种搜索模式自动切换
- **层级导航**：支持多级路径搜索和精确路径导航
- **无缝体验**：50ms 防抖优化，状态自动保存，焦点智能管理
- **隐私安全**：所有数据本地处理，不上传任何信息

## 功能特性

### 🚀 快捷键唤起

- **全局快捷键**：`Ctrl+K` (Windows/Linux) 或 `Command+K` (macOS)
- **智能聚焦**：面板已打开时重复按快捷键自动聚焦搜索框
- **状态保存**：关闭面板后 1.5 秒内重新打开，自动恢复搜索内容

### 🔍 智能搜索引擎

- **多模式自动切换**：
  - **默认模式**：展示所有二级书签
  - **模糊搜索**：支持书签名称、URL、拼音匹配
  - **路径导航**：使用 `/` 开头精确导航到指定目录

- **拼音匹配**：基于 `pinyin-pro` 库，支持：
  - 全拼匹配：`woaixuexi` → "我爱学习"
  - 首字母匹配：`wxxx` → "我爱学习"
  - 混合匹配：`w学xi` → "我爱学习"
  - 非连续匹配：`我学` → "我爱学习"
  - 多音字、生僻字支持

- **层级匹配**：支持多关键词搜索，如 `学习 读书` 在"学习"目录下搜索"读书"

### 📁 层级导航

- **精确路径导航**：`/学习/课程` 直接进入指定目录
- **路径搜索混合**：`/学习/课程 语文` 在指定路径下搜索
- **快速返回**：`Cmd/Ctrl + ↑` 返回上一层
- **快速进入**：`Cmd/Ctrl + ↓` 进入目录或后台打开书签

### ⌨️ 完整键盘操作

- **导航**：`↑` `↓` 选择，`Cmd/Ctrl + ←` `→` 快速跳转首尾
- **打开方式**：
  - `Enter`：新标签页打开并切换（关闭面板）
  - `Ctrl+Enter`：后台打开（保持面板和搜索状态）
  - `Cmd/Ctrl + ↓`：同 `Ctrl+Enter`（键盘友好）
- **快速操作**：`Cmd/Ctrl + Backspace` 清空搜索框，`Esc` 关闭面板

### 🎨 Spotlight 风格界面

- **简洁美观**：半透明磨砂背景，圆角阴影设计
- **图标优化**：自动获取网站 Favicon，文件夹使用 SVG 图标
- **高亮提示**：选中项淡蓝色高亮，滚动自动跟随
- **性能优化**：图标预加载，DocumentFragment 批量渲染

## 安装方法

### 方式一：Chrome 网上应用店安装（推荐）

> 🚧 **开发中**：插件正在准备发布到 Chrome 网上应用店，敬请期待。

### 方式二：开发者模式安装（适合测试和开发）

1. **克隆或下载项目**：
   ```bash
   git clone https://github.com/Helchan/Marsunso.git
   cd Marsunso
   ```

2. **打开 Chrome 扩展程序管理页面**：
   - 在地址栏输入 `chrome://extensions/` 并回车
   - 或通过菜单：`更多工具` → `扩展程序`

3. **启用开发者模式**：
   - 点击页面右上角的 "开发者模式" 开关

4. **加载扩展程序**：
   - 点击 "加载已解压的扩展程序" 按钮
   - 选择项目根目录（包含 `manifest.json` 的文件夹）

5. **验证安装**：
   - 扩展程序列表中出现 "Marsunso - 书签快捷搜索"
   - 按 `Ctrl+K` 或 `Command+K` 测试唤起面板

### 兼容性要求

| 浏览器 | 最低版本 | 说明 |
|--------|---------|------|
| Google Chrome | 88+ | 推荐使用最新稳定版 |
| Microsoft Edge | 88+ | 基于 Chromium，完全兼容 |
| 其他 Chromium 浏览器 | 88+ | 理论兼容，建议测试验证 |

> ⚠️ **注意**：本插件使用 Manifest V3 标准，不兼容 Manifest V2 或更低版本的浏览器。

## 使用指南

### 快速上手

1. **唤起搜索面板**：按 `Ctrl+K` (Windows/Linux) 或 `Command+K` (macOS)
2. **输入关键词**：直接输入书签名称、URL 或拼音
3. **选择结果**：使用 `↑` `↓` 方向键或鼠标点击
4. **打开书签**：按 `Enter` 或点击打开
5. **关闭面板**：按 `Esc` 或点击其他区域

### 搜索模式详解

#### 模式一：默认模式（搜索框为空）

**触发条件**：搜索框内容为空或仅包含空格

**展示内容**：所有二级书签（书签栏下的直接子项，深度为 2 的项目）

**典型场景**：快速浏览常用书签分类

---

#### 模式二：模糊搜索模式

**触发条件**：搜索框包含文字，且不以 `/` 开头

**支持的匹配方式**：

| 输入示例 | 匹配规则 | 说明 |
|---------|---------|------|
| `vue` | 单关键词匹配 | 搜索书签名称或 URL 包含 "vue" 的项 |
| `wxxx` | 拼音首字母 | 匹配 "我爱学习" 等汉字 |
| `woaixuexi` | 全拼匹配 | 匹配 "我爱学习" |
| `w学xi` | 混合输入 | 拼音与汉字混合匹配 "我爱学习" |
| `我学` | 非连续匹配 | 跳跃式匹配 "我爱学习" |
| `学习 读书` | 多级搜索 | 上层匹配 "学习"，下层匹配 "读书" |
| `学习 读书 ` | 获取子项 | 获取 "读书" 目录的所有直接子项 |
| `前端 vue react` | 三级搜索 | 上层 "前端"，中层 "vue"，下层 "react" |

**匹配优先级**：
1. 完全匹配 > 前缀匹配 > 包含匹配
2. 书签名称匹配 > URL 匹配
3. 层级深度越浅优先级越高

---

#### 模式三：路径导航模式

**触发条件**：搜索框以 `/` 开头

**语法规则**：
- 必须以 `/` 开头（`/` 不能出现在任何空格之后）
- 斜杠分隔的每一段表示精确目录名称
- 可以与空格搜索混合使用

**示例**：

| 输入内容 | 匹配效果 |
|---------|----------|
| `/学习/课程` | 精确进入 "学习" → "课程" 目录 |
| `/学习/课程 语文` | 在 "课程" 目录下模糊搜索 "语文" |
| `/学习/课程/` | 末尾斜杠，展示 "课程" 目录的所有子项 |
| `学习/课程` | ❌ 无效（未以 `/` 开头） |
| `学习 /课程` | ❌ 无效（`/` 在空格后） |

---

### 键盘操作完整列表

| 按键 | 功能 | 详细说明 |
|------|------|----------|
| `Ctrl+K` / `Command+K` | 打开搜索面板 | 全局快捷键，任意页面可触发 |
| `↑` | 向上选择 | 循环选择，第一项向上到最后一项 |
| `↓` | 向下选择 | 循环选择，最后一项向下到第一项 |
| `Cmd/Ctrl + ←` | 跳转到第一项 | 快速定位到列表首项 |
| `Cmd/Ctrl + →` | 跳转到最后一项 | 快速定位到列表末项 |
| `Enter` | 确认操作 | 目录：进入；书签：新标签页打开并切换，关闭面板 |
| `Ctrl/Cmd + Enter` | 后台打开 | 书签在后台打开，停留当前页面，保持面板 |
| `Cmd/Ctrl + ↑` | 返回上层 | 删除最后一个路径段，触发搜索更新 |
| `Cmd/Ctrl + ↓` | 进入/后台打开 | 目录：进入；书签：后台打开 |
| `Cmd/Ctrl + Backspace` | 清空搜索框 | 快速清空，触发默认模式 |
| `Esc` | 关闭面板 | 关闭搜索面板，保存当前状态 |

> **💡 提示**：Mac 系统使用 `Command` 键，Windows/Linux 使用 `Ctrl` 键。

---

### 鼠标操作

| 操作 | 效果 |
|------|------|
| **单击书签** | 新标签页打开并切换，关闭面板 |
| **Ctrl + 单击书签** | 后台打开，保持当前页面和面板 |
| **单击文件夹** | 进入该文件夹，更新搜索框为完整路径 |
| **Ctrl + 单击文件夹** | 同单击（文件夹不支持后台打开） |

---

### 高级技巧

**批量打开书签**：
1. 使用 `Ctrl+Enter` 或 `Ctrl+单击` 后台打开第一个书签
2. 面板保持打开，搜索内容不变
3. 继续点击其他书签，实现快速批量打开

**快速定位**：
- 使用 `Cmd/Ctrl + ←` 和 `Cmd/Ctrl + →` 在长列表中快速跳转首尾
- 使用 `Cmd/Ctrl + ↑` 逐层返回上级目录

**状态保存**：
- 关闭面板后 2 秒内重新打开，自动恢复上次的搜索内容
- 适合快速查找、临时关闭、再次查找的场景

## 贡献指南

我们欢迎任何形式的贡献，包括但不限于：

- 🐛 **报告 Bug**：在 [Issues](https://github.com/Helchan/Marsunso-Release/issues) 页面提交问题
- 💡 **功能建议**：提出新功能或改进建议
- 📝 **文档改进**：修正文档错误或补充说明
- 🔧 **代码贡献**：提交 Pull Request 修复 Bug 或添加功能

### 提交 Issue

在提交 Issue 之前，请确保：

1. **搜索现有 Issue**：避免重复提交
2. **提供详细信息**：
   - 问题描述（期望行为 vs 实际行为）
   - 复现步骤
   - 浏览器版本和操作系统
   - 截图或错误日志（如有）

### 行为准则

- 尊重他人，友善交流
- 遵守开源社区规范
- 专注于技术讨论，避免无关话题

## 常见问题

### Q1: 快捷键不生效？

**A**: 检查以下几点：
1. 扩展是否正确加载（`chrome://extensions/` 查看状态）
2. 快捷键是否与其他扩展冲突（`chrome://extensions/shortcuts` 查看）
3. 某些特殊页面（`chrome://`、`chrome-extension://`）不支持扩展快捷键

### Q2: 拼音搜索不准确？

**A**: 拼音匹配支持多种模式，尝试以下输入方式：
- 全拼：`woaixuexi`
- 首字母：`wxxx`
- 混合：`w爱xi`
- 非连续：`我学`

### Q3: 图标显示异常？

**A**: 
1. Favicon 依赖 Google 服务，确保网络畅通
2. 某些网站可能没有 Favicon，会显示默认书签图标
3. 图标加载失败会自动降级到默认图标

### Q4: 如何清除缓存？

**A**: 
1. 关闭所有插件面板
2. 在扩展管理页面点击 "刷新" 按钮
3. 重新打开面板，缓存将重新构建

### Q5: 支持其他浏览器吗？

**A**: 理论上支持所有基于 Chromium 88+ 的浏览器（如 Edge、Brave、Opera），但建议测试验证。暂不支持 Firefox（需要适配 WebExtensions API）。

## 隐私与安全

**本插件承诺**：
- ✅ 所有数据仅在本地处理，不上传到任何服务器
- ✅ 不收集用户浏览记录或书签内容
- ✅ 不使用第三方统计或分析服务
- ✅ 不注入任何跟踪代码到网页
- ✅ 图标获取仅发送域名信息（不含完整 URL）
- ✅ 输入内容自动过滤危险字符，防止 XSS 攻击

**权限说明**：
- `bookmarks`：读取书签数据，用于搜索功能
- `tabs`：打开和管理标签页
- `storage`：本地存储搜索状态（2秒缓存）

## 许可证

本项目采用 [Apache License 2.0](LICENSE) 开源协议。

```
Copyright 2024-2026 Marsunso Contributors

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

---

## 鸣谢

感谢以下开源项目和服务：

- [pinyin-pro](https://github.com/zh-lx/pinyin-pro) - 强大的汉字拼音转换库
- [Google Favicon API](https://www.google.com/s2/favicons) - 网站图标服务
- Chrome Extensions API - 提供强大的浏览器扩展能力

---

<div align="center">

**如果这个项目对你有帮助，欢迎 Star ⭐️ 支持！**

[报告问题](https://github.com/Helchan/Marsunso-Release/issues) • [功能建议](https://github.com/Helchan/Marsunso-Release/issues) • [贡献代码](https://github.com/Helchan/Marsunso-Release/pulls)

Made with ❤️ by Marsunso Contributors

</div>
