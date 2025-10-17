# Test Translation Sync (Source)

**⚠️ Testing Repository - Not for Production Use**

This repository is for testing the `quantecon/action-translation-sync` GitHub Action.

## Purpose

Test bed for translation sync action development and validation.

## Structure

- `lectures/` - Test lecture content in MyST Markdown
  - `intro.md` - Basic concepts with math and code
  - `advanced.md` - Advanced topics with dynamic programming
  - `_toc.yml` - Table of contents
- `.github/workflows/` - Translation sync workflow

## Target Repository

Translations are synced to: [`quantecon/test-translation-sync.zh-cn`](https://github.com/quantecon/test-translation-sync.zh-cn)

## Workflow

1. Make changes to lectures
2. Create pull request
3. Merge PR
4. Action runs automatically
5. Check target repo for translation PR

## Testing

See [action-translation-sync documentation](https://github.com/quantecon/action-translation-sync/blob/main/docs/TEST-REPOSITORIES.md) for testing guide.
