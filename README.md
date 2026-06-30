# meme.fun — Program IDL

Anchor IDL for the meme.fun Solana launchpad program (public interface schema).

- **Program (devnet):** `8FKy3VMhpL5xk2tgfp8LsXs8trBghymzD6WxuswTVvYv`
- **Key instructions:** `create_token`, `buy`, `sell`, `swap`
- **Key events:** `TradeEvent`, `CreateEvent`, `ClaimEvent`
- **State account:** `BondingCurve` (one PDA per token)

`memefun.json` is the canonical Anchor IDL — instructions, accounts, events, and types.
Pre-mainnet; production address + verified build provided at mainnet launch.
