# Chainlink CCIP Architecture & Verification Methodology

An interactive architecture explorer and cross-language formal verification methodology for [`smartcontractkit/chainlink-ccip`](https://github.com/smartcontractkit/chainlink-ccip).

## Reports

1. **[Interactive Architecture Explorer (`index.html`)](https://fredluv.github.io/chainlink-ccip-verification-architecture/)** ([source](index.html))
   - Clickable topology spanning **Source OnRamp & TokenPools**, **Off-Chain OCR3 Role DON & RMN**, and **Modular CCVs (`CommitteeVerifier`, `SuccinctZKVerifier`, `CCTPVerifier`, `LombardVerifier`) + `OffRamp`**.
   - Function-level inspector with line-verified links into [`smartcontractkit/chainlink-ccip`](https://github.com/smartcontractkit/chainlink-ccip) and `chains/evm/contracts/invariants/`.
   - Interactive **`_mergeCCVLists` Composition Simulator** (`CCV_INVARIANTS.md` rules) and **OCR3 Commit/Execute Lifecycle Walkthrough**.

2. **[Verification Methodology Report (`methodology.md`)](methodology.md)**
   - **Cross-Language, Context-Sliced Assume-Guarantee Verification** across 5 strata:
     - **Stratum 0**: Multi-language (`solc` + Go) dependency slicing along `ICrossChainVerifierV1` & codec seams
     - **Stratum 1**: Dual `solc` + `go/ast` structural gates
     - **Stratum 2**: Converting `chains/evm/contracts/invariants/*.md` prose specs into bytecode-bound symbolic rules + Go↔Solidity `merklemulti` parity fuzzing
     - **Stratum 3**: Multi-lane stateful adversarial fuzzing (reordering, gas-buffer OOG retries, RMN curse injection)
     - **Stratum 4**: Synthetic `AdversarialCCV.sol` & `AdversarialTokenPool.sol` injection + SHA-256 `ProofKernel` receipt

## Local Preview

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```
