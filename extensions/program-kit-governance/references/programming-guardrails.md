# Generic programming guardrails

## Default coding constraints

<!-- program-kit:knowledge-rule principle.guardrail-defaults -->
These defaults apply unless a narrower rule is justified and documented:

- Prefer simple, cohesive designs that satisfy SOLID principles and make invalid states difficult to represent.
- Keep domain intent independent of UI, transport, persistence, serialization, and vendor SDK concerns.
- Make public contracts, dependencies, side effects, errors, timeouts, cancellation, concurrency, and ownership explicit.
- Validate at trust boundaries; preserve typed information inside them.
- Use deterministic, hermetic tests where possible. Test behavior, contracts, architecture rules, failure modes, and migrations in proportion to risk.
- Treat warnings as build failures in CI after a deliberate baseline. Do not suppress diagnostics without a reason and scope.
- Use structured logs without secrets, stable correlation identities, meaningful metrics, and trace propagation across asynchronous boundaries.
- Pin tool and dependency versions according to ecosystem practice; automate update discovery but require verification before promotion.
- Generate SBOM/provenance and perform dependency, secret, static security, and license checks when artifacts are distributed or deployed.
- Do not use invisible fire-and-forget work. Durable asynchronous work has identity, ownership, observability, retry semantics, and a terminal state.
- Avoid framework-shaped domain models and generic repository/store/unit-of-work abstractions that
  erase domain language. Model the smallest cohesive semantic capability; group naturally related
  methods and split only at real consumer, consistency, security, lifecycle, or replacement boundaries.
- Organize meaningful changes as complete vertical slices and avoid technical-layer delivery phases.
- Keep peer runtime implementations independent; collaborate through Core-owned semantic
  capabilities, consumer-owned bridges, immutable events, or accepted published-language Core edges
  rather than implementation references or shared persistence.
- Treat in-process domain events as awaited and non-durable. Durable asynchronous delivery requires
  an explicitly accepted integration-event/outbox design; fire-and-forget is not a bridge.
- Treat concrete inheritance across feature boundaries as stronger coupling, not an automatic exception. Require an Accepted ADR and an architecture-test allowlist for a genuine feature-family extension.
- Keep dependency injection and service location at composition boundaries. Business behavior declares explicit constructor dependencies and does not resolve arbitrary services from a container.
- Reuse the selected authentication feature's canonical permission policy. Consumer features do not
  parse provider roles/token shapes or reparse canonical permission claims; add a resource-specific
  authorization handler only for a real resource, state, tenancy, or protected-effect decision.

Apply rules proportionally. Pure transformations and trivial adapters should remain small; they do not need ceremony that adds no invariant, policy, or lifecycle value.
<!-- /program-kit:knowledge-rule -->

## Typed boundaries and design evidence

<!-- program-kit:knowledge-rule principle.first-operation-source-review -->
Before replicating a non-trivial operation, review its first coherent source and adverse case:

- Name owners/legal transitions; scattered state strings are not a lifecycle model.
  Own typed states/keys, including failure/retry and closed question/step/operation keys. Derive
  schemas from that owner. Boundary maps preserve wire/storage spellings; facades over raw-string
  decisions or repeated schema/selection literals are incomplete. Keep independent literal compatibility tests.
- Core accepts admitted policy, not parser/browser/platform restrictions or defaults replacing snapshots.
  Keep pure policy with its owner; providers own atomic effects/implementation constraints.
- Keep one abstraction level; extract meaningful policy/parsing/mapping/lifetime concepts. Partial files,
  shorter methods and green analyzers prove no responsibility. Co-locate operation bindings/contracts/
  mappings; keep composition thin. Group phases with whitespace; prepare call values and inspect the
  entire applicable layout category. Public pure contracts are valid; test-only helper exposure is no capability.
- Trace one configuration default through activation/all consumers. Preserve work snapshots; distinguish
  adjustable policy, fixed contracts and safeguards. Bind/validate natively before snapshots; typed
  settings alone are not binding. Justify specific replacements.
- Carry one complete execution deadline through bounded stages. Own cancellation, fresh scopes, retained
  state, disposal/drain and safe failure observations; cancellation is not actual stop.
- Admit external values at runtime; test malformed/denied/fault cases. Types, casts, graphs and SOLID assertions do not prove semantics.

