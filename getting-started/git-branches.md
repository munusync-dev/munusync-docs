# Working with Git Branches and Pull Requests

## Branches Overview

- **main (or master):** Stable, production-ready.
  _Never push directly._

- **dev:** Integration branch for testing new features.
  _Never push directly._

---

## Branch & PR Naming Convention

- **Branch format:**

  ```
  [type]/[ticket-number]-[short-description]
  ```

  Examples:

  - `feature/42-user-authentication`
  - `fix/17-login-error`
  - `chore/105-update-docs`

- **PR title format:**

  ```
  [type] [ticket-number]: short description
  ```

  Examples:

  - `feature 42: implement user authentication`
  - `fix 17: resolve login issue`

---

## Rules

- Always branch off from `dev`.
- Never push directly to `dev` or `main`.
- Use PRs to merge into `dev`.
- After testing, merge `dev` into `main`.

---

## Steps

1. **Sync dev branch**

   ```bash
   git checkout dev
   git pull origin dev
   ```

2. **Create new branch**

   ```bash
   git checkout -b feature/42-user-authentication
   ```

3. **Make changes**

4. **Stage changes**

   ```bash
   git add .
   ```

5. **Commit changes**

   ```bash
   git commit -m "Implement user registration API"
   ```

6. **Push branch**

   ```bash
   git push origin feature/42-user-authentication
   ```

7. **Create Pull Request** on GitHub

   - Add title and description
   - Assign reviewers
   - Submit

8. **Review & update**

   - Make fixes if requested
   - Push to same branch

9. **Merge PR** into `dev` once approved

10. **Update local branches**

    ```bash
    git checkout dev
    git pull origin dev
    git checkout main
    git pull origin main
    ```
