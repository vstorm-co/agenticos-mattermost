# AgenticOS Mattermost plugin

This repository owns the installable Mattermost server plugin. AgenticOS owns
channel transport, Vault, identity linking and agent execution. Do not introduce
a central relay or another agent runner here.

- Work on a feature branch, never commit on `main`. Commit and push finished,
  verified pieces. Use Conventional Commits, no AI attribution, and scoped diffs.
- Keep the Go toolchain, SDK and dependencies pinned. Run `make check bundle`:
  formatting, vet, race tests, govulncheck and both Linux architecture builds.
- All setup commands and HTTP callbacks require a current Mattermost system
  administrator. Bind one-time dialogs to identity, action, channel and config.
- Never persist or log the AgenticOS setup access token or Mattermost bot token.
  Only send bot credentials directly over verified HTTPS to the chosen instance's
  organization-bound Vault. Do not follow redirects or use environment proxies.
- Preserve cleanup handles and distinguish failure, unknown remote acceptance and
  success. Revoke locally before remote cleanup; never retry uncertain creation.
- Preserve the same per-sender identity and permissions as existing channels.
- Test new behavior and refusal paths; explain live-test limitations honestly.
- Update README and security instructions when behavior changes. The copied logo
  comes from AgenticOS `docs/assets/logo.svg`; keep its provenance and license.
