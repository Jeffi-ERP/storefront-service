<!-- Managed from AloysJehwin/Jeffi_Stores (oss/templates); edits here are overwritten by the next export. -->
<p align="center"><a href="https://github.com/Jeffi-ERP"><img src="https://raw.githubusercontent.com/Jeffi-ERP/.github/main/assets/jeffi-erp-logo.svg" width="64" alt="Jeffi ERP"></a></p>

# storefront-service

Customer storefront (Next.js): catalogue, search, cart, checkout and accounts.

Part of [Jeffi ERP](https://github.com/Jeffi-ERP), where the Jeffi Stores commerce platform is developed in the open. In the workspace this repo is `storefront-service/`. It builds and tests inside the assembled workspace, not on its own.

## Set up

```bash
git clone https://github.com/Jeffi-ERP/workspace.git jeffi-erp
cd jeffi-erp
node oss/assemble.mjs                  # clones every Jeffi ERP repo into its folder
ONNXRUNTIME_NODE_INSTALL=skip npm ci
```

Then follow [Set up the workspace](https://github.com/Jeffi-ERP/.github/blob/main/CONTRIBUTING.md#set-up-the-workspace) for the database, `.env.local` and a local admin. You never need Jeffi Stores' own keys. To change this repo, fork it and add your fork as a remote inside `storefront-service/`.

## How a change gets in

1. Open a pull request against `main`. Nothing runs yet.
2. A maintainer reads it and adds the `ok-to-test` label. That runs **PR checks** and **Guard**. A new push removes the label until a maintainer looks again.
3. When both pass, a maintainer squash-merges it. The merge runs pre-build and build, then waits for a maintainer to approve the promotion.
4. After approval the change is opened as a pull request on [AloysJehwin/Jeffi_Stores](https://github.com/AloysJehwin/Jeffi_Stores) and ships with a later release. The export from that release brings it back here.

`.github/` and `LICENSE` (and `oss/` in workspace) come from AloysJehwin/Jeffi_Stores, and Guard rejects pull requests that change them. Open an issue for those instead.

## Checks

| Stage | Check | Command (from the workspace root) |
|---|---|---|
| PR checks (after `ok-to-test`) | Lint | `npx next lint storefront-service` |
| PR checks (after `ok-to-test`) | Type check | `npx tsc --noEmit -p storefront-service/tsconfig.typecheck.json` |
| PR checks (after `ok-to-test`) | Unit tests | `npx vitest run --project storefront --passWithNoTests` |
| Pre-build (after merge) | Lint | `npx next lint storefront-service` |
| Pre-build (after merge) | Type check | `npx tsc --noEmit -p storefront-service/tsconfig.typecheck.json` |
| Build (after merge) | Unit tests | `npx vitest run --project storefront --passWithNoTests` |
| Build (after merge) | Build | `npm run build:storefront` |

Run a stage locally from the workspace root: `node oss/checks.mjs storefront-service pr`.

## Licence

[Business Source License 1.1](../LICENSE). You may read, modify and make non-production use of this code. Production use needs a commercial licence from Jeffi Stores until the Change Date in the licence, when it becomes Apache-2.0. Contributions are accepted on the terms in [CONTRIBUTING](https://github.com/Jeffi-ERP/.github/blob/main/CONTRIBUTING.md).
