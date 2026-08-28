# SDKs

AuthNest ships two official SDKs to make integration fast. These are
maintained, versioned, and distributed **separately** from this
repository and from the core platform's private source code — nothing
below is source code, just a description of what each SDK does.

## AuthNest React SDK

A React client library for apps built with React. It provides:

- A hook-based API for authentication state (loading, authenticated,
  current user) without manually wiring up API calls
- Login/logout handlers, including support for a "fresh login" flow and
  automatic auth-state retry
- Pre-built, drop-in authentication modals for common flows (login,
  signup, verification) so a Client app can ship an auth UI without
  designing one from scratch
- Navigation helpers for linking into AuthNest-hosted account pages

Typical integration is a handful of lines: install the package, wrap the
app in a provider, and use the auth hook wherever login state is needed.

## AuthNest Server SDK

A Node.js/Express server library for backend integration. It provides:

- A client class initialized with a Client's API key/secret pair and the
  relevant service URLs
- Pre-configured route handlers covering registration, login, user-data
  retrieval, email verification, and related endpoints — so a Client's
  backend doesn't need to hand-build these routes
- Ready-to-use security middleware for protecting those routes

Typical integration is: install the package, initialize the client with
your credentials, and mount the provided route handlers into an existing
Express app.

## Where to get them

Both SDKs are published as independent npm packages, maintained and
versioned on their own release cadence. _[Add package names/links here
once you're ready to share them publicly — they are intentionally not
included in this documentation repository.]_
