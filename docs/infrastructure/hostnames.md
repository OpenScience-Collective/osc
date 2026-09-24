# Hostnames

**Rule: a plane is a subdomain, a project is a path.**

Every public address the Open Science Collective (OSC) serves is `{plane}.osc.earth/{project}/...`.
A *project* is one of the collective's products, such as the Open Science Assistant (OSA) or OSCAR.
A *plane* is a kind of service that several projects share, such as the API or the documentation.
The project's own page lives on the apex, at `osc.earth/{project}`.

| Plane | Serves | Example |
|---|---|---|
| (apex) | each project's home page | `osc.earth/osa/` |
| `api` | backends | `api.osc.earth/osa` |
| `widget` | the edge in front of embedded widgets | `widget.osc.earth/osa` |
| `docs` | documentation | `docs.osc.earth/osa/` |
| `status` | status and usage dashboards | `status.osc.earth/osa/` |
| `notebook` | hosted notebooks | `notebook.osc.earth/osa/` |

A new plane is a new subdomain, named for what it serves, never for a project.
A new project is a new path on the planes it uses, never a new subdomain.

## Environments

A non-production environment prefixes the plane: `develop-widget.osc.earth/osa`, `develop-notebook.osc.earth/osa/`.
The project path stays the same in every environment, so a path works unchanged on any of them.

## What this rules out

- **A per-project subdomain,** such as `osa.osc.earth`.
  It was never created, and it does not resolve.
- **An account hostname in anything a reader sees,** such as `*.pages.dev` or `*.workers.dev`.
  Those belong to whichever hosting account deploys the project today,
  and they change when the account does.
  Documentation, embed snippets and error messages use the `osc.earth` name.
  A pinned third-party content delivery network (CDN) address, such as jsDelivr at a release tag with Subresource Integrity (SRI),
  is a different case: it is immutable by design, and a project may offer it alongside its `osc.earth` address.

## Known exceptions

These predate the rule, and each is recorded so it is not copied:

- `demo.osc.earth` serves OSA's demo page and its widget script at the host root,
  and branch previews use `{branch}-demo.osc.earth`.
  Under the rule these would sit under a `demo` plane's `/osa/` path.
- `api.osc.earth/osa-dev` puts the environment in the path rather than in a prefix on the plane.

Moving either is a change for the project that owns it,
made so the old address keeps working while readers move.

Recorded 2026-09-23.
