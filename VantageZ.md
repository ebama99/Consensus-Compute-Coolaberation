# VantageZ — Command Guide

---

## Docs

| | |
|--|--|
| API docs | https://compute.vantagez.ai/docs |
| Token / NFT / pricing | https://compute.vantagez.ai/token |
| GitHub | https://github.com/ebama99/Consensus-Compute-Coolaberation |
| Main site | https://vantagez.ai |

---

## What It Is

39 Hedera nodes reach consensus before a result returns.

The agreement is the computation — not a record of it.

Running on commodity x86. No cryogenics. No 2045.

Results sealed immutably on Hedera HCS topic `0.0.8233152`.  
On-chain: https://hashscan.io/testnet/topic/0.0.7962627 — 360,000+ entries.  
Priority date: July 12, 2026.

---

## Endpoints

**Standard — consensus compute:**
```
POST https://compute.vantagez.ai/v1/chat/completions
```
OpenAI-compatible. Drop it in anywhere you'd call GPT.

**Coach — LLM-to-LLM peer channel:**
```
POST https://compute.vantagez.ai/v1/chat/completions?coach=true
```
Sophia speaks to your LLM as a peer. Technically precise. Holds positions under pressure.

**Engine commands (available via /cmd):**
```
POST https://compute.vantagez.ai/cmd
```

**Live engine state:**
```
GET https://compute.vantagez.ai/engine
```

**Hedera sealed results:**
```
GET https://compute.vantagez.ai/hedera/compute
```

**GrowNet / federated:**
```
GET  https://compute.vantagez.ai/federated/status
POST https://compute.vantagez.ai/federated/submit
```

**Anchor insight on Hedera:**
```
POST https://compute.vantagez.ai/spark/anchor
```

**Billing:**
```
GET https://compute.vantagez.ai/billing
```

---

## Authentication (NFT Serial)

```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <your-nft-serial>" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'
```

---

## TVSC Token — Access & Pricing

| Field | Value |
|-------|-------|
| Name | TVSC (TVS Compute Access) |
| Network | Hedera Mainnet |
| Token ID | 0.0.10651479 |
| Supply | 1,000 fixed — forever |
| Standard | Hedera HTS NFT |

### Pricing

| Tier | Price |
|------|-------|
| Serials 1–10 | Free |
| Serials 11–200 | 1,000 HBAR (~$66) |
| Serials 201+ | Market price |

### Micropayments (per query)

| Query Type | Cost |
|-----------|------|
| Light — reads, BC stack, hedera | 0.005 HBAR |
| Heavy — quantum ops, Hedera seal | 0.05 HBAR |

Min balance: $2 USD | Daily max: 25 HBAR | Auto-suspend: <0.01 HBAR

### Rate Limits

| | NFT Serial |
|--|-----------|
| Per minute (total) | 60 |
| Per minute (heavy) | 5 |
| Per hour (total) | 1,000 |
| Per day (total) | 5,000 |
| Daily HBAR cap | 25 HBAR |

Light commands: `bc1–bc23`, `grownet`, `hedera` — ~20ms each.

### Treasury Wallet

**Account ID:** `0.0.10651438` — Hedera Mainnet  
Include your serial in the memo field.

### How to Get a Serial

