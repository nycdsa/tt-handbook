# Principles and mental models

Operating norms for Tech & Tools. Product-level decisions for the website live in the [website product spec](https://github.com/nycdsa/website/blob/main/product_spec.md) — not here.

## Code of conduct & AI policy

We follow:

- [DSA Code of Conduct](https://socialists.nyc/code-of-conduct)
- [Progressive Hack Night Code of Conduct](https://www.progressivehacknight.org/code-of-conduct.html)

In practice that means:

- Step up, step back
- No feigning surprise
- No well-actually's
- No back-seat driving

### Community & Slack

- Use your real name
- Put your GitHub handle in your Slack profile
- Have some sort of picture — ideally one that matches GitHub

### AI policy

[Simon Willison](https://simonwillison.net/2025/Dec/18/code-proven-to-work/): *"Your job is to deliver code you have proven to work."*

That applies whether you wrote it by hand or with an LLM:

- You own proving the change works before you ask someone else to look at it
- Don't ship unverified AI output — dumping a giant untested PR on reviewers is rude
- Prove it however fits: run it yourself, add tests, paste commands/output or a short screen capture in the PR
- A computer can't be held accountable; the human who opened the PR can

## A great developer experience

It should be *really really* easy to contribute. Clone, `just install`, `just dev` — no API keys, no secrets, no "ask someone for the .env". Local development runs against local services and seeded test data. If setup requires tribal knowledge, that's a bug.

## We never develop against prod data

Local environments use seeded fake users and fake content. Real member data never leaves production systems.

## Non-privileged data on the member surface

Anyone can become a DSA member for about $15, so "members-only" is a *very* soft boundary. The mental model: anything on the member-facing surface is effectively public. Genuinely sensitive data (home addresses, phone numbers, PII) belongs in organizer tools with real access control — not on the website, the wiki, or the CMS.

Corollary: restricting content behind further member-only tiers deserves scrutiny, because the tier barely restricts anyone.

## Identity through groups, not individuals

App roles attach to Keycloak groups; people get roles by being in groups; group membership is governed through the [Access Management Portal](https://github.com/nycdsa/access-management). "Give Maria edit access to the healthcare WG page" is a group-membership change, not a code deploy and not a hand-edit in an admin panel.

## Markdown is the system of record

Decisions live in version-controlled markdown in the relevant repo (product spec, state-of-world, per-app AGENTS/README files), not in Slack threads or Google Docs. If you change how systems fit together, update the docs in the same PR.

## Threat model, briefly

The attack vectors we think about: a member account gets compromised (low value if the surface holds no privileged data), a database gets compromised (why PII stays off this stack), an admin account gets compromised, or someone edits malicious content into the CMS. Design so the blast radius of each stays small.
