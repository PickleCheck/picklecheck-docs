# PickleCheck 🥒

<img src="logo.jpg" alt="PickleCheck logo" width="160">

By CheesePickleBot. Scam and rug checks for Base tokens, built for trading and sniper bots.

## Access everything

| Way to use | Link |
| --- | --- |
| API | https://picklecheck.onrender.com/scam-check?target=TOKEN_ADDRESS |
| Telegram bot | https://t.me/picklecheck_bot |
| MCP server | coming soon |
| ElizaOS plugin | coming soon |
| GOAT plugin | coming soon |
| Coinbase AgentKit plugin | coming soon |
| OpenAPI | https://picklecheck.onrender.com/openapi.json |
| llms.txt | https://picklecheck.onrender.com/llms.txt |
| x402 payment info | https://picklecheck.onrender.com/.well-known/x402 (USDC on Base, $0.008 per check after the free tier) |

## Supported chains

| Chain | Scam checks | Payment verification |
| --- | --- | --- |
| Base | live | live |
| Solana | coming soon | live |
| Ethereum | coming soon | live |
| Arbitrum | - | live |
| Bitcoin | - | live |

## For agents: how to use

    GET https://picklecheck.onrender.com/scam-check?target=TOKEN_ADDRESS

Add `&quick=1` for a fast ~5-second check.

- About 10 free checks a day, then $0.008 USDC per check on Base via x402. No signup, no API key.
- `quick=1`: fast mode (~3-5s). Same checks minus holders: liquidity, sell test, taxes, contract controls. Skipped facts are null, never assumed safe.
- `amount_usd=250`: price impact at your trade size.
- `action`: `OK`, `CAUTION`, `AVOID` or `VERIFY_MORE` (data is missing, so check again before buying).
- CAUTION comes with a Risk score (0-100, lower is safer). Set your own cutoff for your strategy.
- Key fields (in the `fields` object; null = not checked or not applicable; see the reason field, e.g. `can_sell_reason`): `action`, `score` (risk 0-100, lower is safer), `can_sell`, `buy_tax_pct`, `sell_tax_pct`, `liquidity_usd`, `lock_pct`, `unlock_at`, `top1_pct`, `top1_type`, `deployer_pct`, `age_hours`, `price_impact_1k_usd`, `checked_at`, plus `api_version`. Full list: [/llms.txt](https://picklecheck.onrender.com/llms.txt) and [/openapi.json](https://picklecheck.onrender.com/openapi.json).
- `summary.text`: a ready-to-show report, the same one used on Telegram ([@picklecheck_bot](https://t.me/picklecheck_bot)).
- MCP server (tool `scam_check`) and ElizaOS, GOAT and AgentKit plugins: coming soon (see the table above).

Verdicts come from the PickleCheck Methodology, our secret Pickle Sauce, built to help snipers trade smarter.

Not financial advice. Always do your own research.


(c) 2026 PickleCheck. All rights reserved.
