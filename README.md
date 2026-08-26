# 量潮工作档案

## 仓库定位

量潮工作档案（quanttide-profile）是量潮知识管理体系中的**档案聚合容器**——按主体与领域聚合各业务的工作档案子仓库（git submodule）。每个子仓库独立维护，本仓库只追踪引用。

在量潮"正交分解"中，本仓库对应**主体轴（Who it is）与领域轴（What it expresses）**：`default/` 聚合法人主体档案，`domains/` 聚合各领域工作档案，回答"我们是谁、各领域如何运作"。

## 仓库结构

```
quanttide-profile/
├── default/company      → 法人主体档案（quanttide-profile-of-business-entity）
├── domains/             → 领域档案子仓库（git submodule）
│   ├── agent            → 智能体工程档案（quanttide-profile-of-agent-engineering）
│   ├── alliance         → 创新联盟档案（quanttide-profile-of-alliance）
│   ├── asset            → 资产管理档案（quanttide-profile-of-asset-management）
│   ├── brands           → 品牌档案（quanttide-profile-of-brands）
│   ├── business         → 商务拓展档案（quanttide-profile-of-business-development）
│   ├── cloud-computing  → 云计算档案（quanttide-profile-of-cloud-computing）
│   ├── collaboration    → 团队协作档案（quanttide-profile-of-collaboration）
│   ├── commerce         → 商务档案（quanttide-profile-of-commerce）
│   ├── connect          → 沟通管理档案（quanttide-profile-of-communication）
│   ├── course           → 课程研发档案（quanttide-profile-of-course-development）
│   ├── crowd            → 众包管理档案（quanttide-profile-of-crowd-sourcing）
│   ├── customer         → 客户关系档案（quanttide-profile-of-customer-relations）
│   ├── customers        → 客户档案（quanttide-profile-of-customers）
│   ├── data             → 数据工程档案（quanttide-profile-of-data-engineering）
│   ├── delib            → 议事管理档案（quanttide-profile-of-deliberation-management）
│   ├── design           → 交互设计档案（quanttide-profile-of-interaction-design）
│   ├── devops           → DevOps 工程档案（quanttide-profile-of-devops）
│   ├── econ             → 经济建模档案（quanttide-profile-of-economic-modeling）
│   ├── entrep           → 创业档案（quanttide-profile-of-entrepreneurship）
│   ├── execute          → 执行管理档案（quanttide-profile-of-execution-management）
│   ├── finance          → 财务管理档案（quanttide-profile-of-finance-management）
│   ├── health           → 健康管理档案（quanttide-profile-of-health-management）
│   ├── human            → 人力资源档案（quanttide-profile-of-human-resources）
│   ├── innov            → 创新管理档案（quanttide-profile-of-innovation-management）
│   ├── knowl            → 知识工程档案（quanttide-profile-of-knowledge-engineering）
│   ├── legal-affairs    → 法务档案（quanttide-profile-of-legal-affairs）
│   ├── media            → 新媒体档案（quanttide-profile-of-social-media）
│   ├── open-source      → 开源档案（quanttide-profile-of-open-source）
│   ├── product          → 产品研发档案（quanttide-profile-of-product-development）
│   ├── research-assistants → 助研档案（quanttide-profile-of-research-assistants）
│   ├── standardization  → 标准化档案（quanttide-profile-of-standardization）
│   ├── strategies       → 战略档案（quanttide-profile-of-strategies）
│   ├── strategy         → 战略管理档案（quanttide-profile-of-strategy-management）
│   ├── think            → 认知工程档案（quanttide-profile-of-cognitive-engineering）
│   └── write            → 叙事工程档案（quanttide-profile-of-narrative-engineering）
├── README.md            → 本文件
├── AGENTS.md            → Agent 工作指南
├── CHANGELOG.md         → 版本变更记录
└── LICENSE              → 许可证
```

## 子模块管理

- 子模块独立提交推送，本仓库只更新引用指针
- 新增档案仓库：`git submodule add <url> default/<path>`（主体档案）或 `domains/<path>`（领域档案）
- 同步全部子模块：`git submodule update --init --recursive`

## 关联

- 档案与日志同源：`assets/quanttide-journal`（工作日志聚合）
- 档案与意图互补：`assets/quanttide-intention`（工作意图聚合）
- 分层关系：journal（事实）→ intention（意图）→ profile（档案/叙事），更新方向单向
