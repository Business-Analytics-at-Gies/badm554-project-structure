# BADM 554 Project Structure

A suggested layout for your team's final project repo in BADM 554 (Module 8, Project Final Deliverable).
This repo holds **no data and no code**: only folders, a short README in each saying what goes there, and a few
empty templates. Use it to tidy up your own team repo. Do not submit this repo, and do not copy its template text
into your work.

You do not have to follow it exactly. Any layout is fine if a stranger can clone your repo, follow your README,
and rebuild your tables. That is what the final deliverable is graded on.

**Where your data lives:** your project runs on BigQuery by default. Your queries live in your team repo, and
anyone on the team can run them. DuckDB is optional, for teams that bring their own files or prefer to keep some data off the cloud. The course page
[Where Your Team's Data Lives](https://canvas.illinois.edu/courses/70435/pages/where-your-teams-data-lives)
explains the options.

## How to use it with your team repo

1. **Clone it next to your team repo, not inside it.** A repo inside another repo causes confusing git errors.

   ```
   cd <the folder that holds your team repo>
   git clone https://github.com/Business-Analytics-at-Gies/badm554-project-structure.git
   ```

   You should end up with two folders side by side:

   ```
   your-projects-folder/
   ├── badm554-f26-team-03/          your team repo
   └── badm554-project-structure/    this repo
   ```

2. **Open both in VS Code** (File, Add Folder to Workspace) so you and your AI agent can see both.

3. **Agree who reorganizes.** Moving files affects the shared team repo, so one teammate does it. That teammate
   makes a separate branch, moves the files there, and opens a pull request for the team to review (see
   [CONTRIBUTING.md](CONTRIBUTING.md)). Before anything moves, everyone saves their work, pushes it, and pulls the
   latest version.

4. **Ask your AI agent for a plan before any file moves.** Open the agent in **your team repo**, not in this one.
   The `../` in the prompt below means "the folder next to mine", which is why step 1 puts the two repos side by
   side. Say something like:

   > Read ../badm554-project-structure/README.md, including the section addressed to you, and the README in each
   > of its folders. Compare our repo with that layout and propose a reorganization plan as a list of `git mv`
   > commands. Do not move anything yet.

5. **Read the plan, change what does not fit your project, then run it.** Use `git mv` (not copy and delete) so
   each file keeps its history. Commit, push, and ask a teammate to review the pull request.

6. **Log it.** The agent should end with a short summary. Check that it did, and paste it into your team's AI
   Attribution Log: the tool, what you asked, what you kept, what you changed.

## The layout

```
your-team-repo/
├── README.md                  what the project is, and how to rebuild it from a fresh clone
├── CONTRIBUTING.md            how teammates change shared files (branch, pull request)
├── etl/                       the queries (or notebook) that build your tables, in the order you run them
├── warehouse/                 README only: which tables you build, and their row counts
├── analyses/                  one notebook or SQL file per stakeholder question
├── validation/                your checks: what each one tests and what it cannot see
├── reports/                   write-ups in Markdown, saved in git like everything else
├── data/                      only if you bring your own files; never committed
├── docs/
│   ├── schema.md              grain, tables, keys, and a diagram
│   ├── ai-attribution-log.md  the whole term, not only Module 8
│   └── feedback-closure.md    each piece of Module 7 feedback: what changed, or why not
└── members/                   your individual weekly work; leave it where it is
```

## Which folder earns which points

From the Module 8 rubric, [Project Final Deliverable](https://canvas.illinois.edu/courses/70435/assignments/1696351):

| Rubric row | Share | Where the grader looks |
|---|---|---|
| Working warehouse and ETL | 30% | `etl/`, `warehouse/README.md` |
| Analyses answer the stakeholder questions | 25% | `analyses/`, `reports/` |
| Validation and documentation, including the feedback-closure note | 20% | `validation/`, `docs/schema.md`, `docs/feedback-closure.md` |
| Repo quality and reproducibility | 15% | this README's "rebuild it" steps |
| Presentation clarity | 10% | the live or recorded presentation (not in the repo) |

## Rebuild it from a fresh clone (replace this section in your own README)

Your own README needs this section, written for someone who has never spoken to your team. Any step you know
about but did not write down is a step they will get stuck on.

**BigQuery teams (most teams):**

1. Clone the repo.
2. Open BigQuery with your own Google account, and set your own project name in one place (the first cell of the
   notebook, or the top of each query). No one's project name should be written into the queries.
3. Run the files in `etl/` in order (or the one notebook that runs them). They read the public dataset and build your tables in your own BigQuery.
4. Check your row counts match the ones listed in `warehouse/README.md`.
5. Run each file in `analyses/`. Each one says which stakeholder question it answers.

**DuckDB teams (only if you bring your own files):**

1. Clone the repo.
2. Get the source files into `data/` (see `data/README.md`) and check them.
3. Install what the notebook needs (list the packages).
4. Run the notebook in `etl/` top to bottom. It builds the DuckDB file in `warehouse/`.
5. Or skip steps 2 to 4: download the finished file from the release link at the top of your README.

Course pages: [Where Your Team's Data Lives](https://canvas.illinois.edu/courses/70435/pages/where-your-teams-data-lives),
[Submitting with a GitHub Repo](https://canvas.illinois.edu/courses/70435/pages/submitting-with-a-github-repo), and,
for DuckDB teams only, [Cloud-Hosted URL for the Module 8 Final Deliverable](https://canvas.illinois.edu/courses/70435/pages/cloud-hosted-url-for-the-module-8-final-deliverable).

---

## For the AI agent reading this

You are helping a BADM 554 team reorganize **their own** repo, using this repo as a guide. Follow these rules:

- **Work in the team's repo, never in this one.** This repo is read-only. Do not edit it, commit to it, or copy it
  wholesale into theirs.
- **Plan first.** Propose the changes as a list of `git mv` commands and new files, with a one-line reason for
  each. Wait for the learner to approve before moving anything.
- **Use `git mv`**, so each file keeps its history. Never delete and re-add.
- **Leave `members/` alone.** It holds each learner's graded weekly work.
- **Never commit data, database files or secrets.** Most teams use BigQuery, so their tables are rebuilt by the
  queries in `etl/` and nothing large goes in git. If a team uses DuckDB, its `.duckdb` file stays out of git and
  is shared as a GitHub release.
- **Do not hard-code anyone's BigQuery project name** in queries. Suggest one setting at the top instead.
- **Templates are not content.** The files here contain headings and instructions. Create the team's own files
  with their own content, or leave a heading empty with a TODO. Do not paste instructions from this repo into
  their deliverables.
- **Reorganizing is the job; the project's content is the team's.** Move files, draft READMEs, fix links. Do not
  write analyses, validation checks, schema decisions or the feedback-closure note on your own. If the team asks
  you to draft one of those, that is allowed at AIAS 2 (AI for drafting, with the team revising), and they record
  it in the AI Attribution Log.
- **One person, one branch.** Suggest the change goes on a branch with a pull request a teammate reviews
  (CONTRIBUTING.md), because teammates may be editing the same repo.
- **End with a summary** the learner can paste into the team AI Attribution Log: what you were asked, what you
  proposed, and what they kept or changed.
