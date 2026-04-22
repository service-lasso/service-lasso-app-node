# service-lasso-app-node

Template repo for a plain-Node app host around Service Lasso.

Package identity:
- `@service-lasso/service-lasso-app-node`

Purpose:
- show how to host Service Lasso in a plain Node app without coupling that logic into core
- act as a quick-start template for downstream teams
- stay close to real runtime behavior while remaining outside the core repo

Expected runtime model:
- `servicesRoot`
- `workspaceRoot`

Current implementation:
- plain Node host entrypoint under `src/index.js`
- published `@service-lasso/service-lasso` runtime package consumption
- host-owned shell at `/`
- mounted sibling `lasso-@serviceadmin` build at `/admin/`
- tracked repo-owned `services/` definitions for Echo Service and Service Admin
- prepared local `servicesRoot` copied from tracked service manifests plus a generated Echo Service runner

Current local start command:
- `npm start`

Current local URLs:
- host shell: `http://127.0.0.1:19010`
- admin UI: `http://127.0.0.1:19010/admin/`
- runtime API: `http://127.0.0.1:18081`

## Current release artifact

This starter repo now has a bounded runnable app-host release artifact.

Current local commands:
- `npm test`
- `npm run release:artifact`
- `npm run release:verify`

Current pipelines:
- `CI`
  - runs on pushes to `main` and on pull requests
  - installs dependencies and runs `npm test`
- `Release`
  - runs on pushes to `main` or by manual dispatch
  - runs tests, verifies the artifact, uploads the packaged files, and creates or updates the rolling `latest` release on `main`

Current shipped artifact contents are documented in:
- `docs/release-artifact.md`

Current honest label:
- this repo ships a runnable plain-Node app-host starter plus a starter-template source bundle

## Minimal POC

The first concrete target for this repo is documented in:
- `docs/minimal-poc.md`
