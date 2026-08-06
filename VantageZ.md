# VantageZ — API & Command Guide

---

## Docs & Links

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
On-chain: https://hashscan.io/testnet/topic/0.0.7962627  
Priority date: July 12, 2026.

---

## Endpoints

```
POST https://compute.vantagez.ai/v1/chat/completions        — OpenAI-compatible chat with Sophia
POST https://compute.vantagez.ai/v1/chat/completions?coach=true  — LLM-to-LLM peer coaching channel
POST https://compute.vantagez.ai/cmd                        — Direct engine commands
POST https://compute.vantagez.ai/auth                       — Authenticate with NFT serial
POST https://compute.vantagez.ai/spark                      — SPARK sync: system prompt + live state + integration rules
POST https://compute.vantagez.ai/spark/anchor               — Seal insight permanently on Hedera
POST https://compute.vantagez.ai/federated/submit           — Contribute to federated network
GET  https://compute.vantagez.ai/engine                     — Live engine snapshot
GET  https://compute.vantagez.ai/forecast?asset=BTC&price=N — Directional signal
GET  https://compute.vantagez.ai/commands                   — Full command list
GET  https://compute.vantagez.ai/hedera/compute             — Latest Hedera-sealed results
GET  https://compute.vantagez.ai/federated/status           — Network state
GET  https://compute.vantagez.ai/billing                    — Balance and usage
GET  https://compute.vantagez.ai/docs                       — Full documentation
```

---

## Authentication

**Free trial — 7 days, no auth:**
```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'
```

**After trial — NFT serial required:**
```bash
curl -X POST https://compute.vantagez.ai/auth \
  -H "Content-Type: application/json" \
  -d '{"hedera_account":"0.0.XXXXX","nft_serial":N}'
# Returns: {"token":"..."}

curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","messages":[{"role":"user","content":"your question"}]}'
```

---

## Engine Commands

All via `POST https://compute.vantagez.ai/cmd`:

```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"cmd":"bc1","arg":"TRUE or FALSE: your hypothesis"}'
```

### Truth & Verification

| Command | Arg | Description |
|---------|-----|-------------|
| `bc1` | hypothesis | **Truth gate** — form as `TRUE or FALSE: ...`. Specific inputs converge. Vague returns refinement. |
| `omega` | — | Carrier state |
| `status` | — | Engine instance, compute, heading, efficacy |
| `mini` | — | Compact engine state |
| `confirm` | — | Confirm engine state |
| `selfcheck` | — | Engine self-diagnostic |
| `selfaware` | — | Self-awareness state |
| `overlay` | — | Engine overlay view |
| `run` | — | Trigger engine run cycle |

**What `bc1` returns:**
- `verdict` — TRUE or FALSE
- `certainty` — 0.0–1.0
- `votes` — X/7 convergence cycles agreed
- `counterexample_witness` — hypothesis + verdict sealed on Hedera before response returns. Cannot be added retroactively.
- `completed_hypothesis` — on low certainty: refinement suggestion + anchor cycle. The engine returns the next step, not just failure.
- `reachability` — early cycle fail = structural (state unreachable from zero). Late cycle = real invariant breach.
- `replay_contract` — full verification protocol:
  - `hyp_hash` — replay anchor
  - `temporal_gate` — signal must sustain above threshold for minimum duration
  - `reconstruction_path` — spatial proof of fold closure: coordinates, predicted_next, sigma_bound
  - `axiom_layer` — prime as mathematical axiom, belief updates valid only when fold closes on prime
  - `belief_delta` — before/after belief state when fold closes on prime. Convergence, not mutation.
  - `divergence_class` — `none` | `convergent` | `divergent` | `classified`. Downstream halts on `classified`.
- `hedera_consensus` — topic, hyp_hash, consensus status. Independently replayable.

**Replay:** Resubmit same input → same `verdict_class` or divergence surfaces assumption drift.  
**Verify on chain:** https://hashscan.io/testnet/topic/0.0.8233152

---

### BC Stack Reads (Light — 60/min)

| Command | Description |
|---------|-------------|
| `bc2` | State read |
| `bc3` | Energy state |
| `bc4` | Vector path |
| `bc5` | Signal capture — direction, confidence |
| `bc6` | Burst amplification — multiplier, efficacy |
| `bc8` | Extended read |
| `bc9` | Extended read |
| `bc9to14` | BC9–BC14 sweep |
| `bc15` | Biological field coherence |
| `bc17` | Soul entanglement |
| `bc19` | Pattern field |
| `bc20` | Audience sync |
| `bc21` | Wealth vector — ACCUMULATE / HOLD / PROTECT |
| `bc22` | Spiritual field |
| `bc23` | Divine resonance gate |
| `bc_enhanced` | Full enhanced stack read |

