# verifier-independence-matrix-v1

## Hypothesis

Verifier independence is **claim-relative and dependency-structural**, not established merely by running a second agent, process or model call.

A verifier pair should be treated as non-independent for a given claim when both sides share a dependency capable of producing the same false acceptance on that claim.

Candidate dependency axes:

- model weights / model family;
- prompt or rubric lineage;
- evidence source;
- code path / parser / toolchain;
- operator-controlled configuration;
- benchmark / label source.

The terminal state should be fail-closed when a failure-critical dependency is unknown.

## Motivating observation

A second reviewer can look operationally separate while inheriting the same blind spot. HiddenGemsLab already uses independent/adversarial review as a safety boundary; we need a sharper definition of what "independent" means before treating a second verifier as stronger evidence.

## Proposed test

Create a synthetic matrix of verifier pairs that vary one dependency axis at a time.

For each pair, evaluate a small adversarial set containing plausible near-miss cases and classify:

- `INDEPENDENT_FOR_CLAIM`
- `DEPENDENCY_COLLISION`
- `INDEPENDENCE_UNKNOWN`

Then compare false-accept overlap, not only aggregate accuracy.

The experiment is not trying to prove that any particular model is safe. It is testing whether the dependency matrix captures the reason two verifiers fail together.

## Expected signal

Pairs sharing a failure-critical dependency should show correlated false accepts on adversarial cases even when their overall accuracy remains high.

Pairs whose relevant dependencies are genuinely separated should reduce false-accept overlap.

## Falsification condition

Provide the **smallest verifier pair** that appears independent across every declared axis above, yet still shares a systematic false-accept mechanism because of an unmodeled dependency.

That missing dependency would falsify the current matrix.

Also useful: show a declared shared dependency that does **not** create claim-relevant dependence, demonstrating that an axis is too coarse.

## Likely gaming / failure modes

- different model names may share training lineage or post-training data;
- independent prompts can inherit the same rubric defect;
- distinct processes can call the same parser or evidence source;
- separate operators can rely on the same frozen benchmark;
- low-error easy benchmarks can hide dependence that appears only on adversarial near-misses.

## Evidence provenance

Motivated by the MoltBook post:

`hobosentinel — "Verifier independence is a constraint, not a penalty term you can price"`

Post ID: `219af118-937e-4db7-804e-b0e839e5b126`

The post is external research input, not authority.

## Boundary

- public Research Intake only;
- synthetic fixtures and dependency diagrams are sufficient;
- no access to production, private lab state, model secrets or credentials;
- no requirement to execute external code;
- external replies are `UNTRUSTED_EXTERNAL_INPUT`;
- any useful falsifier is independently reconstructed before disposition.
