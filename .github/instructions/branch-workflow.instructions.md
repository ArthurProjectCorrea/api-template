# Branch Naming and Workflow Guide

## Branch Protection Rules

### Protected Branches

Direct commits to these branches are **BLOCKED**:

- `main` - Production-ready code
- `master` - Alternative name for main branch

### Allowed Branch Patterns

All branches must follow these naming conventions:

#### 1. **Feature Branches**

```
feature/<descriptive-name>
```

**Examples:**

- `feature/user-authentication`
- `feature/payment-integration`
- `feature/admin-dashboard`

**When to use:** New features or functionality

---

#### 2. **Bugfix Branches**

```
bugfix/<descriptive-name>
```

**Examples:**

- `bugfix/fix-memory-leak`
- `bugfix/null-pointer-exception`
- `bugfix/login-error`

**When to use:** Bug fixes for develop branch

---

#### 3. **Hotfix Branches**

```
hotfix/<descriptive-name>
```

**Examples:**

- `hotfix/critical-security-patch`
- `hotfix/production-crash`
- `hotfix/data-corruption`

**When to use:** Urgent fixes for production (main branch)

---

#### 4. **Release Branches**

```
release/v<major>.<minor>.<patch>
```

**Examples:**

- `release/v1.0.0`
- `release/v2.1.0`
- `release/v1.2.3`

**When to use:** Preparing a new release (created by Semantic Release or manually)

---

#### 5. **Main Branches**

```
main
develop
```

**main**: Production-ready code only
**develop**: Integration branch for features

---

## Workflow

### Starting New Work

1. **Create a feature branch from develop:**

   ```bash
   git checkout develop
   git pull origin develop
   git checkout -b feature/your-feature-name
   ```

2. **Make commits using Commitizen:**

   ```bash
   git add .
   pnpm run commit
   ```

3. **Push your branch:**

   ```bash
   git push -u origin feature/your-feature-name
   ```

4. **Create Pull Request** to `develop`

### Hotfix Workflow

1. **Create hotfix branch from main:**

   ```bash
   git checkout main
   git pull origin main
   git checkout -b hotfix/critical-fix
   ```

2. **Make commits and push:**

   ```bash
   git add .
   pnpm run commit
   git push -u origin hotfix/critical-fix
   ```

3. **Create Pull Request** to `main` AND `develop`

### Release Workflow

Releases are managed by **Semantic Release** via GitHub Actions.

1. Go to **Actions** → **Release** workflow
2. Click **Run workflow**
3. Select branch: `develop` (for beta) or `main` (for stable)
4. Semantic Release will:
   - Analyze commits
   - Determine version
   - Update CHANGELOG.md
   - Create release commit: `chore(release): x.y.z [skip ci]`
   - Create Git tag: `vx.y.z`
   - Create GitHub Release

## Validation

### Automatic Validation

Every commit will validate:

- ✅ Branch name follows the pattern
- ✅ No direct commits to `main`/`master`
- ✅ Commit message follows Conventional Commits

### Manual Validation

Check if your branch name is valid:

```bash
pnpm run branch:validate
```

## Error Messages

### ❌ Invalid Branch Name

```
Branch name must follow the pattern:
  - main
  - develop
  - release/v{major}.{minor}.{patch}
  - feature/{name}
  - bugfix/{name}
  - hotfix/{name}
```

**Solution:** Rename your branch:

```bash
git branch -m feature/my-new-feature
```

### ❌ Direct Commit to Main

```
ERROR: Direct commits to 'main' branch are not allowed!
```

**Solution:** Create a feature branch:

```bash
git checkout -b feature/my-feature
git commit --amend --no-edit
```

## Best Practices

1. **Use descriptive names**: `feature/add-user-auth` not `feature/fix`
2. **Keep branches short-lived**: Merge frequently to avoid conflicts
3. **Delete branches after merge**: Keep repository clean
4. **Always use lowercase**: `feature/user-auth` not `Feature/User-Auth`
5. **Use hyphens, not underscores**: `feature/user-auth` not `feature/user_auth`

## Branch Naming Rules

- ✅ Lowercase only
- ✅ Use hyphens (`-`) for word separation
- ✅ Alphanumeric characters, dots (`.`), and underscores (`_`) allowed
- ❌ No spaces
- ❌ No special characters except `-`, `.`, `_`
- ❌ No uppercase letters

---

**Remember**: These rules are enforced automatically by Git hooks. Invalid branches will be rejected on commit! 🛡️
