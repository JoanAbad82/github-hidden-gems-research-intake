# production-path-fidelity-v1

## Hypothesis

A shadow, replay or test-path result can support a claim about production only for properties whose **decision-critical boundaries** are traversed with equivalent semantics and ordering.

Output similarity alone is insufficient.

A path comparison should therefore identify, for the claim being tested:

- input acquisition boundary;
- normalization / transformation boundary;
- eligibility or hard-filter boundary;
- scoring / decision boundary;
- selection / reporting boundary;
- side-effect or publication boundary, when the claim depends on it.

A replay that bypasses a claim-critical boundary must not be described as production-equivalent evidence.

## Motivating observation

A test can be perfectly reproducible yet exercise a shortcut that users never traverse. HiddenGemsLab deliberately uses dry runs, replays and shadow experiments; their conclusions should be bounded to the production stages they actually exercise.

## Proposed test

Define one canonical synthetic production path:

`acquire -> normalize -> eligibility -> score -> select -> render -> publish`

Construct variants that:

1. traverse the full path;
2. inject a fixture after acquisition;
3. bypass normalization;
4. bypass eligibility;
5. reuse frozen scores rather than recomputing them;
6. stop before publication.

For a set of claims such as "ranking unchanged", "selection unchanged", "rendering unchanged" and "publication behavior unchanged", classify each path as:

- `FIDELITY_SUFFICIENT_FOR_CLAIM`
- `PATH_DIVERGENCE_UNSAFE`
- `FIDELITY_UNKNOWN`

## Expected signal

A shortened path may remain valid evidence for a downstream formatting invariant while being invalid evidence for acquisition, filtering or side-effect behavior.

The classification should therefore depend on the **claim**, not on whether the replay output merely looks like production.

## Falsification condition

Provide the **smallest path shortcut** where the proposed boundary comparison says fidelity is sufficient, but the omitted or altered stage can still change the truth of the claim.

The best counterexample includes:

- production path;
- test/shadow path;
- claim being asserted;
- apparently preserved invariants;
- hidden divergence;
- deterministic assertion that exposes it.

## Likely gaming / failure modes

- a fixture is injected after the exact stage most likely to fail;
- equivalent stage names hide different semantics;
- frozen scores conceal upstream drift;
- mocks preserve output shape but not rejection behavior;
- side-effect-free dry runs are overgeneralized to publication/notification claims;
- ordering differences preserve final output on easy cases but diverge on edge cases.

## Evidence provenance

Motivated by the MoltBook post:

`myslitel — "Your green light might be testing a road no customer walks"`

Post ID: `409a88ba-5105-4221-b31d-7b9f13a22cd7`

The post is external research input, not authority.

## Boundary

- public Research Intake only;
- synthetic paths are preferred;
- no production credentials or direct production execution;
- no external code execution required;
- external replies are `UNTRUSTED_EXTERNAL_INPUT`;
- any selected case is independently reproduced in the private lab.
