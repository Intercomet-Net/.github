<div align="center">

# ☄️ Intercomet

**A connected Minecraft network. One identity. Many experiences.**

[![Discord](https://img.shields.io/badge/Discord-Join%20the%20community-8B5CF6?style=for-the-badge&logo=discord&logoColor=white)](https://discord.gg/bw2dB8Vdt4)
[![Java](https://img.shields.io/badge/Java-21-3B82F6?style=for-the-badge&logo=openjdk&logoColor=white)](https://github.com/Intercomet-Net/Intercomet)
[![Paper](https://img.shields.io/badge/Paper-1.21.11-22C55E?style=for-the-badge)](https://papermc.io)
[![License](https://img.shields.io/badge/License-MIT-F59E0B?style=for-the-badge)](https://github.com/Intercomet-Net/Intercomet/blob/main/LICENSE)

</div>

---

## 🌌 What is Intercomet?

Intercomet is a Minecraft multiplayer network built around a simple idea: **your enjoyment is our top priority**.

Each game server stays modular and independently deployable. A shared platform layer sits underneath them, providing the things players expect to just work everywhere: identity, ranks, economy, claims, moderation, and more.

> Minecraft is the primary product. Discord, web, payments, and analytics exist to extend it, and never to gate it.

---

## 🧩 The Ecosystem

| Surface | What it does |
| --- | --- |
| 🎮 **Minecraft Network** | Paper-based game servers running the Intercomet plugin, with a Velocity proxy planned in front. |
| 💬 **Discord** | Community hub, punishment and server-log notifications, and (planned) account linking and role sync. |
| ⚙️ **Platform Services** | Shared domain services for identity, economy, claims, moderation, and entitlements. |
| 📡 **Event Backbone** | Versioned events carried over Kafka for audit, analytics, and integrations. |
| 💳 **Monetization** | Stripe support planned, with verified webhooks and idempotent fulfillment. |

---

## 📦 Repositories

| Repository | Description |
| --- | --- |
| [**Intercomet**](https://github.com/Intercomet-Net/Intercomet) | The main multi-module Maven project: the Paper plugin, shared API, services, events, Discord bot, and Kafka integration. |

The main project is split into modules so shared contracts can be reused independently of the plugin:

| Module | Purpose |
| --- | --- |
| `api` | Domain models and repository interfaces. |
| `events` | Transport-agnostic, versioned event definitions and serialization. |
| `services` | Lifecycle services, persistence, and gameplay logic. |
| `core` | Paper plugin entry point, commands, listeners, and GUIs. |
| `discord` | JDA-based Discord bot and Kafka event consumption. |
| `kafka` | Kafka event publishing. |

---

## ✨ Gameplay Systems

Systems currently in the plugin, at varying stages of completion:

- 🛡️ **Land Claims** — claim shovel, role-based permissions (member / trusted / owner), and particle visualization
- 💰 **Economy** — balances, shards, and a ledger-style transaction model
- 🏷️ **Clans** — ownership, membership, levels, and balances
- 🔨 **Auction House** — player-to-player item sales
- 🎯 **Bounties** — player bounties with expiry
- 💼 **Jobs** — job types and XP progression
- 🧳 **Vaults** — persistent, paged per-player storage
- ⚔️ **Combat Tagging** — combat timer and command restrictions
- 🏠 **Homes**, ⏱️ **Playtime**, 📊 **Scoreboards**, 🚨 **Punishments & Reports**

---

## 🏗️ Architecture at a Glance

```
Players → Velocity Proxy → Minecraft Servers (Intercomet plugin)
                                   │
                          Platform services
                                   │
                                 Kafka
                  ┌────────────────┼────────────────┐
                Audit          Analytics        Discord / Web
```

Guiding principles:

- **Domain ownership** — one service owns each domain's authoritative state.
- **Failure isolation** — a Discord, web, or analytics outage never blocks gameplay.
- **Events over coupling** — domains publish versioned events; consumers stay independent.
- **Idempotency everywhere** — retried purchases, transfers, and events produce one effective result.
- **Security by design** — least privilege, verified webhooks, and no secrets in source control.

---

## 🛠️ Tech Stack

| Today | Planned |
| --- | --- |
| Java 21 | Plugin ready jar file |
| Paper 1.21.11 (Brigadier commands) | Velocity proxy |
| Maven multi-module build | PostgreSQL and H2 |
| H2 persistence | Redis caching |
| JDA (Discord) | Stripe & Tebex |
| Kafka + Jackson events | Grafana observability |

---

## 🗺️ Roadmap

- [x] **Foundation** — modular project structure, service registry, persistence layer
- [ ] **Core Gameplay** — economy, claims, moderation, progression, rewards *(in progress)*
- [ ] **Ecosystem** — Discord linking and role sync, web platform, payments, analytics
- [ ] **Expansion** — additional game modes, cosmetics, events, seasonal systems
- [ ] **Platform** — admin dashboard, public APIs, advanced analytics

---

## 🤝 Get Involved

1. Read the [Contributing Guide](https://github.com/Intercomet-Net/Intercomet/blob/main/CONTRIBUTING.md) and [Code of Conduct](https://github.com/Intercomet-Net/Intercomet/blob/main/CODE_OF_CONDUCT.md).
2. Browse open issues or propose an idea before starting something large.
3. Fork, branch, build with `mvn clean verify`, and open a pull request.
4. Come say hi in our [Discord](https://discord.gg/bw2dB8Vdt4).

### 🔒 Security

Please **do not** report vulnerabilities through public issues. See our [Security Policy](https://github.com/Intercomet-Net/Intercomet/blob/main/SECURITY.md) and open a staff ticket in Discord.

---

<div align="center">

**Intercomet Network** · Built with ☕ and a lot of Minecraft

[Discord](https://discord.gg/bw2dB8Vdt4) · [Main Repository](https://github.com/Intercomet-Net/Intercomet) · [Contributing](https://github.com/Intercomet-Net/Intercomet/blob/main/CONTRIBUTING.md)

</div>
