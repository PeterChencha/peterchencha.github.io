## Summary

<!-- What changed, in one or two sentences. -->

## Route

<!-- e.g. feature/scan-retries -> dev -->

## Reason for the change

<!-- The problem being solved. Link the issue if there is one. -->

## Implementation notes

<!-- Anything non-obvious: new files, config keys, migration steps, follow-ups. -->

## Validation performed

<!--
List what actually ran and its result. Do not write "tests pass" unless they did.
e.g. python -m unittest discover -s tests  ->  42 tests, OK
     manual run on Windows (G:\Hermes\kplc) -> ingest + query checked
-->

## Testing status

- [ ] Unit tests run locally
- [ ] CI green on this PR
- [ ] Exercised on the host that runs it (Windows / macOS) where relevant
- [ ] Not tested — reason:

## Known risks

<!-- Blast radius, data touched, anything that could behave differently. -->

## Deployment implications

<!--
Does merging this deploy anything? For peterchencha.github.io: yes, every push to
main redeploys Pages. For kplc: no, production changes only when G:\Hermes\kplc is
fast-forwarded. Say which.
-->

## Rollback

<!-- The exact action that restores the previous behaviour. -->

## Checklist

- [ ] Target branch is `dev` (or `main` only for a promotion/hotfix)
- [ ] Commits follow Conventional Commits
- [ ] No secrets, tokens, or personal data added
- [ ] No history rewrite or force-push was used
- [ ] Branch can be deleted after merge
