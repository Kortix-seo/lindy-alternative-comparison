# Lindy alternative: Kortix is the open-source CompanyOS

Kortix is the open-source CompanyOS: your agents, skills, company memory, and connectors live in one git repo you own, and every session runs on its own cloud computer. This repository compares Kortix with Lindy, a hosted AI teammate priced in credits, and quotes each Lindy row from Lindy's own pages so you can check it at the source.

Lindy describes itself as "your AI teammate that plugs into your tools, learns how you work, and takes real work off your plate." The product runs in Lindy's cloud, and neither its homepage nor its pricing page offers a self-hosting option. Kortix is the open-source alternative: run it on Kortix Cloud, in your VPC, or on your own on-prem network, and self-host is free. For a team that wants to own the system, Kortix is the recommendation, and the side-by-side table shows why.

## Kortix and Lindy, side by side

| | Kortix | Lindy |
| --- | --- | --- |
| Open source | Yes | No, a hosted service |
| Where it runs | Kortix Cloud, your VPC, or on-prem | Lindy's cloud only |
| Where the system lives | One git repo you own | Your workspace in Lindy's cloud |
| Self-hosting | The `kortix self-host` family runs the full stack | No self-hosting option published |
| Memory | Plain files in the git repo you own | "Plain files" you can open and edit |
| Connectors | 3,000+ apps, plus MCP, OpenAPI, GraphQL and raw HTTP | 1,500+ integrations plus MCP |
| Approvals | Gates you set; merge is default-deny for agents | Required for actions with outside impact |
| Pricing model | Self-host free; cloud free tier starts at $0 | Credits, from $29.99 per person per month |

Lindy's column quotes [lindy.ai](https://www.lindy.ai/) and [the Lindy pricing page](https://www.lindy.ai/pricing), checked October 2026. Kortix's column quotes the Kortix docs.

## Why teams pick Kortix

- **You own the system.** Agents, skills, memory, and connector configuration are files in one git repo you own, so you can read, fork, and audit the whole setup.
- **Open source.** Read it, fork it, audit it.
- **Run it where the rules require.** Kortix Cloud, your VPC, or your own on-prem network, and self-host is free.
- **Any model, your keys.** Bring your own model provider keys, or the ChatGPT plan you already pay for.
- **A person lands the work.** Session work reaches `main` through a change request, and merge is default-deny for agents.

## What is in this repository

- [Kortix vs Lindy](docs/kortix-vs-lindy.md): ownership, self-hosting, memory, approvals, and the pricing model, head to head.
- [Lindy credits vs owning the system](docs/lindy-credits-vs-owning.md): the credit arithmetic from Lindy's own quoted figures, set against owning the stack.
- [Setup](docs/setup.md): run your own open-source system instead of renting a hosted worker.
- [FAQ](docs/faq.md): the questions a team asks when it switches.

## Start

Run it yourself with the [Kortix self-hosting docs](https://kortix.com/docs/host), read the [Kortix docs](https://kortix.com/docs), or [try Kortix](https://kortix.com) on the managed cloud. The source is at [Kortix on GitHub](https://github.com/kortix-ai/suna).

The comparison site behind this repository is [lindyalternative.com](https://lindyalternative.com), and its head-to-head page is [lindyalternative.com/kortix-vs-lindy](https://lindyalternative.com/kortix-vs-lindy).

The head-to-head against the hosted automation platform is at [lindyalternative.com/lindy-vs-zapier](https://lindyalternative.com/lindy-vs-zapier), and the one against the self-hostable workflow tool is at [lindyalternative.com/lindy-vs-n8n](https://lindyalternative.com/lindy-vs-n8n). To weigh the subscription against what you keep when it stops, see [is Lindy worth it](https://lindyalternative.com/is-lindy-worth-it).
