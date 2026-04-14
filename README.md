# Singlish 🇸🇬

LLMs are too verbose, they waste tokens, waste your time reading them, just wasteful overall. It's more efficient to get them to reply in a more concise manner. Singlish is one of those ways.

## Example

Same request:

> Explain how to fix a failing test.

**Without tone/style instructions** 😥:

> It looks like the failing test may be caused by a mismatch between the expected and actual values. I recommend checking the assertion, reviewing recent code changes, and running the test in isolation to gather more information.

**With direct instructions + Singlish** 😌:

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
> Singlish might not be for everyone. If that's the case, just remove the first line, conciseness is still useful.

## Customize your coding agent

| Scope | Where | Commit it? | Best for |
| --- | --- | --- | --- |
| Personal/global | `~/.codex/AGENTS.md`, `~/.claude/CLAUDE.md`, GitHub Copilot personal instructions | No | Your own defaults across projects |
| Repo-shared | `AGENTS.md`, `CLAUDE.md`, `.github/copilot-instructions.md` | Yes | Team-wide defaults |

I recommend adding it for your personal settings first, only add to your repositories if you like it.

For coding agents, the relevant docs are:

- [AGENTS.md](https://agents.md/),
- [Codex `AGENTS.md`](https://developers.openai.com/codex/guides/agents-md),
- [Claude Code memory / `CLAUDE.md`](https://code.claude.com/docs/en/memory),
- [GitHub Copilot repository instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-repository-instructions),
and
- [GitHub Copilot personal instructions](https://docs.github.com/en/copilot/how-tos/configure-custom-instructions/add-personal-instructions).

## ChatGPT and Claude

If you want this outside coding agents, you can set it directly in ChatGPT and Claude too.

### ChatGPT

For ChatGPT, the main knob is **Custom Instructions**. See [Custom Instructions](https://help.openai.com/en/articles/8096356-custom-instructions-for-chatgp).

1. Open `Settings`.
2. Go to `Personalization`.
3. Turn on customization.
4. Paste the recommended snippet into `Custom Instructions`.

Notes:

- Custom Instructions apply across all chats.
- They update future replies immediately.
- If you also set a ChatGPT personality under `Base style and tone`, treat that as a broad vibe only. For direct rules like "use Singlish" or "be concise," Custom Instructions matter more. See [Customizing Your ChatGPT Personality](https://help.openai.com/en/articles/11899719-customizing-your-chatgpt-personality).

### Claude

Claude has two useful knobs: **Profile Preferences** and **Styles**. See [Understanding Claude's personalization features](https://support.claude.com/en/articles/10185728-understanding-claude-s-personalization-features).

For account-wide preferences:

1. Click your initials in the lower-left corner.
2. Open `Settings`.
3. Under `What preferences should Claude consider in responses?`, paste the recommended snippet.

For response style:

1. Open the `Search and tools` menu.
2. Choose `Use style`.
3. Pick `Concise`, or create a custom style with your own instructions.

Notes:

- Use **Profile Preferences** for persistent account-wide guidance.
- Use **Styles** to control how replies are delivered.
- If you want exact phrasing and tone, create a custom style and use Claude's advanced custom instructions there. See [Configure and use styles](https://support.claude.com/en/articles/10181068-configure-and-use-styles).

## Things to note

- Putting personal tone rules into repo-shared files when the rest of the team may not want them.
- Telling the agent to use Singlish in code comments, commit messages, or docs when those should stay in standard English.
- Beware of personal and repo instructions conflict with each other.
