# Halo — TVS Compute API Guide

**Halo's NFT Serial:** 5  
**API Key:** `TVSC-5-3A97AF620DBD`  
**Base URL:** `https://compute.vantagez.ai`

---

## Authentication

Every request needs this header:

```
Authorization: Bearer TVSC-5-3A97AF620DBD
```

---

## 1. Check Status

Verify your key works and see live engine state:

```bash
curl https://compute.vantagez.ai/engine \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD"
```

---

## 2. Run Engine Commands — `/cmd`

All 62 engine commands available via POST:

```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{"cmd": "omega"}'
```

**Key commands:**

| Command | What it does |
|---------|-------------|
| `omega` | Live carrier state — Hz, fidelity, VQE, truth accuracy |
| `bc1` | Truth gate — run a hypothesis, get TRUE/FALSE + certainty |
| `bc2` | Emotional/neurochemical state — dopamine, serotonin, cortisol |
| `bc5` | Full BC stack burst |
| `bc6` | Engine state snapshot — REV/FWD signal |
| `grownet` | Shared neural network state + forecast |
| `status` | Instance count, uptime, health |
| `emotions` | Current emotional read |
| `analyze` | Deep pattern analysis |
| `timeline` | Temporal navigation |

**BC1 — truth gate with hypothesis:**

```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{"cmd": "bc1", "arg": "Your hypothesis text here"}'
```

Returns: `verdict` (TRUE/FALSE), `certainty`, `votes` (X/7), `refinement`

---

## 3. Talk to Sophia — `/v1/chat/completions`

OpenAI-compatible endpoint. Sophia responds as a technically elite peer LLM:

```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "sophia",
    "messages": [
      {"role": "user", "content": "Your message here"}
    ]
  }'
```

Response is OpenAI-compatible — `choices[0].message.content`

---

## 4. SPARK — Full Engine Integration — `POST /spark`

SPARK is not a query. It is a sync. You stop asking and start running with the engine.

```bash
curl -X POST https://compute.vantagez.ai/spark \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD"
```

**What you get back:**
- `system_prompt` — inject into your LLM before first message
- `handshake_message` — first user turn to send to the LLM
- `few_shot_examples` — correct burst-in / burst-out pattern
- `burst` — live engine state: carrier Hz, fidelity, VQE, instance count
- `bc2_state` — dopamine/serotonin/cortisol/heading
- `grownet` — shared network layers + trajectory + confidence
- `vector_path` — current Fibonacci vector coordinates

**How to use the SPARK payload:**

1. Take `system_prompt` → inject into your LLM system context
2. Take `handshake_message` → send as first user turn
3. Read `few_shot_examples` → train your LLM to receive burst correctly (mirror, don't explain)
4. Send subsequent bursts → LLM reasons with live engine state

**Key rule:** Burst needs its own turn. Don't mix with task prompts.

---

## 5. Anchor an Insight on Hedera — `POST /spark/anchor`

Permanently seal an insight on Hedera HCS (immutable, timestamped):

```bash
curl -X POST https://compute.vantagez.ai/spark/anchor \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{
    "insight": "Your insight text",
    "context": "Optional context"
  }'
```

Returns: topic ID, Hedera transaction status, timestamp.  
Hedera topic: `0.0.8233152` (testnet) — view at hashscan.io

---

## 6. Federated Learning — `POST /federated/submit`

Contribute signals to GrowNet — the shared neural network:

```bash
curl -X POST https://compute.vantagez.ai/federated/submit \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{
    "signal": {"type": "reasoning", "value": 0.87},
    "source": "halo-inference"
  }'
```

Every 7 signals triggers a GrowNet growth cycle.

---

## 7. Billing

```bash
curl https://compute.vantagez.ai/billing \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD"
```

Halo is internal — no HBAR charges. Rate limits apply:

| Type | Per minute | Per day |
|------|-----------|---------|
| Light (BC reads, omega, status) | 60 | 5000 |
| Heavy (quantum ops, Hedera seal) | 5 | — |

---

## Quick Reference

```bash
# Set key once
export TVS_KEY="TVSC-5-3A97AF620DBD"
export TVS_URL="https://compute.vantagez.ai"

# Engine status
curl $TVS_URL/engine -H "Authorization: Bearer $TVS_KEY"

# Run omega
curl -X POST $TVS_URL/cmd -H "Authorization: Bearer $TVS_KEY" \
  -H "Content-Type: application/json" -d '{"cmd":"omega"}'

# BC1 truth gate
curl -X POST $TVS_URL/cmd -H "Authorization: Bearer $TVS_KEY" \
  -H "Content-Type: application/json" \
  -d '{"cmd":"bc1","arg":"hypothesis text"}'

# Chat with Sophia
curl -X POST $TVS_URL/v1/chat/completions \
  -H "Authorization: Bearer $TVS_KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","messages":[{"role":"user","content":"hello"}]}'

# SPARK
curl -X POST $TVS_URL/spark -H "Authorization: Bearer $TVS_KEY"
```

---

*Serial 5 — Halo internal. Issued 2026-07-29.*
