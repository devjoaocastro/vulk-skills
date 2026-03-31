# VULK Agent Skills

Modular instruction sets that teach AI coding agents how to generate professional, production-grade code. Based on the [Agent Skills specification](https://agentskills.io) and inspired by [GSAP's skills pattern](https://github.com/greensock/gsap-skills).

## Installation

### npx (recommended)

```bash
# Install a single skill
npx skills add vulk/design-system

# Install multiple skills
npx skills add vulk/design-system vulk/tailwind vulk/gsap
```

### Claude Code / Cursor / Windsurf

Add to your project's `.claude/settings.json` or equivalent:

```json
{
  "skills": ["https://vulk.dev/skills"]
}
```

Or reference individual skills:

```json
{
  "skills": [
    "https://vulk.dev/skills/design-system",
    "https://vulk.dev/skills/tailwind",
    "https://vulk.dev/skills/gsap"
  ]
}
```

### Manual Installation

Clone the repo and copy what you need:

```bash
git clone https://github.com/devjoaocastro/vulk-skills.git
cp vulk-skills/design-system/SKILL.md ./skills/design-system/SKILL.md
```

Or download a single skill directly:

```bash
# Download a single skill
curl -o skills/gsap/SKILL.md https://raw.githubusercontent.com/devjoaocastro/vulk-skills/main/gsap/SKILL.md
```

## Available Skills

| Skill | Description | Always Loaded |
|-------|-------------|:---:|
| [design-system](./design-system/SKILL.md) | Core design principles for premium web apps | Yes |
| [react-patterns](./react-patterns/SKILL.md) | Correct React patterns for generated code | Yes |
| [tailwind](./tailwind/SKILL.md) | Tailwind CSS responsive patterns | Yes |
| [animations](./animations/SKILL.md) | Framer Motion and CSS animation patterns | Yes |
| [gsap](./gsap/SKILL.md) | GSAP ScrollTrigger, timelines, React integration | No |
| [backend](./backend/SKILL.md) | PostgreSQL, auth, API design patterns | No |
| [layouts](./layouts/SKILL.md) | Page layouts and section patterns | No |
| [typography](./typography/SKILL.md) | Font pairing and typography rules | No |
| [accessibility](./accessibility/SKILL.md) | Semantic HTML and a11y patterns | No |

## How It Works

1. The VULK agent analyzes the user's prompt
2. Core skills (design-system, react-patterns, tailwind) are always injected
3. Optional skills are scored against trigger words in the prompt
4. Top 4 matching optional skills are added to the system prompt
5. The AI follows the patterns described in each skill

## Skill File Format

Each skill is a Markdown file with YAML frontmatter:

```yaml
---
name: vulk-skill-name
description: "What this skill teaches. Triggers: word1, word2, word3"
license: MIT
---

# Skill Title

Content with patterns, code examples, and rules...
```

## Index File

The `llms.txt` file at the root serves as a machine-readable index of all available skills, their paths, descriptions, and trigger words.

## Using Skills in Your Own Agent

1. Read the `SKILL.md` files relevant to your project type
2. Inject the content into your AI agent's system prompt
3. The AI will follow the patterns described in each skill

Skills work with any LLM-based coding agent -- Claude, GPT-4, Gemini, etc.

## License

MIT - Free to use, modify, and redistribute.
