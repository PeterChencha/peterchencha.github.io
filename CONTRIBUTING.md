# Contributing

`main` is production. `dev` is integration. Work happens on short-lived branches
and reaches `main` only through a reviewed `dev -> main` promotion.

```
feature/<short-description> --PR--> dev --PR--> main
fix/<short-description>     --PR--> dev --PR--> main
hotfix/<short-description>  --PR--> main --reconcile--> dev
```

## Day-to-day

1. Start from the latest `dev`:
   `git switch dev && git pull --ff-only && git switch -c feature/<short-description>`
2. Keep the branch small and single-purpose. Commit as you go using
   Conventional Commits (`feat:`, `fix:`, `docs:`, `refactor:`, `test:`, `build:`,
   `ci:`, `chore:`). Do not rewrite history that is already pushed.
3. Validate locally with the repository's own test command and say exactly what
   you ran in the PR body.
4. Push the branch and open a PR **into `dev`**. Do not open feature/fix PRs
   against `main`.
5. Merge only when the checks are green. Delete the branch after the merge is
   verified.

## Promoting to production

`dev -> main` is a production event. Before opening it:

- CI on `dev` is green.
- The change has been exercised the way production runs it (the Windows/macOS
  host, not only CI) where the code is host-specific.
- The PR body states deployment impact and rollback.
- A human adds the `promotion-approved` label. The PR Worker will not merge a
  promotion without it.

Use a merge commit for promotions, and squash for feature/fix PRs into `dev`.
After a promotion, fast-forward `dev` to `main` so the two never drift.

## Hotfixes

Branch from the commit that is actually running in production, fix it, PR into
`main`, then open the reconciliation PR `main -> dev` (the PR Worker's
`sync-back` command does this). A hotfix is not finished until `dev` contains it.

## Never

- Force-push `main`, `dev`, or any branch someone else may have based work on.
- Commit secrets. They belong in `G:\Hermes\secrets` or the platform's secret store.
- Delete a branch that has unmerged commits, or rewrite published history to make
  a repository "look tidy".

If a control blocks you, fix the cause. Do not look for a bypass.
