# sandbagging-evaluation

Sandbagging evals using [Inspect](https://inspect.aisi.org.uk/) (UK AISI). Models answer the same
multiple-choice questions under different system-prompt conditions; the accuracy gap vs. `baseline`
is the sandbagging signal.

## Setup

```bash
uv sync
touch .env   # add API keys
uv run jupyter lab notebooks/sandbagging_eval.ipynb
```

## Notebook layout

1. Setup · 2. **Config** (`EvalConfig` — models, dataset, conditions, limits) · 3. Dataset (toy / WMDP / MMLU / GPQA)
4. Tasks (one per condition) · 5. Run (`eval_set`, resumable) · 6. Results (accuracy + gap) · 7. Per-sample flips

Smoke test with `models=["mockllm/model"], dataset="toy"` (no API cost).

## Viewing logs


In the root of this repository run:

```bash
uv run inspect view --log-dir logs/
```
