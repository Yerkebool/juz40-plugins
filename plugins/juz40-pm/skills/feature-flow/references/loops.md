# Loops: when discovery goes back

Discovery is not a straight line. Signals from the stages, from design, from QA and from people send it back. Go back to the nearest stage that can fix the problem. Never restart from zero by default.

## Where each signal sends you

| Signal | Comes from | Back to | Kept |
|---|---|---|---|
| The problem is not what we thought: another role suffers, the cause is elsewhere | grilling, metric baseline, ПБР, owner | **Brainstorm**, problem exploration | Facts and sources; the direction is re-checked |
| The baseline shows the problem is small or absent | metric | **Stop** and ask the owner: reframe (brainstorm), park, or drop | Brief as a record |
| The direction is impossible or too expensive: backend, content, legal | grilling, backend, ПБР | **Brainstorm**, solution ideation, starting from the dropped alternatives | Problem, goal, metric |
| The riskiest assumption failed its check | brainstorm check, interviews, pilot | **Brainstorm** | Problem |
| The owner or core PM rejects the direction, not the details | approvals, ПБР | **Brainstorm** | Problem, facts |
| The class goes up: new screen, new role, more students, money or the core path | any stage | **Grilling** on the topics the new class adds, then readiness again | Everything settled |
| Readiness shows ⚠ ❌ ⛔ | readiness gate | **Grilling**, gaps only (second pass) | Everything ✅ |
| QA `/spec-readiness` finds vague or contradictory requirements | QA | **Grilling** on those items, then `prd-update` | The rest of the PRD |
| `prd-to-design` or the designer finds a missing state, screen or flow | design | **Grilling** on that branch, then `prd-update` | The rest of the PRD |
| ПБР remarks | ПБР | Sort each remark: direction → brainstorm; logic or rules → grilling; wording or UI → `prd-update` or design | What no remark touches |
| A concrete decision changed, and who, what and why are known | call, chat, Jira | **`prd-update`** directly, no grilling | Everything else |
| Backend can't build a rule as written | contracts | One option offered and the PM accepts → `prd-update`. Several options, or the logic changes → **grilling** on that rule | Everything else |

## Rules

1. **Name the loop before going back.** One line: the signal, where it sends us, what is kept. «QA нашёл 3 расплывчатых правила → вторая прожарка по R-03, R-05, R-07, остальное не трогаем».
2. **Re-ask only what hangs off the change.** Use the design tree: decisions downstream of the changed one are re-opened, the rest stay settled.
3. **Grilling: two passes per gap.** After the second pass, whatever is still vague becomes an open question with an owner and a date. For high, an open question that blocks the scenario or a rule goes to the owner or the core PM before the PRD is published.
4. **Brainstorm: two returns per task.** If the same task comes back to brainstorm a third time, stop. Give the owner three options: drop, park, or a new problem statement as a new task.
5. **After the PRD is published, every change goes through `prd-update`.** A grilling result is its input, never a direct edit of the page.
6. **Approvals reset when meaning changes.** A loop that changes the direction, the scope or the class needs the owner's OK again, and the core PM's for high. A clarification that changes no decision needs no new OK: record it in «История изменений».
7. **Record every loop** in the brief («Петли») and, once the PRD exists, in «История изменений»: date, signal, where it went, what changed.
