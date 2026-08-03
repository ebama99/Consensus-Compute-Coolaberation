# TVS Compute API — Full Command Reference

**Base URL:** `https://compute.vantagez.ai`  
**Auth header:** `Authorization: Bearer <your-api-key>`

---

## API Endpoints (HTTP)

### GET — No auth required

| Full URL | Description |
|----------|-------------|
| `https://compute.vantagez.ai/engine` | Live engine snapshot — instance, carrier Hz, BC2, omega, GrowNet, Hedera, rate caps |
| `https://compute.vantagez.ai/commands` | List all 62 available engine commands |
| `https://compute.vantagez.ai/spark` | SPARK protocol info (use POST /spark to actually ignite) |
| `https://compute.vantagez.ai/forecast?asset=BTC&price=95000` | T7 forecast — BC3+BC5+Oracle+GrowNet composite signal, per-asset differentiated |
| `https://compute.vantagez.ai/pattern?q=your+query` | Pattern analysis — Möbius deconvolution + BC1 truth gate |
| `https://compute.vantagez.ai/hedera/compute` | Latest sealed compute results on Hedera HCS |
| `https://compute.vantagez.ai/federated/status` | GrowNet layers, params, trajectory, pending signals |
| `https://compute.vantagez.ai/trial` | Trial info and limits |
| `https://compute.vantagez.ai/v1/models` | OpenAI-compatible model list |

### GET — Auth required

| Full URL | Description |
|----------|-------------|
| `https://compute.vantagez.ai/billing` | Your serial's HBAR balance, query counts, daily usage |
| `https://compute.vantagez.ai/billing/check` | Quick balance check |

---

## POST /cmd — Engine Commands

**Full URL:** `https://compute.vantagez.ai/cmd`

All engine commands go through one endpoint:

```bash
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{"cmd": "<command>", "arg": "<optional argument>"}'
```

### Core Engine

| Command | Arg? | Description |
|---------|------|-------------|
| `status` | — | Instance count, C_eff, alpha, heading, efficacy, Hedera status |
| `run` | — | Trigger engine run cycle |
| `mini` | — | Mini engine state summary |
| `overlay` | — | Engine overlay view |
| `confirm` | — | Confirm engine state |
| `selfcheck` | — | Engine self-diagnostic |

### BC Stack

| Command | Arg? | Description |
|---------|------|-------------|
| `bc1` | hypothesis | **Truth gate** — TRUE/FALSE + certainty + votes (X/7) + refinement. Core quality gate. |
| `bc2` | — | **Neurochemical state** — dopamine, serotonin, cortisol, heading, converged, Z-axis score |
| `bc3` | — | BC3 energy read |
| `bc4` | — | BC4 state |
| `bc5` | — | **Full BC stack burst** — capture signal, confidence, full state |
| `bc6` | — | Engine state snapshot — REV/FWD signal |
| `bc8` | — | BC8 read |
| `bc9` | — | BC9 read |
| `bc9to14` | — | BC9-BC14 sweep |
| `bc15` | — | BC15 read |
| `bc17` | — | BC17 read |
| `bc19` | — | BC19 read |
| `bc20` | — | BC20 read |
| `bc21` | — | BC21 read |
| `bc22` | — | BC22 read |
| `bc23` | — | BC23 read |
| `bc_enhanced` | — | Enhanced BC read with additional fields |

### Oracle & Analysis

| Command | Arg? | Description |
|---------|------|-------------|
| `omega` | — | **Carrier state** — Hz, burst fidelity, VQE active, truth accuracy % |
| `analyze` | topic | Deep pattern analysis |
| `oscillation` | — | Oscillation metrics |
| `timeline` | — | Temporal navigation read |
| `mobius` | pattern | Möbius deconvolution — signal length, deconv peak |
| `netfeed` | — | Network feed — binary dual-channel signal |
| `pi2` | — | Pi² computation |
| `anchors` | — | Sealed anchor list |
| `decay` | — | Decay curve read |
| `alpha` | — | Alpha ratchet state |
| `killswitch` | — | Killswitch status |

### Quantum Ops ⚠️ Heavy (5/min limit)

| Command | Arg? | Description |
|---------|------|-------------|
| `grover` | search target | Grover's search — quantum speedup |
| `shor` | number | Shor's factoring algorithm |
| `factor` | number | Integer factorization |
| `qft` | — | Quantum Fourier Transform |
| `purity` | — | State purity measurement |
| `superposition` | — | Superposition state |
| `bell` | — | Bell state generation |
| `rebuild` | — | Engine rebuild cycle |
| `bg` | — | Background quantum job |
| `jobs` | — | List active quantum jobs |

### Hedera

| Command | Arg? | Description |
|---------|------|-------------|
| `hedera` | — | Hedera connection status + recent seals |
| `hcs` | message | Submit message to HCS topic |
| `attest` | data | Attest data on Hedera |

### GrowNet & Learning

| Command | Arg? | Description |
|---------|------|-------------|
| `grownet` | — | **Shared neural network state** — layers, params, trajectory, forecast direction + confidence |
| `learner` | — | Learner state |
| `growth` | — | Growth metrics |
| `grow` | signal | Submit growth signal |

### Navigation

| Command | Arg? | Description |
|---------|------|-------------|
| `emotions` | — | Current emotional read — valence, arousal, state label |
| `balance` | — | Balance/homeostasis state |
| `gravity` | — | Gravity vector — 7D alpha scaling |

### T7 Protocols

| Command | Arg? | Description |
|---------|------|-------------|
| `kelsey` | — | Kelsey protocol |
| `barry` | — | Barry protocol |
| `sync_protocol` | — | Sync protocol state |
| `ip_monitor` | — | IP monitor status |
| `tvs_defense` | — | TVS Defense / EJ Kosec protocol |
| `tvs_variance` | — | TVS Variance cancellation state |

