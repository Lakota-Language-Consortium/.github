# .github

Organization-level configuration and governance for the Indigenous Keyboard
Project.

## Contents

| File | Purpose |
|---|---|
| [DATA-SOVEREIGNTY.md](DATA-SOVEREIGNTY.md) | **The policy that governs every repository here.** Read this first. |
| [profile/README.md](profile/README.md) | Renders as the public org landing page at github.com/Lakota-Language-Consortium |

## The short version

The machinery is public. The language is private.

Keyboard engines, layouts, fonts, and schemas are open source, because they
contain character mappings and no language. Dictionaries, corpora, and prediction
models live in private repositories owned by individual nations, because a
language is the property of the people who carry it — not infrastructure to be
published, and not a dataset to be scraped.

The engine builds and runs with zero language packs installed. That is enforced
in CI, because a seam that isn't tested isn't a seam.

## Required organization settings

These are part of the policy, not optional hardening. Verify them periodically:

- [ ] Two-factor authentication **required** for all members
- [ ] Members **cannot** change repository visibility (owners only)
- [ ] Members **cannot** delete repositories (owners only)
- [ ] GitHub Copilot and code-indexing integrations **disabled** org-wide
- [ ] Forking of private repositories **disabled**
- [ ] Secret scanning and push protection **enabled**

The visibility setting matters most. A member flipping a language pack to public
is the single worst failure mode available to this organization, and it is one
click.

## Reporting a data exposure

If language data reaches a public repository, email
**security@lakotalanguageconsortium.org**. Do not open a public issue — an issue
describing the leak reproduces it.
