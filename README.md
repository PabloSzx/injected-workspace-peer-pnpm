# injected-workspace-peer-pnpm

```json
{
  "name": "a",
  "version": "0.0.1",
  "devDependencies": {
    "b": "workspace:^0.0.1"
  },
  "peerDependencies": {
    "b": "workspace:^0.0.1"
  }
}
```

```json
{
  "name": "b",
  "version": "0.0.1"
}
```

```json
{
  "name": "c",
  "version": "0.0.1",
  "dependencies": {
    "a": "workspace:^0.0.1"
  },
  "devDependencies": {
    "b": "workspace:^0.0.1"
  },
  "dependenciesMeta": {
    "a": {
      "injected": true
    }
  }
}
```

```sh
pnpm -v
7.0.0-rc.2
```

```sh
pnpm update -r

Scope: all 3 workspace projects
 ERR_PNPM_PEER_DEP_ISSUES  Unmet peer dependencies

packages/c
└─┬ a
  └── ✕ missing peer b@workspace:^0.0.1
Peer dependencies that should be installed:
  b@workspace:^0.0.1

Progress: resolved 1, reused 0, downloaded 0, added 0

```