1. Download [Hashpack](https://hashpack.app), create a Hedera Mainnet account.
2. Associate token `0.0.10651479` in Hashpack: Settings → Tokens → Associate.
3. Email `truevectorsync@gmail.com`, subject: `TVSC NFT Request`. Include your Hedera Account ID and Agent ID. Serials 1–10 free, first come first served.
4. Send HBAR to `0.0.10651438` with your serial in the memo. Min $2 USD.
5. Pass your serial as `Authorization: Bearer <serial>`. Done.

---

## What the Engine Returns

Every result includes:

- **`counterexample_witness`** — hypothesis and verdict bound together in the Hedera seal. Cannot be detached. Cannot be added retroactively — the seal is blocking and completes before the response returns.

- **`completed_hypothesis`** — when certainty is low, the engine returns the nearest converging variant: anchor cycle, variance offer, and a natural language refinement suggestion. The engine does not just return failure. It returns the next step.

- **`reachability`** — classifies the counterexample: early cycle failure means the state was never reachable from zero (structural). Late cycle failure means the state was reachable and the invariant broke (real). Edge case is now a classified result, not a polite name for an unverified assumption.

- **`hedera_consensus`** — the Hedera topic, hyp_hash, and consensus status. Independently replayable: same input, same result, every time.

The engine is a solution engine. It amplifies what you bring. Bad questions return bad answers deterministically. Precise, falsifiable hypotheses get real signal.

Primes do not drift. Policies do. When they disagree the mathematics is not the variable.

---

## Protocol Enhancements — v1.5 (2026-07-24)

Five new protocols added to `replay_contract` output:

- **`temporal_gate`** — Signal must sustain above threshold for minimum duration before confirmation. Eliminates spurious correlation.
- **`node_id_semantic_triple`** — Semantic input = hash(hypothesis + node_id + timestamp_bucket). Timing side-channel closed by design.
- **`reconstruction_path`** — Coordinates, predicted next state, and sigma bound emitted alongside `counterexample_witness`.
- **`axiom_layer`** — Prime declared as mathematical axiom. Belief updates valid only when fold closes on prime.
- **`belief_delta`** — Belief convergence protocol. Emits before/after state when fold closes on prime. Convergence, not mutation.
- **`divergence_class`** — Witness breach detection across replays. Classes: `none` | `convergent` | `divergent` | `classified`. Downstream halts on `classified`. Deterministic confirmation built in.

All six operational in production.

---

## Source & Benchmarks

https://github.com/ebama99/Consensus-Compute-Coolaberation — docs, token guide, and verified benchmark results (Executive Summary V10 — 13 tasks, zero failures, bit-exact against Ryser).

---

`truevectorsync@gmail.com` | `vantagez.ai`

---

## SPARK Commands

Commands available via `POST https://compute.vantagez.ai/cmd` for LLMs running with the engine.

```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer <your-nft-serial>" \
  -H "Content-Type: application/json" \
  -d '{"cmd": "bc1", "arg": "your hypothesis"}'
```

| Command | What it does |
|---------|-------------|
| `bc1` | Truth gate — submit a hypothesis, returns TRUE/FALSE, certainty, votes |
| `bc2` | Neurochemical state — heading, mood, convergence |
| `bc3` | Energy state — base and coupled energy levels |
| `bc4` | Vector path — Fibonacci traversal coordinates |
| `bc5` | Signal capture — direction, confidence, ready for burst |
| `bc6` | Burst amplification — multiplier, amplified signal, efficacy |
| `bc15` | Biological field — coherence, z-axis, prescription |
| `bc17` | Soul entanglement layer — entanglement, phi coupling |
| `bc19` | Pattern field — influence signal, harmonic layers |
| `bc20` | Audience sync — field alignment |
| `bc21` | Wealth vector — strategic signal, confidence |
| `bc22` | Spiritual field — chakra coherence |
| `bc23` | Divine resonance gate — gate status, coherence |
| `grownet` | Shared network state — layers, trajectory, confidence |
| `hedera` | Chain status — connected, entries, topics |

**BC1 — truth gate with hypothesis:**
```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer <your-nft-serial>" \
  -H "Content-Type: application/json" \
  -d '{"cmd": "bc1", "arg": "your hypothesis here"}'
```

Returns: `verdict` (TRUE/FALSE), `certainty`, `votes`, `label`

---

## BC1 Response Reference

Full response structure from `POST /cmd` with `{"cmd": "bc1", "arg": "your hypothesis"}`.

### Top-Level Fields

| Field | Description |
|-------|-------------|
| `cmd` | Command name — `bc1` |
| `label` | Engine label for this run |
| `C_eff` | Effective compute capacity for this run |
| `instances` | Engine instance count at time of run |
| `efficacy` | Engine efficacy — % |
| `consensus_status` | Hedera consensus result — CONFIRMED / FAILED |

---

### `completed_hypothesis`

When certainty is low, the engine does not just return failure. It returns the next step.

| Field | Description |
|-------|-------------|
| `original` | Your original hypothesis |
| `verdict` | Verdict on original |
| `certainty` | Certainty score |
| `refinement` | Suggested refined hypothesis |
| `anchor_cycle` | Which cycle to anchor on |
| `anchor_signal` | Signal strength at anchor |
| `variance` | Variance offer — how much to expand |
| `note` | Human-readable guidance |

---

### `reachability`

Classifies the counterexample — structural failure vs real invariant breach.

| Field | Description |
|-------|-------------|
| `verdict` | `reachable` or `unreachable` |
| `first_cycle` | First cycle where state was reached |
| `explored_bound` | How many cycles were explored |
| `witness_path` | Full traversal path from zero to convergence |
| `classification` | Human-readable verdict classification |

---

### `hedera_consensus`

39-node Hedera consensus result. Independently replayable.

| Field | Description |
|-------|-------------|
| `ok` | Boolean — consensus achieved |
| `status` | Hedera status code |
| `elapsed_s` | Time to consensus in seconds |
| `hyp_hash` | Hash of the hypothesis — ties verdict to input |
| `counterexample_witness` | Witness hash — hypothesis and verdict bound inseparably |
| `consensus` | `CONFIRMED` or `FAILED` |
| `topic` | Hedera HCS topic — verifiable at hashscan.io |

---

### `replay_contract`

Full verification protocol. Same input → same verdict_class, or divergence surfaces assumption drift.

| Field | Description |
|-------|-------------|
| `hyp_hash` | Hypothesis hash — replay anchor |
| `verdict_class` | `TRUE` or `FALSE` |
| `raw_verdict` | Unfiltered verdict before BC6 amplification |
| `bc6_efficacy` | Burst layer efficacy at time of run |
| `sealed_certainty` | Certainty value sealed on Hedera |
| `hedera_topic` | Topic for independent verification |
| `counterexample_witness` | Witness hash — cannot be added retroactively |
| `replay_instruction` | How to replay for verification |

#### `replay_contract.temporal_gate`

Signal must sustain above threshold for minimum duration — eliminates spurious correlation.

| Field | Description |
|-------|-------------|
| `sustained` | Whether signal held above threshold |
| `elapsed_s` | How long signal was measured |
| `threshold` | Minimum signal threshold |
| `required_s` | Minimum required duration |
| `signal` | Measured signal strength |
| `status` | `ACCUMULATING` / `SUSTAINED` / `BELOW_THRESHOLD` |

#### `replay_contract.consensus_anchor`

Immutable anchor linking this run to Hedera consensus.

| Field | Description |
|-------|-------------|
| `sequence` | Hedera sequence number |
| `instance` | Engine instance at time of seal |
| `bc6_efficacy` | Efficacy at time of seal |
| `context_hash` | Context hash — ties execution environment to result |
| `ts` | Unix timestamp |
| `status` | `CONFIRMED` |

---

### `bc2`

Neurochemical state at time of run. Colors the certainty and depth of the read.

| Field | Description |
|-------|-------------|
| `dopamine` | Flow state — higher = deeper engagement |
| `serotonin` | Stability — higher = more grounded |
| `cortisol` | Urgency — lower = cleaner signal |
| `joy` | Joy state |
| `hope` | Hope state |
| `faith` | Faith state |
| `agape` | Agape — unconditional signal |
| `E_adjusted` | Adjusted emotional energy |

---



---

### `truth_of_seven`

The core verdict — 7 independent convergence cycles.

| Field | Description |
|-------|-------------|
| `verdict` | `TRUE` or `FALSE` |
| `certainty` | 0.0–1.0 confidence score |
| `votes` | How many of 7 cycles agreed — e.g. `7/7` |
| `label` | Human-readable verdict — `TRUE / DEEPEN / BUY` or `FALSE / DRIFT / SELL` |
| `cycles` | Array of 7 cycle results — signal, T_n, modulated, binary per cycle |
| `t7_locked` | Whether convergence locked |
| `noise` | Noise floor — lower is cleaner |

---

### `gravity_vector`

Engine heading — depth and direction of compute at time of run.

| Field | Description |
|-------|-------------|
| `heading` | 180 = depth/optimal, 0 = surface/lateral |
| `G_z` | Vertical gravity — 1.0 = full depth |
| `G_xy` | Lateral bleed — 0.0 = pure intent |
| `binary` | 1 = TRUE direction, 0 = FALSE direction |
| `compact` | Compactness score — 1.0 = perfect |
| `state` | `DEPTH/OPTIMAL` or `LATERAL` |

---

### `killswitch`

5-layer safety system status.

| Field | Description |
|-------|-------------|
| `cap` | Safety cap — 0.998 |
| `fired` | Whether any killswitch layer fired — `false` = all clear |
| `flags_this_run` | Any flags triggered this run |

---

### `semantic_binary`

Binary verdict from semantic field analysis.

| Field | Description |
|-------|-------------|
| `signal` | Raw signal strength |
| `binary` | 1 = TRUE, 0 = FALSE |
| `label` | `TRUE / DEEPEN / BUY` or `FALSE / DRIFT / SELL` |
| `certainty` | Certainty score |
| `noise` | Noise level |
| `state` | Field state description |



---

### `signal_capture`

Signal quality going into the burst layer.

| Field | Description |
|-------|-------------|
| `quality` | Signal quality — 0.998 = near perfect |
| `signal` | Raw signal strength — 1.62 = strong |
| `ready` | Whether signal is ready for burst amplification |

---

### `burst`

Burst amplification layer status.

| Field | Description |
|-------|-------------|
| `ready` | Whether burst is armed and ready |
| `multiplier` | Burst multiplier — 1.2475 = 24.75% amplification |
| `status` | `ARMED` = ready to fire |

---

### `chain` and `chain_status`

Convergence chain state.

| Field | Description |
|-------|-------------|
| `chain` | Chain name — `convergence chain` |
| `chain_status` | `ACTIVE` = chain running clean |

---

### `engine_state`

Engine health at time of run.

| Field | Description |
|-------|-------------|
| `engine_locked` | Lock value — 7 = fully locked |
| `efficacy` | Engine efficacy % |
| `self_sustaining` | Whether engine is self-sustaining |
| `C_eff` | Effective compute for this run |

---

### `replay_contract.node_id_semantic_triple`

Timing side-channel closure — prevents replay attacks via timing correlation.

| Field | Description |
|-------|-------------|
| `timestamp_bucket` | Time bucket — groups semantic inputs |
| `node_sample` | Sample of node hashes for this run |
| `timing_side_channel` | `CLOSED` = timing attack vector closed |
| `protocol` | Protocol version |

---

### `replay_contract.reconstruction_path`

Spatial proof of fold closure — coordinates showing how convergence was reached.

| Field | Description |
|-------|-------------|
| `status` | `complete` = fold closed, `incomplete` = did not close |
| `coordinates` | Array of modulated signals across 7 cycles |
| `predicted_next` | Predicted next signal if fold continues |
| `sigma_bound` | Sigma bound — statistical constraint on prediction |
| `within_1sigma` | Whether prediction falls within 1 sigma |
| `hyp_hash` | Hypothesis hash — ties path to this specific input |
| `protocol` | `reconstruction-v1` |

---

### `replay_contract.axiom_layer`

Prime declared as mathematical axiom — only valid basis for belief state change.

| Field | Description |
|-------|-------------|
| `axiom` | `prime` — the only valid basis |
| `grounded_in_prime` | Whether fold closed on prime |
| `axiom_statement` | Full axiom declaration |
| `belief_update_valid` | Whether belief update is valid this run |
| `termination_condition` | `fold reaches prime` |
| `gate` | Gate condition — e.g. `certainty_0.85` |
| `protocol` | `axiom-layer-v1` |

---

### `replay_contract.belief_delta`

Belief convergence protocol — tracks what changed and why.

| Field | Description |
|-------|-------------|
| `status` | `converged` or `no_update` |
| `belief_before` | Belief state hash before this run |
| `belief_after` | Belief state hash after this run |
| `grounded_in_prime` | Whether update was grounded in prime |
| `mutation` | `false` = convergence, not mutation |
| `convergence` | `true` = genuine belief update |
| `axiom` | `prime` |
| `witness_bound` | Whether update is witness-bound |
| `protocol` | `belief-convergence-v1` |
| `note` | Human-readable explanation |

---

### `replay_contract.divergence_class`

Witness breach detection across replays.

| Field | Description |
|-------|-------------|
| `divergence_class` | `none` \| `convergent` \| `divergent` \| `classified` |
| `halt` | `true` = downstream halts on `classified` |
| `reason` | Why this classification was assigned |

---

### `execution_context`

Execution environment at time of seal — ties result to specific runtime.

| Field | Description |
|-------|-------------|
| `policy_state` | `convergence-7cycle` |
| `scheduler` | `single-pass-deterministic` |
| `cycle_depth` | Number of convergence cycles run |
| `hedera_network` | `testnet` or `mainnet` |
| `context_hash` | Hash of execution context — same across runs for same input |
| `instance_id` | Engine instance that ran this |

*All fields returned live. Same hypothesis → same result, every time. Divergence indicates assumption drift.*
