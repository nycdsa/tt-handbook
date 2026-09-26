# Principles and mental models

Operating norms for Tech & Tools.

## Code of conduct & AI policy

We follow the [DSA Code of Conduct](https://socialists.nyc/code-of-conduct). We also borrow Progressive Hack Night's social rules:

- Step up, step back
- No feigning surprise
- No well-actually's
- No back-seat driving

### Community & Slack

- Use your real name
- Put your GitHub handle in your Slack profile
- Have some sort of picture — ideally one that matches GitHub

### AI orientation

See [`ai-orientation.md`](ai-orientation.md) for our AI orientation.

## A great developer experience

It should be *really really* easy to contribute. Clone the repo, follow the README, and get a running local environment — no API keys, no secrets, no "ask someone for the .env". Local development runs against local services and seeded test data. If setup requires tribal knowledge, that's a bug.

## Center the users

We solve problems for people, we don't just build tech. At the beginning of a project, interview the people who will use what you’re building to understand their needs. Then, show them your solutions and watch them complete top tasks. Follow a cycle of learn > build > test > repeat. Designers can help with this, but everyone can do it.

Instead of writing a list of requirements that describe features and products, develop a list of user stories. For example: As a [type of person], in order to [accomplish a goal], I need [to do a task]. This will help you better understand and prioritize people’s needs, give you flexibility in how you solve problems, and ultimately build solutions they love.

## We never develop against prod data

Local environments use seeded fake users and fake content. Real member data never leaves production systems.

## Non-privileged data on the member surface

Anyone can become a DSA member for about $15, so "members-only" is a *very* soft boundary. The mental model: anything on the member-facing surface is effectively public. Genuinely sensitive data (home addresses, phone numbers, PII) belongs in organizer tools with real access control — not on the public site, the wiki, or other soft-gated surfaces.

Corollary: restricting content behind further member-only tiers deserves scrutiny, because the tier barely restricts anyone.

## Identity through groups, not individuals

App roles attach to Keycloak groups; people get roles by being in groups; group membership is governed through the [Access Management Portal](https://github.com/nycdsa/access-management). "Give Maria edit access" is a group-membership change, not a code deploy and not a hand-edit in an admin panel.

## Markdown is the system of record

Decisions live in version-controlled markdown in the relevant repo (README, AGENTS.md, and similar), not in Slack threads or Google Docs. If you change how systems fit together, update the docs in the same PR.
