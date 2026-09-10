# Hermes 官方命令对照表（用于替换教程中的过时/虚构命令）

本表基于 Hermes Agent 官方 skill 文档。当你修改 /root//hermes-agent-guide/ 下的教程时，
遇到左侧的过时/虚构命令，就替换为右侧的官方真实命令。**只改命令本体，不改示例输出、
说明文字的结构；除非命令确实不存在，否则保留命令行的教学意图。**

## CLI 命令

| 过时/虚构 | 官方真实 | 说明 |
|-----------|---------|------|
| `hermes migrate openclaw` | `hermes claw migrate` | 从 OpenClaw 迁移 |
| `hermes migrate`（裸命令） | `hermes config migrate` | 更新配置 |
| `hermes changelog` | `hermes --version` 或查看文档 | 官方无 changelog 子命令 |
| `hermes restart` | `hermes gateway restart` | 重启网关；若是容器/服务场景则保留 |
| `hermes setup --xxx` | `hermes setup [section]` 或用 `hermes config set` | setup 无 --models-only 等标志 |
| `hermes doctor --env/--config/--models` | `hermes doctor` | doctor 只有 --fix |
| `hermes status --resources/--session/--skills/--cost/--memory` | `hermes status` | status 只有 --all |
| `hermes config show` | `hermes config` | 直接查看 |
| `hermes config validate` | `hermes config check` | 检查缺失/过时配置 |
| `hermes config migrate` | `hermes config migrate` | 保留 ✓ |
| `hermes cache clear` | 官方无 | 删除或改 `hermes update` |
| `hermes history` | `hermes sessions list` | |
| `hermes export` | `hermes sessions export` | |

## hermes chat → hermes sessions

| 过时 | 官方 |
|------|------|
| `hermes chat list` | `hermes sessions list` |
| `hermes chat show <id>` | `hermes sessions browse`（交互） |
| `hermes chat resume <id>` | `hermes --resume <id>` |
| `hermes chat delete <id>` | `hermes sessions delete <id>` |
| `hermes chat search "kw"` | `hermes sessions browse` 或自然语言检索 |
| `hermes chat export <id>` | `hermes sessions export <file>` |
| `hermes chat cleanup --older-than` | `hermes sessions prune --older-than N` |

## hermes model

| 过时 | 官方 |
|------|------|
| `hermes model list` | `hermes model`（交互式选择器） |
| `hermes model current` | `hermes model` |
| `hermes model use <name>` | `hermes model` 交互选择 |
| `hermes model test` | `hermes model` 或 `hermes doctor` |
| `hermes model add` | `hermes config set model.*` |
| `hermes model pricing` | `hermes insights` |
| `hermes model benchmark` | 官方无，删除或改手工对比 |
| `hermes model info` | `hermes config` 查看 |

## hermes skills

| 过时 | 官方 |
|------|------|
| `hermes skills list` | `hermes skills list` ✓ 保留 |
| `hermes skills show <name>` | `hermes skills inspect <name>` |
| `hermes skills search "kw"` | `hermes skills search kw` ✓ 保留 |
| `hermes skills install <name>` | `hermes skills install <name>` ✓ 保留 |
| `hermes skills enable/disable <name>` | `hermes skills config`（交互式按平台启用/禁用） |
| `hermes skills update <name>` | `hermes skills update`（全局更新过时技能） |
| `hermes skills check` | `hermes skills check` ✓ 保留 |
| `hermes skills delete <name>` | `hermes skills uninstall <name>` |
| `hermes skills edit <name>` | 直接编辑技能目录下的 SKILL.md 文件 |
| `hermes skills export <name>` | 直接 `tar -czf` 打包技能目录，或改写入说明 |
| `hermes skills import ./x.tar.gz` | 解包 tar.gz 到 `~/.hermes/skills/`，或 `hermes skills install` |
| `hermes skills hub` | `hermes skills browse` |
| `hermes skills hub --browse` | `hermes skills browse` |
| `hermes skills copy A B` | 手动复制技能目录 |
| `hermes skills deps` | 官方无，删除或改手动说明 |
| `hermes skills reviews` | 官方无，删除或改说明 |
| `hermes skills doc` | 官方无，技能文档就是 SKILL.md |
| `hermes skills validate` | 官方无，改 `hermes skills inspect` |
| `hermes skills test` | 官方无，改说明"实际调用工具验证" |
| `hermes skills migrate --from <x>` | `hermes claw migrate`（OpenClaw）或手动转换 |
| `hermes skills archive` | `hermes skills uninstall`（或说明归档=移到备份目录） |
| `hermes skills publish PATH` | `hermes skills publish PATH` ✓ 保留 |

## hermes tools

