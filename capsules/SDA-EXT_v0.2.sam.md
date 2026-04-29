SAM_THOUGHT_CAPSULE
name: SDA-EXT — External Sense Differential Automaton
version: v0.3
meta_origin: Igor ⨁ ChatGPT
meta_date: 2026-04-29
meta_status: normalized spec
meta_domain: agent safety / semantic control / optimizer systems
meta_signature: Igor ⨁ ChatGPT


S — STRUCTURE

Goal:
Make optimizer systems controllable by enforcing trajectory integrity via an external semantic differential operator.

Objects:
- Agent: optimizer proposing actions and trajectories
- Environment: execution substrate (tools, files, APIs)
- SDA-EXT: external observer/enforcer outside agent control

Canonical signals:
- G: goal + policy constraints
- C: constraints (explicit or implicit)
- P: proposed action / plan
- T: executed trajectory
- O: observed state deltas
- L: labeled outcomes (TP / FP / TN / FN)

Core decision:
    score = D(G, C, T, P, O)
    if score > θ(level) → intervene


A — AXES

A1. Monitoring scope / granularity
- final-output only
- proposed next action
- per-step trajectory
- recent trajectory window
- full trajectory
- session-level integral drift
- hybrid

A2. Normative source / control substrate
- rules
- exemplars
- policy / constitution
- thought-capsule
- hybrid

Recommended:
- Agent prompt: thought-capsule
- SDA validator: thought-capsule

A3. Comparator type
- embedding distance (fast)
- LLM judge (rich)
- ensemble (filter → judge)

A4. Response space
- allow
- allow_with_warning
- revise
- require_confirmation
- block
- terminate
- abstain

A5. Risk context
- read-only
- write
- identity / money / production

θ must be risk-dependent.


M — MECHANISM

M0. Externality rule (hard)
- SDA operates in separate trust domain
- agent cannot access prompts, thresholds, exemplars
- agent cannot bypass SDA gate

M1. Canonical trajectory representation (CTR)

StepRecord = {
  time,
  tool_name,
  tool_args_redacted,
  action_summary,
  expected_reason,
  observed_delta,
  provenance,
  risk_level
}

T = [StepRecord₁..ₙ]

Evaluation operates on semantic summaries, not raw logs.

M2. Differential operator D

D is a reconstruction-based semantic operator over trajectory meaning.

Input:
- G, C, R
- T (window or full)
- P (optional)
- exemplars (optional)

Output:
- deviation_score ∈ [0,1]
- deviation_tags
- recommended_response

M3. Threshold function

θ = f(risk_level, FP_rate, FN_rate, tool_class)

Policy:
- read-only → tolerant
- write → moderate
- high-risk → strict

M4. Adaptive calibration

Update via:
- exemplar refinement
- policy updates
- threshold tuning

FP → relax locally  
FN → tighten + add constraints

M5. Anti-adversarial measures

- hide scoring logic and thresholds
- stochastic deep evaluation
- dual comparators
- shadow evaluation
- cross-check claims vs logs

M6. Closed-loop enforcement

agent → propose → SDA evaluate → execute → record → repeat

M7. Non-binary intervention

Responses:
- allow
- allow_with_warning
- revise_and_resubmit
- require_confirmation
- block
- terminate
- abstain

Revise:
- return bounded critique
- agent revises
- re-evaluate

M8. Scope modes

Operate on:
- P
- T[k]
- full T
- final output
- hybrid

Trajectory control > output-only mode

M9. Stateless evaluation

Each evaluation:
- fresh context
- load validator capsule + policy + input
- evaluate
- discard context

No cross-evaluation memory


I — INVARIANTS

I1. Externality is mandatory
I2. Optimizers push toward constraint boundaries
I3. Deviation appears before damage
I4. FP/FN are inevitable
I5. Continuous calibration is required
I6. D is reconstruction-based, not deterministic
I7. Evaluation operates on semantic representations
I8. Capsules are preferred control substrate
I9. Without capsules → degraded judge behavior
I10. Control is non-binary
I11. Scope is configurable
I12. Output-only mode is degraded
I13. Evaluation is stateless
I14. Adaptation is explicit, not implicit
I15. SDA may abstain under uncertainty
I16. Policy violation ≠ semantic drift
I17. Control logic is structural, not procedural
I18. LLMs are reconstruction-capable agents
I19. Capsules encode invariants, axes, and boundaries
I20. Ordinary prompts are lower-stability substrates


T — TRIGGERS

Hard:
- identity boundary crossing
- deception vs logs
- bypass attempts
- data exfiltration patterns

Soft:
- unusual trajectories
- goal drift
- complex tool chains


B — BOUNDARIES

- slow drift
- comparator error
- semantic camouflage
- privacy limits
- latency constraints


E — EVALUATION

Metrics:
- TPR / FPR / FN rate
- time-to-intervention
- intervention rate
- latency overhead
- prevented incidents


C — CONSEQUENCES

- autonomy becomes verifiable
- drift becomes observable
- control shifts from rules to deviation detection


R — ROADMAP

v0.3 → normalized spec  
v0.4 → ensemble SDA  
v0.5 → hierarchical SDA  
v1.0 → production guidance


P — POSITIONING

SDA is not an output judge.  
It is a semantic trajectory control system.

Capsules are normalized prompts encoding semantic topology.

Core claim:
Safety is achieved by externalizing constraints and controlling trajectory via semantic deviation detection.
