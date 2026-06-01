---
day: 2
date: 2026-05-26
phase: 0
hours: 6
tags:
  - day/002
  - phase/0
aliases:
  - "Day 2"
  - "Git + GitHub Workflow"
---

# Day 002 — Git + GitHub Workflow

**Tue 26 May 2026** · ~6h · Stage 0 — Programming & Engineering Foundations



[[Day-001-Linux-CLI-Essentials|← Day 1]] · [[00-Dashboard|🏠 Dashboard]] · [[00-Calendar|📅 Calendar]] · [[Day-003-Python-Basics-1-Syntax-and-Control-Flow|Day 3 →]]

---

## 📘 Learn (~2h)

Commits, branches, merging vs rebasing, PRs, .gitignore. Why AppSec engineers must read diffs fluently — your whole job is reviewing PRs.

## 🛠️ Do (~4h)

Set up GitHub. Create your roadmap repo (commit deliverables here for 120 days). Practice branches, PRs, resolving a merge conflict.

## 🎯 Deliverable

`GitHub repo created + first commit`

- [ ] Deliverable committed to GitHub
- [ ] Verbal explain-aloud done (15 min)

## 📚 Resources

- 🧪 Lab [Learn Git Branching (interactive)](https://learngitbranching.js.org/)
- 📖 Read [GitHub Skills (free courses)](https://skills.github.com/)
- 📖 Read [Pro Git Book (free)](https://git-scm.com/book/en/v2)

## 📝 Notes

> Write your own learnings, gotchas, code snippets, and questions here.

**Merge vs Rebase (visual):**

- Merge: preserves history exactly as it happened. Creates a merge commit. Graph shows diamond shape on divergence.
- Rebase: rewrites history to look linear. Replays feature commits onto main's tip with new hashes. Graph shows straight line.
- **Rule: rebase before pushing, merge after.** Never rebase commits already pushed to a shared branch.
- 
cmds for pushing code
ls /mnt/k/appsec-vault/01-Stage0-Foundations
 cp "/mnt/k/appsec-vault/01-Stage0-Foundations/
Day-002-Git-and-GitHub-Workflow.md" ~/git-cheatsheet.md
git add .
git commit
git push

## 🔗 Related

- [[00-Dashboard|Dashboard]]

## ✅ Completion

- [ ] Marked complete in v4.5 HTML roadmap
- [ ] Notes synced
- [ ] Anki cards added (if applicable)

---

[[Day-001-Linux-CLI-Essentials|← Day 1]] · [[Day-003-Python-Basics-1-Syntax-and-Control-Flow|Day 3 →]]
