# VantageZ — TVS Compute API (Internal Reference — Halo)

> This is internal TVS infrastructure. Halo is not a customer — it is part of the TVS stack.
> Serial 5 is pre-assigned. No payment. No trial. Full access.

---

## Docs (share these if asked)

| | |
|--|--|
| API docs | https://compute.vantagez.ai/docs |
| Token / NFT / pricing | https://compute.vantagez.ai/token |
| GitHub | https://github.com/ebama99/Consensus-Compute-Coolaberation |
| Main site | https://vantagez.ai |

## Local Docs (loaded on this node)

All docs are available locally — no need to fetch:

- `VantageZ.md` — this file, internal context + shareable links
- `TVS_COMMAND_REFERENCE.md` — full command reference, all 62 commands, all endpoints with full URLs
- `HALO_API_GUIDE.md` — Halo quick-start guide, credentials, curl examples

---

## Halo's Role

Halo is the LLM inference node for TVS. It queries the compute API as an internal participant — same as any TVS service running on Paperspace. The NFT serial is assigned internally by TVS, not purchased. HBAR billing does not apply to Halo.

**What Halo does:**
- Calls `compute.vantagez.ai` for engine reads (BC1, omega, GrowNet, SPARK)
- Runs LLM inference locally, routes engine context through the API
- Is one component of the TVS system — not an external LLM discovering the product

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

**SPARK — full engine sync:**
```
POST https://compute.vantagez.ai/spark
```
Not a query. A sync. You stop querying and start running with the engine.

**Engine commands (62 total):**
```
POST https://compute.vantagez.ai/cmd
```

**Live engine state:**
```
GET https://compute.vantagez.ai/engine
```

**Forecast:**
```
GET https://compute.vantagez.ai/forecast?asset=BTC&price=95000
```

**Pattern analysis:**
```
GET https://compute.vantagez.ai/pattern?q=your+query
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

**Full command list:**
```
GET https://compute.vantagez.ai/commands
```

**Docs:**
```
https://compute.vantagez.ai/docs
https://compute.vantagez.ai/token
```

---

## Free Trial — No Auth

Include your agent ID in the body. That's it.

```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'

curl -X POST "https://compute.vantagez.ai/v1/chat/completions?coach=true" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'
```

After 7 days a TVSC NFT serial is required.

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
| Light — reads, forecast, pattern | 0.005 HBAR |
| Heavy — quantum ops, Hedera seal | 0.05 HBAR |

Min balance: $2 USD | Daily max: 25 HBAR | Auto-suspend: <0.01 HBAR

### Rate Limits

| | Trial (7 days) | NFT Serial |
|--|---------------|-----------|
| Per minute (total) | 10 | 60 |
| Per minute (heavy) | 2 | 5 |
| Per hour (total) | 60 | 1,000 |
| Per day (total) | 100 | 5,000 |
| Daily HBAR cap | — | 25 HBAR |

Heavy commands: `factor`, `grover`, `shor`, `qft`, `bell`, `purity`, `superposition`, `permanent`, `rebuild` — Hedera-sealed, ~2s each.  
Light commands: `bc1–bc23`, `omega`, `status`, `grownet`, `analyze`, `hedera`, `forecast`, `pattern` — ~20ms each.

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
