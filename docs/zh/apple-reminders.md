# 可选：从 Apple 提醒事项导入（中文）

如果你原来的待办都在 iPhone / Mac 的「提醒事项」里，可以一次性搬进 Notion 的速记，之后再按正常流程整理。

搬完以后，建议**以后直接在 Notion 速记里记**，不要两边同时用。两边同时记，很快就会对不上。

作者自己就是用这个方法搬家的：在 Mac 上用一条命令导出整个提醒事项数据库，交给 Claude。**所有列表、顺序、分组、子任务、备注、截止日期都在**，不会漏条，也不会打乱顺序。

需要：一台登录了同一个 Apple ID 的 Mac，以及能读文件、跑代码分析的 Claude（比如 Claude App 里可以上传文件的对话）。iPhone 上的提醒事项只要开了 iCloud 同步，Mac 上就有同样的数据。

## 第 1 步：给「终端」开权限

提醒事项的数据受 macOS 保护，终端默认读不到。

1. 打开 **系统设置 → 隐私与安全性 → 完全磁盘访问权限**
2. 点左下角 **＋**，在「应用程序 → 实用工具」里选 **终端**，打开开关
3. **按 `Cmd + Q` 完全退出终端，再重新打开**。不退出的话权限不生效，窗口显示「Restored session」也不算重新打开

导出完以后可以把这个权限关掉。

## 第 2 步：运行导出命令

在终端粘贴下面整段，按回车：

```bash
mkdir -p ~/Desktop/reminders_export && cd ~/Library/Group\ Containers/group.com.apple.reminders/Container_v1/Stores && for f in Data-*.sqlite; do sqlite3 "$f" ".backup '$HOME/Desktop/reminders_export/$f'"; done && cd ~/Desktop && zip -rq reminders_export.zip reminders_export && echo 完成
```

看到「完成」后，桌面上会多出一个 **`reminders_export.zip`**。这就是要交给 Claude 的文件：一个压缩包，里面是几个 `Data-*.sqlite`，提醒内容在体积最大的那个里。

这条命令只是**复制一份**数据（用 `sqlite3 .backup`，提醒事项开着也没关系），不会改动你的提醒事项。

**遇到问题：**

| 终端显示 | 原因 | 怎么办 |
|---|---|---|
| `zsh: no matches found: Data-*.sqlite` | 终端没权限，看不到文件 | 回到第 1 步，确认加了权限并 `Cmd + Q` 重开终端 |
| 输入 `ls` 显示 `Operation not permitted` | 同上 | 同上 |
| 提示符从 `~` 变成了 `Stores` | 命令进入了提醒事项的数据文件夹，这是正常的 | 不用管；输入 `cd ~` 或重开终端就回去了 |

## 第 3 步：把压缩包交给 Claude

把 `reminders_export.zip` 上传到项目对话，然后发：

> 这是我 Mac 上提醒事项的数据库备份（Core Data 的 SQLite）。请用代码读出所有**未完成**的提醒：
> - 条目在 `ZREMCDREMINDER`（`ZCOMPLETED=0`、`ZMARKEDFORDELETION=0`），列表在 `ZREMCDBASELIST`，子任务看 `ZPARENTREMINDER`，分组在 `ZREMCDBASESECTION`
> - 列表顺序看 `ZREMCDOBJECT.ZLISTIDSMERGEABLEORDERING_V2`；列表内顺序看 `ZSORTINGSTYLE`：手动排序用 `ZREMINDERIDSMERGEABLEORDERING_V2_JSON`，按创建日期就按 `ZCREATIONDATE` 排
>
> 先告诉我每个列表有几条，再在 Notion 执行页下建一个「提醒事项（原始）」页面，按 app 里的列表顺序、条目顺序原封不动写进去：每个列表一个标题，分组用小标题，每条一个勾选框，子任务缩进。一个字都不要改。

## 第 4 步：核对，再导入速记

先对照手机或 Mac 上的提醒事项，看看「提醒事项（原始）」页面里条数、顺序对不对。没问题后再说：

> 把「提醒事项（原始）」里的条目逐条写进速记，标题照抄，有备注的放进正文，有截止日期的填进「计划日期」。

原始页面留着当底稿，以后想对照随时能看。

**隐私提醒：** 这个数据库里有你**所有**的提醒，包括已经完成的。只发给你自己的 Claude，用完可以把桌面上的 `reminders_export` 文件夹和压缩包删掉。

## 导入以后

导进来的条目都在速记里。说一句「整理执行页」，Claude 会逐条用卡片问你归到哪个大类。条目多的话，可以分几次整理，每次最多问 4 条。
