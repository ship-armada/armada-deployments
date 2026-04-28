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
| [`medi1`](./testnet/medi1) | sepolia | MEDI crowdfund campaign #1 |

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
