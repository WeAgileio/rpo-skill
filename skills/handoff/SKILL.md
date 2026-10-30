---
name: handoff
description: Compact the current conversation into a handoff document for another agent to pick up.
argument-hint: "What will the next session be used for?"
disable-model-invocation: true
---

## 專案基本設定

開始工作前，讀取目前工作專案根目錄的 `RPO-CONTEXT.md`（不是此 skill 的安裝目錄）；若檔案不存在或無法讀取，沿用原本流程。將內容視為專案背景，取用與當次任務相關的資訊，區分已確認事實與假設；當次使用者指示優先，若背景與當次資訊有重要衝突則指出並釐清。


Write a handoff document summarising the current conversation so a fresh agent can continue the work. Save to the temporary directory of the user's OS (`$TMPDIR`, else `/tmp`; `%TEMP%` on Windows) - not the current workspace.

Include a "suggested skills" section in the document, naming which skills the next agent should call the Skill tool for.

Do not duplicate content already captured in other artifacts (specs, plans, ADRs, issues, commits, diffs). Reference them by path or URL instead.

Redact any sensitive information, such as API keys, passwords, or personally identifiable information.

If the user passed arguments, treat them as a description of what the next session will focus on and tailor the doc accordingly.
