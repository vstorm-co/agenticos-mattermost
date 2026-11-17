# Security policy

Use the latest reviewed plugin build. Install it only on a Mattermost server you
administer, and verify its source and build result. A build passing automated
checks is not an independent penetration test or live deployment acceptance.

## Report a vulnerability

Use [GitHub private vulnerability reporting](https://github.com/vstorm-co/agenticos-mattermost/security/advisories/new).
If that is unavailable, email `dev@vstorm.co`. Include the affected commit/version,
impact and minimal reproduction. Do not include real access tokens, bot tokens,
user content or customer secrets in an issue, email or attachment.

## Credential boundaries

The plugin temporarily uses a short-lived AgenticOS access token only to pair or
remove the configured connection. It sends the Mattermost bot token directly to
the chosen AgenticOS organization's Vault and retains only revocation IDs.
Use valid TLS and keep request-body recording disabled on setup endpoints.

Disabling or uninstalling the plugin does not revoke the bot token. Disconnect
first; in an emergency revoke the bot token in Mattermost and remove its channel
registration in AgenticOS. See README for interrupted-setup recovery.
