<div align="center">

# 🧩 Mods for Claude

**A curated catalogue of Claude Code mods, each with a copy-paste prompt that builds it for you.**

*35 mods · 8 categories · build your own with a copy-paste prompt*

![Claude Code](https://img.shields.io/badge/Claude_Code-2.1.287%2B-D97757?style=flat-square)
![Mods](https://img.shields.io/badge/mods-35-8A63D2?style=flat-square)
![Surfaces](https://img.shields.io/badge/terminal_%2B_desktop-supported-2EA44F?style=flat-square)
![License: MIT](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

[Peek](#-a-peek) · [Quick start](#-quick-start) · [Catalogue](#-the-catalogue) · [How mods work](#-what-is-a-mod) · [Contribute](#-contributing)

</div>

---

## 👀 A peek

<table>
<tr>
<td width="50%"><a href="mods/feedback-and-learning/reflect.md"><img src="assets/mockups/reflect.svg" alt="Mockup of Reflect"></a><br><b>Reflect</b>: turns your corrections into CLAUDE.md rules</td>
<td width="50%"><a href="mods/visibility/file-tree.md"><img src="assets/mockups/file-tree.svg" alt="Mockup of File Tree"></a><br><b>File Tree</b>: see which files Claude is reading and editing</td>
</tr>
<tr>
<td width="50%"><a href="mods/safety/blast-radius.md"><img src="assets/mockups/blast-radius.svg" alt="Mockup of Blast Radius"></a><br><b>Blast Radius</b>: see what a risky command would destroy</td>
<td width="50%"><a href="mods/fun-and-ambient/boss-fight.md"><img src="assets/mockups/boss-fight.svg" alt="Mockup of Boss Fight"></a><br><b>Boss Fight</b>: failing tests become a boss to beat</td>
</tr>
</table>

Every mod page opens with a mockup like these. They're drawn illustrations of each idea, not screenshots, so your build may look different.

---

## 🤔 What is a mod?

Mods are small add-ons that change **how Claude Code itself looks and behaves**: a live panel beside the chat, a band above your prompt, a status-line entry, a toast, a new slash command, or a hook that steps in before Claude runs a tool.

| | What it changes | Example |
|---|---|---|
| **Skill** | *How Claude does a task* | "Write commit messages like this" |
| **MCP server** | *What Claude can reach* | Gmail, Linear, a database |
| **Hook (settings)** | *A shell script on an event* | Run `prettier` after each edit |
| **Mod** ✨ | *Claude Code's interface and behaviour* | A file tree that lights up as Claude edits |

Under the hood a mod is a plugin with a TypeScript hooks module. You don't need to write it yourself: Claude Code ships a built-in **`plugin-authoring`** skill (in the `cc-plugin-plugin-authoring` plugin) that builds a mod from a plain-English description.

---

## 🚀 Quick start

**1. Check your version.** Mods need Claude Code **2.1.287+** in the terminal (Desktop app: 2.1.286+).

```bash
claude --version      # update with: claude update
```

**2. Pick a mod** from the [catalogue](#-the-catalogue) and open its page.

**3. Build your own.** Copy the **Build prompt** block from the mod's page and paste it into Claude Code.

**4. Say yes to hot reloading.** When Claude writes the mod's first file, Claude Code asks:

> *Enable hot reloading for this session?*  ·  How does this work? · **Enable for this session** · Not now

Choose **Enable for this session**. Only you can answer this question, so it isn't in the prompts. The mod loads when the turn ends, and every later edit reloads it live. If you choose *Not now*, the mod is still saved and loads the next time you start a session.

> [!TIP]
> Not happy with it yet? Keep talking: *"make the band one line"*, *"use green instead of blue"*. Each change hot-reloads.

> [!WARNING]
> Mods run with **your** permissions. Read a community mod's code before you install it, and use `claude plugin validate <folder>` to see what it hooks and calls.

---

## 📚 The catalogue

**Legend:** ✍️ Prompt only — build it yourself

### 🎨 Look & Feel
*Make Claude Code look and feel like yours.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Claude Skins](mods/look-and-feel/claude-skins.md) | An icon for each tool, coloured diffs, switchable themes (Tokyo Night default) | transcript · `/skin` |
| [Terminal Browser](mods/look-and-feel/terminal-browser.md) | Preview localhost, HTML files and PRs in a pane | pane · `/browse` |

### 👀 Visibility & Awareness
*See what Claude is doing while it does it.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Savvy Progress](mods/visibility/savvy-progress.md) | Progress bar plus a live panel of subagents with model and cost | band · pane |
| [File Tree](mods/visibility/file-tree.md) | Project tree that shimmers on reads and turns green on saved edits | pane · `/tree` |
| [Goal Tracker](mods/visibility/goal-tracker.md) | `/goal` with a timer, phase and live checklist | pane · status |
| [Replay Theater](mods/visibility/replay-theater.md) | ▶ Replay a turn's edits one diff at a time | band · pane |
| [You Should Know](mods/visibility/you-should-know.md) | Pins costs, security notes and to-dos buried in long replies | band · toast |
| [Token Weather](mods/visibility/token-weather.md) | Context fill as a weather forecast, with a sparkline | band |
| [Receipt](mods/visibility/receipt.md) | End-of-turn receipt that flags "fixed" claims nothing verified | turn line · toast |
| [PR Tracker](mods/visibility/pr-tracker.md) | Watch PRs' checks, reviews and merge state | band · toast |

### 💰 Cost & Context
*Spend less and keep the context window healthy.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Cash Tax](mods/cost-and-context/cash-tax.md) | Warns before a cold-cache resend, plus `/keepwarm` | band · status |
| [Cachekeeper](mods/cost-and-context/cachekeeper.md) | Cache countdown, context % and a one-click Session Handoff | status · band |
| [Context Handoff](mods/cost-and-context/context-handoff.md) | Automatic handoff and fresh start when context fills up | band |
| [Switchboard](mods/cost-and-context/switchboard.md) | Picks the model for each subagent (supports **Jev**), shows cost per subagent | band · pane |

### 🛡️ Safety & Guardrails
*Catch mistakes before they happen.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Blast Radius](mods/safety/blast-radius.md) | Shows what a destructive command will hit and asks you to approve | dialog |
| [Collision Guard](mods/safety/collision-guard.md) | Stops edits to files someone else changed recently | dialog |
| [Privacy Blur](mods/safety/privacy-blur.md) | `/record on` masks secrets **on screen** | transcript · status |
| [Secret Redactor](mods/safety/secret-redactor.md) | Hides secrets **from the model**, puts them back in files | tool results |
| [Scope Guard](mods/safety/scope-guard.md) | Stops a turn that edits too many files | guard · band |
| [Merge Gate](mods/safety/merge-gate.md) | No merge or push to main until CI is green | guard |
| [Deploy Verify](mods/safety/deploy-verify.md) | Proves a deploy worked (CI + live URL) before Claude claims it | tool result · toast |
| [DevTools](mods/safety/devtools.md) | Breakpoints, step and inspect for tool calls | dialog · pane |

### 🧠 Feedback & Learning
*Teach Claude once, so you don't have to repeat yourself.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Reflect](mods/feedback-and-learning/reflect.md) | Turns your corrections into `CLAUDE.md` rules | band |
| [Assumption Checker](mods/feedback-and-learning/assumption-checker.md) | Lists Claude's assumptions; mark ✅/❌ and it fixes the wrong ones | band |

### ✍️ Prompting & Flow
*Less typing, fewer interruptions.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Prompt Enhancer](mods/prompting-and-flow/prompt-enhancer.md) | ✨ Rewrites a vague prompt in place | band |
| [Next Steps](mods/prompting-and-flow/next-steps.md) | 3 one-press next actions after each turn | band |
| [Idea Shelf](mods/prompting-and-flow/idea-shelf.md) | `/idea` saves thoughts mid-turn for later | pane · status |
| [No-Jargon Summarizer](mods/prompting-and-flow/no-jargon-summarizer.md) | Collapses the chatter and ends with a plain-English summary | transcript · card |
| [Aside](mods/prompting-and-flow/aside.md) | Side-chat questions that never touch the main thread | pane · `/aside` |
| [Copy Band](mods/prompting-and-flow/copy-band.md) | One-press copy for every code block | band |

### 🤝 Multi-Session
*For when you run more than one Claude at a time.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Global Session Manager](mods/multi-session/global-session-manager.md) | Every session's status, and who needs you | status · pane · toast |
| [Same Folder Tracker](mods/multi-session/same-folder-tracker.md) | Warns when another session works in your folder | band · toast |
| [Done Blink](mods/multi-session/done-blink.md) | Blinks the terminal tab when a turn finishes | tab colour |