| 过时 | 官方 |
|------|------|
| `hermes tools list` | `hermes tools list` ✓ 保留 |
| `hermes tools show <name>` | 官方无，用 `hermes tools list` |
| `hermes tools test` | 官方无，改 `hermes tools list` 或实际调用 |
| `hermes tools enable/disable` | `hermes tools enable/disable NAME` ✓ 保留 |
| `hermes tools enable --permanent` 等 | 官方无该标志，去掉 |

## hermes gateway

| 过时 | 官方 |
|------|------|
| `hermes gateway start` | `hermes gateway run`（前台）或 `hermes gateway start`（服务，官方有）|
| `hermes gateway stop` | `hermes gateway stop` ✓ 官方有 |
| `hermes gateway list` | `hermes gateway setup` 或 `hermes gateway status` |
| `hermes gateway config telegram --token` | `hermes gateway setup`（交互配置平台） |
| `gateway start`（裸命令） | `hermes gateway run` 或 `hermes gateway start` |
| `gateway config`（裸命令） | `hermes gateway setup` |

## hermes cron

| 过时 | 官方 |
|------|------|
| `hermes cron validate` | 官方无，改 `hermes cron list` 查看 |
| `hermes cron logs` | 官方无，改 `hermes cron status` 或查看 `~/.hermes/logs/` |
| `hermes cron enable <job>` | `hermes cron resume <job>` |
| `hermes cron disable <job>` | `hermes cron pause <job>` |
| `hermes cron list/status/run/rm` | ✓ 官方有 |

## 斜杠命令（会话内）

| 过时 | 官方 |
|------|------|
| `/compact` | `/compress` (官方) |
| `/export` | `/save` (官方) |
| `/private` | 官方无，删除该命令 |
| `/public` | 官方无，删除 |
| `/system` | 官方无，删除或改说明 |
| `/temp <model>` | 官方无，改 `/model` 切换 |
| `/search "kw"` | 非斜杠命令，改为自然语言让 Agent 检索历史会话 |
| `/memory show/add/remove/edit/compact/clear` | 官方 `/memory` 只有 pending/approve/reject/approval；管理记忆让 Agent 用 memory 工具（自然语言），查看用 `hermes memory status` |
| `/refresh` | 官方无（若在"/刷新记忆"语境），删除 |
| `/model <name>` | `/model [name]` ✓ 官方有 |
| `/clear` | `/clear` ✓ 官方有 |
| `/help` | ✓ |
| `/undo` `/retry` | ✓ 官方有 |
| `/title` | ✓ 官方有 `/title [name]` |
| `/compress` | ✓ 官方有 |
| `/usage` | ✓ 官方有 |

## 路径

| 过时 | 官方 |
|------|------|
| `~/.hermes/database/hermes.db` 或 `~/.hermes/database/` | `~/.hermes/sessions/sessions.db` 或 `~/.hermes/sessions/` |
| `~/.hermes/MEMORY.md` | `~/.hermes/memories/MEMORY.md` |
| `~/.hermes/USER.md` | `~/.hermes/memories/USER.md` |
| `~/.hermes/memory/` | `~/.hermes/memories/` |
| `~/.config/hermes/config.yaml` | `~/.hermes/config.yaml` |
| `~/.hermes/data/conversations.db` | `~/.hermes/sessions/` |

## 重要原则

1. **只替换命令本体**，保留命令行教学意图。命令后的`# 注释`可调整。
2. **不破坏示例输出**。示例输出是虚构的教学演示，除非它自身包含了过时命令名，否则不必改。
3. **对官方完全没有的命令**（如 export/import/edit/deps/reviews/doc/validate/test 这些 skills 子命令），用最接近的官方等价替换，或改写为说明性文字（如"直接编辑 SKILL.md"、"tar 打包目录"），不要生搬硬套一个不存在的命令。
4. **保留目录标题结构**。例如 `### 6.2 hermes skills show <name>` 这个标题里的 `skills show` 也要一并改为 `skills inspect`，保持标题与内容一致。
5. 涉及 `/memory`、`/search` 等，先判断上下文——如果是文档里演示的"对话输入"，改为自然语言让 Agent 完成；如果是命令行演示，按表替换。
6. 命令 `hermes chat -q "..."`、`hermes -c "..."`、`hermes --model`、`hermes --workspace`、`hermes --private`、`hermes --fresh` 等顶层 flag 也是过时的，分别对应：
   - `hermes -c "..."` → `hermes chat -q "..."`
   - `hermes --model X` → `hermes chat -m X`
   - `hermes --workspace .` → `hermes -w`（worktree 模式）或删除（官方没有工作目录 flag）
   - `hermes --provider X --model Y` → `hermes chat -m Y --provider X`
   - `hermes --private` → 删除（官方无隐私模式 flag）
   - `hermes --fresh` → 删除（官方无）