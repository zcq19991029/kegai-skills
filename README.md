# kegai-skills

面向高职机电一体化、电气自动化、工业机器人等专业课程的课改材料 Skill。它用于撰写完整教案、80 分钟教学设计、实训工单和复习课材料，先核对信息，再依据课程资料写作和自检。

仓库中只有通用规则：[SKILL.md](SKILL.md) 和 [详细范式与验收规则](references/material-spec.md)。**不含具体课程资料、学校 Word 模板或学生信息**；使用时请在自己的工作区提供这些文件。

## 最简单的安装方法：直接让 AI 安装

在有网络和本地文件访问能力的 Codex 或 Claude Code 中，直接发送下面这段话即可。只给仓库名 `zcq19991029/kegai-skills` 也可以，但附上完整地址与目标名称更容易核对结果。

> 请从 https://github.com/zcq19991029/kegai-skills 安装 `vocational-mechatronics-lesson-materials` Skill 到我的个人 Skills 目录。请保留 `SKILL.md` 和 `references/material-spec.md` 的相对位置；安装后检查两个文件均可读取，并告诉我如何调用。

在 Codex 中也可以先输入 `$skill-installer`，再发送上面的安装要求。安装是否需要额外确认，取决于你使用的软件权限设置。Codex 的官方说明支持从其他仓库安装 Skill；Claude Code 支持个人和项目级 Skill。[Codex Skills 文档](https://learn.chatgpt.com/docs/build-skills) · [Claude Code Skills 文档](https://code.claude.com/docs/en/skills)

## 手动安装

将**整个仓库目录**放入下列位置之一。安装后应能找到 `.../vocational-mechatronics-lesson-materials/SKILL.md` 和同目录下的 `references/material-spec.md`。不要只复制 `SKILL.md`，否则详细规则无法加载。

| 使用范围 | Codex | Claude Code |
| --- | --- | --- |
| 所有本地项目 | `~/.agents/skills/vocational-mechatronics-lesson-materials/` | `~/.claude/skills/vocational-mechatronics-lesson-materials/` |
| 当前项目 | `<项目根目录>/.agents/skills/vocational-mechatronics-lesson-materials/` | `<项目根目录>/.claude/skills/vocational-mechatronics-lesson-materials/` |

部分 Codex 安装器使用 `$CODEX_HOME/skills`（默认 `~/.codex/skills`）作为个人 Skill 目录；使用内置 `$skill-installer` 时，以安装器实际写入的位置为准。上述 `~/.agents/skills` 是 [Codex 官方文档](https://learn.chatgpt.com/docs/build-skills) 列出的个人目录，Claude Code 的两个目录见其 [Skills 文档](https://code.claude.com/docs/en/skills)。

### 方法一：Git 克隆

先创建目标目录，再克隆本仓库。下面以**个人安装**为例；若只想在一个项目中使用，把目标路径换成上表中的项目级路径。

Windows PowerShell，安装到 Codex：

```powershell
New-Item -ItemType Directory -Force "$HOME/.agents/skills" | Out-Null
git clone https://github.com/zcq19991029/kegai-skills.git "$HOME/.agents/skills/vocational-mechatronics-lesson-materials"
```

Windows PowerShell，安装到 Claude Code：

```powershell
New-Item -ItemType Directory -Force "$HOME/.claude/skills" | Out-Null
git clone https://github.com/zcq19991029/kegai-skills.git "$HOME/.claude/skills/vocational-mechatronics-lesson-materials"
```

macOS、Linux 或 WSL，安装到 Codex：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/zcq19991029/kegai-skills.git ~/.agents/skills/vocational-mechatronics-lesson-materials
```

安装到 Claude Code 时，把上面两处 `~/.agents/skills` 改为 `~/.claude/skills`。以后在克隆得到的目录中运行 `git pull` 即可获取仓库更新。

### 方法二：下载 ZIP

打开仓库页面，点击 **Code → Download ZIP**，解压后把文件夹改名为 `vocational-mechatronics-lesson-materials`，再复制到上表中的个人或项目目录。确认文件夹内直接有 `SKILL.md`，而不是多套一层目录。

## 准备课程资料并使用

1. 为课程准备单独的“XX课程课改”文件夹，放入教学进度表、课程标准、大纲、教材、教学PPT和单双周课表。若有学校的教案或教学设计 Word 模板，也放在工作区并告诉 AI 路径。
2. 在课程工作区打开 Codex 或 Claude Code。告诉它使用本 Skill；缺少必要信息时，Skill 会先列出一份补充清单。授课任务和核心知识点若要从进度表确定，直接说明“请先按课表计算每次80分钟的周次与知识边界，再按进度表分配”。同一天连上4学时应拆成两次各80分钟；两班进度相同时可指定一个代表班级共用内容。
3. 核对成品的班级、地点、课次与时长。提供了原始 Word 模板时，要求继续沿用原字体、字号、颜色、表格和页边距。

第一次课可用课程说明和生活案例导入，无须虚构本课程旧知。PPT按进度选用：一份PPT可能分多次讲，一次课也可能覆盖几个小节。修改成品后只保留一个最新文件，不留多个带版本后缀的副本。

Codex 调用示例：

```text
$vocational-mechatronics-lesson-materials
课程名称：单片机应用技术；授课班级：XX机电1班；课时：2学时（80分钟）；
授课地点：教学楼A101（机房）；文档类型：教学设计；
授课任务和核心知识点：请按“单片机课改”文件夹的教学进度表第1次课确定。
请使用我提供的机房教学设计 Word 模板，先核对资料，再生成可编辑文件。
```

Claude Code 可将首行改为 `/vocational-mechatronics-lesson-materials`。两款工具也可在任务与 Skill 描述匹配时自动选用；如果没有自动选中，直接点名调用。Codex 的显式调用方式见 [官方文档](https://learn.chatgpt.com/docs/build-skills)，Claude Code 的斜杠调用方式见 [官方文档](https://code.claude.com/docs/en/skills)。

## 常见检查

- **提示找不到 Skill**：检查安装目录、`SKILL.md` 是否位于该目录第一层，以及文件夹名是否为 `vocational-mechatronics-lesson-materials`。Codex 若未显示新 Skill，可重启后再试。
- **只能看到一部分规则**：检查 `references/material-spec.md` 是否与 `SKILL.md` 一起复制。
- **内容与课程不符**：确认当前工作区里有对应课程资料，并在指令中写清课次、班级、场景和模板路径。
