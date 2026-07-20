# The stack, explained

What each technology is and where it runs today. No prior familiarity assumed.

## Keycloak

[Keycloak](https://www.keycloak.org/) is an open-source identity provider: one DSA account, one login page, used by apps that need auth (wiki, member app, and others). Apps never see your password — they get signed tokens with claims (who you are, what groups you're in, what roles those groups grant). Hosted on Cloudron today.

Two rules worth internalizing early:

1. Roles attach to **groups**, never directly to individual users.
2. Access changes are group-membership changes, managed through the [Access Management Portal](https://github.com/nycdsa/access-management) — not code deploys, not manual Keycloak clicking.

## Windmill

[Windmill](https://www.windmill.dev/) is a self-hosted platform for running scripts and scheduled workflows (in the same family as n8n or Retool). We use it to sync events from Action Network into our databases and as a small HTTP backend for the member app. If you need a cron job or a data sync, it probably belongs in Windmill.

## Postgres

Our databases run on the K8s cluster. Different apps currently have different databases (calendar events, canvass data, and so on) — historical, not sacred.

## Kubernetes + Pulumi

The "DSA cloud" is a Kubernetes cluster on DigitalOcean, fully described as code with [Pulumi](https://www.pulumi.com/) in the [`infrastructure`](https://github.com/nycdsa/infrastructure) repo. If it runs on our servers, its config should exist in that repo.

## Cloudron

[Cloudron](https://www.cloudron.io/) is a self-hosting app platform (one-click installs of open-source apps). The wiki and Keycloak live there today, outside the Pulumi-managed stack.

## DokuWiki

The wiki engine behind wiki.socialists.nyc. File-based, boring, works. Members-only via its OIDC plugin pointed at Keycloak.

## WordPress / Netlify / React / etc.

Individual apps also use more familiar pieces — WordPress for socialists.nyc, React SPAs and Netlify functions for the calendar and member app, TanStack Start / Bun for canvass. See [`systems.md`](systems.md) for which stack sits where.