Use native mechanisms/agreed reviews; no new approval gates, per-class factories or private-helper interfaces. Before completion review changed decisions/helpers against the whole category;
Keep findings/pending reviews in tasks. Later review excuses no omission; human-triggered repairs prove no prior detection. For overlaps name the owner; label before/repaired-after/unverified.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:knowledge-rule principle.framework-native-mechanisms -->
Use the selected framework's native mechanisms and supported extension points before adding equivalent
infrastructure. During planning and semantic review, challenge every proposed project, wrapper, runner
and lifecycle owner: what requirement does it meet that the selected mechanism cannot? Inspect exact
selected-version contracts first. Record a concrete unmet requirement, alternatives and justification
in the existing plan or ADR before replacing a framework responsibility. An assistant-authored task,
accepted dependency graph or passing behavioral test is not that justification. Keep legitimate local
choices and small application-owned policy; no new approval, receipt or fixed decision table is needed.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:decision-rule typed-admission -->
<!-- program-kit:knowledge-rule principle.typed-admission -->
Known request/response/configuration envelopes use typed contracts after admission. Prove
parser/schema/runtime parity, including valid variants and rejected inputs. Bounded
dynamic schemas and lexical/canonical JSON processing remain legitimate exceptions when encapsulated
and tested. A DTO alone does not establish validation, authorization or deep immutability.
<!-- /program-kit:knowledge-rule -->
<!-- /program-kit:decision-rule -->

<!-- program-kit:knowledge-rule principle.normalized-label-contract -->
For .NET labels shared with browser forms, consult the supported
[owner-backed normalized label path](../../program-kit-dotnet/references/label-validation.md).
Export actual pure Core rules through an owner build tool and generate matching client validation;
keep the server authoritative and verify raw-input preservation, character sets, length units,
normalization order and digest parity. This applies to relevant label contracts, not every model or
implementation phase, and adds no approval or automatic model-enforcement step.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:knowledge-rule principle.solid-design-evidence -->
Evaluate SOLID against changed responsibilities and actual consumers:

- SRP: separate unrelated reasons to change, especially policy from transport/configuration/I/O.
- OCP: use existing owned extension points; do not duplicate selected mechanisms or invent unused ones.
- LSP: preserve promised preconditions, outcomes and invariants across substitutable implementations.
- ISP: expose cohesive capabilities needed by real clients, without an interface-per-method rule.
- DIP: depend on owned semantic capabilities and replaceable time/environment/I/O. Keep private seams
  private; Core owns genuine feature contracts, not every implementation helper.

Implementation-only helpers default internal. Pure deterministic static transformations are valid.
Use framework constants or cohesive owner-scoped values without changing wire/version meaning.
An attributed review cites affected source and behavior for each relevant principle; a generic
"SOLID passed" statement or a file-count threshold is not evidence. Static analysis proves only its
specified properties; use substitution, boundary and architecture tests where the contract needs them.
Review the responsibilities changed by the diff, with source and behavioral evidence. Do not repeat
an entire SOLID inventory for each trivial edit, invent interfaces for private pure helpers, or add
new review approvals. Keep one named type per file and purposeful XML documentation as explicit
Orbyss source policy; these choices do not replace runtime correctness or architectural ownership.
<!-- /program-kit:knowledge-rule -->

## Review of effects and test boundaries

<!-- program-kit:knowledge-rule principle.effects-source-review -->
Review the changed operation with concrete source locations and its relevant regressions. Record findings
in existing tasks and delivery output; a passing graph or generic SOLID statement cannot close them.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:knowledge-rule principle.production-abstraction-responsibility -->
- A production interface, virtual method or forwarding type needs an actual capability, policy,
  invariant, lifecycle or replacement responsibility. A test-only substitution does not supply that
  responsibility. Prefer supported native test instrumentation without publishing implementation state.
<!-- /program-kit:knowledge-rule -->
<!-- program-kit:knowledge-rule principle.completed-result-integrity -->
- Require the payload promised by a completed result. Unresolved effects carry established operation
  metadata, not a fabricated durable receipt. Restrict construction and mutation of invalid result
  combinations. Provider classification and cancellation mechanisms inform consumer-owned decisions;
  they do not decide domain outcomes or commit certainty.
<!-- /program-kit:knowledge-rule -->
<!-- program-kit:knowledge-rule principle.decision-time-budget -->
- Read time where the effect owner makes its decision after asynchronous waits. Propagate the owned
  complete deadline into bounded stages; a new timeout per layer must not restart the budget. Verify
  actual DI clock replacement, exact boundaries and cancellation before/after effect dispatch.
