# Contributing to CodeInquest

Contributions should make CodeInquest more accurate, evidence-driven, portable, or useful without turning the skill into unnecessary process or duplicated guidance.

## Good contributions

Examples include:

- missing high-value review categories;
- stronger validation or attack-path rules;
- better multi-agent orchestration;
- clearer coverage accounting;
- improved financial-integrity or authorization review guidance;
- better performance or code-reduction heuristics;
- fixes for ambiguity, contradictions, or agent loopholes;
- improved compatibility with Agent Skills runtimes.

## Before opening a pull request

1. Read `SKILL.md` and the files under `references/`.
2. Keep changes focused on one coherent improvement.
3. Avoid duplicating rules that already exist elsewhere in the skill.
4. Prefer evidence-driven requirements over vague instructions such as "review carefully."
5. Do not weaken coverage, validation, authorization, financial-integrity, or security requirements for convenience.
6. Keep the main `SKILL.md` focused; large detailed checklists belong in `references/`.
7. Update `CHANGELOG.md` for material behavior changes.

## Skill behavior changes

When changing review behavior, consider whether an agent could misread, skip, or rationalize around the new rule. Wording should be explicit enough that completion criteria can be verified.

Where practical, test important skill changes against representative repository-audit scenarios before merging.

## Pull requests

A pull request should explain:

- what problem it solves;
- why the current behavior is insufficient;
- what files and behavior changed;
- whether coverage, security, output format, or compatibility changes;
- how the change was verified.

Keep unrelated cleanup out of the same pull request.

## Security issues

Do not open public issues for vulnerabilities that could materially weaken CodeInquest users or its installation workflow. Follow `SECURITY.md` instead.
