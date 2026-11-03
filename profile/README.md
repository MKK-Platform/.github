<div align="center">

<img src="../banner.svg" alt="RoomScope — Real-time intelligence for TikTok LIVE" width="100%"/>

<br/>

[![Website](https://img.shields.io/badge/roomscope.io-18181b?style=for-the-badge&logo=googlechrome&logoColor=white)](https://roomscope.io)
[![Status](https://img.shields.io/badge/status-rebuilding-ef4444?style=for-the-badge)](#-roadmap)
[![Stack](https://img.shields.io/badge/Django%20%C2%B7%20Next.js%20%C2%B7%20Postgres-27272a?style=for-the-badge)](#-tech-stack)

**We watch thousands of TikTok LIVE rooms at once, so creators, agencies and brands don't have to.**

</div>

---

## 🔴 What is RoomScope?

RoomScope is a SaaS platform that turns TikTok LIVE into data you can act on. It tracks who is live, listens to each room in real time, and turns gifts, chat and viewer counts into alerts, rankings and reports.

<table>
<tr>
<td width="50%" valign="top">

### 📡 Live tracking
Knows which creators are live right now and connects to their rooms to capture every gift, comment and viewer change as it happens.

</td>
<td width="50%" valign="top">

### 🔔 Instant alerts
Rule-based notifications on Telegram the moment a creator goes live, a big gift lands or a watched gifter shows up.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🏆 Rankings & leaderboards
Official boards by region, ranking history, and leaderboards for creators and top gifters.

</td>
<td width="50%" valign="top">

### 🧑‍🤝‍🧑 Agency tools
Host rosters, watchlists, live history and performance per creator, so agencies can manage and grow their talent.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 📊 Analytics & exports
Session history, gift and gifter rollups, best time to go live, CSV exports and outbound webhooks.

</td>
<td width="50%" valign="top">

### 🔑 Built for teams
Workspaces, member invites, API keys, usage-based credits and self-serve billing.

</td>
</tr>
</table>

## 🧭 How it works

```mermaid
flowchart LR
    TT(("TikTok LIVE")) -->|websocket events| ING["Ingestion workers"]
    ING -->|stream| BUS[("Redis Streams")]
    BUS --> HIST["History & rollups"]
    BUS --> RANK["Rankings"]
    BUS --> NOTI["Alerts"]
    HIST --> DB[("PostgreSQL")]
    RANK --> DB
    NOTI -->|Telegram| USER(("Customers"))
    DB --> API["REST API"]
    API --> APP["Dashboard<br/>app.roomscope.io"]
    API --> WEB["Website<br/>roomscope.io"]
```

## 📦 Repositories

| Repository | Role | Stack |
|---|---|---|
| 🧩 **[mkplatform](https://github.com/MKK-Platform/mkplatform)** | Parent repo: docs, roadmap, decisions, submodules | Git submodules |
| ⚙️ **[mkbackend](https://github.com/MKK-Platform/mkbackend)** | REST API and every background worker | Django · DRF · Celery · Redis · Postgres |
| 🖥️ **[mkdashboard](https://github.com/MKK-Platform/mkdashboard)** | Customer app and ops admin | Next.js 16 · React 19 · Tailwind 4 |
| 🌐 **[mkwebsite](https://github.com/MKK-Platform/mkwebsite)** | Marketing site, public showroom, CMS | Payload CMS 3 · Next.js 16 · shadcn/ui |
| 🚢 **[mkdevops](https://github.com/MKK-Platform/mkdevops)** | Compose stacks, proxy, deploy scripts, monitoring | Docker Compose · Traefik · just |

> [!NOTE]
> Most repositories are private. Ask an owner for access if you are joining the team.

## 🛠 Tech stack

<p>
  <img src="https://img.shields.io/badge/Python-3.14-3776AB?style=flat-square&logo=python&logoColor=white" alt="Python"/>
  <img src="https://img.shields.io/badge/Django-092E20?style=flat-square&logo=django&logoColor=white" alt="Django"/>
  <img src="https://img.shields.io/badge/Celery-37814A?style=flat-square&logo=celery&logoColor=white" alt="Celery"/>
  <img src="https://img.shields.io/badge/PostgreSQL-4169E1?style=flat-square&logo=postgresql&logoColor=white" alt="PostgreSQL"/>
  <img src="https://img.shields.io/badge/Redis-FF4438?style=flat-square&logo=redis&logoColor=white" alt="Redis"/>
  <img src="https://img.shields.io/badge/TypeScript-3178C6?style=flat-square&logo=typescript&logoColor=white" alt="TypeScript"/>
  <img src="https://img.shields.io/badge/Next.js-000000?style=flat-square&logo=nextdotjs&logoColor=white" alt="Next.js"/>
  <img src="https://img.shields.io/badge/React-61DAFB?style=flat-square&logo=react&logoColor=black" alt="React"/>
  <img src="https://img.shields.io/badge/Tailwind_CSS-06B6D4?style=flat-square&logo=tailwindcss&logoColor=white" alt="Tailwind CSS"/>
  <img src="https://img.shields.io/badge/Payload_CMS-000000?style=flat-square&logo=payloadcms&logoColor=white" alt="Payload CMS"/>
  <img src="https://img.shields.io/badge/Docker-2496ED?style=flat-square&logo=docker&logoColor=white" alt="Docker"/>
  <img src="https://img.shields.io/badge/Traefik-24A1C1?style=flat-square&logo=traefikproxy&logoColor=white" alt="Traefik"/>
  <img src="https://img.shields.io/badge/Grafana-F46800?style=flat-square&logo=grafana&logoColor=white" alt="Grafana"/>
  <img src="https://img.shields.io/badge/Telegram-26A5E4?style=flat-square&logo=telegram&logoColor=white" alt="Telegram"/>
</p>

## 🗺 Roadmap

| | Phase | Scope | Status |
|:-:|---|---|:-:|
| 🧱 | **Foundations** | Local stack, CI, app skeletons, branding | ✅ Done |
| 🔁 | **Phase A** | Rebuild the core product: accounts, workspaces, billing, ingestion, alerts, rankings, history, dashboard, website, ops admin | 🟢 Nearly done |
| 🚀 | **Phase B** | Gifter intelligence, extended alerts and rankings, creator analytics, host CRM, agency directory | 🟡 In progress |
| 🎉 | **Launch** | Production release as RoomScope | ⏳ Next |

## 🤝 How we work

```text
feature branch  ──PR──▶  develop  ──auto release──▶  main  ──▶  production
```

- One issue, one branch (`<type>/<N>-<slug>`), one squash-merged PR into `develop`.
- `main` is production and only moves through the release workflow.
- Port behaviour, not code: every rule from the old system ships with its tests.

## 📩 Contact:

- Email: `tuantq.itwork@gmail.com`
- Telegram: `@twain_tran`

---

<div align="center">

<sub>Made with ❤️ by the MKK Platform team · RoomScope is not affiliated with TikTok or ByteDance.</sub>

</div>
