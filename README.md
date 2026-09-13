# Duayne Gregg — Web3 Security Researcher

Independent vulnerability researcher working across the full protocol stack — Go consensus clients, Rust cryptographic libraries, Solidity — and building the tooling I hunt with. Sole director of [Sovereign Hive Pty Ltd](https://sovereignhive.com.au). Approved under Anthropic's Cyber Verification Program.

Hervey Bay, QLD, Australia (UTC+10) · Remote · [yorhealthduayne@gmail.com](mailto:yorhealthduayne@gmail.com) · [LinkedIn](https://linkedin.com/in/duayne-gregg-44b35840b)

---

## Findings

All findings were reported through the target's disclosure programme with a working proof-of-concept and a proposed fix. **Mechanism-level detail is withheld here until each issue is patched or the programme permits publication** — that's what responsible disclosure means. Full reports, PoCs and reproduction steps are available to hiring teams on request.

| Target | Stack | Class | Severity | Status |
|---|---|---|---|---|
| Morph L2 — Tendermint fork | Go | Unauthenticated fullnode wedge (unreachable loop exit; same class as CometBFT CVE-2025-24371) | High | Reported 2026-08 |
| Morph L2 — batch submitter | Go | Deterministic batch rejection halting L1 commitments (compression non-monotonicity) | High | Reported 2026-09 |
| Morph L2 — L1CrossDomainMessenger | Solidity | Permissionless exhaustion of a finite replay budget, removing user recovery | High | Reported 2026-07 |
| Unitus / dForce — TransitAggregator | Solidity | Composite Chainlink oracle reports stale sub-feed as fresh; confirmed live on 4 chains via read-only `eth_call` | Medium → High at mainnet TVL | Reported 2026-07; direct disclosure in progress |
| Cregis — anychain-kms | Rust | Ed25519 secret-key aliasing (non-canonical scalar accepted) → key-identifier collision | Medium | Reported 2026-07 |
| Cregis — anychain-ffi-rust | Rust | Ambiguous JSON canonicalization → digest collisions on signed payloads | Medium | Reported 2026-07 |
| ERC-4337 EntryPoint v0.9.0 | Solidity | Paymaster-signature suffix malleability + userOpHash collision; EIP-7702 init-index DoS. Verified against upstream `b36a1ed` | Medium / High | HackenProof |
| VeChainThor v2.5.0 | Go | Oversized-header consensus-path DoS; txpool admission-order gap | Medium | HackenProof, in review |
| Bitget Wallet (extension) | Wallet UX | EIP-712 confirmation omits domain context (chainId / verifyingContract) | High | Reported 2026-07 |

Each row will link to a public write-up once disclosure completes.

---

## Tooling

**FORGE** — a red-team benchmarking and evaluation harness. A position-swap-debiased LLM judge calibrated against executable ground truth; a versioned break-level grader with provenance stamping; telemetry-integrity diagnostics. The measurement layer for adversarial evaluation that can be reproduced on demand.

**Sovereign Hive** — a local-first, air-gapped platform for simulating and defending autonomous agent systems: syscall-level containment, multi-agent orchestration, tiered memory, protobuf wire contracts. Built under `ruff` / `mypy --strict`, frozen interfaces, audit trails and reproducible verification gates.

**Quantisation research (HSAQ)** — a sensitivity-profile scale law for mixed-precision tier assignment, with a production pipeline across HQQ, GGUF and ternary workflows.

---

## How I work

Every report ships with the repository, the exact commit, the PoC and the reproduction steps. I don't declare anything verified that hasn't been verified, and I distinguish plainly between what's demonstrated and what's theorised. That posture comes from 15+ years in safety-critical heavy industry, where the gap between "should work" and "checked" is the whole job.

---

## Platforms

HackenProof · 0DIN (Mozilla) · BugRap

## Stack

Go · Rust · Solidity · Python · TypeScript · Foundry · EVM internals · Tendermint/CometBFT · ERC-4337 / EIP-7702 · oracle design · cross-chain messaging · Ed25519 / secp256k1 · fuzzing & static analysis
