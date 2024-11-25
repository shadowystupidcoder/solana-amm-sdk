# Solana AMM SDK

A powerfully simple SDK for market making on Solana.

## Installation

```bash
npm install solana-amm-sdk
```

## Usage

```javascript
import { Connection, Keypair, PublicKey } from "@solana/web3.js"
import { Amm } from "solana-amm-sdk"

const connection = new Connection("https://rpc.helius.xyz/?api-key=9682e038eb")
const payerWallet = Keypair.fromSecretKey(Uint8Array.from([132,203,205,98,129,210,181]))

const mint = new PublicKey("GDfnEsia2WLAW5t8yx2X5j2mkfA74i5kwGdDuZHt7XmG")

const amm = new Amm(connection, payerWallet, {disableLogs: false})

const minSolPerSwap = 0.001111
const maxSolPerSwap = 0.001511
const mCapFactor = 1
const speedFactor = 1

await amm.volume(mint, minSolPerSwap, maxSolPerSwap, mCapFactor, speedFactor, {includeDexes: ["Whirlpool", "Raydium", "Meteora", "Orca"], jitoTipLamports: 100000})

await amm.makers(mint, 5000, {includeDexes: ["Whirlpool", "Raydium", "Meteora", "Orca"], jitoTipLamports: 100000 })

const swap = await amm.swap(mint, "buy", 0.001, {jitoTipLamports: 100000})
```

## Features

- 🚀 Easy to use
- 📈 Customizable volume generation
- ⚡ Jito MEV protection
- 🔧 Select which Dex to include

## Support

- 🐛 [Report Issues]
- 💬 [Open a PR]
- 📚 [Join our Discord]

## License

MIT License - see [LICENSE](LICENSE) for details