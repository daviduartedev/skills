# grill-to-ship runs the spec-driven loop after a grill

The published GitHub repo is `daviduartedev/skills`. Earlier ADRs kept SDD orchestrators out of the collection. That changes for one runner: **grill-to-ship**, run by hand at the end of a grill, chains `to-spec`, `to-tickets`, `prototype`, `implement` (one commit per ticket), and `dvd-tests`, with a human gate at each stage. It does not reimplement those skills; it orders them and holds the gates. It is user-invoked only, so it adds no always-loaded description. The 0.7 line is nine skills. Scanners and an evaluation harness stay out.
