# Systems map

Every live surface T&T runs or cares about, one paragraph each. As-is details and diagrams: [`state-of-world.md` in the website repo](https://github.com/nycdsa/website/blob/main/docs/state-of-world.md).

## Member-facing (consolidating into socialists.nyc)

### Public website — [socialists.nyc](https://socialists.nyc)

WordPress today. The chapter's front door and our most important SEO asset (first Google result for "nyc dsa"). Being replaced by an Astro site on Cloudflare fed by Payload CMS — the main active project, in [`nycdsa/website`](https://github.com/nycdsa/website).

### Calendar — [calendar.socialists.nyc](https://calendar.socialists.nyc)

React SPA (MUI) on Netlify; Netlify functions talk to a Postgres database via Prisma. Public, no login. Repo: [`nyc-dsa-calendar`](https://github.com/nycdsa/nyc-dsa-calendar). Destination: an Events surface on the main site, merged with the canvass map.

### Canvass map — [canvass.socialists.nyc](https://canvass.socialists.nyc)

TanStack Start + Tailwind/shadcn, Bun runtime, own Postgres on our Kubernetes cluster. Windmill syncs canvassing events from Action Network into its database. Public. Repo: [`canvass-map`](https://github.com/nycdsa/canvass-map). Destination: same Events surface as the calendar (list/map toggle).

### New member app — [member.socialists.nyc](https://member.socialists.nyc)

React/Vite SPA on Netlify with an onboarding checklist and event suggestions; Netlify functions call Windmill as the backend; Keycloak for login. Repo: [`new-member-app`](https://github.com/nycdsa/new-member-app). Conceptually the closest thing to the target experience — its nav, tap-in dashboard, and mobile-first design carry into the main site.

### Wiki — [wiki.socialists.nyc](https://wiki.socialists.nyc)

DokuWiki, hosted via Cloudron (not the main K8s stack). Members-only; DSA login works via a DokuWiki OIDC plugin pointed at Keycloak. Repos: [`wiki-conf`](https://github.com/nycdsa/wiki-conf), [`wiki-data`](https://github.com/nycdsa/wiki-data), [`mikio-dokuwiki-template`](https://github.com/nycdsa/mikio-dokuwiki-template). Staying a wiki — not being rewritten into the CMS.

## Shared infrastructure

### Kubernetes cluster ("the DSA cloud")

Self-managed K8s on DigitalOcean, defined with Pulumi in [`infrastructure`](https://github.com/nycdsa/infrastructure). Runs the canvass app, Postgres databases, Windmill, and (target state) Payload CMS.

### Keycloak

Our identity provider (IdP) — one DSA login across apps. Lives in the `nycdsa` realm, currently hosted on Cloudron (moving off is a goal). Access governance (who is in which groups, which groups grant which app roles) is handled by the [Access Management Portal](https://github.com/nycdsa/access-management), not by hand-assigning roles to users.

### Windmill

Self-hosted workflow/automation platform (think open-source Zapier/retool for scripts). Syncs data from Action Network and SolidarityTech into our Postgres databases and serves as a lightweight backend for the member app. Stays outside the website monorepo. Repo: [`member-app-windmill`](https://github.com/nycdsa/member-app-windmill).

## Out of scope for the website project (but T&T territory)

| Thing | What it is |
|-------|------------|
| Organizer tools | Onboarder, phone tree, canvass-with-me — leadership/organizer-only tooling with access to PII |
| Shopify store | shop.socialists.nyc |
| WG microsites | e.g. healthcare, powerup.nyc, techaction.nyc — being folded into `/wg/:slug` pages on the main site over time |
| The Thorn | Chapter-adjacent news site (thethorn.nyc, Jekyll) — relationship to the main site TBD |
| results / ballot sites | Election-cycle one-offs (results.socialists.nyc, ballot.socialists.nyc) |
