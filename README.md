# KCD3 Reconstruction Benchmark Evidence

Benchmark evidence for the KCD3 single-pass UAV reconstruction pipeline.

## Test Conditions

- Same ~35 second UAV footage
- Same hardware
- NVIDIA RTX 4060 Laptop GPU — 8 GB VRAM
- Same MASt3R-SLAM reconstruction configuration
- Visualization disabled during both tests

## Results

| Metric | Full-Frame Baseline | KCD3 Adaptive |
|---|---:|---:|
| Frames Processed | 2,097 | 70 |
| Streaming Elapsed | 850.631 s | 34.737 s |
| Average Start Lag | 399,386.3 ms | 24.3 ms |
| Maximum Start Lag | 815,391.4 ms | 408.7 ms |
| Maximum Completion Lag | 815,677.4 ms | 907.8 ms |
| Stream Status | BACKLOG DETECTED | PASS — keeping up with 2 FPS |

## Optimization Result

**850.631 s → 34.737 s**

**24.49× faster reconstruction**

Adaptive frame selection reduced the reconstruction workload from:

**2,097 raw frames → 70 informative frames**

This represents a **96.66% reduction in processed frames**.

## Logs

- `logs/baseline_fullframes_20260927_202118.log`
- `logs/optimized_70frames_20260927_204938.log`

## Important Note

The baseline log contains:

`Input stream span : 1048.000 s`

This field comes from a legacy benchmark calculation designed for a 2 FPS image-sequence input and is not valid for the raw ~60 FPS MP4 baseline.

The raw-video stream itself reaches:

`frame=2096 t=35.0s`

Therefore, the optimization comparison uses **Streaming elapsed**, which is directly comparable between the two reconstruction runs.
