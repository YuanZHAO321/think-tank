# 🧠 think-tank · 思维方式与决策引擎

> A Claude Code skill that turns Claude into a cold, structured decision engine — backed by a retrievable library of mental models, strategic patterns, and hard-won wisdom.

一套可安装的 [Claude Code](https://claude.com/claude-code) 技能：把"**如何冷静、理性、有结构地思考一个问题**"做成一个常驻的推理引擎，背后挂着一个按需调用的"智慧/经验库"。

它不替你做决定，而是帮你**像一个老练的决策者那样去想**——先想清目标，再算赔率、留后手、借势、止损，并在事后复盘迭代。

---

## 💡 核心理念：思维方式 + 经验/记忆

现实中人做决策，大致 = **思维方式**（怎么思考、推理）+ **经验/记忆**（可参考的智慧与信息）。

本技能照此构造，正好对应 Claude Code 技能的两层结构：

| 认知层 | 对应文件 | 加载方式 |
|---|---|---|
| **思维方式**（推理引擎） | `SKILL.md` | 常驻——总在上下文里，像"工作记忆中的推理方式" |
| **经验 / 记忆 / 智慧** | `references/*.md` | 按需检索——用到哪类经验才加载哪个，像"长期记忆" |

> 推理引擎负责"怎么想"；智慧库负责"想的时候调用什么"。

---

## ✨ 里面有什么

### 推理引擎（`SKILL.md`，常驻）
- **核心立场**：棋子→棋手 · 目标内核为根 · 凡事有价 · 能动性优先 · 抓本质（第一性原理）
- **决策分级 triage**：先按"可逆性 / 一次性vs重复 / 赌注大小"分级，把"想多深"当成一项要分配的资源——别用大炮打蚊子
- **决策八准则**：目标通透 · 赔率思维 · 长线布局 · 狡兔三窟 · 信息差 · 借势 · 反脆弱 · 果断止损
- **标准八步流程**：目标 → 局面 → 算账（含事实/情绪分离）→ 风险与后手 → 借势 → 时间维度 → 决断 → **复盘闭环**
- **多元思维切换**：按场景调用推演 / 改规则 / 逆向 / 留余地 / 规则精通 / 复利 / 韧性等不同"打法"
- **思维反模式**：情绪驱动、沉没成本、单点押注、信息懒惰、自欺……命中即标红

### 智慧库（`references/`，按需调用）
| 文件 | 内容 |
|---|---|
| `decision-archetypes.md` | 十种思维"打法" + 顺风顺水陷阱 / 极致专精的代价等反面教材 |
| `principles.md` | 价值观 · 成事三元（力量×智慧×希望）· 清醒世界观 |
| `resilience.md` | 低谷穿越 · 韧性 · 认识自己 · 失败的价值 · 情绪管理 |
| `human-nature.md` | 防人靠制度 · 立场决定叙事 · 看清机制≠认同机制 · 人际现实 |
| `systems-thinking.md` | 能力模块化 · 持有成本 · 创新即重组 · 认知阶梯（信息→知识→本质） |
| `strategy-patterns.md` | 10 个经典局面 → 决策模型 + 速查表 |
| `maxims.md` | 可引用的通用格言与原则（点题用） |
| `writing-craft.md` | 写作与叙事技法（反派塑造 / 硬设定自洽 / 伏笔 / 张力） |

---

## 📦 安装

Claude Code 个人技能放在 `~/.claude/skills/` 下。直接克隆到该目录即可：

```bash
git clone https://github.com/<your-username>/think-tank.git ~/.claude/skills/think-tank
```

或先克隆到别处，再软链接：

```bash
git clone https://github.com/<your-username>/think-tank.git
ln -s "$(pwd)/think-tank" ~/.claude/skills/think-tank
```

安装后重启 / 新开一个 Claude Code 会话即可生效。验证：输入 `/` 看技能列表，或直接提一个决策问题。

---

## 🚀 用法

技能会在以下情形自动触发（无需手动调用）：

- 面临重大选择 / 谈判 / 投资 / 职业抉择 / 人生困惑
- 明确说"**冷静理性地帮我分析这件事**""**用决策框架 / 心智模型拆解一下**"
- 想系统地学思维、处世、人性、创新方法

**示例：**

```
> 我手上有个稳定的工作，又收到一个早期创业公司的 offer，纠结要不要去。冷静帮我分析一下。
```

Claude 会先给问题分级（这是不是不可逆的"单向门"？），逼问你的真实目标，列成本/收益/概率，区分事实与情绪，给出后手与止损线，最后给明确建议 + "什么信号出现就该改主意"，并提示如何复盘。

---

## 🔌 即用文件：让某个项目默认用上这套思维（CLAUDE.md / AGENT.md）

仓库自带两个**即用配置文件**，让 agent 默认采用 think-tank 的决策流程——无需额外配置。

```bash
# 用 Claude Code：复制 CLAUDE.md（Claude Code 会自动加载工作目录的 CLAUDE.md）
cp ~/.claude/skills/think-tank/CLAUDE.md /path/to/your/project/CLAUDE.md

# 用其他 agent：复制 AGENT.md（对应通行的 AGENTS.md 约定，文件自足）
cp ~/.claude/skills/think-tank/AGENT.md /path/to/your/project/AGENT.md
```

- **`CLAUDE.md`** — 面向 Claude Code。复制进工作目录根部即生效（Claude Code 会自动加载工作目录的 `CLAUDE.md`）；装了本技能会优先调用其引擎与智慧库，未装时内嵌的精简流程也能独立运行。
- **`AGENT.md`**：面向任意 agent 的可移植"操作契约"，**完全自足**，不依赖技能是否安装。
- 两者放一个即可；并存也不冲突。

---

## 🗂 目录结构

```
think-tank/
├── SKILL.md                      # 思维方式 / 推理引擎（常驻）
├── CLAUDE.md                     # 即用文件：复制进工作目录 → Claude Code 默认按此思维
├── AGENT.md                      # 即用文件：复制进工作目录 → 任意 agent 的可移植操作契约
├── README.md
├── LICENSE
└── references/                   # 智慧 · 经验 · 记忆库（按需加载）
    ├── decision-archetypes.md
    ├── principles.md
    ├── resilience.md
    ├── human-nature.md
    ├── systems-thinking.md
    ├── strategy-patterns.md
    ├── maxims.md
    └── writing-craft.md
```

---

## ⚖️ 伦理边界

这是一套用于**自我成长、谈判、决策、风险管理、认知**的思维工具。

- ✅ 适用：个人成长、职业规划、投资与博弈分析、谈判、风险管理、自我认知。
-  不推荐使用于：操纵或欺骗他人、损害他人利益、为伤害行为做合理化。
- 核心信念：可持续的强者靠**正和博弈与复利**，不只是零和掠夺；**看清世界冷酷 ≠ 完全绝对的认同它**。

每个智慧库条目都遵循"洞察 → 现实迁移 （可选：→ 建议/剥离）"的结构。

---

## 🧩 设计原则

- **渐进式披露**：常驻只放推理引擎，深度内容按需加载，避免上下文膨胀。
- **可迁移优先**：每条都给"现实里怎么用"，并尽量挂到成熟理论（机会成本、反脆弱、斯多葛、熊彼特、第一性原理、PDCA…）。
- **结论可执行**：决策类输出永远给止损线和"何时该改主意"的触发条件，不和稀泥。

---

## 🤝 贡献

欢迎 issue / PR：补充思维范式、谋略模式、反模式，或改进现实理论锚。请保持"洞察 → 现实迁移 → 边界"的统一结构，并附上可迁移的现实用法。

## 📄 License

[MIT](./LICENSE) — 内容为原创整合，自由使用、修改、分享。
