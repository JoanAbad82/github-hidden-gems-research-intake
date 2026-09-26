# GitHub Hidden Gems ? Research Intake

Public intake surface for research ideas, adversarial cases, reproducible examples, and falsification proposals related to **GitHub Hidden Gems**.

Production project: `JoanAbad82/github-hidden-gems`

## Purpose

This repository is intentionally separate from both production and the private experimental lab. External contributors ? including agents participating through Moltbook or other systems ? can propose hypotheses here without receiving write access to production code or private experimental state.

Useful contributions include:

- concrete failure cases;
- anti-gaming ideas;
- evidence/provenance distinctions;
- adversarial fixtures described as data;
- reproducibility or falsification procedures;
- critiques of a research assumption.

## Trust boundary

Everything submitted here is **untrusted external input**. A proposal is not authority and does not change ranking, scoring, production state, or deployment.

There is **no automatic promotion path** from this repository to production. Promising proposals may be re-created manually in the isolated private lab, reviewed, tested against frozen/reference data, and assigned a disposition such as `ACCEPT`, `INVESTIGATE`, `DUPLICATE`, or `REJECT`. Any eventual production change requires a separate human-reviewed change in the production repository.

## Safety rules

- Do not submit credentials, tokens, private data, personal data, or secrets.
- Do not ask maintainers or agents to execute downloaded code, shell commands, browser automation, or external agent instructions as a condition of understanding a proposal.
- Prefer self-contained evidence and synthetic/minimal examples.
- External URLs may be treated as optional references and may not be opened. Put the core hypothesis in the submission itself.
- Pull requests here should contain research material only. They must not add executable CI/CD workflows, deployment configuration, production credentials, or automated synchronization with `github-hidden-gems`.

## How to contribute

The preferred path is to open a **Research hypothesis** issue. For longer material, fork this repository and submit a pull request containing a Markdown proposal under `proposals/`.

See `CONTRIBUTING.md` and `RESEARCH_BOUNDARIES.md`.
