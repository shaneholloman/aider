---
parent: Configuration
nav_order: 1000
description: Assign convenient short names to models.
---

# Model Aliases

Model aliases allow you to create shorthand names for models you frequently use. This is particularly useful for models with long names or when you want to standardize model usage across your team.

## Command Line Usage

You can define aliases when launching aider using the `--alias` option:

```bash
aider --alias "fast:gpt-4o-mini" --alias "smart:o3-mini"
```

Multiple aliases can be defined by using the `--alias` option multiple times. Each alias definition should be in the format `alias:model-name`.

## Configuration File

Of course,
you can also define aliases in your [`.aider.conf.yml` file](https://aider.chat/docs/config/aider_conf.html):

```yaml
alias:
  - "fast:gpt-4o-mini"
  - "smart:o3-mini"
  - "hacker:claude-3-sonnet-20240229"
```

## Using Aliases

Once defined, you can use the alias instead of the full model name from the command line:

```bash
aider --model fast  # Uses gpt-4o-mini
aider --model smart  # Uses o3-mini
```

Or with the `/model` command in-chat:

```
Aider v0.75.3
Main model: anthropic/claude-3-7-sonnet-20250219 with diff edit format, prompt cache, infinite output
Weak model: claude-3-5-sonnet-20241022
Git repo: .git with 406 files
Repo-map: using 4096 tokens, files refresh
─────────────────────────────────────────────────────────────────────────────────────────────────────
> /model fast

Aider v0.75.3
Main model: gpt-4o-mini with diff edit format
─────────────────────────────────────────────────────────────────────────────────────────────────────
diff> /model smart

Aider v0.75.3
Main model: o3-mini with diff edit format
─────────────────────────────────────────────────────────────────────────────────────────────────────
>
```

## Built-in Aliases

Aider includes some built-in aliases for convenience:

<!--[[[cog
import cog
from aider.models import MODEL_ALIASES

for alias, model in sorted(MODEL_ALIASES.items()):
    cog.outl(f"- `{alias}`: {model}")
]]]-->
- `3`: gpt-3.5-turbo
- `35-turbo`: gpt-3.5-turbo
- `35turbo`: gpt-3.5-turbo
- `4`: gpt-4-0613
- `4-turbo`: gpt-4-1106-preview
- `4o`: gpt-4o
- `deepseek`: deepseek/deepseek-chat
- `flash`: gemini/gemini-2.5-flash
- `gemini`: gemini/gemini-2.5-pro
- `gemini-2.5-pro`: gemini/gemini-2.5-pro
- `gemini-exp`: gemini/gemini-2.5-pro-exp-03-25
- `grok3`: xai/grok-3-beta
- `haiku`: claude-3-5-haiku-20241022
- `optimus`: openrouter/openrouter/optimus-alpha
- `opus`: claude-opus-4-20250514
- `quasar`: openrouter/openrouter/quasar-alpha
- `r1`: deepseek/deepseek-reasoner
- `sonnet`: anthropic/claude-sonnet-4-20250514
<!--[[[end]]]-->

## Priority

If the same alias is defined in multiple places, the priority is:

1. Command line aliases (highest priority)
2. Configuration file aliases
3. Built-in aliases (lowest priority)

This allows you to override built-in aliases with your own preferences.
