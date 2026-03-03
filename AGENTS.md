# AGENTS.md - Agent 工作指南

本文档为 Agent 在本仓库中工作提供指南。

## 项目概述

本仓库是**量潮工作档案**的父仓库，采用 Git 子模块结构管理多个独立文档模块：

- **domain/** - 领域知识模块
  - `asset/` - 数字资产
  - `innov/` - 创新
  - `knowl/` - 知识管理
  - `stdn/` - 标准化
  - `think/` - 思考
  - `write/` - 写作
  
- **entity/** - 实体档案模块
  - `company/` - 企业档案
  - `founder/` - 创始人档案

每个子模块都是独立的 Jupyter Book 文档项目。

---

## 构建命令

### Jupyter Book 构建

```bash
# 进入子模块目录
cd entity/founder  # 或其他模块

# 构建 HTML（单文件方式，避免 EISDIR 错误）
jupyter-book build index.md --site

# 构建并预览
jupyter-book start .

# 清理构建文件
jupyter-book clean .
```

### 质量检查

```bash
# Markdown linting
markdownlint "**/*.md"

# 验证 YAML 配置
yamllint .
```

### 验证清单

- [ ] 所有内部链接指向已存在的文件
- [ ] `_toc.yml` 中引用的文件均已创建
- [ ] YAML 文件语法正确
- [ ] 新增文件已添加到 `_toc.yml`
- [ ] 构建无错误

---

## 代码风格指南

### Markdown 规范

**文件命名**
- 使用小写字母
- 单词间用下划线 `_` 分隔
- 示例：`think/index.md`, `llm_learning.md`

**标题格式**
- 使用 ATX 风格（`#`、`##`、`###`）
- 标题使用中文或英文，保持一致性

**列表格式**
- 使用 `-` 或 `1.`，保持统一
- 列表项之间保留空行

**代码块**
- 使用 fenced code（\`\`\`）
- 标注语言：` ```python `, ` ```bash ` 等

**链接**
- 使用相对路径
- 内部引用：`[文字](目录/文件.md)`

### 目录结构规范

```
板块名/
├── index.md        # 板块入口，内容摘要
├── README.md       # 板块说明（可选）
├── 子1.md
└── 子目录主题/
    ├── index.md
    └── 内容.md
```

- 目录使用小写字母
- 目录使用复数形式
- 示例：`think/`、`write/`、`learn/`

### 板块划分参考

| 目录 | 含义 |
|------|------|
| `think/` | 思考 |
| `write/` | 写作 |
| `knowl/` | 知识工程 |
| `learn/` | 学习 |
| `stdn/` | 标准化 |
| `connect/` | 沟通 |
| `code/` | 编程 |
| `brand/` | 品牌管理 |
| `acad/` | 学术研究 |
| `product/` | 产品研发 |
| `execute/` | 执行 |
| `finance/` | 财务 |
| `health/` | 健康 |

---

## 人机协作范式

### 核心原则

1. **最小干预**：仅在用户明确请求时操作，不主动修改非相关文件
2. **信息复用**：优先使用已有文档内容，避免重复记录已知信息
3. **查询 index**：每次维护前先查询相关 index.md 了解内容结构和关联
4. **维护 index**：修改内容后同步更新对应 index.md 的内容摘要
5. **验证优先**：完成修改后必须运行构建命令验证
6. **原子提交**：每次提交应包含完整且独立的变更

### 工作流程

1. **理解需求**：明确用户的具体任务和范围
2. **查询 index**：查看相关 index.md 了解内容结构和关联
3. **检查现状**：查看 _toc.yml 确认文件注册状态
4. **执行操作**：按规范进行修改
5. **更新 index**：同步更新相关 index.md 的内容摘要
6. **验证结果**：运行 `jupyter-book build index.md --site` 确认无错误
7. **提交推送**：创建提交并推送到远程

---

## 常见任务

### 添加新文档

1. 在对应目录下创建 `.md` 文件
2. 更新该目录的 `index.md`
3. 在 `_toc.yml` 中注册文件
4. 运行 `jupyter-book build index.md --site` 验证

### 添加新板块

1. 创建目录（遵循命名规范：小写、复数）
2. 创建 `index.md` 介绍板块内容
3. 在根目录 `index.md` 板块边界部分添加说明
4. 在 `_toc.yml` 中注册
5. 运行构建验证

### 更新子模块

```bash
# 拉取子模块最新代码
git submodule update --init --recursive

# 进入子模块并切换到最新
cd entity/founder
git checkout origin/main

# 更新父仓库引用
cd ../..
git add entity/founder
git commit -m "Update founder submodule to latest"
```

### 子模块最佳实践

**1. 始终在父仓库操作**
- 子模块变更应在子模块仓库独立提交推送
- 父仓库仅更新子模块引用（commit hash）

**2. 更新子模块流程**
```
# 方式一：在父仓库中更新（推荐）
git submodule update --init --remote entity/founder

# 方式二：进入子模块手动更新
cd entity/founder
git fetch origin
git checkout origin/main
cd ..
git add entity/founder
git commit -m "Update submodule"
```

**3. 查看子模块状态**
```bash
# 查看所有子模块状态
git submodule status

# 查看特定子模块是否有新提交
git submodule summary entity/founder
```

**4. 拉取包含子模块的仓库**
```bash
# 克隆包含子模块的仓库
git clone --recurse-submodules <repo-url>

# 或先克隆再初始化子模块
git clone <repo-url>
git submodule update --init
```

**5. 避免的操作**
- 不要在父仓库直接修改子模块文件
- 不要使用 `git submodule update`（无参数）更新单个子模块
- 不要忽略子模块的远程更新

### 发布新版本

1. **检查 CHANGELOG**：查看已有版本记录格式
2. **更新 CHANGELOG**：在 `[Unreleased]` 下新增版本块
3. **提交推送**：确保所有变更已推送到远程
4. **创建 Release**：
   - 草稿发布：`gh release create <version> --title "v<version>" --notes-file CHANGELOG.md --draft`
   - 正式发布：`gh release edit <tag> --draft=false`

---

## 版本规范

### 版本号语义

遵循语义化版本（SemVer）：`主版本.次版本.修订号`

### 版本更新规则

| 类型 | 场景 | 示例 |
|------|------|------|
| 修订号 | 错别字修正、格式调整 | 0.0.1 → 0.0.2 |
| 次版本 | 新增内容、新增板块 | 0.0.1 → 0.1.0 |
| 主版本 | 架构调整、板块边界变化 | 0.1.0 → 1.0.0 |

---

## 子模块独立维护

各子模块独立维护，可单独提交：

- `entity/founder/` - 创始人档案（详细规范见 [entity/founder/AGENTS.md](entity/founder/AGENTS.md)）
- `entity/company/` - 企业档案
- `domain/stdn/` - 标准化
- `domain/asset/` - 数字资产

---

## 注意事项

- 本项目为文档项目，无需传统 lint/test 流程
- Jupyter Book 2.x 版本使用 `jupyter-book build .` 会报 EISDIR 错误，需使用单文件构建
- 更新目录结构后需同步更新 index.md、README.md、_toc.yml 三处
- 子模块更新后需要提交父仓库的子模块引用变更
