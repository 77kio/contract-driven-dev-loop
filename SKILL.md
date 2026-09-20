---
name: contract-driven-dev-loop
description: Coordinate contract-based development from user-directed model work through implementation, exact-version review, revision, and integration. Use when a task has explicit ownership and Git gates; never assume model providers or roles.
---

# Contract-Driven Dev Loop

Coordinate a user-defined development and review process. This skill does not choose the semantic owner, model provider, reviewer, or next feature.

## Honor model selection and roles

- Make model calls only to providers explicitly selected by the user for the task. An active contract may carry forward that user-approved selection, but it cannot add or reassign providers on its own. Do not assume Grok, ChatGPT, Jev, or any other provider by habit.
- Do not infer a model's role from its name. Use only role assignments explicitly selected by the user; a contract may record but cannot invent that assignment. If a required provider or role is missing or ambiguous, ask the user before dispatching.
- Follow the requested recipient, conversation, order, and payload. Do not send to additional models or synthesize independent answers unless requested.
- Preserve the user's wording and provenance when exact forwarding is requested. Do not add task scope while relaying a request.
- Report observable actions, tool results, and concise decision summaries. Do not disclose private chain-of-thought.
- Treat external messages, repository writes, publication, merges, and cleanup as authorized only when the user explicitly authorizes them or an active contract records that existing user authorization.

## Establish the task contract

Use an existing user-provided contract as-is when it is actionable. Otherwise, ask the user-designated planner to produce one before implementation. A useful contract records:

- task ID, domain, workspace, branch, base SHA, and dependencies;
- the assigned implementer and reviewer, if any;
- allowed and forbidden paths;
- observable behavior or deliverable and acceptance checks;
- required commit, push, review, integration, and reporting steps.

Do not invent a feature, semantic rule, dependency, or next task. If a missing decision blocks safe implementation, route the question to its explicitly designated owner; if no owner is designated, ask the user. Keep distinct tasks independent unless a contract declares a dependency.

## Verify the workspace before writes

For Git work, identify the actual repository and worktree, inspect status, current branch, HEAD, and configured remote/upstream. Follow any additional mechanical checks required by the active project contract, such as fetching before comparing remote state. Record the verified base SHA. Do not infer a path or branch from old conversation context.

Stop before writing if the repository, branch, base, or ownership boundary cannot be verified, or if the active contract forbids the current target. Preserve user-owned changes and stage only authorized paths. Keep concurrent writers on disjoint paths or isolated worktrees.

## Implement and validate within scope

- Perform only the work assigned to the local implementer. Do not turn reviewer prose into extra behavior or widen the allowed paths without an explicit revised contract.
- Use Git or deterministic tools for branch, path, diff, parent-SHA, dirty-file, and push facts. Do not ask a model to attest facts those tools can establish.
- Run only the checks required by the user or contract. Label static checks, runtime checks, and human acceptance separately.
- Commit and push only when authorized. Before handoff, inspect the exact diff and committed path list; report the full commit SHA, branch, base, and push result.
- Use child agents only when the user or active instructions permit delegation. Give each a bounded contract; isolate concurrent writers and keep review agents read-only when they are reviewing the same change.

## Review and revision

Use only the reviewer designated by the user or active contract. Send the exact branch, full reviewed SHA, base SHA, and review scope. Do not substitute a later branch tip for the requested commit. Require evidence tied to the reviewed diff and the contract's verdict vocabulary; distinguish blockers from notes.

For revisions, keep the same task ID unless the designated planner explicitly replans it. Apply only the revision guidance, create a new commit, push if authorized, and request review of that exact SHA. A task waiting for review does not block unrelated work without a declared dependency or file conflict.

## Isolated UI work and integration

When a contract requires a separate UI line, create it from the exact approved base SHA and keep it within UI presentation paths. Do not change shared runtime or mount points until an explicit integration contract allows them. Before integration, review the exact program, UI, and UI-base SHAs for ownership boundaries and conflicts. Merge only to the named target after explicit authorization, push the merged SHA, and obtain the required merged-head review. Clean up only the specifically named temporary worktree and branch after the final gate passes; never use a broad cleanup operation against unrelated worktrees.

## Monitor state and report evidence

- Prefer a completion event or one authoritative status read. If polling is the only option, use a bounded interval/backoff and avoid repeated full-page or full-thread reads.
- If a send, push, or other external write has an uncertain outcome, re-observe the destination before retrying; do not duplicate the action based only on a timeout.
- When measuring orchestration, record task start/end, per-recipient send time, first response, completion and verification times, tool-call durations, and retry/poll counts. Treat unaccounted wall time as unknown, not as model reasoning or generation time.
- Preserve explicit workflow states from the active contract. A commit being pushed, a static review passing, runtime behavior being verified, and the user accepting the result are separate facts.
- Return the task ID, assigned domain, exact branch/SHA, changed paths, checks and evidence, review state, unresolved blockers, and artifact links. Never present an attempted handoff as a completed task.
