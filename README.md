# BADM 554 Project Structure

A reference layout for your team's final project repo in BADM 554 (Module 8, Project Final Deliverable).
It holds **no data and no code**: only folders, a short README in each saying what belongs there, and a few
skeleton files with headings. Use it to reorganize your own team repo. Do not submit this repo, and do not copy
its placeholder text into your work as if it were content.

You decide how far to follow it. Any layout is fine if a stranger can clone your repo, follow your README, and
get your warehouse. That is the standard the final deliverable is graded on.

## How to use it with your team repo

1. **Clone it next to your team repo, not inside it.** A clone inside your repo becomes a repo within a repo and
   causes confusing git errors.

   ```
   cd <the folder that holds your team repo>
   git clone https://github.com/Business-Analytics-at-Gies/badm554-project-structure.git
   ```

   You should end up with two sibling folders, for example `badm554-f26-team-03/` and
   `badm554-project-structure/`.

2. **Open both in VS Code** (File, Add Folder to Workspace) so you and your AI agent can see both.

3. **Agree who reorganizes.** Moving files is a change to shared files, so one teammate does it on a branch and
   opens a pull request (see [CONTRIBUTING.md](CONTRIBUTING.md)). Everyone pulls first and pushes their own work
   before the move starts.

4. **Ask your agent for a plan before any file moves.** Open your agent in **your team repo**, not in this one,
   and say something like:

   > Read ../badm554-project-structure/README.md, including the section addressed to you, and the README in each
   > of its folders. Compare our repo with that layout and propose a reorganization plan as a list of `git mv`
   > commands. Do not move anything yet.

5. **Read the plan, change what does not fit your project, then run it.** Use `git mv` (not copy and delete) so
   your file history moves with the files. Commit, push, and ask a teammate to review the pull request.

6. **Log it.** The reorganization is AI-assisted work, so add an entry to your team's AI Attribution Log: the tool,
   what you asked, what you kept, what you changed or rejected.

## The layout

```
your-team-repo/
├── README.md                  what the project is and how to run it from a fresh clone
├── CONTRIBUTING.md            how teammates change shared files (branch, pull request)
├── data/                      source files, never committed; README says how to fetch and check them
├── etl/                       the notebook that builds the warehouse
├── warehouse/                 README only; the .duckdb file is published as a GitHub release
├── analyses/                  one notebook or SQL file per stakeholder question
├── validation/                your checks: what each verifies and what it is blind to
├── reports/                   write-ups in Markdown, versioned like everything else
├── docs/
│   ├── schema.md              grain, tables, keys, and an ER diagram
│   ├── ai-attribution-log.md  the whole term, not only Module 8
│   └── feedback-closure.md    each piece of Module 7 feedback: what changed, or why not
└── members/                   your individual weekly work; leave it where it is
```

## Which folder earns which points

From the Module 8 rubric, [Project Final Deliverable](https://canvas.illinois.edu/courses/70435/assignments/1696351):

| Rubric row | Share | Where the grader looks |
|---|---|---|
| Working warehouse and ETL | 30% | `etl/`, `warehouse/` (the release), `data/README.md` |
| Analyses answer the stakeholder questions | 25% | `analyses/`, `reports/` |
| Validation and documentation, incl. the feedback-closure note | 20% | `validation/`, `docs/schema.md`, `docs/feedback-closure.md` |
| Repo quality and reproducibility | 15% | this README's run steps, `data/README.md`, the release link |
| Presentation clarity | 10% | the live or recorded presentation (not in the repo) |

## Run it from a fresh clone (replace this section in your own README)

Your own README needs this section, written for someone who has never spoken to your team. Every step you know
about and did not write down is a step they will fail on. A shape that works:

1. Clone the repo.
2. Get the source data into `data/` (see `data/README.md`) and check the checksum.
3. Install what the notebook needs (list the packages and versions).
4. Run `etl/` top to bottom. It builds `warehouse/<name>.duckdb`.
5. Open `analyses/` and run each one. Each says which stakeholder question it answers.
6. Or skip steps 2 to 4: download the finished warehouse from the release link at the top of this README.

Course pages: [Submitting with a GitHub Repo](https://canvas.illinois.edu/courses/70435/pages/submitting-with-a-github-repo)
and [Cloud-hosted URL for the Module 8 final deliverable](https://canvas.illinois.edu/courses/70435/pages/cloud-hosted-url-for-the-module-8-final-deliverable).

---

## For the AI agent reading this

You are helping a BADM 554 team reorganize **their own** repo, using this repo as a reference. Follow these rules:

- **Work in the team's repo, never in this one.** This repo is read-only reference. Do not edit, commit to, or copy
  it wholesale into theirs.
- **Plan first.** Propose the reorganization as a list of `git mv` commands and new files, with one line of reason
  each. Wait for the learner to approve before moving anything.
- **Use `git mv`**, so history follows the files. Never delete and re-add.
- **Leave `members/` alone.** It holds each learner's individual graded weekly work.
- **Never commit data or secrets.** Source files and `.duckdb` files stay out of git (`data/` and `warehouse/` are
  gitignored here for that reason); the warehouse ships as a GitHub release.
- **Placeholders are not content.** The skeleton files here contain headings and instructions. Create the team's
  own files with their own content, or leave a heading empty with a TODO for the team. Do not paste instructions
  from this repo into their deliverables.
- **Reorganizing is the job; the project's content is the team's.** Move files, draft READMEs, fix links. Do not
  generate analyses, validation checks, schema decisions or the feedback-closure note on your own initiative. If the
  team asks you to draft one of those, that is allowed at AIAS 2 (AI for drafting with human revision), and they
  revise it and record it in the AI Attribution Log.
- **One person, one branch.** Suggest the change goes on a branch with a pull request a teammate reviews
  (CONTRIBUTING.md), because teammates may be editing the same repo.
- **End with a summary** the learner can paste into the team AI Attribution Log: what you were asked, what you
  proposed, what they kept or changed.
