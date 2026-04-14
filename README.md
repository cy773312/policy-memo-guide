<div align="right">

中文 | **[English](README_EN.md)**

</div>

<div align="center">

# policy-memo-guide

**把分析、笔记和研究材料，稳定转成真正可交付的 Policy Memo。**

[![Skill](https://img.shields.io/badge/Skill-policy--memo--guide-111827)](#)
[![Language](https://img.shields.io/badge/language-中文主%20%7C%20English-0f766e)](#)
[![Genre](https://img.shields.io/badge/genre-Policy%20Memo-7c3aed)](#)
[![Reference](https://img.shields.io/badge/reference-Duke%20Writing%20Studio-b45309)](references/duke-policy-memo-guide.md)
[![Optimized%20with](https://img.shields.io/badge/optimized%20with-darwin--skill-2563eb)](https://github.com/alchaincyf/darwin-skill)

</div>

---

## 这是什么

`policy-memo-guide` 是一个面向 Agent / Codex 工作流的写作 skill，专门处理这类任务：

- 把零散分析改写成正式 `policy memo`
- 在信息不完整时，先产出 `memo-ready outline`
- 在受众、建议、证据不稳定时，给出更稳妥的结构化 fallback
- 按 Duke Writing Studio 的 memo 逻辑组织内容，而不是滑向普通议论文

它不是通用写作助手，而是一个**决策导向文书 skill**。

---

## 为什么它有用

很多模型“知道” policy memo 长什么样，但在真实任务里仍会出现几个常见问题：

- 信息一不完整，就开始过度追问
- 写成一般分析文，而不是 memo
- 背景写太多，建议写太晚
- audience 不明确时，没有先给可用骨架

这个 skill 的目标就是把这些常见失误压下去，让输出更像一个真正给决策者看的 memo。

---

## 设计原则

这个 skill 以 Duke Writing Studio 的 policy memo 指南为核心参考，重点强化四件事：

1. **Audience-first**
   先锁定 memo 是写给谁、为了解决什么决策问题。

2. **Inverted pyramid**
   重要结论靠前，背景和细节靠后。

3. **Executive-summary discipline**
   即使只读标题和前一段，也能抓到主张。

4. **Outline-before-stall**
   信息不完整时，优先给可用结构，而不是只抛回问题。

---

## 适用场景

适合这些典型请求：

- “帮我写一份给市长办公室的政策备忘录”
- “把这份分析改成 policy memo”
- “turn this into a memo for the minister”
- “我老师要求从分析文改成 policy memo”
- “我还没想清楚建议，但先帮我把 memo 结构搭出来”

不适合：

- 普通学术论文
- 文献综述
- 纯评论文章
- 不需要 memo 格式的泛化写作任务

---

## 输出模式

这个 skill 不会把所有请求都硬写成同一种成品，而是按上下文切到最合适的模式：

| 模式 | 适用情况 | 结果 |
| --- | --- | --- |
| `Full memo` | 信息足够完整 | 直接起草完整 memo |
| `Memo-ready outline` | 关键信息缺失，但已能搭结构 | 先给可用骨架与假设 |
| `Rewrite` | 用户已有分析稿/笔记/brief | 提炼后改写成 memo |
| `Recommendation options` | 核心建议还不明确 | 先给选项，再选出最强建议 |

---

## 示例 Prompt

```text
请把下面这些分析整理成给市长办公室的政策备忘录，主题是是否扩大夜间公交服务。
```

```text
Turn my notes on export controls and semiconductor supply chains into a policy memo for the Minister of Trade.
```

```text
我有一篇背景分析，但老师要求改成 policy memo。受众还没定，建议也不够明确。你先帮我搭好结构并指出缺什么。
```

---

## 仓库结构

```text
policy-memo-guide/
├── SKILL.md
├── README.md
├── README_EN.md
├── test-prompts.json
├── agents/
│   └── openai.yaml
└── references/
    └── duke-policy-memo-guide.md
```

---

## 参考来源

- Duke Writing Studio Policy Memo Guide
- 本仓库内的清洗版 reference：[`references/duke-policy-memo-guide.md`](references/duke-policy-memo-guide.md)
- Duke 原始 PDF：`https://twp.duke.edu/sites/twp.duke.edu/files/file-attachments/policy-memo.original.pdf`

---

## 迭代优化说明

这个 skill 不是一次写完的，而是专门用 **[darwin-skill](https://github.com/alchaincyf/darwin-skill)** 做过多轮迭代优化。

优化方法不是“拍脑袋改文案”，而是更接近一个小型的 skill hill-climbing loop：

- 先按 8 个维度评分
- 每轮只改一个最低分维度
- 使用独立子 agent 做 with-skill / baseline 评测
- 如果总分不升，就回滚

这意味着现在这个版本不是“作者主观看着顺眼”的版本，而是经过多轮对照和回退后留下来的版本。

---

## 快速使用

把这个目录放进你的 skill 目录里即可，例如：

```bash
mkdir -p ~/.codex/skills
cp -R policy-memo-guide ~/.codex/skills/
```

然后在支持 skill 的环境里直接调用：

```text
Use $policy-memo-guide to turn my notes into a concise policy memo for a named audience.
```

或者直接自然语言触发。

---

## 适合谁

- 经常要写政策备忘录的学生
- 做公共政策、国际关系、公共管理相关写作的人
- 想把研究笔记压缩成决策文书的人
- 想让 Agent 在 memo 场景下更稳定的人

---

## 状态

当前版本已经过独立子 agent 评分与对照评测，属于可直接使用的稳定版本。  
如果后续继续优化，优先会沿着：

- 更强的 edge-case coverage
- 更高的 with-skill 实测表现
- 更低的无谓追问率

继续迭代。