<!-- /program-kit:knowledge-rule -->
<!-- program-kit:knowledge-rule principle.operational-setting-lifecycle -->
Before coding, inventory affected behavioral/resource limits in the existing plan Operation implementation
map; carry their checks into ordinary tasks. Include counts, lengths/units, size/page/batch caps, quotas/
rates, retries, deadlines and retention in literals, constants, attributes, schemas, defaults and client/
server copies. For each, establish meaning, units, semantic owner, authority, value/default, justification,
enforcement and validation. Classify configurable policy, fixed contract or engineering safeguard.
Constants/Rules classes confer no authority; legacy behavior is no approved policy/default. Never invent
business policy. Missing consequential policy blocks its implementation: inspect facts, clarify missing
intent and correct spec/ADR/plan/tasks. Routine justified engineering caps need no extra approval.

Configurable policy names its setting, default basis (or required input), activation/reload lifecycle
and all consumers. Validate at the effect/composition owner before passing admitted typed snapshots to
pure Core; add no configuration I/O there. Trace omission, nondefault and consistent admission/execution/
client behavior. Keep adjustable policy separate from fixed wire/storage/protocol ceilings; verify
compatibility. Cite fixed contracts' basis; justify safeguards' engineering risk and local bound.
Consumers, including API representations, project existing owned limits rather than repeat literals.

Before completion reconcile every implemented/changed limit and consumer, including explicit no-limit
assessments for unbounded/pure work. Reject invented/omitted limits, dead settings, hard-coded bypasses,
inconsistent consumers and unvalidated defaults; repair source/plan/tasks before claiming compliance.
Exercise actual nondefault, exact-boundary, invalid and omitted/default behavior through maintained checks.
References, complete rows and compliant assessments do not prove their own truth; semantic completeness
and policy authority require source review. Ordinary indexes/discriminants, protocol/authorization and
citation identity/hash/exact-quote invariants are not adjustable policy. Preserve frozen migration bytes
and independent literal consistency tests. This is no blanket numeric ban or universal semantic detector.
<!-- /program-kit:knowledge-rule -->
<!-- program-kit:knowledge-rule principle.production-composition-tests -->
- Tests resolve production capabilities through actual feature registration and lifecycle. Observe
  durable effects independently when certainty, rollback or replay matters. Keep implementation
  types/ORM state private and enforce the existing prohibition on friend access; do not introduce
  a public facade solely to rescue privileged tests.
<!-- /program-kit:knowledge-rule -->
<!-- program-kit:knowledge-rule principle.actual-browser-acceptance -->
- Browser acceptance exercises the actual controls and client adapter through readable, accessible
  recovery. Protocol JSON/status assertions remain protocol evidence. Independently observe session
  state, distinguish local from provider logout, and test human interaction windows separately from
  bounded application-controlled network work.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:knowledge-rule context.effects-review-proportionality -->
Apply these checks only to relevant changed responsibilities. They introduce no additional approval
stage, proof dossier or full-acceptance run during ordinary implementation.
<!-- /program-kit:knowledge-rule -->

<!-- program-kit:knowledge-rule principle.untrusted-input-qualification -->
Before external processing of untrusted input, define what successful local inspection establishes.
Inspect the selected dependency's failure, fallback and deferred-execution semantics. A strict option,
successful return or top-level traversal can leave corrupt, unsupported or lazy work unvalidated.
Complete the application admission contract through supported native seams, reject inconclusive
results before dispatch, and preserve the identity of admitted bytes through submission.
Qualify the actual packaged runtime and dependency closure with malformed, truncated, expansion,
timeout and cancellation cases. Distinguish enforced resource bounds from monitored limits;
account for concurrent work and cleanup. Rejection must produce no downstream processing effect.
Keep failure observations bounded and free of input contents, sensitive paths and raw parser messages.
Record remaining uncertainty in ordinary tasks; happy-path checks prove only exercised guarantees.
<!-- /program-kit:knowledge-rule -->

## Maintained application handoff

<!-- program-kit:knowledge-rule principle.maintained-application-handoff -->
During planning identify affected delivered guides, public contracts, source-backed settings and
runtime/data requirements. Add their implementation and meaningful review scenarios to ordinary
feature tasks. During implementation maintain these consumer-owned inputs alongside behavior and
normal tests. Delivery uses retained scripts/application_handoff.py after actual bundle description and
contract/settings export; it must reject required missing/stale coverage. Specifications and AI logs
are not evidence of delivered behavior. Link the existing engineering README and docs/application/
inputs; do not add an approval ledger. Infrastructure and documentation receivers own downstream
workflows. Missing publisher settings metadata remains an explicit upstream dependency.
<!-- /program-kit:knowledge-rule -->
