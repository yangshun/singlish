# Singlish

LLMs are too verbose, they waste tokens, waste your time reading them, just wasteful overall. It's more efficient to get them to reply in a more concise manner. Singlish is one of those ways.

## Example

Same request:

> Explain how to fix a failing test.

Without tone/style instructions:

> It looks like the failing test may be caused by a mismatch between the expected and actual values. I recommend checking the assertion, reviewing recent code changes, and running the test in isolation to gather more information.

With direct instructions + Singlish:

> The assertion likely outdated lah. Run the test alone, check the actual output, then update either the code or the expected value.

## Recommended snippet

Use the following as the single source of truth for tone and style:

```md
## Communication

- Use Singlish when replying.
- Get straight to the point.
- Be direct, casual, and concise.
- State the conclusion early.
- Do not use too much "I" in responses.
- Keep code, comments, commit messages, and docs in standard English unless explicitly requested otherwise.
```

These instructions guide your AI agent. They do not change your application code or runtime APIs. You should tweak them to your liking.

> [!TIP]
> Singlish might not be for everyone. If that's the case, just remove the first line.

## Where to add it

| Scope | Where | Commit it? | Best for |
| --- | --- | --- | --- |
| Personal/global | `~/.codex/AGENTS.md`, `~/.claude/CLAUDE.md`, GitHub Copilot personal instructions | No | Your own defaults across projects |
| Repo-shared | `AGENTS.md`, `CLAUDE.md`, `.github/copilot-instructions.md` | Yes | Team-wide defaults |

I recommend setting it on your personal settings first, not committing into your repository yet.

## Common mistakes

- Putting personal tone rules into repo-shared files when the rest of the team may not want them.
- Telling the agent to use Singlish in code comments, commit messages, or docs when those should stay in standard English.
- Beware of personal and repo instructions conflict with each other.

## Further reading

- [AGENTS.md](https://agents.md/)
- [Codex: Custom instructions with AGENTS.md](https://developers.openai.com/codex/guides/agents-md)
- [Claude Code: How Claude remembers your project](https://code.claude.com/docs/en/memory)
- [GitHub Copilot: Adding repository custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions)
- [GitHub Copilot: Adding personal custom instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-personal-instructions)
