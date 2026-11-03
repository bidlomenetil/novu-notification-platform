# Novu

## Source development guide

### Product and architecture

Notification workflows that deliver messages through multiple providers and expose an embeddable inbox.

Nx/pnpm workspace with API, worker, websocket and dashboard applications in `apps/`, domain/shared libraries in `libs/`, and provider/SDK packages in `packages/`. Workers coordinate delivery using backing data and queue services.

### Requirements and local development

Node >=22 <23 and pnpm ^11.28.0; database and queue services configured by the development scripts.

Run these commands from the repository root unless a `cd` is shown:

```sh
pnpm install
pnpm dev-environment-setup
```

These are source-defined entry points. Full dependency installation and service startup were not run during the portfolio maintenance audit; successful application deployment is not claimed.

### Environment configuration

Inspect `scripts/setup-env-files.js` and the component-specific environment templates before startup. Supply local database, service URLs and integration credentials through untracked environment files or a secret manager. Do not copy production credentials into tracked files.

### Testing

```sh
pnpm test:providers
pnpm build:api
```

The full application suite requires the dependencies and services described above. Source paths and documented script names were inspected, and `git diff --check` passed. Application tests and builds were not executed.

### Deployment and integrations

Start with `docker` and review image versions, persistent data paths, authentication, exposed ports and backups before production use. Integration implementations and configuration are in the source directories described above; generated API clients must stay in sync with server contracts.

### Source provenance and license

Imported from [novuhq/novu](https://github.com/novuhq/novu); upstream functionality and copyright belong to the original contributors. Local Git history begins with a 2026 source snapshot import, not historical authorship. The exact imported upstream revision is unknown. The upstream GitHub repository was created on 2021-08-26; the local year directory is organizational metadata.

Read [LICENSE-ENTERPRISE](LICENSE-ENTERPRISE), [LICENSE-MIT](LICENSE-MIT) and nested license/notice files before redistribution; enterprise and bundled third-party components may use different terms. Restored root license text was retrieved verbatim from the official upstream repository during this maintenance pass.

## Distribution status

Further publication of this complete imported snapshot is on hold: `EE-PACKAGES-LICENSE and LICENSE-ENTERPRISE` restricts redistribution of enterprise code. The existing remote import was not deleted or rewritten. Resolve permission or obtain a correctly scoped community source tree before publishing additional history. Root community licensing does not override enterprise terms.
