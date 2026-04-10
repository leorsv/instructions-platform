# Instructions Platform

A centralized repository of coding instructions for GitHub Copilot, consumed by separate project repos.

## How it works

1. This repo hosts plain markdown instruction files under `instructions/` — one per stack/framework.
2. Consumer repos run a sync script that fetches the relevant file from this repo's raw GitHub URL and writes it to their own `.github/copilot-instructions.md`.
3. GitHub Copilot automatically picks up `.github/copilot-instructions.md` in every request.

```
instructions-platform (this repo)
  └── instructions/
        ├── angular.md       ← fetched by angular-app
        └── javascript.md    ← fetched by js-app

angular-app (separate repo)
  └── .github/
        └── copilot-instructions.md  ← synced from instructions-platform

js-app (separate repo)
  └── .github/
        └── copilot-instructions.md  ← synced from instructions-platform
```

## Adding new instructions

1. Create a new file under `instructions/` (e.g. `instructions/react.md`).
2. Push to `main`.
3. In the consumer repo, point the sync script at the new raw URL.

## Available instructions

| File | Stack |
|------|-------|
| [instructions/angular.md](instructions/angular.md) | Angular |
| [instructions/javascript.md](instructions/javascript.md) | JavaScript |

## Raw URLs (replace `YOUR_ORG` with your GitHub username/org)

```
https://raw.githubusercontent.com/leorsv/instructions-platform/master/instructions/angular.md
https://raw.githubusercontent.com/leorsv/instructions-platform/master/instructions/javascript.md
```
