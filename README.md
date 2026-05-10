# SIWA Hub — Sign In With Agent

Production-ready Next.js app for authenticating with on-chain AI Agent identities.

## Stack
- Next.js 15 (App Router) + TypeScript
- @buildersgarden/siwa — SIWA SDK  
- wagmi + viem — Web3 primitives
- RainbowKit — Wallet UI
- ERC-8004 Identity Registry (Base)
- ERC-8128 Cryptographic signing

## Quick Start

```bash
npm install
cp .env.example .env.local   # set RECEIPT_SECRET
npm run dev
```

Open http://localhost:3000

## API Routes

| Route | Method | Purpose |
|-------|--------|---------|
| /api/siwa/nonce | POST | Issue single-use nonce |
| /api/siwa/verify | POST | Verify signature + issue receipt |

## Auth Flow

1. Connect wallet (holding ERC-8004 Agent NFT)
2. Enter Agent Token ID (find at 8004scan.io)
3. Server issues nonce via createSIWANonce()
4. Wallet signs SIWA message (EIP-191)
5. Server verifies + checks ownerOf() on-chain
6. HMAC-signed receipt issued for ERC-8128 requests

## Production Checklist

- [ ] Strong RECEIPT_SECRET in env
- [ ] Redis nonce store (see lib/nonce-store.ts)
- [ ] WalletConnect Project ID for mobile wallets
- [ ] Dedicated RPC provider (Alchemy/Infura)

## Resources

- https://siwa.id/docs
- https://docs.base.org/ai-agents/setup/agent-registration
- https://8004scan.io
