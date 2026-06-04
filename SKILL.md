---
name: "need-reader"
description: "Processes 'need:' / 'need：' prompts embedded in Markdown. Invoke when a document contains inline need notes that must be classified, answered, and separated from正文."
disable-model-invocation: true
---

# Need Reader

处理 Markdown 里的 `need:` / `need：`。

触发：
---
- 文档里出现 `need:` / `need：`
- 用户想把 `need` 和正文分开
- 用户会在已有 `Need` 块里继续补 `need:` / `need：`

规则：
---
1. 每个 `need:` / `need：` 都必须被替换，不能留在原句里。
2. 顶层 `need` 在原位置展开成独立卡片，不要揉进正文。
3. 顶层卡片保留红球，`Need-` 前必须加 `🔴 `，默认格式如下：

```md
---

> **🔴 Need-01 | 标题** | 原 prompt（...）
>
> 一句自然语言说明。
>
> - 要点 1
> - 要点 2

```
 4. 如果新的 `need:` / `need：` 出现在已有 Need 块里，就在那个位置展开成子卡片，不要移到父块末尾，也不要平铺到外层。
 5. 子卡片用块内块表示，`Need-` 前必须加 `🔴 `，默认格式如下：
```md
>>> **🔴 Need-01.1 | 追问：一句话** | 原 prompt（...）
>>>
>>> - 要点 1
>>> - 要点 2

```
 6. 第二版及之后保持简短，不写"类型"、"处理状态"、"原问题"这类标签。
 7. 只有确实需要时才补"证据"、"阅读顺序"、"待确认"。
 8. 证据不足时写"无法确认"或"待确认"，不要编造。
 9. 处理完后补一份 ## Need 处理清单。
 10. Need 标题行后追加 `| 原 prompt（...）`，内容照抄 `need:` / `need：` 冒号后的原始文本；标题可自行提炼，不要求与原 prompt 一致。
 11. 对“做什么”类 `need:` / `need：`，即使已完成正文改写，也要在原位置保留 Need 块，记录原 prompt 和处理结果；不要只在清单里记录。
## 自检：
 * 所有 `need:` / `need：` 都处理了
 * 红球还在
 * 顶层 need 在原位置展开
 * 第二层是块内块
 * 没有把意图字面标签写回去
## 示例：
```md
原文：
说明这条包链路。need: 解释成大白话。

处理后：
说明这条包链路。

---

> **🔴 Need-01 | 解释成大白话** | 原 prompt（解释成大白话。）
>
> 这条链路...

```
```md
原文：
> **🔴 Need-01 | 谁在决定 shardId**
> 这里先给出一轮解释。need: 为什么 Mapper 不自己算？

处理后：
> **🔴 Need-01 | 谁在决定 shardId**
> 这里先给出一轮解释。
>
>>> **🔴 Need-01.1 | Mapper 不自行计算的原因** | 原 prompt（为什么 Mapper 不自己算？）
>>>
>>> - 因为 Mapper 只能...
>>> - 真正决定 shardId 的还是执行器。

```
