# Chat Playground — Mobile

> **Template copy.** This repo is one of the name-substituted Expo SDK 53 / Expo Router
> template copies in `bookchaowalit-mobile`. The canonical template is
> [`bookchaowalit-mobile/community-hub-mobile`](https://github.com/bookchaowalit-mobile/community-hub-mobile);
> this copy keeps its own code (no shared package). Consolidation/archive is pending
> owner decision D5 (BD-033) per `repository-catalog/portfolio/MOBILE-CONSOLIDATION-2026-10.md`
> in solo-empire.

React Native mobile app (Expo) for **Chat Playground**.

Part of [Chaowalit Greepoke](https://bookchaowalit.com)'s 101 Portfolio Projects.

## Tech Stack

- **Framework:** Expo SDK 53 + Expo Router
- **Language:** TypeScript
- **Navigation:** Expo Router (file-based)
- **UI:** React Native + Ionicons

## Features

- **Chat playground** (home tab): send messages and get replies from a local,
  deterministic mock assistant, so the app works fully offline and never
  sends data anywhere. Try `hello`, `/help`, `/reverse`, `/count`, `/upper`,
  `/tokens`.
- **System prompt / persona** field included in the conversation.
- **Token estimates** (~4 chars/token) for the draft and the whole
  conversation, a selectable plain-text **transcript** view, and Clear.
- Pure logic in `lib/chat.ts` (also includes `trimToBudget` for fitting a
  conversation into a context budget). Plugging in a real model API is on the
  backlog and must go through a server-side proxy, never an API key in the app.

## Getting Started

```bash
npm ci
npx expo start
```

## Validation

```bash
npm run validate   # expo lint + tsc --noEmit + vitest
npx expo export --platform android --output-dir dist   # bundle smoke check
```

Pure logic lives in `lib/` and is unit-tested with Vitest (`lib/*.test.ts`).
CI (`.github/workflows/ci.yml`) calls the shared `bookchaowalit/platform-ci-workflows`
`ci-node.yml` and `security.yml` (v1.1.1, SHA-pinned): `npm ci`, lint, typecheck, tests,
the Android JS bundle export above, plus Gitleaks, Semgrep, OSV-Scanner and Trivy.
Failures are not masked. There is no EAS / Expo cloud build in CI: that needs an
owner-linked Expo account (owner action).

## Build

```bash
# Android
npx eas build --platform android --profile preview

# iOS
npx eas build --platform ios --profile preview
```

## Related

- **Frontend:** [bookchaowalit-website/chat-playground-frontend](https://github.com/bookchaowalit-website/chat-playground-frontend)
- **Portfolio:** [bookchaowalit.com](https://bookchaowalit.com)

## License

MIT
