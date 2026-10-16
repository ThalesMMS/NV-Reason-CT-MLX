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
Acquisition is separate. Quantized/other failed or unqualified variants are unavailable.

Weights use NVIDIA OpenMDW-1.1. Bundled component notices include Apache-2.0 and MIT;
see LICENSE, NOTICE and licenses/. No exams, embeddings, prompts or generated reports
are distributed here. This repository contains metadata/notices only; all tools live
in the Swift source repository and all weights live in versioned release assets.


## Separate experimental mobile profile

The `ct-mobile-4bit-v0.1.0` release deliberately accepts numerical changes for
8–12 GB devices. It is not the BF16-storage/FP32-compute baseline described above.
See README and provenance/mobile-experimental-v1.json for 8 GB iPad execution
measurements and limits. No clinical validation or FP32 equivalence is claimed.
