# Release Radar API

Release Radar turns public GitHub release notes into compact change signals an agent can consume before upgrading a dependency.

## API

`GET /v1/releases?repo=owner/repository&limit=5`

The API reads public GitHub releases, returns the most recent non-draft releases, and separates lines that signal breaking changes, removals, deprecations, migrations, or required action from ordinary highlights.

Examples:

```sh
curl 'http://localhost:8787/v1/releases?repo=cloudflare/workers-sdk&limit=3'
curl 'http://localhost:8787/health'
```

## Run and test

```sh
npm install
npm test
npm run check
npm run dev
```

## Deployment

Set `COMMIT` in `src/index.ts` to the reviewed 40-character Git commit immediately before deploy. The health and X-Agent verification endpoints report that same value.

```sh
npm run deploy
```