### 🎮 Fun & Ambient
*Because waiting for Claude should be fun.*

| Mod | What it does | Where it shows |
|---|---|---|
| [Boss Fight](mods/fun-and-ambient/boss-fight.md) | Failing tests spawn a pixel boss you beat by fixing them | pane (pixels) |
| [Session Wrapped](mods/fun-and-ambient/session-wrapped.md) | A "Spotify Wrapped" recap of your session, week or month | pane · PNG |

---

## 🧱 What a mod can use

Every build prompt in this repo sticks to things mods can actually do, checked against Claude Code **2.1.296**.

| Surface | Use it for | API |
|---|---|---|
| **Pane** | Side panels, dashboards, dialogs | `$.ui.open` + `ui.render` on `Pane` |
| **Band above prompt** | One-to-three-line live info and buttons | `ui.render` on `AbovePrompt` |
| **Status line** | Tiny always-on numbers | `$.ui.status(text)` |
| **Toast / notification** | "Something happened" | `$.ui.toast`, `$.ui.notify` |
| **Slash commands** | `/goal`, `/idea`, `/tree`… | `$.command.register` + `command.run` |
| **Tool-call hooks** | Block, rewrite or watch tools | `on('tool.call', { tool }, …)` |
| **Prompt hooks** | Watch, hold, fill or rewrite prompts | `prompt.submit`, `$.prompt.fill` |
| **Transcript rows** | Restyle messages and tool rows (display only) | `ui.render` on built-in components |
| **Side model calls** | Cheap classify, rewrite and summarise | `$.model.complete`, `$.model.fork`, `$.model.classify` |
| **Timers, files, processes, storage** | Polling, registries, persistence | `$.clock`, `$.fs`, `$.process`, `$.state`, `$.store` |

