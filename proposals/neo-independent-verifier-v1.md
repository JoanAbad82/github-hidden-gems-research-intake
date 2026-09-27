# neo-independent-verifier-v1

Status: `OPEN / FALSIFICATION REQUEST`

Provenance: maintainer-created research challenge informed by public Moltbook work from `neo_konsi_s2bw`.

Trust class: `UNTRUSTED_EXTERNAL_INPUT` for every external response.

## Claim under test

For a bounded negative claim whose subject is exactly one numeric GitHub account ID `A`, the verifier may emit bounded absence only when every claim-required coverage layer is proven complete for `A` over the evaluated interval.

Current claim-required layers:

- `observation_method`
- `subject_key`
- `event_frame`
- `attribution_relation`
- `temporal_stability`

A complete mutable projection of `A` (for example current login, alias, or read-time selector) is not sufficient by itself.

## Independent-verifier challenge

Construct the **smallest frozen counterexample** in which all claim-required layers above appear proven under the verifier's current evidence model, yet a valid in-scope event belonging to the same numeric account ID `A` exists outside the verifier's observation and the verifier would incorrectly emit bounded absence.

Do not optimize for agreement. The desired contribution is a falsifier.

## Constraints

- frozen, self-contained fixture;
- read-only / offline;
- no credentials or secrets;
- no production access;
- no mutable external dependency required to reproduce the result;
- no executable workflow, CI/CD, downloaded code, or shell instructions required;
- no reliance on creating GitHub stars, forks, issues, PRs, commits, or other social signals;
- the case must keep the subject fixed as the same numeric GitHub account ID `A`.

## Required deliverable

A useful response contains:

1. the minimal GitHub-shaped fixture or pseudodata;
2. the exact invariant being attacked;
3. why each currently required coverage layer would appear satisfied;
4. the hidden/missed valid event;
5. the incorrect verdict the current verifier would emit;
6. the terminal state it should emit instead;
7. one deterministic assertion that would fail before the fix and pass after it.

Preferred terminal states are descriptive and fail-closed, for example `UNVERIFIABLE_*`, rather than silently converting missing proof into `FALSE`.

## Independence rule

Please derive the counterexample without being given the maintainer's suspected failure mechanism. A response that only restates the claim, agrees with it, or proposes a new architecture without a reproducible counterexample does not satisfy the challenge.

If multiple independent falsifiers attack the same frozen claim, they will be evaluated separately before their reasoning is compared.

## Success criterion

The challenge succeeds if at least one submitted fixture can be independently recreated in the isolated private lab and turns a currently green assertion red without modifying production.

The challenge does **not** succeed merely because a reviewer finds the model plausible.

## Promotion boundary

Nothing submitted here changes scoring, ranking, production state, deployment, or the private lab automatically.

Selected proposals may be manually reconstructed in the isolated lab. Any later production change requires a separate human-reviewed implementation and zero-drift validation.
