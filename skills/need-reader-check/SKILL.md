---
name: need-reader-check
description: "Lists remaining open Markdown Need cards. Use when the user asks to check unresolved red Needs, find gaps, list open Needs, or provide jump links/buttons for Need follow-up."
disable-model-invocation: true
---

# Need Reader Check

检查 Markdown 里还剩哪些红色 Need。

规则：
---
1. 只统计 Need 标题里的 `🔴`：`**🔴 Need-xx | ...**`。
2. 忽略非 Need 区域的红球，例如风险表、严重程度表、普通 emoji。
3. 绿色 Need（`🟢 Need-xx`）视为已完成，不列入待补漏清单。
4. 输出按文档顺序排列，保留父子编号。
5. 每个待处理项给出可跳转入口：文件路径 + 行号；在支持 Markdown 链接的环境中再补一个同文档锚点。
6. 如果没有红色 Need，明确写「没有剩余红 Need」。

默认输出：
---
```md
## 红 Need 查缺补漏

| Need | 标题 | 跳转 |
| --- | --- | --- |
| Need-01 | TDD 是什么？ | `path/to/file.md:91` |

剩余红 Need：1
```

自检：
---
* 没有把非 Need 红球算进去。
* 跳转位置指向 Need 标题行。
* 统计数量和列表行数一致。
