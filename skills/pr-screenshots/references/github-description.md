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

Fill `src` with the URL returned by the upload below. That URL is `https://github.com/user-attachments/assets/<uuid>`. On a private repository it renders for someone who can open the PR. An anonymous fetch of the same URL is a 404; that is expected.

## What not to put in `src`

- `raw.githubusercontent.com/...` on a private repo — Camo fetches without auth, images break
- `?token=` download URLs from the Contents API — they expire
- Repo-relative paths (`docs/foo.png`) — they do not resolve in a PR description
- A branch named `pr-assets`, `assets/`, or any folder of screenshots on the consumer git remote

## Upload

After the PR exists, upload each file. Do not print the token.

1. Repository id: `gh api repos/<owner>/<repo> --jq .id`
2. Token: `gh auth token` (OAuth, classic PAT, or fine-grained PAT with write). GitHub Enterprise Server does not serve this endpoint.
3. `POST https://uploads.github.com/user-attachments/assets?name=<filename>&content_type=image/png&repository_id=<id>`
   - `Authorization: Bearer <token>`
   - `Accept: application/vnd.github+json`
   - `Content-Type: application/octet-stream`
   - Body: the file bytes
4. A 201 body has `url`. Put that URL in `src`. Then `PATCH` the pull request body (`gh api repos/<owner>/<repo>/pulls/<n> -X PATCH` with a UTF-8 JSON `{"body": …}`).

A 404 from that POST means the token cannot write. Then, and only then, list the local filenames and ask the human to drop them in the GitHub description.
