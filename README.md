# gh-auto-pr-review

A [`gh` CLI extension](https://cli.github.com/manual/gh_extension) that streamlines reviewing pull requests from the terminal. It shows the PR diff (with noise filtered out), then lets you approve + auto-merge, request a Dependabot rebase, or skip — all in a single command.

## How it works

1. **Resolves the PR** — looks up the PR URL using `gh pr view`.
2. **Prints the diff** — runs `gh pr diff` and displays it with colour, skipping `pnpm-lock.yaml` to reduce noise.
3. **Prompts for an action**:

   | Input | Action |
   |-------|--------|
   | `y` / `yes` | Approves the PR (`gh pr review --approve`) and enables squash auto-merge (`gh pr merge -m --auto`). |
   | `r` | Posts a `@dependabot rebase` comment on the PR. |
   | anything else | Skips without taking action. |

## Requirements

- Python 3
- [GitHub CLI (`gh`)](https://cli.github.com/) installed and authenticated

## Installation

Install as a `gh` extension by cloning this repo into the gh extensions directory:

```bash
gh extension install xmatthias/gh-auto-pr-review
```

Or manually:

```bash
git clone https://github.com/xmatthias/gh-auto-pr-review \
  ~/.local/share/gh/extensions/gh-auto-pr-review
```

## Usage

```bash
gh auto-pr-review <PR_NUMBER_OR_URL>
```

### Examples

```bash
# By PR number (in the current repo)
gh auto-pr-review 42

# By full URL
gh auto-pr-review https://github.com/owner/repo/pull/42
```

## License

MIT
