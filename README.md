# OmniMemory

基于 markdown 文件树的跨会话 AI agent 持久记忆系统。

## 它解决什么问题

每次打开新的 AI agent 会话，agent 对你一无所知——不记得你的项目、偏好、之前踩过的坑。你需要反复解释同样的上下文。

OmniMemory 通过一组结构化的 markdown 文件解决这个问题。Agent 在 session 开始时阅读根指引文档，瞬间获取你的全局规则、项目上下文和工作进展，然后在 session 结束时自动更新记忆。

## 特点

- **零依赖**：纯 markdown + git，不需要 Docker、数据库或任何服务
- **Agent 无关**：Claude Code、Codex、Cursor、任何能读写文件的 agent 都能用
- **树形结构**：信息分层组织，agent 按需读取，不浪费 token
- **自生长**：遇到新场景时 agent 自动创建对应文档，系统越用越完善
- **版本控制**：每次更新自动 git commit，完整追踪变更历史
- **风格覆盖**：用户偏好存储在记忆中，agent 执行 skill 时直接应用，无需二次修改

## 目录结构

```
OmniMemory/
├── OMNI.md                 # 根指引文档 — Agent 唯一入口
├── global/                 # 全局共享知识
│   ├── preferences.md      # 用户风格偏好
│   ├── graveyard.md        # 失败经验记录
│   └── skills/             # 全局技能指南（按需创建）
├── workspaces/             # 各工作区的记忆（按需创建）
│   └── {workspace-id}/
│       ├── README.md       # 工作区规则 + 子文档索引
│       ├── progress.md     # 已完成进展 + TODO
│       └── ...             # 其他子文档按需创建
```

## 使用方法

1. Clone 本仓库到本机任意位置
2. 打开你的工作目录，启动任意 AI agent
3. 告诉 agent：

```
阅读 {OmniMemory 路径}/OMNI.md 接入记忆系统
```

Agent 会自动理解协议、加载上下文、在任务完成后更新记忆。

## 许可证

MIT
