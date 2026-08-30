# AuthNest — Authentication-as-a-Service Platform

> Drop-in login, signup, OTP, social auth, and MFA for your app — without building an auth system yourself.

**🔗 Live demo:** _[coming soon — add link here]_
**🎥 Demo video:** _[coming soon — add YouTube / Loom link here]_

---

## Overview

AuthNest is a multi-tenant Authentication-as-a-Service platform.
Developers ("Clients") sign up, get an API key/secret pair, and use
AuthNest to add production-grade authentication — login, signup, OTP
verification, social login, password/PIN management, and MFA — to their
own app without building or maintaining that system themselves.

The platform is built around three account types (platform Admins,
integrating Clients, and Clients' end Users), each with their own
dashboard and flow, and ships with SDKs that make integration a matter of
minutes rather than days.

---

## ✨ Key Features

### For integrating developers (Clients)
- API key + secret key pair issued on signup, used to authenticate every
  request
- Email/password authentication plus Google and GitHub social login
- OTP email verification, forgot-password flow, and magic links
- Multi-factor authentication with backup codes, plus security PIN and
  device/session management
- Custom registration form builder — tailor the signup experience per app
- Team invitations for managing an integration collaboratively
- Subscription plan management with usage export (PDF/CSV/JSON)
- Dynamic, per-Client CORS — a new custom domain works immediately, no
  redeploy required
- Real-time updates via WebSockets for account/session events

### For platform admins
- System health monitoring and audit logs
- Database maintenance tooling
- Versioned privacy policy / terms of service with a publish workflow

### Official SDKs
AuthNest ships two official, independently published integration SDKs so
developers rarely need to touch the raw API directly:

- **A React client SDK** — hooks and drop-in components for authentication
  state, login/logout flows, and modal-based auth UI in a React app
- **A Node.js/Express server SDK** — pre-configured route handlers and
  security middleware for wiring AuthNest into an existing backend in a
  few lines of code

Both SDKs are maintained and versioned separately from the core platform.
_[Add links to the SDK packages/docs here once ready to share.]_

### Reliability & scale
- Asynchronous processing (email delivery, audit logging, metrics) is
  decoupled from the request path via a message queue, so a slow email
  provider never blocks a login
- Designed for elastic autoscaling of background workers under load,
  independent of the core API

---

## 🏗️ Architecture (high level)

```
                     ┌──────────────────────────┐
   Browser ────────▶│    Web Dashboard         │
                     │  (Public site, User/     │
                     │   Client/Admin portals)  │
                     └───────────┬──────────────┘
                                 │
                                 ▼
                     ┌──────────────────────────┐
                     │   Authentication API     │
                     │  Signup/login, OTP,      │
                     │  OAuth, MFA, sessions,   │
                     │  per-Client API keys,    │
                     │  realtime updates        │
                     └──────────┬───────────────┘
                                │
                    ┌───────────┴─────────────┐
                    ▼                         ▼
          ┌───────────────────┐     ┌───────────────────────┐
          │      Database     │     │   Async Job Queue     │
          │  (users, Clients, │     │  (email, audit,       │
          │   sessions, keys) │     │   metrics workers)    │
          └───────────────────┘     └───────────────────────┘
```

Integrating apps talk to AuthNest through the API (directly, or via one
of the official SDKs). Background work — email delivery, audit logging,
usage metrics — runs asynchronously off a job queue so it never blocks
the authentication path itself.

*(Full internal architecture, database schema, and API implementation
are kept in the private engineering repository.)*

---

## 🧰 Tech Stack

- **Backend:** Node.js, Express, MongoDB, real-time updates via
  WebSockets, message-queue-based async processing
- **Frontend:** React, Vite
- **Auth:** JWT + session-based authentication, OAuth (Google, GitHub),
  OTP, MFA
- **SDKs:** Official React client SDK and Node.js/Express server SDK,
  published and versioned independently for integrators
- **Infrastructure:** Designed for containerized deployment with
  autoscaling background workers

---

## 📸 Screenshots

_Screenshots coming soon — see [screenshots/README.md](screenshots/README.md) for the exact pages that will be captured here._

<!--
  Once you have images in /screenshots, replace this block with something like:

  ### Client dashboard
  ![Client dashboard](screenshots/client-dashboard.png)

  ### Custom registration form builder
  ![Form builder](screenshots/form-builder.png)
-->

---

## 🎬 Demo Video

_A walkthrough video / GIF demo will be embedded here soon._

<!--
  Once you have a video, embed it like this:

  [![Watch the demo](screenshots/video-thumbnail.png)](https://youtube.com/your-video-link)
-->

---

## 📄 Documentation

- [Product overview & feature notes](docs/FEATURES.md)
- [SDK overview](docs/SDKS.md)
- [Roadmap](docs/ROADMAP.md)

> Note: this repository contains product documentation only. The core
> platform's application source code lives in a private repository and
> is available to qualified partners and investors under NDA. The
> AuthNest React and Server SDKs are maintained and distributed
> separately from this repository.

---

## 📬 Contact

Interested in a demo, partnership, or investment? _[Add your contact email / calendly link / website here]_

---

## License

Proprietary — all rights reserved. This repository and the underlying
AuthNest platform are not open source. (The AuthNest React and Server
SDKs are distributed separately under their own license terms — see
their respective package listings.)
