# Resource 3 — Move 1 Public Evaluator Package

**Package ID:** `MOVE1-RESOURCE3-BLIND-EVALUATOR-PACK-1.0`  
**Status:** Prepared for a proposed independent M1 blind-evaluation step.  
**Ground-truth contents:** Withheld from this public package.

## 1. Public files

The public evaluator package consists of these files:

1. `systems_public.json` — 20 synthetic system templates across five architecture labels, with four templates per label and 16 internal variables per template.
2. `probe_suite_B.json` — synthetic reference-oracle observations: 60 planned run records, 50 probes per run (25 objective-focused and 25 constraint-focused), with 16 single-variable zero-ablation observations per probe.
3. `ablation_operator_A.json` — frozen `A_ZERO_SINGLE_VARIABLE_V1` operator definition.
4. `pre_reg_Move1.json` — frozen configuration, counts, threshold, metrics, bootstrap procedure, and hash commitments.
5. `public_manifest.json` — public input hashes, commitments, counts, and scope limitations.
6. `README.md` — this scope and handling document.

Verify exact-file-byte SHA-256 digests against `public_manifest.json` before use. A digest match establishes byte integrity relative to the published commitment; it does not by itself establish authorship, when a commitment was made, scientific validity, or proper execution.

## 2. Frozen design counts

- 20 system templates, distributed evenly across five labels: `MLP2`, `MLP4`, `Transformer2`, `RNN`, and `CNN` (four templates per label).
- 16 internal variables per template (`u00`–`u15`).
- Three seeds per template; 60 planned run records in total.
- 50 probes per run: 25 objective-focused and 25 constraint-focused.
- 3,000 probe responses overall and 16 zero-ablation observations per probe (48,000 observations overall).
- Frozen threshold: `tau = 0.1`.
- Frozen ablation operator: `A_ZERO_SINGLE_VARIABLE_V1`.
- Planted identity size: 5–10 variables per system; explicit ground-truth membership is not disclosed here.

## 3. Synthetic-data and architecture limitations

The architecture strings are **synthetic surrogate-family labels**, not evidence that trained or framework-backed MLP, Transformer, RNN, or CNN implementations were constructed or executed. Do not interpret the labels as validation of behavior in real models or deployed systems.

`probe_suite_B.json` contains **synthetic reference-oracle data** prepared for the specified setup. It is not output from an independent M1 estimator evaluation. The ablation observations are supplied reference observations; their presence does not establish that an independent evaluator reproduced the system or independently executed the ablation operator.

No independent M1 evaluation runs have been executed as part of this preparation. No estimator scores, bootstrap confidence intervals, or acceptance decisions are claimed. In particular, no conclusions about precision, recall, projector similarity (`rho`), SDI, G, or broader system correctness should be inferred from package preparation alone.

## 4. Blind ground-truth handling

The ground-truth file is named `sealed_E_star.json`. It is **organizer-only** and is intentionally excluded from the public evaluator files and public archive. Its published SHA-256 commitment is:

```text
d8a0bbd889463cda08bbba5c5189180f5f542d7adb3ffaa3836e38c7d1e1d416
```

This commitment publishes no ground-truth membership. Do **not** send, attach, paste, or otherwise disclose `sealed_E_star.json` or its membership fields to Resource 4 before the blind evaluation and its outputs are locked. Retain the sealed file separately under organizer control; a separate archive alone does not enforce access control.

After the evaluator's output is locked and organizer-authorized release occurs, verify the sealed file's exact-byte SHA-256 against the commitment before any ground-truth scoring. Do not use the sealed file to guide the blind estimator or revise the public probes, estimator, thresholds, or metrics after seeing evaluation outputs.

## 5. Hash commitments

`B_hash` for the exact bytes of `probe_suite_B.json`:

```text
7c5ba38162ae05b035a73b5cb3dedd6943671fbdc57ea37d4ff562b1f7e13cb6
```

`A_hash` for the exact bytes of `ablation_operator_A.json`:

```text
2ffc6e24cd8893357b17ecd60fc93994e90736cca6537655105027cec900ebb3
```

The system-file and pre-registration hashes are listed in `public_manifest.json`. The manifest does not embed its own hash; doing so would be self-referential. If the manifest's own hash is needed, record it externally after finalizing the file.

## 6. Pre-registration and timestamp limitation

`pre_reg_Move1.json` records the frozen configuration and states that it was frozen before independent M1 evaluation. A timestamp written into a file is not, by itself, independent proof that the file existed in that form before evaluation. Establishing that chronology requires a verifiable timestamp service, a public or independently controlled append-only record, or another independently auditable commitment made before evaluation.

The pre-registration currently lists `manifest_public.json` and `README_PUBLIC.md` in its `evaluator_may_receive` array, while this delivery uses the requested filenames `public_manifest.json` and `README.md`. These are filename differences, not equivalent cryptographic identities. Do not silently rewrite the frozen pre-registration. If strict filename-level conformance is required, record and approve a versioned erratum or an independently timestamped addendum before the blind evaluation; preserve the original file and its hash.

## 7. Scope and EDCP status

This package prepares public synthetic inputs and records the intended pre-registration. It does **not** establish full EDCP compliance, prove that independent evaluation occurred, enforce evaluator access controls, validate a real device or deployed model, or establish the metaphysical or scientific truth of the planted identity. Later steps must separately document the independent M1 method and outputs, lock evaluator results before unsealing, verify the sealed commitment, and report scoring and limitations reproducibly.

Any failed or missing run should be recorded as `FAILED` / `NOT_ESTIMATED` and must not be imputed or silently omitted from the run count. Report per-run results and aggregate by system template and architecture as specified in the frozen protocol; keep threshold pass/fail distinct from precision, recall, and `rho`.
