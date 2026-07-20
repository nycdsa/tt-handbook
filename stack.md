# The stack, explained

What each technology is and where it runs today. No prior familiarity assumed.

## Astro

[Astro](https://astro.build/) is a web framework focused on content-heavy sites. It renders pages to plain HTML on the server (fast, great SEO) and only ships JavaScript for the interactive "islands" that need it. Used in the website monorepo (`nycdsa/website`) for the rebuild of socialists.nyc.

## Cloudflare (Workers / Pages)

[Cloudflare](https://www.cloudflare.com/) hosts the Astro public site at the edge. The live socialists.nyc front door today is still WordPress; Cloudflare is part of the website project's current stack.

## Payload CMS

[Payload](https://payloadcms.com/) is a headless CMS — a content database with an admin UI, but no opinions about how the site looks. Schema is defined in code (TypeScript). Lives in `apps/cms` in the website monorepo.

## Keycloak

[Keycloak](https://www.keycloak.org/) is an open-source identity provider: one DSA account, one login page, used by apps that need auth (wiki, member app, CMS admin, and others as they wire it up). Apps never see your password — they get signed tokens with claims (who you are, what groups you're in, what roles those groups grant).

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

## The dev toolchain

The website monorepo uses [pnpm](https://pnpm.io/) workspaces and [`just`](https://github.com/casey/just) as a command runner. The contract there: `git clone`, `just install`, `just dev` — local Keycloak, local Postgres, seeded test data, no secrets or external accounts required. Other repos vary; improving toward that bar is welcome.
