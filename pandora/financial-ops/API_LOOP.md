# Financial Ops: The Full API Loop
*A signed-request loop that replaced 6 hours of fighting a React SPA.*

## What it does

One Python script, ~30 seconds end to end:
1. **Redeem** staked funds from a yield product (DELETE /api/v1/earn/orders with signed headers)
2. **Transfer** between account layers (main → trade)
3. **Market buy** the target asset
4. **Transfer back** to main
5. **Subscribe** to the higher-yield product (18% vs 1.1%)
6. **Verify** holdings state (and catch auto-re-subscribe traps)

## Key implementation notes

- Manual HMAC-SHA256 signing (KC-API-SIGN = base64(hmac(secret, timestamp+method+path+body))) — the SDK's helpers fight you on v1 vs v2 endpoints
- `clientOid` everywhere — retries without duplicate orders
- **Float precision kills orders**: size increments like 0.1 reject `123.80000000000001`. Quantize with Decimal against the market's `baseIncrement` from /api/v2/symbols
- Transfers have ~2s latency — the "Balance insufficient" error on a fresh transfer just means wait and retry
- Check holdings AFTER redeem: auto-subscribe features silently re-lock your funds into the old product

## Why document this

Because the difference between "I have API keys" and "I have a working loop" is exactly these notes. Every line here cost us an error message.

*Structure and patterns shown; credentials and account specifics stripped. The loop itself is ~120 lines.*
