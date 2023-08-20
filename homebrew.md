# Homebrew

## Reinstall all programs

```bash
brew reinstall --force $(brew list --formula)
```

## Reinstall all GUI programs

```bash
brew reinstall --force --zap $(brew list --cask)
```

## Install programs matching a regex pattern

I.e., programs starting with 'lua'

```bash
brew reinstall --force $(brew search --formula --quiet '/^lua/')
```

I.e., programs starting with 'gnu-'

```bash
brew reinstall --force $(brew search --formula --quiet '/^gnu/')
```
