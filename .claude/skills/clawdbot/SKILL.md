```markdown
# clawdbot Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you how to contribute to the `clawdbot` codebase, a TypeScript project using the Express framework. You'll learn the project's coding conventions, commit patterns, testing strategies, and detailed workflows for adding features, providers, preparing releases, refactoring, and maintaining robust tests. This guide ensures your contributions are consistent, well-tested, and easily integrated.

## Coding Conventions

- **Language:** TypeScript
- **Framework:** Express
- **File Naming:** Use kebab-case for all file names.
  - Example: `user-service.ts`, `message-handler.test.ts`
- **Import Style:** Use relative imports.
  - Example:
    ```typescript
    import { sendMessage } from './utils/send-message';
    ```
- **Export Style:** Use named exports.
  - Example:
    ```typescript
    // In src/utils/send-message.ts
    export function sendMessage(msg: string) { ... }
    ```
    ```typescript
    // In another file
    import { sendMessage } from './utils/send-message';
    ```
- **Commit Patterns:** Use conventional commits with prefixes like `fix`, `test`, `refactor`.
  - Example: `fix: correct message parsing for telegram provider`

## Workflows

### Feature or Bugfix with Tests and Changelog
**Trigger:** When adding a new feature or fixing a bug that needs to be tested and documented.
**Command:** `/feature-or-bugfix`

1. Edit or add implementation files in `src/` or `extensions/`.
2. Edit or add corresponding test files (`*.test.ts`).
3. Update `CHANGELOG.md` with a summary of your change.

**Example:**
```typescript
// src/services/message-service.ts
export function parseMessage(input: string): Message { ... }
```
```typescript
// src/services/message-service.test.ts
import { parseMessage } from './message-service';
test('parses a simple message', () => { ... });
```
```markdown
# CHANGELOG.md
- feat: add message parsing for new provider
```

---

### Plugin or Extension Provider Addition or Update
**Trigger:** When adding or updating a provider in an extension/plugin.
**Command:** `/add-provider`

1. Edit or add provider implementation files in `extensions/[provider]/`.
2. Edit or add provider test files in `extensions/[provider]/`.
3. Update provider documentation in `docs/providers/` or `extensions/[provider]/README.md`.
4. Update `CHANGELOG.md`.

**Example:**
```typescript
// extensions/telegram/index.ts
export function sendTelegramMessage(msg: string) { ... }
```
```typescript
// extensions/telegram/index.test.ts
import { sendTelegramMessage } from './index';
test('sends a telegram message', () => { ... });
```
```markdown
# docs/providers/telegram.md
## Telegram Provider
Usage instructions...
```

---

### Release Preparation
**Trigger:** When preparing for a new release version.
**Command:** `/prepare-release`

1. Update `CHANGELOG.md` with release notes.
2. Update version numbers in `package.json` and/or platform-specific config files.
3. Regenerate schema/config files (e.g., `src/config/schema.base.generated.ts`, `docs/.generated/*`).
4. Update platform-specific version files (e.g., `apps/ios/Config/Version.xcconfig`, `apps/macos/Sources/OpenClaw/Resources/Info.plist`).

**Example:**
```json
// package.json
{
  "version": "1.2.0"
}
```
```typescript
// src/config/schema.base.generated.ts
// (Regenerated file)
```
```markdown
# CHANGELOG.md
## 1.2.0
- Added WhatsApp provider support
```

---

### Test Suite Consolidation or Hardening
**Trigger:** When improving or consolidating test coverage or reliability.
**Command:** `/consolidate-tests`

1. Edit or merge multiple `*.test.ts` files within a feature or extension.
2. Update or add test utility scripts or fixtures.
3. Sometimes update related documentation.

**Example:**
```typescript
// test/helpers/mock-provider.ts
export function mockProvider() { ... }
```
```typescript
// extensions/feishu/feishu.test.ts
import { mockProvider } from '../../test/helpers/mock-provider';
test('feishu integration', () => { ... });
```

---

### Refactor Extension or Core Module
**Trigger:** When improving code structure, separation, or maintainability in an extension or core module.
**Command:** `/refactor-module`

1. Edit/refactor implementation files in `src/` or `extensions/`.
2. Edit/update corresponding test files.
3. Sometimes update related types or helper files.

**Example:**
```typescript
// Before: extensions/whatsapp/handler.ts
export function handleMsg(msg) { ... }

// After: extensions/whatsapp/message-handler.ts
export function handleMessage(msg: Message) { ... }
```
```typescript
// extensions/whatsapp/message-handler.test.ts
import { handleMessage } from './message-handler';
test('handles whatsapp message', () => { ... });
```

## Testing Patterns

- **Framework:** [vitest](https://vitest.dev/)
- **Test File Pattern:** All test files use the `.test.ts` suffix and are placed alongside or near the files they test.
  - Example: `src/services/user-service.test.ts`
- **Test Example:**
    ```typescript
    import { myFunction } from './my-function';

    test('should return true for valid input', () => {
      expect(myFunction('valid')).toBe(true);
    });
    ```
- **Test Utilities:** Common helpers are placed in `test/helpers/`.

## Commands

| Command              | Purpose                                                         |
|----------------------|-----------------------------------------------------------------|
| /feature-or-bugfix   | Add a new feature or fix a bug, with tests and changelog update |
| /add-provider        | Add or update a provider/extension, with docs and changelog      |
| /prepare-release     | Prepare a new release: changelog, versioning, schema/config     |
| /consolidate-tests   | Consolidate or harden test suites                               |
| /refactor-module     | Refactor an extension or core module, update tests              |
```