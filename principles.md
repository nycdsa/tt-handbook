# Principles and mental models

The reasoning behind recurring decisions. Product-level tenets live in the [website product spec](https://github.com/nycdsa/website/blob/main/product_spec.md); these are the T&T-wide ones.

## A great developer experience

It should be *really really* easy to contribute. Clone, `just install`, `just dev` — no API keys, no secrets, no "ask someone for the .env". Local development runs against local services and seeded test data. If setup requires tribal knowledge, that's a bug.

## We never develop against prod data

Local environments use seeded fake users and fake content. Real member data never leaves production systems.

## Mobile-first

Most people hit our sites from a phone, often from a link someone texted them. Decreasing friction on mobile matters more than desktop polish.

## Non-privileged data on the member surface

Anyone can become a DSA member for about $15, so "members-only" is a *very* soft boundary. The mental model: anything on the member-facing surface is effectively public. Genuinely sensitive data (home addresses, phone numbers, PII) belongs in organizer tools with real access control — not on the website, the wiki, or the CMS.

Corollary: restricting content behind further member-only tiers deserves scrutiny, because the tier barely restricts anyone.

## Public to read, log in to act

Like Hacker News: the site is readable by anyone; authentication exists to *do* things (track your onboarding checklist, see your dashboard, edit CMS content). Auth is not primarily a secrecy mechanism here.

## Identity through groups, not individuals

App roles attach to Keycloak groups; people get roles by being in groups; group membership is governed through the [Access Management Portal](https://github.com/nycdsa/access-management). "Give Maria edit access to the healthcare WG page" is a group-membership change, not a code deploy and not a hand-edit in an admin panel.

## Reliability split

The public website runs on Cloudflare's edge and must survive our self-hosted infrastructure having problems. The CMS runs on our K8s cluster; the site caches CMS content (stale-while-revalidate) so a CMS outage degrades freshness, not availability.

## Fight sprawl with consolidation, not rules

The historical pattern — every need becomes a new subdomain with its own stack — is what we're unwinding. Before building a new standalone app, ask whether it's a route on socialists.nyc.

## Markdown is the system of record

Decisions live in version-controlled markdown in the relevant repo (product spec, state-of-world, per-app AGENTS/README files), not in Slack threads or Google Docs. If you change how systems fit together, update the docs in the same PR.

## Threat model, briefly

The attack vectors we think about: a member account gets compromised (low value if the surface holds no privileged data), a database gets compromised (why PII stays off this stack), an admin account gets compromised, or someone edits malicious content into the CMS. Design so the blast radius of each stays small.
