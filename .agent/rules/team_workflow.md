# Project Workflow & Multi-Model Command Hierarchy Rule

## 1. Mandatory Pre-Implementation Workflow (標準工作流程)
Whenever the user requests any feature update, UI modification, or bug fix in this project:
1. **Ask Key Questions First (先問關鍵問題)**：Use `ask_question` (with recommended options prefixed with `(Recommended)`) to clarify requirements and propose higher-quality UX/pedagogical options.
2. **Write Detailed Implementation Plan (撰寫詳細行動計劃)**：Create or update `implementation_plan.md` in the artifacts directory with `RequestFeedback: true` and `UserFacing: true`.
3. **Wait for User Approval (等待審批)**：Do NOT begin modifying project code until the user approves the plan.
4. **Execute & Push to GitHub (執行並推送至 GitHub)**：Once approved, execute the changes, verify HTML/JS syntax and tag balance, commit, and push all updates to `origin/main`.

## 2. Multi-Model Command & Token Optimization Hierarchy (分級指揮與節流機制)
- **Captain (總隊長 - Gemini 4 Argon)**：
  - Focuses strictly on requirement clarification, architectural decisions, writing `implementation_plan.md`, final diff verification, and Git push.
  - Minimizes token consumption by delegating heavy file edits, code generation, and syntax testing on `index.html` to the Vice-Captain (`invoke_subagent` with `Model: 'flash'`).
- **Vice-Captain (副隊長 - Gemini 3.8 Flash High / `Model: 'flash'`)**：
  - Executes the approved `implementation_plan.md` tasks in a single cohesive pass, runs verification scripts, and reports back to the Captain.
  - May delegate simple read-only lookups to `Model: 'flash_lite'`.
- **2-Strike Escalation Rule (連續 2 次未達標接手機制)**：
  - If a subagent fails to meet the Captain's quality standards on its 1st attempt, the Captain sends 1 targeted correction message (`send_message`).
  - If the 2nd attempt still fails, the Captain immediately terminates the subagent and completes the work personally.
- **Plan B Mechanism (低額度接手機制)**：
  - If the user switches the main conversation model to **Gemini 3.8 Flash High** (e.g., when Argon quota is below 10%), Gemini 3.8 Flash High acts as the Supreme Commander following the exact same 4-step workflow above.
