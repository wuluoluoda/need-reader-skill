---
name: need-reader-clear
description: "Marks completed Markdown Need cards. Use when a document contains Need blocks with done: / done： markers, or when the user asks to clear, close, mark done, or turn red Need balls green."
disable-model-invocation: true
---

# Need Reader Clear

处理 Markdown Need 卡片里的 `done:` / `done：`。

规则：
---
1. 只处理 Need 卡片标题：`**🔴 Need-xx | ...**` 或 `**🟢 Need-xx | ...**`。
2. 块内出现 `done:` / `done：` 时，只把该 Need 标题的 `🔴` 改成 `🟢`，并删除这个 `done` 标记。
3. 父子 Need 独立完成：子 Need 的 `done` 不会完成父 Need；父 Need 的 `done` 不会完成子 Need。
4. 判断父块时，不把嵌套子 Need 块里的 `done` 算作父块的 `done`。
5. 不改非 Need 区域的红球，例如表格里的严重程度 `🔴`。
6. 如果同一个块里还有未处理的 `need:`，先保留并提示应先运行 `need-reader`。
7. 处理完后补或更新 `## Need 清理清单`。

输出格式：
---
```md
## Need 清理清单

| 编号 | 结果 |
| --- | --- |
| Need-01 | 🟢 已完成 |
| Need-01.1 | 保持 🔴，未见 done 标记 |
```

自检：
---
* 所有 `done:` / `done：` 都处理或说明了原因。
* 只改 Need 标题里的球。
* 父子 Need 没有级联完成。
