# 朝堂 Chaotang — Multi-Agent Collaborative Skill

> 从圆桌议事到三省六部执行的全链路多 Agent 协同系统

## What is this?

朝堂 (Chaotang) is a multi-agent orchestration skill that combines two ancient Chinese governance concepts into a modern AI workflow:

- **Roundtable Discussion** (圆桌议事): Multi-perspective deliberation with 3 expert roles
- **Three Departments & Six Ministries** (三省六部): Structured plan → review → execute pipeline

The result is a complete "think it through → get it done" pipeline for complex tasks.

## Architecture

```
User Goal
  │
  ├─ Complex ──→ Roundtable (PMO + Finance + OD)
  │                  │
  │                  ▼
  │              Decision Output
  │                  │
  ├─ Clear ─────────┤
  │                  ▼
  │              Zhongshu (Planning)
  │                  │
  │                  ▼
  │              Menxia (Review / Veto)
  │                  │
  │                  ▼
  │              Shangshu → Six Ministries (Execute)
  │                  │
  │                  ▼
  └─ Simple ──→ Delivery
```

## Seven Phases

| Phase | Name | Role |
|-------|------|------|
| 0 | Load Memory | Read team profile, history, action tracker |
| 1 | Triage | Route to roundtable vs direct execution |
| 2 | Roundtable | 3-role deliberation (3 rounds) |
| 3 | Decision | Consensus + action items output |
| 4 | Planning | Zhongshu drafts structured execution plan |
| 5 | Review | Menxia reviews (can veto up to 3x) |
| 6 | Execute | Shangshu dispatches to Six Ministries |
| 7 | Deliver | Aggregate results + quality check |

## Six Ministries

| Ministry | ID | Focus |
|----------|-----|-------|
| 吏部 People | libu | HR, scheduling, team status |
| 户部 Data | hubu | Data analysis, budgets, reports |
| 礼部 Comms | libu_rites | Email, external comms, meeting notes |
| 兵部 Ops | bingbu | Task execution, project management |
| 刑部 Audit | xingbu | Quality review, compliance |
| 工部 Build | gongbu | Document creation, tooling, templates |

## Quick Commands

| Command | Effect |
|---------|--------|
| 议 | Enter roundtable discussion |
| 干 | Skip discussion, go straight to execution |
| 拍板 | Finalize decisions, enter execution pipeline |
| 封驳 | Veto current plan |
| 交差 | Collect and deliver results |
| 回顾 | Review history and pending actions |

## File Structure

```
chaotang/
├── SKILL.md              # Main orchestration (410 lines)
├── references/
│   ├── ministries.md     # Role definitions for 3 depts + 6 ministries
│   └── protocol.md       # Flow rules and message protocol
└── roles/
    ├── pmo-director.md   # Roundtable: PMO Director
    ├── finance-bp.md     # Roundtable: Finance Business Partner
    └── org-developer.md  # Roundtable: Organization Development
```

## Installation

### Claude Desktop / Cowork
Save the chaotang.skill file and install via the skill installer.

### Claude Code
Copy the chaotang/ directory to your project's .claude/skills/ folder.

### Other LLM Systems
Use SKILL.md as the system prompt, and reference files as needed per phase.

## Test Results

| Metric | with_skill | without_skill |
|--------|-----------|--------------|
| Assertion Pass Rate | **100%** (21/21) | 17.9% (4/21) |
| Avg Time | 238.3s | 74.9s |
| Avg Tokens | 67,334 | 38,217 |

## License

MIT
