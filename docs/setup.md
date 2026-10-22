# Run your own open-source system instead of renting a hosted worker

Kortix is the open-source AI Operating System, and the `kortix self-host` command family installs and runs the full stack on infrastructure you control. Lindy is a hosted service with no self-hosting option on its own pages, so its work runs in Lindy's cloud on a credit plan. For a team that has to run the agent layer itself, the path from an empty server to a working instance follows the Kortix self-hosting docs.

## What runs where

A self-hosted instance is the full Kortix platform on a server you control: one Docker Compose stack that the `kortix self-host` commands install, configure, and update. The server runs the platform. Sessions run on a cloud sandbox provider, not on the server, and the instance has to be reachable from the internet so those sandboxes can call back to it. That reachability is a requirement of the design, so plan for a public address rather than a box behind a closed network.

## Before you start

- **A Linux server with a public IP.** The setup installs Docker Engine and the Compose plugin when they are missing. If the server already has them, you only need the Kortix CLI, which runs on Linux and macOS, on x86_64 and arm64.
- **DNS records.** An A or AAAA record for your instance domain and one for its `api.` subdomain, both pointed at the server before the first start, plus a wildcard record such as `*.p.your-domain` for sandbox browser previews.
- **Ports 80 and 443 open inbound,** so the instance can terminate TLS with a certificate.
- **A sandbox provider key.** Kortix self-host starts with Platinum, and keeps Daytona as a legacy fallback. Without a provider key, sessions do not start.
- **A model provider key.** Self-hosted Kortix ships no managed models; you add a model key in the app after the first sign-in.

## The path from a bare server to a running instance

The command family is `kortix self-host`. A first run in a terminal:

```sh
kortix self-host init
kortix self-host start
kortix self-host doctor
```

- `kortix self-host init` writes the Compose file and the `.env` file into the instance directory. On a first run it asks the setup questions: where the instance is reachable (a domain for TLS, or a Cloudflare tunnel for a quick trial), the admin email, the sandbox provider and its key, the preview domain, and the update policy.
- `kortix self-host start` pulls the images and starts the stack.
- `kortix self-host doctor` runs a fixed set of checks and exits non-zero when one fails. Fix every failing check before you hand the instance to a team.

To change an answer later, run `kortix self-host configure` and then `kortix self-host start`, which applies the answers to the running services.

## First sign-in and setup

1. **Sign up as the admin** at your instance address, with an address you listed as an admin.
2. **Connect managed git.** Open the admin git page and connect a GitHub identity. Until it is set, Kortix cannot create project repositories, though you can still connect an existing one.
3. **Create the team account and a project.** The sign-up account is personal; the team account is the one that holds the team's projects and SSO.
4. **Add a model key** in the project. Each project needs its own key, because a self-hosted instance has no Kortix-managed models. Any model provider is available through your own keys.
5. **Turn on email or close public sign-up.** A new instance confirms sign-ups without an email. Set an email connection string so sign-in and invitation mail goes out, or disable public sign-up once your team is in. The `doctor` command flags this as the `open-sign-up` check.

## What you own after the install

- **The system.** Agents, skills, company memory, and connector configuration live as files in one git repo you own, with `kortix.yaml` at its root.
- **The platform.** The instance directory holds the Compose file, the environment file, the database volumes, and the stored files. Back up that directory to back up the instance.
- **The model path.** Any model provider with your own keys. A self-hosted instance ships no managed models.
- **The landing rule.** Session work reaches `main` through a change request, and merge is default-deny for agents.

## What self-hosting does not change

Two product behaviors hold on your own infrastructure as they do on the managed cloud. Connector credentials are brokered server-side and never enter the machine, so the sandbox does not hold them. Model choice stays yours through your own keys, whether the instance runs on your VPC or on-prem.

## Keep it running

- `kortix self-host status` reports container state, the last update, and configuration drift.
- `kortix self-host update` applies the tracked release channel on demand; auto-update is on by default and runs on a daily schedule.
- `kortix self-host logs` follows the service logs when something needs a closer look.
- Roll back to a previous release if an update misbehaves, and keep the instance directory backed up so a recovery is a directory restore.

The canonical walkthrough, including the reachability modes and the full command list, is in the [Kortix self-hosting docs](https://kortix.com/docs/host). For the feature view of Kortix against Lindy, see [Kortix vs Lindy](kortix-vs-lindy.md); for the cost question, see [Lindy credits vs owning the system](lindy-credits-vs-owning.md). The [README](../README.md) indexes the rest.
