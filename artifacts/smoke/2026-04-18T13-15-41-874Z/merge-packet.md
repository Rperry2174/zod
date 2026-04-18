# Smoke test — merge packet

## Repository root

This workspace clone lives at **`/workspace`**. The repo is the **[Zod](https://github.com/Rperry2174/zod)** validation library (`Rperry2174/zod` on GitHub): a pnpm monorepo (`packages/zod`, `packages/docs`, tooling packages, shared config). Root layout includes workspace package folders, tooling (`pnpm`, Vitest, Biome), and standard library documentation and tests typical of this project.

## Current branch (cloud workspace)

Working branch in this cloud workspace: **`main`** (tracks `origin/main`; clean working tree aside from intentional smoke artifacts).

## Why artifact handoff goes through the controller

Artifact handoff is routed **through the controller** so outputs land in one **trusted, audited path**: the controller enforces **policy** (allowed paths like `artifacts/smoke/…`, naming, retention), **provenance** (who/when/tool run), and **delivery guarantees** for downstream merge or review. Without the controller, ad hoc writes risk **wrong directories**, **credential leakage**, **skipped verification**, or **artifacts that never attach to the workflow**—so merges and audits cannot rely on them. The controller is the gate that binds runnable commands, recorded metadata, and stable artifact URLs or paths for handoff.
