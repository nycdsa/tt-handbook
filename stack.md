# The stack, explained

Quick glossary — what each technology is. Which app uses what is in [`systems.md`](systems.md). No prior familiarity assumed.

## Keycloak

[Keycloak](https://www.keycloak.org/) is an open-source identity provider: one DSA account, one login page, shared by apps that need auth. Apps never see your password — they get signed tokens with claims (who you are, what groups you're in, what roles those groups grant). How access is governed is a norm, not a tech detail: see "Identity through groups, not individuals" in [`principles.md`](principles.md).

## Windmill

[Windmill](https://www.windmill.dev/) is a self-hosted platform for running scripts and scheduled workflows (in the same family as n8n or Retool). If you need a cron job or a data sync, it probably belongs in Windmill.

## Postgres

Standard relational database. Each app currently has its own database on the K8s cluster — historical, not sacred.

## Kubernetes + Pulumi

The "DSA cloud" is a Kubernetes cluster on DigitalOcean, fully described as code with [Pulumi](https://www.pulumi.com/) in the [`infrastructure`](https://github.com/nycdsa/infrastructure) repo. If it runs on our servers, its config should exist in that repo.

## Cloudron

[Cloudron](https://www.cloudron.io/) is a self-hosting app platform (one-click installs of open-source apps). We use it for the wiki and Keycloak, outside the Pulumi-managed stack.

## DokuWiki

The wiki engine behind wiki.socialists.nyc. File-based, boring, works.

## WordPress / Netlify / React / etc.

Individual apps also use more familiar pieces — WordPress for socialists.nyc, React SPAs and Netlify functions for the calendar and member app, TanStack Start / Bun for canvass. See [`systems.md`](systems.md) for which stack sits where.
