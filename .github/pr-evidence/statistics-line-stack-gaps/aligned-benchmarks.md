# Aligned downsampling benchmark

All three runs used the same current source (commit `90adaebc96cfe69baead462b6f14f840b1531356`) and the same deterministic seeded fixtures. Runs 1 and 2 are the required repeated baseline; run 3 is the fresh measurement. No runtime source optimization was made in this task.

| Benchmark | Run 1 mean ms | Run 2 mean ms | Run 3 mean ms | Run 3 ops/sec | Run 3 latency RME |
| --- | ---: | ---: | ---: | ---: | ---: |
| min/max small (1k points) | 0.04748 | 0.03124 | 0.03713 | 30101.34 | 2.08% |
| min/max medium (10k points) | 0.18742 | 0.15275 | 0.13739 | 7299.65 | 0.17% |
| min/max large (100k points) | 1.25788 | 1.06273 | 1.01462 | 985.82 | 0.10% |
| mean large (100k points) | 1.11064 | 0.89935 | 0.81519 | 1234.21 | 0.51% |
| min/max large object points (100k points) | 1.72496 | 1.20347 | 1.20487 | 840.21 | 0.87% |
| min/max large with a few gaps (100k points) | 1.89643 | 1.62604 | 1.80937 | 569.51 | 1.70% |
| min/max large mostly gaps (100k points) | 1.71657 | 1.51700 | 1.28304 | 783.00 | 0.55% |
| aligned stack min/max dense (2x100k points) | 68.66492 | 55.91891 | 57.87724 | 17.56 | 3.96% |
| aligned stack min/max mostly gaps (2x100k points) | 25.47759 | 12.18452 | 13.60660 | 73.91 | 1.79% |

The new aligned cases characterize the current implementation only. Because no optimization was requested or made here, this is not a before/after performance claim.

Reproduce with `yarn test:bench down-sample --reporter=default --reporter=json --outputFile=results.json`. Raw reports: [run 1](aligned-bench-run1.json), [run 2](aligned-bench-run2.json), [run 3](aligned-bench-run3.json).
