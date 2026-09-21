# Screenshots belong in the PR description, not on the branch

The published GitHub repo is `daviduartedev/skills`. A fifth published skill, **pr-screenshots**, captures UI evidence for a pull request. Image files must not land in the implementation diff (`assets/`, `pr-assets/`, or similar). GitHub has no public API to upload them into the description; the human drops the named files in the GitHub UI. That is the only path that renders on a private repository. Scanners and SDD orchestrators stay out.
