# evidence-driven-workflow

> 一套从真实项目实践中提炼的通用工程与科研工作流 skill（Agent Skills 规范）。
> 中文名：**证据驱动工作流** —— 任何结论都要有可复现的证据，任何改动都要先确认后执行，任何知识都要沉淀成资产。

## 这是什么

一个供 AI 编程代理（agent）加载的 **skill**：当你在做科研实验、排查线上问题、准备发布上线、管理数据口径时，它给代理一套可执行的工作纪律，而不是空泛口号。

核心内容：

- **八条核心纪律**：证据链闭环 / 单一事实源 / 隔离与归档 / 确认式推进 / 自动化验证+回滚 / 诚实口径 / 知识沉淀 / 资源与风险记账
- **八步任务流水线**：开工核对 → 澄清问题 → 取证 → 最小修改 → 验证 → 收尾 → 沉淀 → 汇报（每步带验收线）
- **四个高频场景细则**：实验/数据管理、线上排障、发布上线、论文/口径管理
- **12 个反模式**：每个都来自真实事故，带后果与正解

## 来源

2026 年夏秋三个并行项目的长期实践沉淀：

1. **非侵入式推理观测工具**（vLLM 运行时代理探针）——浮点不确定性根因定位、开销量化、90+ 测试真机证据链
2. **联邦学习论文实验**（30-cell 实验矩阵 + 消融 + 期刊论文）——实验面隔离、口径管理、确认式大纲
3. **多机平台部署与排障**（四台服务器、双环境栈、CI 自动部署与回滚、端到端 API 测试）——发布链路、线上取证

这些项目里踩过的坑（OOM 假成功、裸 SQL 绕过缓存、200 包错误信封、验证集选模冒充最终结果……）都对应成了反模式条目。

## 安装

### 方式一：npx skills（推荐）

```bash
npx skills add lska367/evidence-driven-workflow -g
```

### 方式二：手动拷贝

```bash
git clone https://github.com/lska367/evidence-driven-workflow.git
cp -r evidence-driven-workflow ~/.pi/agent/skills/evidence-driven-workflow   # Pi
cp -r evidence-driven-workflow ~/.claude/skills/evidence-driven-workflow     # Claude Code
cp -r evidence-driven-workflow ~/.codex/skills/evidence-driven-workflow      # Codex
```

安装后代理会在任务匹配时（触发词见 SKILL.md 的 description）自动加载。

## 目录结构

```
evidence-driven-workflow/
├── SKILL.md                      # 主文件：纪律 + 流水线 + 场景细则（必读）
├── references/
│   ├── task-pipeline.md          # 八步流水线详解：验收线、检查清单
│   └── anti-patterns.md          # 12 个反模式 + 真实事故对照
├── LICENSE                       # MIT
└── README.md
```

## 与其他 skill 的关系

本 skill 是**公共底座**，不与专用 skill 冲突：

- 论文大纲撰写 → `paper-outline-confirm`（本 skill 的场景 D 引用它）
- 论文审稿/审计 → `paper-audit`
- 幻灯片制作 → `light-slides` 等

专用 skill 管"怎么把这件事做专业"，本 skill 管"怎么把任何事做严谨"。

## License

MIT