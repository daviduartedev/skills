# GitHub description

Load when drafting the evidence section of the pull request body.

## Pattern

Place screenshots in the description body. Do not wrap them in `<details>`. Reviewers skip collapsed images.

```markdown
**After** — store badges render at native size on the mobile mockup:

<img src="" width="360" alt="mobile mockup: store badges and lockup">
```

One heading, one sentence saying what to notice, one image. Several visual changes: several of those blocks, not a gallery without captions.

Before/after when both files exist:

```markdown
**Before** — lockup clipped at the last word:

<img src="" width="360" alt="clipped lockup">

**After** — full lockup visible:

<img src="" width="360" alt="complete lockup">
```

Leave `src` empty in the draft the agent writes. The human drop in the GitHub UI fills it with `user-images.githubusercontent.com` (or `private-user-images`) URLs. Those are the URLs that render on a **private** repository.

## What not to put in `src`

- `raw.githubusercontent.com/...` on a private repo — Camo fetches without auth, images break
- `?token=` download URLs from the Contents API — they expire
- Repo-relative paths (`docs/foo.png`) — they do not resolve in a PR description
- A branch named `pr-assets`, `assets/`, or any folder of screenshots on the consumer git remote

## Human drop

After `gh pr create` (or equivalent), print:

> Drop these files into the PR description on GitHub, matching by filename:
> - `01-….png` — \<caption\>
> - …

The GitHub API cannot upload those binaries into the body. That is why the drop is the human's.
