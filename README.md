# StellarWork

StellarWork is an open-source decentralized freelance marketplace on Stellar. Payments are held in Soroban escrow and released by state transitions, not platform custody logic.

## Repository Layout

```
stellarwork
├── contracts/escrow
├── frontend
└── docs
```

## Local Setup

### 1) Contract

```bash
cd contracts/escrow
cargo test
```

### 2) Frontend

```bash
cd frontend
cp .env.example .env.local
npm install
npm run dev
```

Open [http://localhost:3000](http://localhost:3000).

## Deploy Contract to Stellar Testnet

Prerequisites:
- Soroban CLI installed
- Testnet identity configured in Soroban CLI

Example flow:

```bash
cd contracts/escrow
soroban contract build
soroban contract deploy --wasm target/wasm32-unknown-unknown/release/escrow.wasm --source <identity> --network testnet
```

After deploy:
- Set returned contract ID as `NEXT_PUBLIC_CONTRACT_ID` in `frontend/.env.local`
- Restart frontend dev server

## Current Feature Set

- Core escrow lifecycle (`post_job`, `accept_job`, `submit_work`, `approve_work`, `cancel_job`)
- On-chain job storage and count queries
- Platform fee accounting (2.5%)
- Contract unit tests for core paths
- Core pages: `/`, `/post-job`, `/job/[id]`


## License

MIT (`LICENSE`).
