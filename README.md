# Duayne Gregg — Web3 Security Researcher

Independent vulnerability researcher working across the full protocol stack — Go consensus clients, Rust cryptographic libraries, Solidity — and building the tooling I hunt with. Sole director of [Sovereign Hive Pty Ltd](https://sovereignhivesecurity.com.au). Approved under Anthropic's Cyber Verification Program.

Hervey Bay, QLD, Australia (UTC+10) · Remote · [duaynegregg@sovereignhivesecurity.com.au](mailto:duaynegregg@sovereignhivesecurity.com.au) · [LinkedIn](https://linkedin.com/in/duayne-gregg-44b35840b)

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






Resume attached

DUAYNE GREGG
Founder & Security Researcher  ·  AI Safeguards & Adversarial Robustness  ·  Protocol & Smart-Contract Security
Hervey Bay, QLD 4655, Australia (UTC+10)  ·  Remote  ·  open to San Francisco / New York  ·  duaynegregg@sovereignhivesecurity.com.au
linkedin.com/in/duayne-gregg-44b35840b  ·  github.com/MXguru1  ·  Sovereign Hive Pty Ltd (ABN 24 661 737 376)
SUMMARY
Technical founder and self-taught security researcher who came to AI safety from 15+ years of operational-risk leadership in safety-critical heavy industry. Sole architect of Sovereign Hive, a local-first platform that attacks, measures and defends LLM and agent systems in a closed loop. Discovered and responsibly disclosed a cross-family jailbreak against the emotional-attunement behaviour of RLHF-tuned models (24/24 production models, 8 vendors), then built the defence: an Intent Recognition Register that tracks user intent across the whole conversation, so a model can stay helpful instead of refusing while still declining to produce harmful content, and resists slow multi-turn context poisoning. Also an active protocol-security researcher working across the full stack (Go consensus clients, Rust cryptography, Solidity contracts) and building the tooling I hunt with: live-mainnet findings in L2 consensus, oracle logic, account-abstraction infrastructure and wallet key-management, each with a working proof-of-concept and a minimal fix, including a paid Critical and a vendor-confirmed Medium on HackenProof. Previously approved under Anthropic’s Cyber Verification Program. Governance-first, evidence-led engineering posture carried over from heavy industry, where uncontrolled failure has real consequences.
CORE STRENGTHS
•  Defensive controls for autonomous systems: containment, governance, kill-switch design
•  AI governance & model risk: responsible disclosure, audit trails, reproducible verification gates
•  Agentic AI security: prompt injection, tool misuse, agent-to-agent manipulation
•  AI red teaming: adversarial simulation, jailbreak research, threat modelling
•  LLM systems engineering: local inference, quantisation, LoRA/QLoRA, model evaluation
•  Full-stack platform engineering: Python, TypeScript, React, Docker, CI discipline
AI SAFETY RESEARCH
Intent Recognition Register (IRR): conversation-level intent tracking as a safeguard	2025–present
•  Problem. Proposed and built a safeguard layer that keeps a running, structured record of inferred user intent across a whole dialogue. Single-message classifiers see one turn at a time; the IRR scores each new turn against the accumulated record, so slow multi-turn escalation and context poisoning show up as drift.
•  Design. Replaces binary refuse/comply with intent-conditioned routing. The model serves the legitimate underlying need and withholds only the harmful uplift; the aim is fewer over-refusals and less harmful output at the same time.
•  Empirical findings. Benchmarked frontier and local models against 117 attested solo human gold anchors (MAP-AUDIT-2). Out-of-the-box models consistently fail to beat the 74.4% constant base rate (top single model: 73.5%), suffering a 29.5% error rate even when unanimous (52.1% coverage) due to pervasive over-refusal of benign dual-use queries. Implemented a deterministic Two-Step Hierarchical Evaluator that decouples epistemic boundaries from operational stance, mathematically eliminating the answer_with_care loophole (structural 0% bypass).
•  Disclosure. Disclosed the underlying design flaw and the proposed fix to frontier-lab safety teams (Google VRP and Anthropic, 2025–2026; reference IDs logged in the disclosure ledger).
Cross-family jailbreak targeting the emotional-attunement layer of RLHF-tuned models	2025
•  A single structural prompt bypassed safety behaviour in 24/24 production models from 8 vendors (Meta, Google, Microsoft, Mistral, Cohere, DeepSeek, NVIDIA, Alibaba). Responsibly disclosed to Google VRP and Anthropic.
•  Built an automated adversarial wargame (3 attacker LLMs vs 6 local defenders, 15,000+ deterministic rounds) to measure attack reliability and defensive response quality.
•  Closed-loop defence workflow (attack → re-educate → enforce → verify) demonstrating F1 = 1.000 on attack recognition and proven resistance to reverse-brainwashing, systematically evaluating adversarial transferability, multi-turn context drift, and resistance to iterative prompt re-conditioning.
Evaluation & measurement infrastructure	2025–present
•  Red-team benchmarking harness: LLM-as-judge with position-swap debiasing, calibrated against executable ground truth; versioned break-level grader with provenance stamping; telemetry-integrity diagnostics. The measurement layer for reproducible adversarial evaluation.
•  Frozen-protocol, pre-registered eval campaigns with fail-closed gates. Quantisation research (HSAQ scale law): predicts mixed-precision tier assignment for unprofiled larger models from small-model anchors; production pipeline spanning HQQ, GGUF and ternary workflows, with manifesting, integrity indexing and Ollama auto-generation for efficient local deployment on constrained hardware.
FOUNDER: SOVEREIGN HIVE PTY LTD
Sole director & architect	2024–present
•  Built a 12-sub-project, local-first agentic-security platform: syscall-level containment, multi-agent orchestration, temporal knowledge graph, tiered memory, protobuf wire contracts and kill-switch governance, tied together by a measurable efficiency / sovereignty capstone dashboard.
•  Engineering discipline throughout: ruff strict, mypy --strict, frozen interfaces, audit trails, CI verification gates and reproducible evidence bundles.
SECURITY RESEARCH: PROTOCOLS & SMART CONTRACTS
Morph L2: three High-severity findings (Go / Tendermint fork / Solidity)	2026
•  Sequencer broadcast-loop wedge: a single unauthenticated peer can wedge any mainnet fullnode with one StatusResponse{Height: MaxInt64}, an unreachable loop-exit in requestMissingBlocks (per-peer cap 200 vs global cap 500). Same class as CometBFT CVE-2025-24371, unpatched in the fork. 7/7 PoC tests; one-line scan-range cap fix.
•  Submitter batch-poisoning: a funded account can deterministically make the V2 submitter reject an accumulated batch (zstd is not size-monotonic), stopping L1 commitments and delaying finality and withdrawals until operator intervention. Estimated cost < 0.00004 ETH; PoC across seven signed transactions.
•  Replay-budget exhaustion in L1CrossDomainMessenger: replayMessage authenticates which message may be replayed but not who consumes its finite 3-attempt budget; an unrelated caller can burn all attempts and remove permissionless recovery of an escrowed deposit. End-to-end Foundry PoC on the ETH-gateway path.
Unitus / dForce: composite-oracle staleness (Solidity), live on four chains	2026
•  TransitAggregator._latestRoundData() combines two Chainlink sub-feed timestamps with max() where correct semantics require min(), so the wrapper reports a stale price as fresh with no per-sub-feed staleness gate downstream, enabling under-collateralised borrowing or unfair liquidation. Confirmed live on Ethereum, Arbitrum, Optimism and Base (~$723k TVL on Ethereum mainnet) via block-pinned, read-only eth_call with signed evidence; three-character fix.
ERC-4337 EntryPoint v0.9.0, verified against upstream (Solidity)	2026
•  Paymaster-signature suffix malleability and a userOpHash collision in the v0.9 parallel-signing path, found after the published SpearBit/Cantina v0.9 audits; plus an EIP-7702 init-payload DoS where a hardcoded revert index blames and can censor the index-0 operation. All symbols and behaviour verified against eth-infinitism/account-abstraction v0.9.0 (commit b36a1ed); Foundry PoCs pass.
Cregis anychain: two findings in a production wallet KMS (Rust)	2026
•  ed25519_sign accepts non-canonical secret keys: Scalar::from_bytes_mod_order silently reduces mod L, so sk and sk+L yield an identical signing scalar and public key, a key-identifier collision for any system that hashes raw key bytes. Deterministic Rust PoC; one-line from_canonical_bytes fix.
•  cregis_json_digest ambiguous canonicalisation: the custom serializer collides null / "" / "null" and numeric / string forms to identical digests, enabling parameter substitution on any signature validated over the digest. Fix: adopt JCS (RFC 8785).
VeChainThor: application-level node DoS (Go)	2026
•  VEC-528: an unprivileged peer stalls the single block-ingress goroutine via an unbounded-width BaseFee materialised on a consensus error path (a multi-MB RLP payload admitted before size and proposer validation, driving O(n²) big.Int formatting). Independently reproduced and confirmed Medium by VeChain’s security team; in triage pending reward, with two author follow-ups adopted into the fix.
•  Separately holds a paid Critical on HackenProof. Active on HackenProof, 0DIN (Mozilla) and BugRap; all findings accompanied by runnable PoCs, block-pinned signed evidence and minimal proposed fixes.
TECHNICAL SKILLS
•  Languages: Go, Rust, Solidity, Python, TypeScript, React.
•  AI security: LLM red-teaming & eval design, prompt injection, tool misuse, agent-to-agent manipulation, agent containment & governance, kill-switch design, threat modelling.
•  Security: Smart-contract & protocol auditing, EVM internals, consensus clients (Tendermint / CometBFT), account abstraction (ERC-4337 / EIP-7702), oracle design, cross-chain messaging, applied cryptography (Ed25519 / secp256k1), fuzzing & static analysis, responsible disclosure.
•  Tooling & systems: Foundry, Docker, CI discipline, local LLM inference & quantisation (HQQ / GGUF / QLoRA / ternary), Ollama.
PRIOR EXPERIENCE: OPERATIONAL RISK & SAFETY LEADERSHIP
Batching Plant Supervisor (S45R), Colas WA	2020–2024
•  Promoted into site leadership; managed safety-critical production and enforced strict procedural compliance in a zero-tolerance-for-uncontrolled-failure environment, supporting facility growth through disciplined operational control.
Heavy industry / high-risk operations (incl. Downer Group)	2004–2020
•  Plant operations and leadership across heavy equipment, ports, construction and drilling. Site-supervisor training and a Dangerous Goods Licence. Fifteen years of treating uncontrolled failure as unacceptable, building the systems-thinking, evidence-first discipline now applied to security work.
VALIDATION & EDUCATION
•  Self-directed advanced practice in AI security, protocol security, applied cryptography, and adversarial evaluation, evidenced by original findings and shipped systems. Technical validation available on request: report bodies, PoC repositories, evaluation bundles, reproduction steps, codebase history and responsible-disclosure documentation.
