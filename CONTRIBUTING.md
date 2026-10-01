# Contributing to AI Toolkit

We welcome contributions from the community! Here's how to add a skill or agent.

## Adding a Claude Code skill

1. Create a new directory under `skills/` with a descriptive kebab-case name (e.g., `my-new-skill`).
2. Add a `SKILL.md` file with the following structure:

   ```markdown
   ---
   name: my-new-skill
   description: One-line description — what it does and when to use it.
   ---

   # Skill Title

   Brief intro paragraph...

   ## Core Responsibilities
   ...

   ## Required Inputs
   ...

   ## Required Output Format
   ...
   ```

3. Update the skills table in [README.md](./README.md).
4. Open a pull request with a short description and an example prompt that triggers the skill.

## Adding an agent

1. Create a new directory under `agents/` with a descriptive kebab-case name.
2. Include a `README.md` explaining the agent's purpose, inputs, outputs, and how to run it.
3. Update [README.md](./README.md) when the agents section is active.
4. Open a pull request.

## Guidelines

- Use lowercase kebab-case for all directory and file names.
- Write `description` fields that make it clear **when** to use the resource, not just what it does.
- Do not include hardcoded credentials, PII, or organization-specific internal URLs.
- Test your skill or agent locally before submitting a PR.
- Keep skills focused — one skill per task domain.

## Questions?

Open a [GitHub Discussion](../../discussions) or file an [issue](../../issues).
