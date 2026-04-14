# Policy Memo Guide Skill

<p align="center">
  <strong>面向政策备忘录写作场景的 Codex Skill</strong><br />
  把分析、笔记和研究材料，稳定转成真正给决策者看的 policy memo，而不是普通议论文。
</p>

<p align="center">
  <a href="./README.en.md">English Version</a> ·
  <a href="./SKILL.md">查看 SKILL.md</a> ·
  <a href="https://github.com/alchaincyf/darwin-skill">Darwin Skill 优化器</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/Codex-技能-111827?style=flat-square" alt="Codex 技能" />
  <img src="https://img.shields.io/badge/语言-中文优先-0f766e?style=flat-square" alt="中文优先" />
  <img src="https://img.shields.io/badge/用途-Policy%20Memo-7c3aed?style=flat-square" alt="Policy Memo" />
  <a href="https://github.com/alchaincyf/darwin-skill">
    <img src="https://img.shields.io/badge/迭代优化-Darwin%20Skill-2563eb?style=flat-square" alt="Darwin Skill 迭代优化" />
  </a>
</p>

<p align="center">
  <sub>English readers can use <a href="./README.en.md">README.en.md</a>.</sub>
</p>

## 一句话介绍

`policy-memo-guide` 是一个专门服务于 **policy memo / 政策备忘录** 写作任务的 skill。  
它的目标不是“帮你写点正式文字”，而是帮助 agent 在 memo 场景下更稳定地做到：

- 先识别受众与决策问题
- 先给 recommendation，再给背景
- 信息不完整时优先给 `memo-ready outline`
- 保持 memo 格式，而不是滑向一般分析文

## 适合什么场景

这个 skill 特别适合：

- 给市长办公室、部长、校长、主任等具体受众写 memo
- 把研究笔记、背景分析、brief 改写成 policy memo
- 老师或上级要求“不要写 essay，要写 memo”
- recommendation 还没完全稳定，但需要先把结构搭出来
- 希望输出更像“可交付文书”，而不是聊天式回答

它**不主要用于**：

- 普通学术论文
- 文献综述
- 评论文章
- 不要求 memo 格式的泛化写作

## 这个 Skill 会做什么

它会根据上下文，把请求路由到最合适的输出模式，而不是无脑只产出一种成品。

默认支持 4 类结果：

1. 完整 `Full memo`
2. `Memo-ready outline`
3. `Rewrite`（把现有材料改写成 memo）
4. `Recommendation options`

核心能力可以概括成 4 件事：

| 能力 | 作用 |
|---|---|
| 先锁定 audience / issue / recommendation | 避免写成“泛政策分析” |
| 倒金字塔组织 | 让结论和建议更早出现 |
| 信息不足时先给结构 | 降低无谓追问率 |
| memo-first 写作约束 | 避免滑向 essay 或评论文 |

## 触发方式

适合被这样调用：

```text
请把下面这些分析整理成给市长办公室的政策备忘录。
```

```text
把这份分析改成 policy memo，受众是教育部。
```

```text
Turn this into a policy memo for the Minister of Trade.
```

```text
我老师要求把这篇背景分析改成 policy memo，你先帮我搭结构。
```

也适合更口语化的请求：

- “帮我写成备忘录”
- “不要 essay，要 memo”
- “先给我一个 memo outline”
- “把这份分析改成给决策者看的版本”

## 输出风格

这个 skill 的输出目标不是“写得像正式作文”，而是“写得像真正的 memo”。

它会尽量做到：

- audience 明确
- recommendation 靠前
- executive summary 清楚
- subheading 可扫读
- 假设和不确定性标注明确

常见输出模式包括：

- `To / From / Date / RE`
- `Executive Summary`
- recommendation-first section headings
- 简洁 tradeoff / implementation 风格

## 快速安装

如果你的 Codex skills 放在 `$CODEX_HOME/skills` 下：

```bash
git clone https://github.com/cy773312/policy-memo-guide.git \
  "${CODEX_HOME:-$HOME/.codex}/skills/policy-memo-guide"
```

也可以手动复制整个目录：

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R policy-memo-guide "${CODEX_HOME:-$HOME/.codex}/skills/"
```

## 仓库结构

```text
policy-memo-guide/
├── README.md
├── README.en.md
├── SKILL.md
├── test-prompts.json
├── agents/
│   └── openai.yaml
└── references/
    └── duke-policy-memo-guide.md
```

## 为什么这个 Skill 值得单独存在

policy memo 是一个很典型、但也很容易被模型“近似做错”的文类：

- 模型往往知道它的名字
- 但在真实任务里常常写成一般分析文
- recommendation 不够前置
- 信息不全时容易过度追问

这个 skill 的设计目标，就是把回答强行拉回到 memo 工作流：

- 先界定 audience 和 decision point
- 再决定是 full memo、outline 还是 options
- 再按倒金字塔方式生成文书

## 使用 Darwin Skill 做迭代优化

这个仓库不是一次性写出来的，而是借助 [`darwin-skill`](https://github.com/alchaincyf/darwin-skill) 做了多轮迭代优化。

优化方式不是“整体重写一遍”，而是更像一个小型 hill-climbing 流程：

1. 先评分
2. 每轮只改一个弱项
3. 改后重新评估
4. 用独立子 agent 跑 `with_skill / baseline`
5. 只有总分上升才保留，否则回滚

实际优化重点包括：

- 什么时候该追问，什么时候该先产出 outline
- 什么时候该直接 full memo
- memo 格式约束是否足够强
- edge case 下是否仍然保持 memo-first

这意味着它不是只在纸面上“写得工整”，而是经过独立对照和回退筛过一轮又一轮。

## 设计原则

- Audience first
- Recommendation early
- Outline before stall
- Memo over essay
- Clarity over theoretical vagueness

## 相关文件

- Skill 主体：[SKILL.md](./SKILL.md)
- UI 元数据：[agents/openai.yaml](./agents/openai.yaml)
- Duke 参考材料：[references/duke-policy-memo-guide.md](./references/duke-policy-memo-guide.md)
- Darwin 优化器：[darwin-skill](https://github.com/alchaincyf/darwin-skill)

## License

当前仓库尚未附带许可证文件。若你希望开放复用条款，建议补一个 `MIT` 或 `Apache-2.0`。

