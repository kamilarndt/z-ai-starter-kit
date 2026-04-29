# z-ai-starter-kit

Config files for using z.ai GLM Coding Plan with popular AI coding tools.

z.ai offers flat-rate API access to GLM models (GLM-5.1, GLM-5-Turbo, GLM-4.7) starting at $18/mo. Works with Claude Code, Cline, Cursor, Aider, and about 20 other tools through one API key.

## Quick start

1. Sign up at z.ai (referral link: you get 10% off, I get credits: https://z.ai/subscribe?ic=LXVCVV38ZL)
2. Get your API key from the dashboard
3. Copy the config files below into your setup
4. Start coding

## Claude Code

```bash
mkdir -p ~/.claude
cp claude-config.json ~/.claude/config.json
# Edit the file and add your API key
```

```json
{
  "providers": {
    "z.ai": {
      "apiKey": "YOUR_ZAI_API_KEY",
      "baseUrl": "https://api.z.ai/v1",
      "model": "glm-5.1"
    }
  },
  "defaultProvider": "z.ai",
  "temperature": 0.7
}
```

## Cline (VS Code)

Open VS Code settings (Cmd+,), search for "Cline", and set:

```json
{
  "cline.apiProvider": "openai-compatible",
  "cline.apiKey": "YOUR_ZAI_API_KEY",
  "cline.baseUrl": "https://api.z.ai/v1",
  "cline.model": "glm-5.1"
}
```

## Aider

```bash
export OPENAI_API_KEY=YOUR_ZAI_API_KEY
export OPENAI_API_BASE=https://api.z.ai/v1
aider --model glm-5.1
```

## Continue.dev

Add to `~/.continue/config.json`:

```json
{
  "models": [
    {
      "title": "z.ai GLM-5.1",
      "provider": "openai",
      "model": "glm-5.1",
      "apiKey": "YOUR_ZAI_API_KEY",
      "apiBase": "https://api.z.ai/v1"
    }
  ]
}
```

## Pricing

| Plan | Monthly | Quarterly (-10%) |
|------|---------|-------------------|
| Lite | $18 | $48.60 |
| Pro | $72 | $194.40 |
| Max | $160 | $432 |

## What works well

- Code generation and boilerplate
- Writing tests
- Debugging
- Documentation
- Code reviews for small-to-medium changes

## What doesn't work as well

- Complex multi-file refactors
- Very long context sessions (model loses track)
- Subtle architectural decisions

## Model info

GLM-5.1 is the flagship model. #1 open-source on LMArena Code, #3 globally. Open-source (you can run it locally if you have the hardware). The z.ai plan is just a convenient way to access it via API without managing infrastructure.

## License

MIT

---

Referral link: https://z.ai/subscribe?ic=LXVCVV38ZL (10% off for you, credits for me)
