# Surfaces

Load this file in step 2 of `explain-infra`. Skip a path that is absent.

1. The _window_ (hosts, ports, account names already stated)
2. `docker-compose.yml`, `Dockerfile`, and documented `pnpm` / `package.json` dev scripts
3. `.github/workflows/` deploy and CI
4. Cycle infra notes (`implementation-notes.md`, `validation.md` for that cycle)
5. IaC when present (Terraform, task definitions described in those notes)
6. Env **names** from `.env.example` or documented tables — never paste a live secret value

Report an expired session or missing cloud login as a blocker, not as a guessed topology.