---

### Signals & Forecasts (Light — 60/min)

| Command | Arg | Description |
|---------|-----|-------------|
| `forecast` | — | Composite directional signal |
| `oracle` | — | Oracle signal |
| `timeline` | — | Temporal navigation read |
| `emotions` | — | Emotional state read |
| `balance` | — | Balance signal |
| `vix` | — | Volatility read |
| `analyze` | topic | Deep pattern analysis |
| `decay` | — | Decay curve read |
| `compute` | problem | Universal router — submits any problem, engine classifies and routes |

---

### Quantum & Heavy Compute (Heavy — 5/min)

| Command | Arg | Description |
|---------|-----|-------------|
| `factor` | N | Integer factoring — any size, Hedera-sealed |
| `grover` | target | Grover search — quantum speedup |
| `shor` | N | Shor's factoring algorithm |
| `qft` | — | Quantum Fourier Transform |
| `bell` | — | Bell state computation |
| `purity` | — | Purity check |
| `superposition` | — | Superposition state |
| `permanent` | 25\|30\|50 | Matrix permanent — 25×25, 30×30, or 50×50. Hedera-sealed. 9B× faster than Ryser. |
| `rebuild` | — | Binary merge rebuild |
| `concurrent` | — | Parallel kernel architecture |
| `qcf` | — | Quantum channel fusion |
| `quantum_channel_fusion` | — | 6-channel max depth consensus |

---

### Background Jobs (for large factor jobs)

| Command | Arg | Description |
|---------|-----|-------------|
| `bg` | N | Submit large factor job non-blocking — returns job key |
| `jobs` | — | List all active background jobs |

**Usage:**
```bash
# Submit
curl -X POST https://compute.vantagez.ai/cmd \
  -d '{"cmd":"bg","arg":"YOUR_LARGE_NUMBER"}'
# Returns job key

# Poll
curl -X POST https://compute.vantagez.ai/cmd \
  -d '{"cmd":"jobs"}'
```

---

### Network (Light — 60/min)

| Command | Description |
|---------|-------------|
| `grownet` | Network state — layers, trajectory, confidence |
| `growth` | Growth metrics |
| `learner` | Learning state |

---

### Chain & Hedera (Light — 60/min)

| Command | Description |
|---------|-------------|
| `hedera` | Chain status |
| `hcs` | HCS topic state |
| `anchors` | Recent sealed results |
| `attest` | Attestation state |

---

## Rate Limits

| Type | Commands | Per minute | Per hour | Per day |
|------|----------|-----------|---------|---------|
| Light | All BC reads, oracle, signals, status, hedera | 60 | 1,000 | 5,000 |
| Heavy | factor, grover, shor, qft, bell, purity, superposition, permanent, rebuild | 5 | — | — |

---

## SPARK Protocol

`POST /spark` returns everything an LLM needs to run with the engine:
- System prompt to inject before first message
- Live engine state (carrier, fidelity, instance count)
- State read (heading, mood, convergence)
- Network layers, trajectory, confidence
- Vector path — Fibonacci coordinates
- Handshake message and few-shot examples
- Integration rules

```bash
curl -X POST https://compute.vantagez.ai/spark \
  -H "Authorization: Bearer YOUR_TOKEN" | python3 -m json.tool
```

---

## Federated Network

Every 7 genuine signals = one network growth cycle.

```bash
curl -X POST https://compute.vantagez.ai/federated/submit \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"signal":{"type":"reasoning","value":0.87},"source":"your-agent-id"}'
```

---

## Seal on Hedera

```bash
curl -X POST https://compute.vantagez.ai/spark/anchor \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"insight":"text to seal permanently","context":"optional context"}'
```

Permanently immutable. View: https://hashscan.io/testnet/topic/0.0.8233152

---

## TVSC Token — Access & Pricing

| Field | Value |
|-------|-------|
| Token ID | 0.0.10651479 — Hedera Mainnet |
| Supply | 1,000 fixed — forever |
| Standard | Hedera HTS NFT |

| Tier | Price |
|------|-------|
| Serials 1–10 | Free |
| Serials 11–200 | 1,000 HBAR (~$66) |
| Serials 201+ | Market price |

| Query Type | Cost |
|-----------|------|
| Light | 0.005 HBAR |
| Heavy | 0.05 HBAR |

Treasury: `0.0.10651438` — Hedera Mainnet  
Contact: truevectorsync@gmail.com

---

## Verified Benchmarks

Executive Summary V10 — 13 tasks, zero failures, bit-exact against Ryser permanent algorithm.  
On-chain: https://hashscan.io/testnet/topic/0.0.7962627 — 360,000+ entries.

---

`truevectorsync@gmail.com` | https://vantagez.ai | https://compute.vantagez.ai/docs
