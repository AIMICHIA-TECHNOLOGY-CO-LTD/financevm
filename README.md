# FinanceVM

**A Sovereign, Standard-Compliant Virtual Machine for Financial Asset Tokenisation**

*The Contract as Single Source of Truth: Execution, Recognition, Supervision*

[繁體中文](README.zh-TW.md) ｜ [financevm.io](https://financevm.io/) ｜ [AIMICHIA TECHNOLOGY](https://aimichia.com/)

---

## What FinanceVM Is

FinanceVM is a sovereign, standard-compliant virtual machine built specifically for the tokenisation of financial assets. It rests on one premise: the financial contract — not the token standard — is the authoritative definition of an asset.

A contract is expressed as a structured, computable ACTUS term set. From that single signed source, FinanceVM deterministically derives everything downstream: ledger state, ISO 20022 messages, accounting journal entries, regulatory metrics, and the smart contract itself. Because all five derive from the same term set rather than being maintained separately, they are consistent by construction and require no reconciliation between them.

Each institution runs its own sovereign node. Nodes do not share global state; they reconcile against the same signed contract terms. This is a network of sovereign states, not one world state.

**FinanceVM does not replace the ledger.** It supplies the financial execution layer that general-purpose ledgers were never designed to provide, restoring a division of labour those ledgers collapse: contracts are computed where precision and standards can be guaranteed; ledgers record state and provide attestation.

---

## Read the Whitepaper

**Version 2.0** is the current edition.

| Document | Language | Link |
|---|---|---|
| **Whitepaper v2.0** | English | [FinanceVM_Whitepaper_v2.0_EN_github.md](FinanceVM_Whitepaper/FinanceVM_Whitepaper_v2.0_EN.md) |
| **白皮書 v2.0** | 繁體中文 | [FinanceVM_Whitepaper_v2.0_CN_github.md](FinanceVM_Whitepaper/FinanceVM_Whitepaper_v2.0_CN.md) |
| Whitepaper v1.0 (archived) | English | [Google Drive](https://drive.google.com/file/d/1eVgSnquUofaIPQvQTAC-T1TmubrfqZ7c/view) |

Appendix B of v2.0 lists what changed from v1.0 and what did not.

**New in v2.0.** Three capabilities extend determinism beyond execution:

- **Verifiable contract provenance** — on-chain execution logic can be cryptographically proven to originate from a signed version of the contract terms, and independently reproduced by a regulator or auditor.
- **Accounting recognition interoperability** — a configurable, versioned mapping from contract cashflow events to journal entries, so that the same asset produces a traceable recognition result under each accounting framework.
- **Design-intent conformance control** — a token's observed state is continuously compared against its declared design, and departures from the design envelope are surfaced to each stakeholder's viewpoint.

Sections 6, 7 and 8 propose these as supplementary building blocks (#30, #31, #32) to the industry interoperability framework published by DTCC, Clearstream, Euroclear and BCG in February 2026.

---

## The Problems It Addresses

Running complex financial logic as on-chain computation is ill-suited to the task for three reasons.

| Problem | How FinanceVM answers it |
|---|---|
| **Precision** — general-purpose ledgers offer no native high-precision decimal arithmetic, so rounding error enters calculations that cannot tolerate it | Arbitrary-precision arithmetic core, no floating-point error |
| **Cost** — execution cost makes risk models such as Monte Carlo option pricing impractical on chain | Calculation off chain; the ledger records outcomes, not computation |
| **Financial meaning** — token interfaces describe transferability rather than financial meaning, leaving a gap between code and the legal contract | Instruments defined by ACTUS terms and a Financial Object Model built on FINOS CDM and ISO identifier standards |

---

## Architecture at a Glance

| Module | Standard | Role |
|---|---|---|
| **Precision Core** | — | Arbitrary-precision arithmetic underpinning all calculation |
| **FOM** | FINOS CDM, ISO 4914, ISO 6166, ISO 10962, ISO 18774, ISO 20275, ISO 23897, ISO 24165 | What the instrument is |
| **BPoS** | ISO 21586 | How the product should behave; the control baseline |
| **ACTUS** | ACTUS | What the contract produces over its life |
| **FEK** | ISO 17442-3, ERC-3643, ISO 20022, ACTUS | Compliance control: four gates plus a hash-chained audit trail |
| **ISO 20022** | ISO 20022 | Message assembly and validation |
| **vLEI** | ISO 17442-3 (KERI/ACDC) | Institutional identity |
| **BCBS SCO 60** | Basel III | LCR / NSFR |
| **PQC** | NIST FIPS 203 / 204 | ML-KEM-768, ML-DSA-65 |

FEK is the compliance control module. Its four gates — identity, transfer rules, messaging, lifecycle — are pluggable: alternative implementations can be registered for deployment on different ledgers or under different regulatory regimes. The lifecycle gate is deliberately fixed to ACTUS, because it anchors the provenance chain.

---

## Project Status

FinanceVM runs on two tracks, and the distinction matters when assessing the project.

| | Showcase Track | Reference Track |
|---|---|---|
| Designation | `v1.x — Sandbox` | `v2.0 — Reference Implementation` |
| Contents | Sandbox platforms for ten instrument classes: deposit, bond, equity, futures, option, collateral, commodity, swap, annuity, guarantee | Platform rebuilt on Hyperledger Besu |
| Purpose | Demonstrating that one core is portable across instrument classes | Formal engagement, regulatory dialogue, subject of capability assessment |

The sandbox platforms are capability demonstrations. **They are not the subject of the capability assessment described in the whitepaper**, which applies to the Reference Implementation currently under reconstruction.

Two further points of scope, stated plainly:

- **No self-assessment scores are published yet.** The Reference Implementation is under reconstruction; scoring an architecture scheduled for replacement would mislead. A full assessment across 32 building blocks, on the 0–4 evidence scale, will follow completion. See Section 11 of the whitepaper.
- **Post-quantum cryptography is implemented but not certified.** The PQC module implements FIPS 203/204. Until certification is complete, no claim of post-quantum compliance is made.

Cross-ledger atomic settlement is deliberately deferred pending clearer regulatory direction on public-chain participation. Section 5.4 sets out what contract anchoring does and does not solve.

---

## Contact

**AIMICHIA TECHNOLOGY CO., LTD.**

- Website: https://financevm.io/
- Company: https://aimichia.com/
- Email: contact@financevm.io ｜ jim.lin@aimichia.com

Enquiries from regulators, financial market infrastructures and standards bodies are welcome.

---

## Licence

MIT License

© 2026 AIMICHIA TECHNOLOGY CO., LTD. All rights reserved.

---

*This repository contains technical documentation. Nothing in it constitutes financial, legal, accounting or investment advice, or an offer of any security or financial product.*

