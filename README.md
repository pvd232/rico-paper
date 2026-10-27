# RICO paper

Reimplement the RICO MIL and asymmetric Hopfield models in JAX, beginning with
the source data download. This repository starts with the learning workspace;
model implementation and scientific comparisons are pending.

Work through [the source-data notebook](notebooks/01_source_data.ipynb) one
step at a time. Put reusable code in [the Python package](src/rico_paper/__init__.py),
validate configuration and saved metadata with Pydantic, and carry runtime
arrays in dataclasses. Keep each notebook cell short enough to inspect its
inputs and outputs together.

[The source manifest](references/sources.toml) records the original model
commits and first dataset download. Consult those commits when implementing
each operation. Copy examined source files individually and record their
origin before publishing them here.

## Environment

Use Python 3.12 and the project-local `.venv`:

```bash
python3.12 -m venv .venv
source .venv/bin/activate
python -m pip install -e '.[dev,notebook]'
```

On a Linux NVIDIA host with a compatible CUDA 13 driver, install
`'.[dev,notebook,cuda13]'` instead. Check the driver against
[JAX's installation requirements](https://docs.jax.dev/en/latest/installation.html)
before selecting a GPU extra. JAX uses the GPU; Viper also requires PyTorch for
its existing checkpoint serializer. A CPU PyTorch wheel is sufficient for that
serializer.

The Viper dependency pins the JAX continuation change from
[PR #22](https://github.com/pvd232/viper/pull/22). That change has passed CPU
continuation tests; numerical parity with the original RICO models remains
to be measured.

## Working together

The learner applies model and data-pipeline edits and runs their checks.
Codex inspects the result and proposes the next bounded change. Infrastructure
setup can be delegated separately.

Before checking Python changes, fix imports and format the actual files:

```bash
ruff check --select I --fix src
ruff format src
pyrefly check
# Run the affected tests here as implementation is added.
ruff format --check src
ruff check src
```

Keep downloads and generated runs outside Git. Preserve each expensive
measurement before running downstream analysis. The original model records
state that HOLD informed model development; comparisons using that split are
development results.
