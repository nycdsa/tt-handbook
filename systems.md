# Systems map

Every live surface T&T runs.

![Current systems](state-of-world.png)

Diagram may be incomplete (pieced together from code + infra) — PRs welcome.

## Member-facing

### Public website — [socialists.nyc](https://socialists.nyc)

WordPress. The chapter's front door and our most important SEO asset (first Google result for "nyc dsa").

### Calendar — [calendar.socialists.nyc](https://calendar.socialists.nyc)

React SPA (MUI) on Netlify; Netlify functions talk to a Postgres database via Prisma. Public, no login. (The repo has self-host paths too; Netlify is what's live.) Repo: [`nyc-dsa-calendar`](https://github.com/nycdsa/nyc-dsa-calendar).

### Canvass map — [canvass.socialists.nyc](https://canvass.socialists.nyc)

TanStack Start + Tailwind/shadcn, Bun runtime, Prisma against its own Postgres on our Kubernetes cluster. Windmill syncs canvassing events from Action Network into its database. Public. Repo: [`canvass-map`](https://github.com/nycdsa/canvass-map).

### New member app — [member.socialists.nyc](https://member.socialists.nyc)

React/Vite SPA on Netlify with an onboarding checklist and event suggestions; Netlify functions call Windmill as the backend; Keycloak for login. Repo: [`new-member-app`](https://github.com/nycdsa/new-member-app).

### Wiki — [wiki.socialists.nyc](https://wiki.socialists.nyc)

DokuWiki, hosted via Cloudron (not the main K8s stack). Members-only; DSA login works via a DokuWiki OIDC plugin pointed at Keycloak. Repos: [`wiki-conf`](https://github.com/nycdsa/wiki-conf), [`wiki-data`](https://github.com/nycdsa/wiki-data), [`mikio-dokuwiki-template`](https://github.com/nycdsa/mikio-dokuwiki-template).

## Organizer-facing

Leadership/organizer-only tooling. Unlike the member-facing surfaces, these handle PII (names, phone numbers, assignments), so access is genuinely restricted.

### Onboarder — [onboarder.socialists.nyc](https://onboarder.socialists.nyc)

React/TypeScript app for managing new-member onboarding: coordinators assign new members to onboarders and track progress through the workflow. Repo: [`onboarder-app`](https://github.com/nycdsa/onboarder-app).

### Phone tree

Mobile-first phone relay tool for organized call campaigns (TypeScript, Bun). Repo: [`phone-tree`](https://github.com/nycdsa/phone-tree).

### Canvass with me

TanStack Start + Bun app for coordinated canvassing, early in development. Repo: [`canvass-with-me`](https://github.com/nycdsa/canvass-with-me).

### Access Management Portal (AMP)

Next.js app governing membership in requestable Keycloak groups: requests, approvals, direct grants, and reconciliation against Keycloak. The repo also holds the human-maintained Keycloak access inventory and a local Keycloak + Postgres dev stack. Repo: [`access-management`](https://github.com/nycdsa/access-management).

### Office booking

Booking app for the chapter office in Brooklyn: members request access, captains approve, approved members reserve the office for co-working and meetings. Next.js + Neon Postgres/Prisma, magic-link email auth, deployed on Vercel. Repo: [`dsa-office-booking`](https://github.com/nycdsa/dsa-office-booking).

## Working group & other sites

### WG microsites

Standalone working-group sites, each with its own stack:

- Healthcare WG — Pelican static site on GitHub Pages. Repo: [`nyc-dsa-healthcare.github.io`](https://github.com/nycdsa/nyc-dsa-healthcare.github.io)
- Tech Action — [techaction.nyc](https://www.techaction.nyc/), Jekyll static site. Repo: [`tech-action-working-group`](https://github.com/nycdsa/tech-action-working-group)
- powerup.nyc — no repo in the org that we know of

### The Thorn — [thethorn.nyc](https://thethorn.nyc)

Electoral working group newsletter. Jekyll static site. Repo: [`the-thorn`](https://github.com/nycdsa/the-thorn).

### Ballot lookup — ballot.socialists.nyc

Enter an NYC address, see NYC-DSA endorsed candidates on your primary ballot. Static Astro site; the lookup runs entirely in the browser. Election-cycle tool. Repo: [`vote-dsa-down-the-ballot`](https://github.com/nycdsa/vote-dsa-down-the-ballot).

### Results — results.socialists.nyc

Election-night results one-off.

### Shopify store — shop.socialists.nyc

Hosted Shopify storefront.

## Shared infrastructure

### Kubernetes cluster ("the DSA cloud")

Self-managed K8s on DigitalOcean, defined with Pulumi in [`infrastructure`](https://github.com/nycdsa/infrastructure). Runs the canvass app, Postgres databases, Windmill, and related services.

### Keycloak

Our identity provider (IdP) — one DSA login across apps. Lives in the `nycdsa` realm, currently hosted on Cloudron. Access governance (who is in which groups, which groups grant which app roles) is handled by the [`access-management`](https://github.com/nycdsa/access-management) portal, not by hand-assigning roles to users.

### Windmill

Self-hosted workflow/automation platform (think open-source Zapier/retool for scripts). Syncs data from Action Network and SolidarityTech into our Postgres databases and serves as a lightweight backend for the member app. Repo: [`member-app-windmill`](https://github.com/nycdsa/member-app-windmill).
