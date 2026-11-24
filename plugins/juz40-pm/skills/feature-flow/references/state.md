# Where the task is: save and resume

Discovery takes days and passes between people: the lead stops mid-grilling, design and QA happen in between, a remark comes back a week later. Any chat and any agent must be able to pick the task up where it stopped. The brief page in Confluence says where that is; Jira and the PRD confirm it.

## 1. Where the brief lives

- Page «<Название> — бриф» in space SD. Template: `brief.md`.
- Parent: the «<Название> — контекст» page if there is one. Otherwise the section where the PRD will live: find the lead's recent pages (`space = SD AND creator = currentUser() AND type = page ORDER BY created DESC`) and propose the same parent.
- Created at intake, right after the class and the Story. Ask once, in the same message as the class: «Бриф буду вести в Confluence: ‹где›. Ок?». After that, save at every checkpoint without asking.
- The Story description links the brief (`../../jira-tasks/templates/story-intake.md`), so the Story key alone leads to it.
- When the PRD is published, `prd` moves the brief under the PRD для людей (`updateConfluencePage` with `parentId`), so all pages of the task stay in one tree.
- Confluence unreachable: keep the brief in the chat, say so, and offer `brief-<slug>.md` in the current folder. Move it to Confluence as soon as the connection works.

## 2. When to save

Save at each checkpoint, not after every message:

| Checkpoint | What changes in the brief |
|---|---|
| Intake and class | Page created: «Где мы», the table, the problem as far as known |
| Before sending a grilling round | Its questions go into «Открытый раунд» first, then you send them |
| After the answers to a round | The answers into their sections; «Открытый раунд» cleared or replaced by the next round |
| Brainstorm converged | Problem, direction, dropped alternatives, riskiest assumption |
| Readiness gate | The result table in «Журнал»; the loop in «Петли» if there is one |
| Metric | «Цель» |
| An approval asked or given | «Апрувы», «Ждём» |
| A loop or a sorted remark | «Петли», and «Где мы» set to the stage it went back to |
| PRD published, design handed off, owner's OK, Jira done | «Где мы», «PRD», «Дизайн» |

Every save updates «Где мы» (with the date, time in Asia/Almaty, and who) and adds one row to «Журнал».

## 3. How to save

1. `getConfluencePage` with `contentFormat: html`.
2. Change only the sections the checkpoint touches. Keep everything else, including inline comments, byte for byte.
3. `updateConfluencePage` with `contentFormat: html` and `versionMessage` «Бриф: ‹этап›».
4. A version conflict means someone else edited the page: read it again, merge, save. Never overwrite another person's edit.

## 4. Resume

Do this before anything else when the person names an existing task — a DV key, a Confluence link, a task name — or says «продолжим», «где мы остановились», «вернулся к задаче».

1. **Find the pages.** The Story (`getJiraIssue`) and the brief link in its description. No link: `space = SD AND title ~ "бриф" AND title ~ "<keyword>"`. Also the context document and the PRD pages (`title ~ "<keyword>"`), and their child pages (`getConfluencePageDescendants`).
2. **Read the state.** «Где мы», «Открытый раунд», the last rows of «Журнал». Then the comments on the brief and the PRD pages (`getConfluencePageFooterComments`, `getConfluencePageInlineComments`): an unresolved comment is a remark, sorted by `loops.md`.
3. **Check it against reality.** What exists in Confluence and Jira wins over «Где мы» when they disagree:

   | What you find | The task is at least at |
   |---|---|
   | A Story, no brief | 0. Intake: build the brief from the Story and the context document |
   | «Открытый раунд» not empty | The stage in «Где мы»: ask those questions again, as they are |
   | Core PM approval Sub-task not Done | 5. Waiting for the core PM |
   | PRD pages exist, status «Черновик» | 6. PRD |
   | A Figma link in the PRD, or mockups in progress | 7. Design |
   | A test-case page exists | QA has the PRD: remarks or 8 |
   | PRD status «На согласовании» | 8. Waiting for the owner |
   | PRD «Согласовано оунером», no Sub-tasks | 9. Jira |
   | Sub-tasks exist under the Story | Discovery closed: development |

4. **Say where we are**, in at most five lines: the task and its class; where it stopped (stage, date, who); what is done; what is next; who or what we wait for. If the brief and reality disagreed, say what you corrected and save the brief.
5. **Who continues.** If the person is not the lead named in the brief, ask once: «Продолжаешь вместо ‹имя›?». Record the answer in «Ведёт» and «Журнал».
6. **Continue** from that stage. If the task waits for someone (owner, core PM, PM-partner, designer) and nothing has changed, say so, offer a short reminder message to send them, and stop.

## 5. Stopping and closing

- **The person stops mid-stage** («потом продолжу», «всё, спать», or simply leaves): save, then tell them in one line how to come back: «Напиши в любом чате: продолжим DV-XXXX».
- **Discovery closed** (after stage 9): «Где мы» becomes «Discovery закрыт ‹дата›. Дальше: разработка». The brief stays as the record of how decisions were made; the PRD is the source of truth.
