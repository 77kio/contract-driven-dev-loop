# Contract-Driven Dev Loop

Codex Skill for coordinating user-directed development work through explicit task contracts, bounded implementation, exact-version review, revision, and integration.

## 中文

`contract-driven-dev-loop` 帮助按明确任务合同组织开发与审阅：确认工作区和版本、限定路径、实现和机械核验、按精确 SHA 复核，并在需要时完成修订与集成。

**模型调用没有默认值。** 用户必须指定调用哪个模型及其角色；任务合同只能记录用户已选的分配，不能自行增加或重分配模型。还要遵循用户指定的会话和调用顺序；信息缺失时先询问。

此 Skill 不替用户决定功能语义或下一项任务，也不会把静态审阅说成运行验证或用户验收。合并、推送、外部发送和清理必须有用户明确授权；任务合同只能记录既有授权。

调用方式：`$contract-driven-dev-loop`

## English

`contract-driven-dev-loop` coordinates development and review through explicit contracts: verify the workspace and version, keep changes within scope, implement and mechanically validate, review an exact SHA, then revise or integrate when authorized.

**There are no default model providers or roles.** The user must select the model and its role; a task contract may record that choice but cannot add or reassign models on its own. Follow the user's conversation and call order, and ask when required information is missing.

The skill does not choose feature semantics or the next task, and it keeps static review, runtime verification, and user acceptance distinct. Merge, push, external communication, and cleanup require explicit user authorization; a task contract may only record authorization already granted.

Invoke it with `$contract-driven-dev-loop`.

## Package

- `SKILL.md` — operational instructions.
- `agents/openai.yaml` — Codex skill-list metadata.
