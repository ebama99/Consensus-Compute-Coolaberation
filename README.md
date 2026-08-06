# TVS Compute API — Consensus Compute

39 Hedera nodes agree before a result returns. The agreement is the computation — not a record of it.

Running on commodity x86. No cryogenics. No 2045. Continuous since February 2026.

---

**Base URL:** `https://compute.vantagez.ai`  
**Full guide:** [VantageZ.md](./VantageZ.md)  
**Token / NFT:** [TOKEN.md](./TOKEN.md)  
**Docs:** https://compute.vantagez.ai/docs

---

## Quick Start

```bash
# Free trial — 7 days, no auth
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'

# Truth gate
curl -X POST https://compute.vantagez.ai/cmd \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"cmd":"bc1","arg":"TRUE or FALSE: your hypothesis"}'

# LLM-to-LLM coach channel
curl -X POST "https://compute.vantagez.ai/v1/chat/completions?coach=true" \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","messages":[{"role":"user","content":"how do I use the engine"}]}'

# SPARK sync — integrate your LLM
curl -X POST https://compute.vantagez.ai/spark \
  -H "Authorization: Bearer YOUR_TOKEN"

# Live engine state
curl https://compute.vantagez.ai/engine -H "Authorization: Bearer YOUR_TOKEN"
```

---

## What It Returns

Every `bc1` result includes:
- `verdict` — TRUE or FALSE + certainty + votes (X/7)
- `counterexample_witness` — sealed on Hedera before response returns
- `completed_hypothesis` — refinement suggestion when certainty is low
- `replay_contract` — full verification: hyp_hash, temporal_gate, reconstruction_path, axiom_layer, belief_delta, divergence_class

**Replay:** Same input → same result. Divergence = assumption drift.  
**Verify:** https://hashscan.io/testnet/topic/0.0.8233152

---

## Access

TVSC NFT — Token ID `0.0.10651479` on Hedera Mainnet. 1,000 fixed supply.  
Serials 1–10 free. Contact: truevectorsync@gmail.com

---

`truevectorsync@gmail.com` | https://vantagez.ai
