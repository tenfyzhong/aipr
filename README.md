# AIPR Command

A CLI tool to automate GitHub PR creation/updates using LLMs (like OpenAI) to generate meaningful PR titles and descriptions.

## Features

- Automatically generates PR titles and bodies using LLMs
- Supports both new PR creation and existing PR updates
- Handles PR templates from `.github/` or `docs/`
- Interactive prompts for remote/branch selection
- Spinner animations during LLM processing
- Colorful terminal output
- Shell completions for bash/zsh/fish

## Installation
```sh
brew install tenfyzhong/tap/aipr
```

## Setup

### GitHub Authentication
1. Authenticate with GitHub:
   ```sh
   gh auth login
   ```
2. Follow the prompts to complete authentication

### LLM Setup
1. Configure your OpenAI API key:
   ```sh
   llm keys set openai
   ```
   (Enter your OpenAI API key when prompted)
2. Alternatively, you can use other supported LLM providers by following their setup instructions

For more details, see:
- GitHub CLI docs: https://cli.github.com/manual/
- LLM docs: https://llm.datasette.io/

## Usage

```sh
aipr [options]
```

### Options

| Flag | Description |
|------|-------------|
| `-h, --help` | Show help message |
| `-r, --remote <name>` | Remote repository to use (default: origin) |
| `-B, --base <branch>` | Base branch to compare against |
| `-H, --head <branch>` | Head branch to compare from (default: current branch) |
| `-T, --template <file>` | Specify a PR template file |
| `--prompt-title <file>` | Path to PR title prompt template |
| `--prompt-body <file>` | Path to PR body prompt template |
| `--model <name>` | LLM model to use |
| `--update-title` | Update PR title when editing existing PR |

All `gh pr create/edit` flags are also supported.

## Configuration

Set these environment variables to customize behavior:

- `LLM_PR_PROMPT_TITLE`: Path to custom title prompt template
- `LLM_PR_PROMPT_BODY`: Path to custom body prompt template
- `LLM_PR_MODEL`: Default LLM model to use

## Examples

Create a PR against default branch:
```sh
aipr
```

Create PR with specific base branch:
```sh
aipr --base develop
```

Update an existing PR:
```sh
anpr --update-title
```

## Credits

- Inspired by [Harper Reed's blog](https://harper.blog/2024/03/11/use-an-llm-to-automagically-generate-meaningful-git-commit-messages/)
