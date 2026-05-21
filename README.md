# armada-deployments

Public registry of [Armada](https://github.com/ship-armada) protocol deployment manifests across all supported chains and environments.

## Layout

```
armada-deployments/
├── testnet/
│   └── <name>/                  # named deployment instance
│       ├── manifest.json        # instance metadata + chain list
│       └── <chain>/             # per-chain deployment artifacts
│           └── <component>.json
└── mainnet/                     # (future)
```

A *named instance* groups a coordinated set of contracts deployed across one or more chains. Frontends consume an instance by name (e.g. `medi1`) and resolve the chains they need from the instance's `manifest.json`.

Multiple instances can be live simultaneously (e.g. `medi1`, `medi2`, `protocol-v1`); a frontend selects which one it targets at build time or runtime.

## Live deployments

### Testnet

| Instance | Chains | Description |
|---|---|---|
| [`demo-1`](./testnet/demo-1) | sepolia, base-sepolia, arbitrum-sepolia | Full Armada protocol (privacy pool + yield + cross-chain) for `armada-interface` designer review |
| [`medi2`](./testnet/medi2) | sepolia | MEDI crowdfund campaign #2 |
| [`medi1`](./testnet/medi1) | sepolia | MEDI crowdfund campaign #1 |

#### `demo-1` — Sepolia hub + Base Sepolia / Arbitrum Sepolia clients

Hub (Ethereum Sepolia, chainId `11155111`):

| Contract | Address |
|---|---|
| PrivacyPool | [`0x014aC1dfC2Bde83d4be2CFFb5bea4dE942DAD77F`](https://sepolia.etherscan.io/address/0x014aC1dfC2Bde83d4be2CFFb5bea4dE942DAD77F) |
| ArmadaYieldVault | [`0x214a3c251E9b064f4420a26Cc879b362A26bAc5A`](https://sepolia.etherscan.io/address/0x214a3c251E9b064f4420a26Cc879b362A26bAc5A) |
| ArmadaYieldAdapter | [`0x148A6A4588062dB433Fa8847017DB42bAc506458`](https://sepolia.etherscan.io/address/0x148A6A4588062dB433Fa8847017DB42bAc506458) |
| AdapterRegistry | [`0xbA5D04B538864593a0eEc2995aCE6502CC93aCb5`](https://sepolia.etherscan.io/address/0xbA5D04B538864593a0eEc2995aCE6502CC93aCb5) |
| MockAaveSpoke | [`0x25844C20C11f842dde6BC733132b6229BC33eFAd`](https://sepolia.etherscan.io/address/0x25844C20C11f842dde6BC733132b6229BC33eFAd) |
| Timelock | [`0xB70D1DcD7E63E0eF7b4c7B83cAb35f5863462889`](https://sepolia.etherscan.io/address/0xB70D1DcD7E63E0eF7b4c7B83cAb35f5863462889) |
| USDC (test) | [`0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238`](https://sepolia.etherscan.io/address/0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238) |

Clients (CCTP V2 destinations):

| Chain | chainId | PrivacyPoolClient |
|---|---|---|
| Base Sepolia | `84532` | [`0x83C80Fa61c5dA2A716326871025a5d0c2B9bD43f`](https://sepolia.basescan.org/address/0x83C80Fa61c5dA2A716326871025a5d0c2B9bD43f) |
| Arbitrum Sepolia | `421614` | [`0xd76105dC158de8d3a1B32AFcAD22C55feC69716d`](https://sepolia.arbiscan.io/address/0xd76105dC158de8d3a1B32AFcAD22C55feC69716d) |

Full deployment artifacts: [`testnet/demo-1/`](./testnet/demo-1)

#### `medi2` — Sepolia (chainId `11155111`)

| Contract | Address |
|---|---|
| ARM Token | [`0x7EB073eeF5953EDAC4554915bfdeFaA31217Fcd8`](https://sepolia.etherscan.io/address/0x7EB073eeF5953EDAC4554915bfdeFaA31217Fcd8) |
| Crowdfund | [`0x75b775b2bBbb5fE8c32D9B82AFCBC217D872859a`](https://sepolia.etherscan.io/address/0x75b775b2bBbb5fE8c32D9B82AFCBC217D872859a) |
| Treasury | [`0x2Ea83D2Fc8B8Fe7b81C5aa152f54b1Da837c3310`](https://sepolia.etherscan.io/address/0x2Ea83D2Fc8B8Fe7b81C5aa152f54b1Da837c3310) |
| Governor | [`0xAC836855C5aCF63E5173b729D1c4746B9Ad31b3b`](https://sepolia.etherscan.io/address/0xAC836855C5aCF63E5173b729D1c4746B9Ad31b3b) |
| Timelock | [`0xB5D1360102B4f6B4B48DDc7F41B7c612B88d624e`](https://sepolia.etherscan.io/address/0xB5D1360102B4f6B4B48DDc7F41B7c612B88d624e) |
| USDC (test) | [`0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238`](https://sepolia.etherscan.io/address/0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238) |

Full deployment artifacts: [`testnet/medi2/sepolia/`](./testnet/medi2/sepolia)

#### `medi1` — Sepolia (chainId `11155111`)

| Contract | Address |
|---|---|
| ARM Token | [`0x96efE3b9716d040D6556211eBE2cd38b4d555194`](https://sepolia.etherscan.io/address/0x96efE3b9716d040D6556211eBE2cd38b4d555194) |
| Crowdfund | [`0xF681A7c700420e5CA93f77c8988d3eED02767035`](https://sepolia.etherscan.io/address/0xF681A7c700420e5CA93f77c8988d3eED02767035) |
| Treasury | [`0x2D00f1370268a4019a9E9270867D1222b6e7e914`](https://sepolia.etherscan.io/address/0x2D00f1370268a4019a9E9270867D1222b6e7e914) |
| Governor | [`0x89EE643CC511628C219790fC0E1260c218f6cF4c`](https://sepolia.etherscan.io/address/0x89EE643CC511628C219790fC0E1260c218f6cF4c) |
| Timelock | [`0xC69158E95410224BBe113ADeB2E4A6451309238E`](https://sepolia.etherscan.io/address/0xC69158E95410224BBe113ADeB2E4A6451309238E) |
| USDC (test) | [`0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238`](https://sepolia.etherscan.io/address/0x1c7D4B196Cb0C7B01d743Fbc6116a902379C7238) |

Full deployment artifacts: [`testnet/medi1/sepolia/`](./testnet/medi1/sepolia)

### Mainnet

_None yet._

## Consuming from a frontend

```ts
const baseURL = "https://raw.githubusercontent.com/ship-armada/armada-deployments/main";
const instance = "medi1";

const manifest = await fetch(`${baseURL}/testnet/${instance}/manifest.json`).then(r => r.json());

const chain = "sepolia";
const crowdfund = await fetch(`${baseURL}/testnet/${instance}/${chain}/crowdfund.json`).then(r => r.json());
const governance = await fetch(`${baseURL}/testnet/${instance}/${chain}/governance.json`).then(r => r.json());

console.log(crowdfund.contracts.crowdfund);
console.log(governance.contracts.armToken);
```

## Updating

To publish a new deployment:

1. Create the instance directory: `testnet/<name>/` (or `mainnet/<name>/`).
2. Add a `manifest.json` listing the chains and artifact paths.
3. Drop per-chain JSON artifacts under `<name>/<chain>/`.
4. Update this README with the new instance and contract addresses.
5. Open a PR.

Filenames inside chain directories should be the component name only (e.g. `crowdfund.json`, `governance.json`) — the chain is already implied by the parent directory.
