# NYC-DSA Tech & Tools Handbook

Welcome. This repo is the starting point for new Tech & Tools (T&T) members. It explains what we run, why the stack looks the way it does, and how to start contributing — assuming zero prior context about NYC-DSA's tech.

## Reading order

1. [`systems.md`](systems.md) — every live surface we run, what it does, where its code lives
2. [`stack.md`](stack.md) — the technologies we use and why (what even is Astro / Payload / Keycloak / Windmill?)
3. [`principles.md`](principles.md) — the mental models behind our decisions
4. [`how-we-work.md`](how-we-work.md) — how to actually contribute

## The short version

NYC-DSA's member-facing tech grew up as independent apps: a calendar here, an onboarding app there, a canvassing map somewhere else — each built quickly to meet a real need. That served us well, but the sprawl now works against us: weak cross-site navigation, no shared identity, and every new campaign page means new DNS and a new deploy.

The big current project is consolidating the member-facing surfaces into **one website** at [socialists.nyc](https://socialists.nyc) — Astro on Cloudflare, content from Payload CMS, login via Keycloak. That work lives in [`nycdsa/website`](https://github.com/nycdsa/website), and its [`product_spec.md`](https://github.com/nycdsa/website/blob/main/product_spec.md) is the product system of record.

This handbook points at the systems of record; it does not duplicate them. If something here contradicts a repo's own docs, the repo is right — and please fix the handbook.

## Credits

Much of this material started as Paul's `members-app.md` writeup in [`nycdsa/socialists-web`](https://github.com/nycdsa/socialists-web), which did the original archaeology of how our systems fit together.
