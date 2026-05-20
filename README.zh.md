# 工作日志记忆 Skill

[English](README.md) | 简体中文

**在细节消失之前，先记住你到底做了什么。**

Worklog Skills 是一个 Codex skill：把很乱的日常工作碎片，整理成可 review 的工作记忆、日报，以及以后写周报、转正、晋升、述职和绩效总结时能用的证据。

## 问题

工作总结经常不是输在“不会写”，而是输在写之前。

1. **想不起来自己到底做了什么。** 到下班、周五或月底才开始回忆，只能从聊天记录、会议、commit、工单和零散印象里倒推。
2. **过程细节很快消失。** 最开始的思路、试错、为什么改方案、谁给过输入、最后怎么迭代出来，过几天就很难还原。
3. **最终结果显得比真实工作量小。** 调研、排查、沟通、返工、判断和取舍，如果当时没留下过程证据，述职和工作总结里就显得很薄。

这个 skill 适合那些本来就能顺手记录几句的场景：地铁上 5 分钟、等外卖的时候、开完会走回工位、下班前快速复盘，或者刚和别人聊完有新判断的时候。

## 解决方案

先把 rough notes 扔出来。skill 会先整理成一版方便人校对的 cleaned draft，确认之后才写正式报告。

| 问题 | skill 做什么 |
| --- | --- |
| “我想不起来今天干了什么。” | 保存 raw notes，并把碎片整理成可 review 的工作 / 过程证据。 |
| “我说着说着才想起一个细节。” | 关系明确时，把后面想起的细节挪回相关任务附近。 |
| “人名、项目名、公司名不一致。” | 根据轻量历史上下文对齐常见专用名词。 |
| “模型可能猜错。” | 不确定修正会标出来，而不是偷偷改写。 |
| “有些内容是八卦、social 或环境信息。” | 把工作证据和 social / 情绪 / 环境上下文分开。 |
| “我要准备转正、述职或年报。” | 在确认后的日报后，给可选的 goal-relative comment。 |

整体流程是 review-first：

```text
raw notes
  -> rough cleaned review draft
  -> 用户明确确认
  -> 日报 / 周报素材 / 述职证据
  -> 可选 goal-relative comment
```

这个 skill **不负责语音转文字**。你可以用任何输入法、听写或笔记工具，最后把 raw text 贴给 Codex。

## 五个核心特点

### 1. 轻量专用名词对齐

skill 可以根据上下文修正常见识别错误，比如同事名字、项目名、公司名、工具名和反复出现的概念。

上下文优先级：

```text
已确认的日报 / 最终记录
  > 明确提供的 glossary-like 上下文
  > raw notes 作为弱证据
```

弱匹配或只来自 raw notes 的匹配要标注不确定。这个 skill 不要求、也不承诺维护一套持久 glossary 系统。

### 2. 粗糙半结构化 cleaned draft

cleaned draft 不是漂亮日报，而是方便你校对和补充的粗糙中间稿。

常见 lanes：

- Work / process evidence
- Communication / collaboration context
- Non-work / social / environment context
- Uncertain items
- Consistency corrections

### 3. 不确定标注

如果某个修正、人名匹配、日期、原因或结论不确定，就明确标出来，方便你 review，而不是藏在流畅文字里。

### 4. 工作和非工作上下文分开

真实碎碎念里会混着工作、social、情绪、八卦、环境信息和个人反思。skill 会把这些分开，避免混进正式工作报告；但有用的环境信息仍然可以帮助后续建议。

### 5. 根据目标给 comment

日报确认生成之后，如果你有明确目标，比如转正、季度述职、年报或晋升准备，skill 可以给一段简短的 goal-relative comment。

comment 会区分：

- 今天观察到的 evidence；
- assessment；
- risk / gap；
- suggested next action。

它不能推断“能不能转正”、manager 期待或没有证据支持的私人信息。如果没有目标，就省略，或标注 `Goal: not provided`。

## 安装

把 skill 文件夹复制到 Codex skills 目录：

```text
worklog-daily-report/
```

项目内安装：

```text
.codex/skills/worklog-daily-report/
```

Windows 用户全局安装：

```text
%USERPROFILE%/.codex/skills/worklog-daily-report/
```

然后对 Codex 说：

```text
帮我把这些 raw notes 整理成 daily worklog。我的目标是转正。
```

它应该先给你一版 cleaned review draft，并等待你确认。

## 仓库结构

```text
worklog-daily-report/
  SKILL.md
  references/
    templates.md
  agents/
    openai.yaml
```

## 开源安全

skill 本身是通用的，但不要把私人 worklog 数据一起开源。

避免提交公司名称、老板/同事姓名、保密项目细节、薪酬信息、交易/策略细节和个人绩效记录。

## License

MIT
