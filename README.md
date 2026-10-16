# NV-Reason-CT: independent native Swift/MLX conversion

Final NVIDIA checkpoint `386b93e034983f6c1fc841a43833a1b6a0cd9c13`; converted bundle `f161b426996994d6a1c224976afe7b89866c678eb36da7fd96730f48d3bb6eac`.
Original BF16 parameter values are stored unchanged; runtime computation/caches are FP32.
BF16 expansion does not recover lost precision. This conversion is independent and unofficial.

The bounded engineering corpus (public-01, chest/abdomen, report/QA/thinking/history replay)
passed the recorded source-comparison gates on one physical M4 Pro 24 GiB. It does not
establish clinical accuracy, certification, physical mobile support, other RAM-tier
requirements or viewer residency. Output may be incorrect and is not an approved final report.

Source implementation/tools: https://github.com/ThalesMMS/NV-Reason-CT-Swift/tree/8bf30189ecb84ac8484709e01d698680f8c7b0f9
Minimum runtime: 0.1.0; profile `nv-reason-ct-bf16-storage-fp32-compute-v1`.
No Python, remote code, ONNX, server or network is used by installed native inference.
Acquisition is separate. Earlier selective-MLP variants remain rejected under the original FP32 gates.

Weights use NVIDIA OpenMDW-1.1. Bundled component notices include Apache-2.0 and MIT;
see LICENSE, NOTICE and licenses/. No exams, embeddings, prompts or generated reports
are distributed here. This repository contains metadata/notices only; all tools live
in the Swift source repository and all weights live in versioned release assets.

## Experimental mobile 4-bit profile

[Mobile release](https://github.com/ThalesMMS/NV-Reason-CT-MLX/releases/tag/ct-mobile-4bit-v0.1.0)
contains a distinct approximate profile for the 8–12 GB device target. Its 249
language matrices and tied head use affine 4-bit group-64 weights with BF16 scales;
vision/activations/KV are BF16 and normalization/recurrence stay FP32. The 192³
crop and all 13,824 visual tokens are retained. Complete download: 2.68 GB.
Native Metal kernels bound attention/prefill working memory and fuse the GDN solve.

A Release probe on a physical iPad Pro M4 marketed with 8 GB RAM completed one
public CT in chest and abdomen modes at EOS: 793/299 tokens in 132/103 seconds,
with 3.76/4.41 GB whole-process peaks. This is standalone execution evidence, not
clinical accuracy, FP32 equivalence, viewer residency or a 12 GB device test.
See [the sanitized receipt](provenance/mobile-experimental-v1.json) and per-release
[checksums](provenance/mobile-SHA256SUMS). The baseline above remains independent.

Use the native SDK at `54ef70550cfe9a25f91b404912ecf6f9e5002d28` or a later reviewed
revision that explicitly contains this profile; old catalogs do not expose it.

## Installation and trust

Release: https://github.com/ThalesMMS/NV-Reason-CT-MLX/releases/tag/ct-fp32-v0.1.0
Model release assets are public and support anonymous application downloads.
No token belongs in the application, source, manifest or index. Each downloaded
asset must match SHA256SUMS and the application's independently pinned catalog.
The index is informational; it cannot grant approval or substitute a trusted identity.

Availability is in index.json. Drafts are downloaded/hashed and installed/tested
offline before the release, index and compiled catalog are explicitly promoted.
Tag/asset contents are never silently overwritten. A withdrawn/incompatible variant
gets an unavailable entry and a source/catalog update; keep its tag/assets/evidence
for reproducibility rather than deleting history.

See provenance/ for qualification/security/resource receipts and manifests/ for
the exact bundle manifest. Publication plan SHA-256: `616937e3cd2f7c283025c8937c676e84f21af7f37d60231bf79b4c19199dee40`.
