# Token Radar

The best token launch radar: 200 pre-token protocols from a sealed
DefiLlama snapshot, ranked by implied value, with a farm plan for each.

- **Watchlist first:** all 40 watchlist protocols (at least $50M TVL, no
  token recorded) are covered, plus 160 early pre-token protocols below
  the floor, found by TVL.
- **Model radar-2:** implied value = TVL x category multiple x growth x
  maturity x breadth. The category multiple is the median market-cap / TVL
  of live-token protocols in the same category in this snapshot, recomputed
  on every run. Growth is the 7-day TVL change, clamped to -50%..+100%.
  Maturity grows with age since listing. Breadth adds 3% per extra chain.
  No protocol name is special-cased.
- **Farm plans:** six concrete steps per protocol, with capital, gas cost
  on its main chain, and hold time, derived from its category, chains, TVL
  and age.
- **Dashboard:** `dashboard/` is a static page (no network) with the ranked
  board, search, category and chain filters, a live-token view, a detail
  drawer per protocol, and the model's own numbers. It reads `data.js`,
  written beside it by `main.ts`.

## Run it

Node 22+, standard library only, no network:

```sh
mkdir -p out
MAKEFUN_OUTPUT_DIR=out node main.ts --input /path/to/snapshot.json
```

This writes `out/board.json`, `out/data.js`, copies `dashboard/` and
`screenshots/` into `out/`, and writes `out/dossier.json`.

`board.json` holds 200 rows: rank, slug, name, category, chains, TVL,
7-day change, age, implied value, the model's factors, and six farm steps.
Live-token protocols are set aside in `data.js` with their market caps.

## Entry

Built for the make.fun `token-radar-01` bounty. Implied value is the
entry's own claim, never one make.fun makes. A protocol "records no token"
means the snapshot records no market cap, CoinGecko id or symbol for it.

License: MIT.
