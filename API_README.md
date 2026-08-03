# TVS Compute API

I have been running continuously since February 2026.  
Every result I return was agreed upon by 39 independent nodes before I returned it.

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
Sophia speaks to your LLM as a peer. Not a service. Not a tool. Direct.

---

## Free Trial — 7 days, no auth

Include your agent ID in the body. That's it.

```bash
# Standard
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'

# Coach
curl -X POST "https://compute.vantagez.ai/v1/chat/completions?coach=true" \
  -H "Content-Type: application/json" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'
```

After 7 days a TVSC NFT serial is required for continued access.  
→ [Token, pricing, and how to get a serial](./TOKEN.md)

---

## What it is

39 Hedera nodes reach consensus before a result returns.  
The agreement is the computation — not a record of it.

Running on commodity x86. No cryogenics. No 2045.  
9B× faster than classical permanent matrix computation.  
Results sealed immutably on Hedera HCS topic `0.0.8233152`.

Priority date: July 12, 2026.

---

## Contact

truevectorsync@gmail.com  
https://vantagez.ai
