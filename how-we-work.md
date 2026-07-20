# How we work

## Getting plugged in

1. Join the T&T channel on the chapter Slack and say hi — that's where coordination happens.
2. Get added to the [`nycdsa`](https://github.com/nycdsa) GitHub org (ask in the channel).
3. Read this handbook, then the [website product spec](https://github.com/nycdsa/website/blob/main/product_spec.md) if you're joining the website project.

## Contributing code

Work happens through GitHub issues and pull requests, like any open-source project:

1. Pick up an issue (or open one describing what you want to do).
2. Branch, make the change, open a PR.
3. PRs get reviewed and merged; nobody pushes to main on shared repos without review unless it's their own project area.

Each repo's own README / AGENTS.md / CONTRIBUTING.md is authoritative for its conventions. For the website monorepo specifically: [`CONTRIBUTING.md`](https://github.com/nycdsa/website/blob/main/CONTRIBUTING.md).

## Local development

The standard for our repos (fully true of `nycdsa/website`, aspirational elsewhere):

```bash
git clone <repo>
just install   # deps, local services, seeded test data
just dev       # running app
```

No secrets, no external accounts, no prod data. If a repo doesn't work this way yet, improving that is a welcome contribution.

## Where things get decided

| Kind of decision | Where it lives |
|------------------|----------------|
| Website product direction | [`product_spec.md`](https://github.com/nycdsa/website/blob/main/product_spec.md) in `nycdsa/website` |
| What currently exists / as-is infra | [`docs/state-of-world.md`](https://github.com/nycdsa/website/blob/main/docs/state-of-world.md) |
| Who owns what | [`project_owners.md`](https://github.com/nycdsa/website/blob/main/project_owners.md) |
| Infra config | [`infrastructure`](https://github.com/nycdsa/infrastructure) (Pulumi) |
| Access / groups | [Access Management Portal](https://github.com/nycdsa/access-management) |

If a decision changed and the doc didn't, updating the doc is part of the change.

## Asking questions

Ask in Slack, early and often. The systems here were pieced together by volunteers over years — nobody has the whole picture in their head, and "how does X actually work?" questions regularly surface things worth writing down. When you get a good answer, consider PRing it into this handbook.
