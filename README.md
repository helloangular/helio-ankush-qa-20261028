# Isolated Helio QA lane for Ankush

Owner: helloangular. Tester: AnkushVishwakarma01. Synthetic workloads only.

Two dispatch-only workflows are copied from qualified QA contracts, changing only
application/environment names and runner routing to GitHub-hosted ubuntu-24.04:

- qa-ankush-provider: one provider-managed run, test then production.
- qa-ankush-managed: Helio segment guards via helio_stage_id.

These workflows never deploy a client application. Their evidence describes a
synthetic file copy/digest check; it is not an F31 catalog artifact qualification.
They do not run on push and use no customer credentials or external deployment targets.

Do not dispatch before the dedicated App, Helio connection, environment protection
and technical reviewer are configured and qualified. Use the Helio UI for normal
Create/Start/gate tests. GitHub-side cancellation/rerun tests use their own fresh run.

Every commit must have helio/workflow/<full commit SHA>, pushed with the commit.
QA's App selects this repository only. Webhook points to a sink; Helio observes by polling.

The tester's reviewer credential must belong to AnkushVishwakarma01 and be entered
through a Helio secret reference. Never use the owner's or a shared lead reviewer token.

Teardown: cancel only owned synthetic runs, close their releases through Helio,
then remove dedicated environments, connection/App and collaborator access only at
the owner's direction. Preserve receipts and original verdicts.
