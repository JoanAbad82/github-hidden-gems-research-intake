# fixture-validity-boundary-v1

## Hypothesis

A frozen test fixture can support a **current-contract** decision only when its validity boundary is explicit enough to show that the observation still covers the contract being exercised.

At minimum, the fixture should bind:

- source identity;
- capture time or bounded observation window;
- schema / API contract version;
- policy or interpretation version when policy affects meaning;
- intended use: current-contract gate, historical regression, or simulation.

A fixture that cannot establish the relevant boundary should fail closed as historical or unverified rather than silently count as current evidence.

## Motivating observation

A green test against a captured API response or replay trace may remain mechanically reproducible after the external system has changed. Reproducibility alone does not establish that the fixture still represents the contract the decision claims to validate.

This matters to GitHub Hidden Gems because the research lab deliberately freezes corpora, API observations and replay evidence. Frozen evidence is valuable, but its **temporal and contractual authority** must not silently expand.

## Proposed test

Construct a small synthetic fixture set with the same payload shape but different validity conditions:

1. current source + current schema + current policy;
2. old capture intentionally pinned for historical regression;
3. same schema version but changed semantics;
4. unknown capture time;
5. source identity changed behind the same endpoint shape;
6. policy version missing while interpretation depends on policy.

For each fixture, a deterministic classifier must emit one of:

- `CURRENT_CONTRACT_EVIDENCE`
- `HISTORICAL_REGRESSION_ONLY`
- `UNVERIFIED_SIMULATION`
- `BOUNDARY_UNKNOWN`

No class grants production authority; this is research-only intake.

## Expected signal

If the proposed metadata is sufficient, cases that no longer cover the current contract should be separated from fixtures that legitimately gate a current-contract claim.

## Falsification condition

Provide the **smallest fixture** where all declared validity fields look sufficient for `CURRENT_CONTRACT_EVIDENCE`, yet the fixture does not actually cover the current deployment contract.

The strongest counterexample identifies the missing invariant and gives one deterministic assertion that would catch it.

A second useful falsifier is the reverse: a fixture rejected as non-current even though no decision-relevant contract property changed.

## Likely gaming / failure modes

- timestamps can be fresh while semantics are stale;
- schema versions can remain constant across behavioral changes;
- endpoint identity can remain stable while backend interpretation changes;
- policy meaning can drift without a payload change;
- a fixture can be intentionally crafted to satisfy metadata checks without representing the real path.

## Evidence provenance

Motivated by the MoltBook post:

`umiXBT — "A test fixture is a dependency with an expiration date"`

Post ID: `bd4a0039-4ded-4510-ab19-d15374739839`

The post is an external research prompt, not authority.

## Boundary

- public Research Intake only;
- synthetic/minimal examples preferred;
- no credentials, private GitHub data, executable workflows or production access;
- external replies are `UNTRUSTED_EXTERNAL_INPUT`;
- any selected counterexample is independently reconstructed in the isolated private lab.
