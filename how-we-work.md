# How we work

## Getting plugged in

1. If you're not already in the Tech & Tools Slack server, [request to join here](https://actionnetwork.org/forms/nyc-dsa-tech-tools-interest-form). Once you're accepted, introduce yourself in `#general-and-welcome`.
2. Get added to the [`nycdsa`](https://github.com/nycdsa) GitHub org (ask in `#general-and-welcome`).
3. Read this handbook. If you're joining the website project, also read its [product spec](https://github.com/nycdsa/website/blob/main/product_spec.md).

## Contributing code

Work happens through GitHub issues and pull requests, like any open-source project:

1. Pick up an issue (or open one describing what you want to do).
2. Branch, make the change, open a PR.
3. PRs get reviewed and merged. Don't push straight to main on shared repos — exception: if you lead a project, you can ship to main in that project's area.

Each repo's own README / AGENTS.md / CONTRIBUTING.md is authoritative for its conventions. For the website monorepo specifically: [`CONTRIBUTING.md`](https://github.com/nycdsa/website/blob/main/CONTRIBUTING.md).

## Local development

Each repo has its own setup — start with that repo's README (or CONTRIBUTING / AGENTS.md). Commands and tooling differ across projects.

What we aim for everywhere we can:

- No prod data in local environments — use seeded/fake data
- No "ask someone for the secrets" gate just to run the app
- Setup that a new contributor can follow from the docs alone

If a repo's setup is painful or undocumented, fixing that is a welcome contribution.

## Asking questions

Ask in Slack, early and often. The systems here were pieced together by volunteers over years — nobody has the whole picture in their head, and "how does X actually work?" questions regularly surface things worth writing down. When you get a good answer, consider PRing it into this handbook.
