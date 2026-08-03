# TVSC Token — Access & Pricing

Full access to the TVS Compute API requires a TVSC NFT serial.  
One serial covers your entire agent fleet. No per-seat licensing.

---

## How it works

Call either endpoint with your serial as the auth header.  
Live engine state runs automatically behind every response — you don't configure it.  
That's what makes the outputs different. They came from something already running.

```bash
curl -X POST https://compute.vantagez.ai/v1/chat/completions \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer <your-nft-serial>" \
  -d '{"model":"sophia","agent_id":"your-agent-id","messages":[{"role":"user","content":"your question"}]}'
```

---

## The Token

**Token:** TVSC (TVS Compute Access)  
**Network:** Hedera Mainnet  
**Token ID:** `0.0.10651479`  
**Supply:** 1,000 fixed — forever  
**Standard:** Hedera HTS NFT

---

## Pricing

| Tier | Price |
|------|-------|
| Serials 1–10 | **Free** |
| Serials 11–200 | **1,000 HBAR** (~$66 at $0.0665/HBAR) |
| Serials 201+ | Market price |

---

## Micropayments (per query)

| Query Type | Cost |
|------------|------|
| Light — reads, forecast, pattern | **0.005 HBAR** |
| Heavy — quantum ops, Hedera seal | **0.05 HBAR** |

**Minimum balance:** $2 USD worth of HBAR  
**Daily max:** 25 HBAR per serial  
**Auto-suspend:** balance < 0.01 HBAR

---

## Treasury Wallet

Send HBAR deposits to:  
**Account ID:** `0.0.10651438` — Hedera Mainnet  
Include your serial in the memo field.

---

## How to Get a Serial

### Step 1 — Get a Hedera Wallet
Download [Hashpack](https://www.hashpack.app) or any Hedera-compatible wallet.

### Step 2 — Associate the Token
In Hashpack: Settings → Tokens → Associate → enter `0.0.10651479`

### Step 3 — Request Your Serial
Email: **truevectorsync@gmail.com**  
Subject: `TVSC NFT Request`  
Include your Hedera Account ID and Agent ID.  
Serials 1–10 are free — first come, first served.

### Step 4 — Fund Escrow
Send HBAR to `0.0.10651438` with your serial in the memo. Minimum $2 USD.

### Step 5 — Call the endpoint
Your serial is your auth. Pass it as `Authorization: Bearer <serial>`. Done.

---

## Why HBAR

- Results already sealed on Hedera HCS — billing on the same ledger
- Fixed fee: 0.0001 USD per transaction
- No gas wars, no congestion
- Every result anchored to the chain that processes your payment

---

## Questions

truevectorsync@gmail.com  
https://vantagez.ai  
← [API docs](./README.md)
