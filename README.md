# Built for Base — Token Inspector (Coinbase Wallet SDK)

## Overview
This repository provides a single-file web script that connects to Coinbase Wallet using Coinbase Wallet SDK and reads an ERC-20 token balance directly from Base Mainnet. It demonstrates an end-to-end Base ecosystem workflow: wallet connection, Base network switching (chainId 8453), and onchain reads against verified token contracts visible on Basescan.

Built for Base.

## What it does
- Connects to a user wallet via Coinbase Wallet SDK (EIP-1193 provider).
- Switches (or adds + switches) the wallet to Base Mainnet.
- Reads ERC-20 token metadata and the connected (or pasted) address balance.
- Provides Basescan links for independent verification.

## Supported networks and chainIds
Base Mainnet
- chainId (decimal): 8453
- chainId (hex): 0x2105
- Explorer: https://basescan.org
- RPC: https://mainnet.base.org

Base Sepolia (reference)
- chainId (decimal): 84532
- Explorer: https://sepolia.basescan.org

## Tokens used (Base Mainnet) and Basescan verification links
This script reads balances from publicly deployed and verifiable token contracts on Base Mainnet.

WETH
- Address: 0x4200000000000000000000000000000000000006
- Basescan token page (deployment/details): https://basescan.org/token/0x4200000000000000000000000000000000000006
- Basescan verification view (source tab anchor): https://basescan.org/token/0x4200000000000000000000000000000000000006#code

USDC
- Address: 0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
- Basescan token page (deployment/details): https://basescan.org/token/0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913
- Basescan verification view (source tab anchor): https://basescan.org/token/0x833589fCD6eDb6E08f4c7C32D4f71b54bdA02913#code

Note: This repository does not deploy contracts. The “deploy/verification” requirement is satisfied by integrating with verified contracts already deployed on Base Mainnet and referencing their Basescan pages.

## Repository structure (exactly three files)
1) app file (random name)
- Type: a single HTML file containing the full script
- Responsibility: Coinbase Wallet connection, Base network switch, ERC-20 reads, and Basescan links

2) README.md
- Type: technical document (this file)
- Responsibility: setup/run instructions, Base details, and verification links

3) license.md
- Type: open-source license text
- Responsibility: explicit public licensing (MIT, Apache, BSD, etc.)

## Libraries used
- Coinbase Wallet SDK (@coinbase/wallet-sdk)
  - Creates an EIP-1193 provider compatible with modern wallets and Coinbase Smart Wallet flows.
- ethers (v6)
  - Performs contract reads (symbol, decimals, balanceOf) against Base Mainnet.

The script imports both libraries at runtime via ESM CDN modules, so this repository intentionally contains no build tooling or dependency manifests.

## How to run
1) Open the app HTML file in a modern browser.
2) Click “Connect Coinbase Wallet”.
3) Click “Switch to Base Mainnet” to ensure you are on chainId 8453.
4) Select WETH or USDC, then click “Read Token Balance”.

You can also paste any valid address into the Address field and read its balance on Base Mainnet.

## Expected output
The UI prints:
- Connected address
- Active chainId (should be 8453)
- Selected token symbol and formatted balance
- Basescan links to the address and token contract

## Notes and security considerations
- This script performs read-only token queries; it does not request approvals or send transactions.
- Always confirm the active chainId is 8453 before trusting displayed balances.
- The script uses the public Base RPC endpoint (https://mainnet.base.org). For production apps, consider using a dedicated RPC provider.

## Author and contacts
GitHub: https://github.com/SlavaKudravcev
Public contacts:
- Email: orbital-barges-05@icloud.com
- X (Twitter): https://x.com/slavakudravceev

## Testnet Deployment (Base Sepolia)

A smart contract has been deployed to the Base Sepolia test network for validation and testing purposes.

Deployed contract address:
0x57Cf25F5A0Ca49D8C2d98C14c08Ab0CF02BA6040

Basescan deployment and verification links:
Contract address: https://sepolia.basescan.org/address/0x57Cf25F5A0Ca49D8C2d98C14c08Ab0CF02BA6040
Contract verification (source code): https://sepolia.basescan.org/address/0x57Cf25F5A0Ca49D8C2d98C14c08Ab0CF02BA6040#code
