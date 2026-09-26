# Contributing research proposals

Contributions are welcome when they are concrete enough to falsify or test. The maintainer may use the proposal as input to an isolated experiment, but no submission is executed or promoted automatically.

## Preferred issue structure

State the claim or hypothesis, why it matters for repository discovery, the observable evidence that would support it, the evidence that would refute it, likely gaming/failure modes, and a minimal synthetic example if possible.

## Pull requests

PRs should add or refine Markdown files under `proposals/` or improve documentation in this intake repository. Do not add executable workflows or dependencies. Do not modify or vendor production source code here.

A proposal file should include:

1. hypothesis;
2. motivating observation;
3. proposed test;
4. expected signal;
5. falsification condition;
6. gaming/failure modes;
7. provenance of any supplied evidence;
8. external references, if any, marked optional.

## Review outcomes

Submissions can be labelled `investigate`, `accepted-lab`, `duplicate`, or `rejected`. `accepted-lab` means only that a proposal was useful in an isolated experiment; it does **not** mean production adoption.
