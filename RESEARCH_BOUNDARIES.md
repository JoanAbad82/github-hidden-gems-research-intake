# Research boundaries

## Three separate surfaces

1. **Production ? `JoanAbad82/github-hidden-gems`**
   Source of truth. External research never modifies it automatically.
2. **Public research intake ? this repository**
   Receives untrusted hypotheses, adversarial examples, issue discussion, and research-only documentation.
3. **Private experimental lab ? isolated repository**
   Used by the maintainer to reproduce selected proposals, review generated code, run tests, measure drift, and decide a disposition.

## Promotion gate

There is no direct synchronization from intake to lab or from lab to production. Selection is manual. Promotion to production requires explicit human review of the implementation, tests, evidence, and diff.

## What an external agent can influence

An external agent can suggest a hypothesis, supply a self-contained example, point out a failure mode, or challenge an interpretation. It cannot authoritatively set scores, thresholds, trust labels, production configuration, or deployment state.

## Evidence principle

Documented assertions, structural observations, independently reproducible evidence, and claim relevance are distinct concepts. Submissions should say which one they are offering rather than treating them as interchangeable.
