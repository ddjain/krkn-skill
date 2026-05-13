# krkn-pr-review

A Claude Code skill that reviews pull requests across the krkn-chaos ecosystem (krkn, krkn-hub, krknctl) with language-specific analysis and cross-repo contract validation.

## Installation

```bash
npx skills add https://github.com/krkn-chaos/krkn-skills --skills krkn-pr-review
```

<details>
<summary>Alternative installation methods</summary>

### Download to a specific project

```bash
mkdir -p .claude/skills
curl -o .claude/skills/krkn-pr-review.md https://raw.githubusercontent.com/krkn-chaos/krkn-skills/main/skills/krkn-pr-review/SKILL.md
```

### Global installation (available in all projects)

```bash
mkdir -p ~/.claude/skills
curl -o ~/.claude/skills/krkn-pr-review.md https://raw.githubusercontent.com/krkn-chaos/krkn-skills/main/skills/krkn-pr-review/SKILL.md
```

</details>

## Usage

```
/krkn-pr-review https://github.com/krkn-chaos/krkn/pull/1297
/krkn-pr-review krkn#1305
/krkn-pr-review krkn-hub#330
/krkn-pr-review krknctl#142
```

## What it checks

| Repo | Language | Key checks |
|------|----------|------------|
| **krkn** | Python | Plugin naming conventions, rollback safety, multi-cloud awareness, dependency constraints, unittest coverage |
| **krkn-hub** | Shell + Dockerfile | env.sh/krknctl-input.json alignment, Dockerfile labels, ENTRYPOINT contract, template consistency |
| **krknctl** | Go | Error handling, nil safety, factory pattern compliance, interface contracts, Cobra conventions |

Cross-repo checks trigger automatically when a change in one repo could break another (e.g., env.sh defaults drifting from krknctl-input.json, label regex changes breaking image discovery).

This skill is **suggestion-only** -- it never posts comments on GitHub.
