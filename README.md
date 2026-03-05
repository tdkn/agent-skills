# Agent Skills

**English** | [日本語](README.ja.md)

A collection of skill definitions for AI coding agents to extend their capabilities with specialized knowledge and workflows.

## Overview

This repository contains skill definitions that help AI agents understand when and how to use specific tools, APIs, and workflows. Each skill provides:

- Clear use cases and triggers
- Step-by-step workflows
- API patterns and examples
- Best practices and troubleshooting tips

## Structure

```
agent-skills/
└── skills/
    └── sosume/
        └── SKILL.md    # Sosumi skill for fetching Apple documentation
```

## Skills

### [Sosumi](./skills/sosume/SKILL.md)

Fetches Apple documentation as Markdown via Sosumi. Essential for:

- Apple platform APIs (Swift, SwiftUI, UIKit, AppKit, Foundation, etc.)
- Human Interface Guidelines
- WWDC session transcripts
- External Swift-DocC documentation

**Quick Start**: Replace `developer.apple.com` URLs with `sosumi.ai` to get AI-readable Markdown versions of Apple documentation.

## Usage

Each skill is defined in a `SKILL.md` file within its own directory. Skills follow a standard format:

- **Frontmatter**: Name and description
- **When to Use**: Clear triggers for when the skill applies
- **Core Workflow**: Step-by-step process
- **Examples**: Concrete usage patterns
- **Best Practices**: Guidelines for optimal results
- **Troubleshooting**: Common issues and solutions

## Contributing

To add a new skill:

1. Create a new directory under `skills/`
2. Add a `SKILL.md` file following the established format
3. Update this README with a brief description in the Skills section

## License

[Specify your license here]