# AGENTS.md

## Cursor Cloud specific instructions

This is **react-color**, a React color picker component library (v1.3.0). It is a client-side-only npm library with no backend services or databases.

### Node.js version

The project requires **Node.js 10.x** (installed via `nvm use 10`). It uses Babel 5, Gulp 3, and Webpack 1, which are incompatible with Node 12+. The CI originally targeted Node 4, but Node 10 is the practical minimum that works with modern npm registries.

### Key commands

All build/test/dev tasks use Gulp (installed globally as `gulp@3.9.1`):

| Task | Command | Description |
|------|---------|-------------|
| Tests | `gulp test` | Runs Mocha test suite (23/26 pass; 3 pre-existing failures due to React internal API changes) |
| Lint | `npx jscs src/` | JSCS with Airbnb preset (pre-existing Flow annotation warnings) |
| Build lib | `gulp lib:dist` | Transpiles `src/` to `lib/` |
| Build modules | `gulp modules:dist` | Transpiles vendored modules |
| Build docs | `gulp docs:dist` | Webpack production build of docs |
| Build all | `gulp dist` | Runs all three dist tasks |
| Dev server | `gulp docs:dev` | Webpack dev server on http://localhost:9100 with HMR |
| Test watch | `gulp test:watch` | Re-runs tests on file changes |

### Gotchas

- Peer dependencies `react@15` and `react-dom@15` must be installed explicitly (`npm install react@15 react-dom@15`) since npm 3+ doesn't auto-install peers.
- `react-addons-test-utils@15` is needed for tests (the `^0.14.0` in devDependencies is incompatible with React 15).
- Always run `source ~/.nvm/nvm.sh && nvm use 10` before any npm/gulp command.
