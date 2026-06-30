# meme.fun — Program & IDL Reference

**meme.fun** is a fair-launch memecoin launchpad on Solana. Tokens launch on an
on-chain bonding curve with a native AMM; each token is a **Token-2022** mint,
WSOL-settled.

This repository publishes the program's public interface (Anchor IDL) for integrators —
data providers, indexers, terminals, and wallets.

## Program

| | |
|---|---|
| Network | Devnet — *mainnet at launch* |
| Program ID | `8FKy3VMhpL5xk2tgfp8LsXs8trBghymzD6WxuswTVvYv` |
| Framework | Anchor |
| IDL | [`memefun.json`](./memefun.json) |

> Pre-mainnet. The production program address and a verified build will be published here at mainnet launch.

## Indexing reference

**Instructions**
- `create_token` — new token launch
- `buy` / `sell` — trade on the bonding curve
- `swap` — WSOL-routed swap
- `claim_creator_fees`, `claim_protocol_fees`, `initialize`, `set_curve_config`, `set_fee_recipient`

**Events**
- **`TradeEvent`** — emitted on every `buy` / `sell` / `swap`; primary event for price & volume.
  `mint, sol_amount, token_amount, is_buy, user, virtual_sol_reserves, virtual_token_reserves, real_sol_reserves, real_token_reserves, timestamp, slot`
- **`CreateEvent`** — emitted on `create_token`.
- **`ClaimEvent`** — fee claims.

**State account**
- **`BondingCurve`** — one PDA per token; holds reserves, total supply, fee state, and the curve config.

## Price derivation
- Spot price (SOL per token) = `virtual_sol_reserves / virtual_token_reserves`
- Market cap = `virtual_sol_reserves × token_total_supply / virtual_token_reserves`
- Per-trade executed price = `sol_amount / token_amount`
- SOL amounts are in lamports (1e9); token amounts in the mint's base units (read decimals from the Token-2022 mint).
- Every `TradeEvent` carries **post-trade reserves**, so price and volume can be derived from the event alone.

## Links
- Site — https://meme.fun
- X — https://x.com/launchonmemefun

## License
[MIT](./LICENSE)
