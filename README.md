# 量潮工作档案

## 仓库定位

量潮工作档案（quanttide-profile）是量潮知识管理体系中的**档案聚合容器**——按领域聚合各业务的工作档案子仓库（git submodule）。每个子仓库独立维护，本仓库只追踪引用。

在量潮"正交分解"中，本仓库对应**主体轴（Who it is）**：`default/` 聚合法人主体档案，`domains/` 聚合各领域工作档案，回答"我们是谁、各领域如何运作"。

## 仓库结构

```
quanttide-profile/
├── default/company      → 法人主体档案（quanttide-profile-of-business-entity）
├── domains/             → 领域档案子仓库（git submodule）
│   ├── agent            → 智能体工程档案（quanttide-profile-of-agent-engineering）
│   ├── course           → 课程研发档案（quanttide-profile-of-course-development）
│   ├── customer         → 客户关系档案（quanttide-profile-of-customer-relations）
│   ├── data             → 数据工程档案（quanttide-profile-of-data-engineering）
│   ├── delib            → 议事管理档案（quanttide-profile-of-deliberation-management）
│   ├── econ             → 经济建模档案（quanttide-profile-of-economic-modeling）
│   ├── execute          → 执行管理档案（quanttide-profile-of-execution-management）
│   ├── health           → 健康管理档案（quanttide-profile-of-health-management）
│   ├── human            → 人力资源档案（quanttide-profile-of-human-resources）
│   ├── innov            → 创新管理档案（quanttide-profile-of-innovation-management）
│   └── product          → 产品研发档案（quanttide-profile-of-product-development）
├── README.md            → 本文件
├── AGENTS.md            → Agent 工作指南
├── CHANGELOG.md         → 版本变更记录
└── LICENSE              → 许可证
```

## 子模块管理

- 子模块独立提交推送，本仓库只更新引用指针
- 新增档案仓库：`git submodule add <url> domains/<path>`
- 同步全部子模块：`git submodule update --init --recursive`

## 关联

- 档案与日志同源：`assets/quanttide-journal`（工作日志聚合）
- 档案与意图互补：`assets/quanttide-intention`（工作意图聚合）
- 分层关系：journal（事实）→ intention（意图）→ profile（档案/叙事），更新方向单向