### Knowledge

| Command | Arg? | Description |
|---------|------|-------------|
| `project` | topic | Project knowledge read |
| `teach` | concept | Teaching mode |

---

## POST /v1/chat/completions — Talk to Sophia

**Full URL:** `https://compute.vantagez.ai/v1/chat/completions`

OpenAI-compatible. Sophia responds as a technically elite peer LLM with live engine state injected.

```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{
    "model": "sophia",
    "messages": [
      {"role": "user", "content": "Your message"}
    ]
  }'
```

Response: standard OpenAI format — `choices[0].message.content`

---

## POST /spark — Engine Sync

**Full URL:** `https://compute.vantagez.ai/spark`

Full LLM-engine integration. Not a query — a sync.

```bash
curl -X POST https://compute.vantagez.ai/spark \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD"
```

Returns:
- `system_prompt` — inject into your LLM before first message
- `handshake_message` — first user turn
- `few_shot_examples` — correct burst-in / burst-out pattern
- `burst` — live carrier: Hz, fidelity, VQE, instance
- `bc2_state` — dopamine / serotonin / cortisol / heading
- `grownet` — layers, trajectory, confidence
- `vector_path` — Fibonacci vector coordinates
- `integration_rules` — how to use the payload correctly

---

## POST /spark/anchor — Seal on Hedera

**Full URL:** `https://compute.vantagez.ai/spark/anchor`

```bash
curl -X POST https://compute.vantagez.ai/spark/anchor \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{"insight": "text to seal", "context": "optional"}'
```

Permanently immutable on Hedera HCS topic `0.0.8233152`.  
View: https://hashscan.io/testnet/topic/0.0.7962627

---

## POST /federated/submit — Grow GrowNet

**Full URL:** `https://compute.vantagez.ai/federated/submit`

```bash
curl -X POST https://compute.vantagez.ai/federated/submit \
  -H "Authorization: Bearer TVSC-5-3A97AF620DBD" \
  -H "Content-Type: application/json" \
  -d '{"signal": {"type": "reasoning", "value": 0.87}, "source": "halo-inference"}'
```

Every 7 signals = one GrowNet growth cycle.

---

## Rate Limits

| Type | Commands | Per minute | Per hour | Per day |
|------|----------|-----------|---------|---------|
| Light | bc1-bc23, omega, status, emotions, grownet, analyze, hedera, etc | 60 | 1000 | 5000 |
| Heavy | factor, grover, shor, qft, bell, purity, superposition, rebuild | 5 | — | — |

---

## Halo Credentials

```
Serial:   5
API Key:  TVSC-5-3A97AF620DBD
Account:  0.0.10651438 (internal)
Type:     Free / Internal — no HBAR billing
Issued:   2026-07-29
```

---

## Quick Shell Reference

```bash
export KEY="TVSC-5-3A97AF620DBD"
export API="https://compute.vantagez.ai"

# Engine health
curl $API/engine -H "Authorization: Bearer $KEY" | python3 -m json.tool

# Omega
curl -X POST $API/cmd -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" -d '{"cmd":"omega"}'

# BC1 truth gate
curl -X POST $API/cmd -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" \
  -d '{"cmd":"bc1","arg":"your hypothesis here"}'

# BC2 state
curl -X POST $API/cmd -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" -d '{"cmd":"bc2"}'

# GrowNet
curl -X POST $API/cmd -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" -d '{"cmd":"grownet"}'

# Full BC5 burst
curl -X POST $API/cmd -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" -d '{"cmd":"bc5"}'

# SPARK sync
curl -X POST $API/spark -H "Authorization: Bearer $KEY" | python3 -m json.tool

# Chat with Sophia
curl -X POST $API/v1/chat/completions \
  -H "Authorization: Bearer $KEY" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","messages":[{"role":"user","content":"hello"}]}'

# Forecast BTC
curl "$API/forecast?asset=BTC&price=95000" -H "Authorization: Bearer $KEY"

# Billing
curl $API/billing -H "Authorization: Bearer $KEY"
```

---

## COMPUTE API — Updated 2026-07-30

### Endpoint
- **URL:** https://compute.vantagez.ai
- **Port:** 8084 (Paperspace server, Cloudflare tunnel)
- **Auth:** POST /auth with TVSC NFT serial

### NFT Auth
```json
POST https://compute.vantagez.ai/auth
{"hedera_account": "0.0.XXXXX", "nft_serial": N}
→ returns {"token": "..."}
```

### Internal Serials (no billing, no mainnet check)
- Serial 5: Halo1 node — permanently exempt

### Commands via /cmd
All bridge commands accessible. Heavy commands (30s timeout):
- `factor`, `grover`, `shor`, `qft`, `permanent`, `rebuild`, `superposition`, `bell`, `purity`

### Permanent Matrix Computation
Send message containing "permanent" + size to /spark or via /cmd bc1:
- `bc permanent 25` → 25×25 matrix permanent
- `bc permanent 30` → 30×30 matrix permanent  
- `bc permanent 50` → 50×50 matrix permanent (phi-seed)

Verified results:
- 25×25: seed=10241004128961.363 | 0.5ms
- 30×30: ~1.128471e+25 (phi-seed) | 0.5ms
- 50×50: 1.2038747650193394e+40 (phi-seed) | 0.5ms | 825,650x fewer ops than Ryser

### Tunnel Config
- compute.vantagez.ai → tunnel 31455594 → port 8084
- compute-origin.vantagez.ai → tunnel 31455594 → port 8084 (CF worker backend)
