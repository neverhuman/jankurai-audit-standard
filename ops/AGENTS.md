# ops Agent Instructions

This cell owns the operational control plane for jankurai-standard: the pinned CI
script entrypoints and the local/CI parity tooling.

## Owns

- `ops/ci/*.sh` — the thin lane scripts (`lib`, `required`, `fast`, `security`,
  `audit`, `tool-adoption`, `quality-gates`) shared by local runs and CI.
- `ops/git-hooks/pre-push` — the mandatory pre-push gate that runs
  `bash ops/ci/quality-gates.sh`.

## Forbidden

- Do not put product, standard, or documentation logic here; this cell is
  CI plumbing only.
- Do not add GitHub Actions workflows. GitHub is a publishing mirror only; CI
  runs on the forge and our own hosts through `ops/ci/*.sh`.
- Do not hand-edit generated zones declared in
  [`agent/generated-zones.toml`](../agent/generated-zones.toml).

## Proof lane

Run the security and workflow-lint proof for this cell with:

```bash
bash scripts/ci-local.sh security
bash scripts/ci-local.sh gates
```

Owner: `ops`. See [`docs/testing.md`](../docs/testing.md) for the full lane map.
