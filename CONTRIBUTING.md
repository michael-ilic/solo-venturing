# Contributing

The most useful contribution is a session where the skill gave bad advice:
it agreed when it should have challenged, skipped a gate, invented a number,
or lost the thread between sessions. Open an issue with what you asked, what
it did and what a good co-founder would have done. Those become eval cases.

## Changing the skill

1. Write or adjust an eval case in `evals/` first, and see it fail.
2. Make the change in `skills/solo-venturing/`.
3. Run the checks:

   ```bash
   claude plugin validate . --strict
   claude plugin eval . --scaffold --allow-tools Write Edit Bash
   ```

4. Bump `version` in `.claude-plugin/plugin.json`. Installed plugins update
   only when it changes.

## What keeps it portable

- `SKILL.md` frontmatter uses only the fields of the
  [Agent Skills specification](https://agentskills.io/specification): `name`,
  `description`, `license`, `compatibility`, `metadata`, `allowed-tools`.
- `SKILL.md` stays under 500 lines. Detail goes into `references/`, one
  level deep, and `SKILL.md` says when to read each file.
- Paths are relative to the skill directory. No home-directory or machine
  paths in any markdown file.
- Scripts use the standard library only, make no network calls, and write
  nothing outside the venture folder.
- Tools, prices and store policies change. Reference files name them as
  starting points and tell the agent to check the current source.