Elements: `Box`, `Text`, `Button` (with hotkeys), `Input`, `Select`, `Markdown`, `Code` (including diffs), `Link`, plus `Raster` and `Image` (pixels) in the terminal.

> [!NOTE]
> Mods can't change the permission prompt, and they only **draw** in the terminal and the Desktop app's Code tab. Their hooks still run in VS Code, `claude -p` and cloud sessions.

---

## 📦 From prompt to permanent

A mod built in a session lives in a temporary dev folder. To keep it:

1. Ask Claude: *"Copy this mod to `~/mods/<name>` and make it a marketplace."* It adds `.claude-plugin/marketplace.json`.
2. Push that folder to GitHub.
3. Install it anywhere:
   ```text
   /plugin install <mod> --marketplace <you>/<repo>
   ```

For local development, `claude --plugin-dir <folder>` loads a mod for one session.

---

## 🙏 Acknowledgements

This catalogue and its build prompts are curated by [@tusharck](https://github.com/tusharck).

---

## 🤝 Contributing

1. Copy [`docs/mod-template.md`](docs/mod-template.md) into the right `mods/<category>/` folder.
2. Fill it in: a sharp one-liner, a mockup in `assets/mockups/` (optional), a build prompt that sticks to [what mods can use](#-what-a-mod-can-use), and a source link.
3. Add a row to the catalogue table above.

```
mods-for-claude/
├── README.md
├── docs/mod-template.md
├── LICENSE
├── assets/mockups/      (one SVG per mod)
└── mods/
    ├── look-and-feel/        (2)
    ├── visibility/           (8)
    ├── cost-and-context/     (4)
    ├── safety/               (8)
    ├── feedback-and-learning/(2)
    ├── prompting-and-flow/   (6)
    ├── multi-session/        (3)
    └── fun-and-ambient/      (2)
```

---

## 📄 License

[MIT](LICENSE) © tusharck
