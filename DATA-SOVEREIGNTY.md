# Data Sovereignty Policy

This policy governs every repository in this organization. It is not aspirational
language. It determines what may be committed, where, and by whom.

## The principle

**A language belongs to the people who speak it.**

Software that types a language is infrastructure. The language itself is not
infrastructure — it is the property of the nation that carries it. These are
different things, and this organization keeps them in different places.

This position follows the [CARE Principles for Indigenous Data Governance][care]
(Collective Benefit, Authority to Control, Responsibility, Ethics) and the
[OCAP® principles][ocap] (Ownership, Control, Access, Possession). Where CARE and
open-source convention conflict, CARE wins.

[care]: https://www.gida-global.org/care
[ocap]: https://fnigc.ca/ocap-training/

## The line

Every artifact in this project falls on one side of a single question:

> Could someone reconstruct meaning in the language from this file?

If **no**, it is machinery, and it is public.
If **yes**, it is language, and it is private.

### Public — machinery

| Artifact | Why it is public |
|---|---|
| Keyboard engine, compilers, build tooling | Contains no language |
| Character inventories (Unicode codepoints) | Already published in the Unicode Standard |
| Keyboard layouts (key → character maps) | A mapping of keys to characters, containing no words |
| Font glyphs and shaping rules | Typographic forms, not meaning |
| Lexical-model *schemas* and *loaders* | The slot, not what fills it |
| Documentation, specs, governance | About the system, not in the language |

A layout says "long-press `s` produces `š`." It does not say what `š` means or
what words contain it. That is why layouts are public and dictionaries are not.

### Private — language

| Artifact | Where it lives |
|---|---|
| Wordlists, dictionaries, lexicons | Private per-nation repository |
| Corpora, text collections, transcriptions | Private per-nation repository |
| N-gram models, frequency data, trained weights | Private per-nation repository |
| Morphological analyzers, FSTs, grammar rules | Private per-nation repository |
| Autocorrect and prediction data | Private per-nation repository |
| Audio, recordings, speaker data | Private per-nation repository |

Frequency data is included deliberately. A frequency-ranked wordlist is a corpus
with the sentences removed; it is still the language.

## Structural rules

These are enforced, not merely requested.

1. **One private repository per language, owned by the relevant nation.**
   Not per-organization. A nation controls its own pack, including the right to
   revoke it.

2. **Private packs are never submodules of public repositories.**
   A submodule reference in a public repo is a public pointer to private content
   and leaks the existence, name, and commit history of the pack. Packs are
   consumed as **built, signed binary artifacts** loaded at runtime.

3. **The engine must build and run with zero packs installed.**
   This is a CI check, not a convention. If the build ever requires a language
   pack, the seam has been breached.

4. **No language data in any public issue, PR, discussion, test fixture,
   commit message, or screenshot.** Test fixtures use the synthetic placeholder
   script defined in the pack template. Bug reports about a real word are filed
   in the private pack repository, not here.

## Machine learning and automated ingestion

Language data in this project **may not be used to train, fine-tune, evaluate, or
condition any machine-learning model** without specific, written, revocable
consent from the nation that owns it. Absence of a refusal is not consent.

Standard open-source licenses do not restrict this. That is precisely why
language packs are **not** open-source licensed — see `LICENSE` in the pack
template.

Required technical measures on every private pack repository:

- Repository visibility **private**; organization-level fork policy disabled
- GitHub Copilot and any code-indexing integration **disabled** at the org level
- `.aiexclude`, `.cursorignore`, `.codeiumignore`, and `CLAUDE.md` guard files
  committed at the repository root
- `noindex` headers and `robots.txt` denial on any hosted build artifact
- Pack payloads encrypted at rest; signing keys held by the owning nation

### Working with AI coding assistants

Contributors frequently use AI assistants. Those tools read the working
directory, and anything they read leaves the device.

**Do not open a language pack in a directory where an AI assistant is running.**
Engine work and pack work happen in separate checkouts, on separate paths, in
separate sessions. The guard files above reduce accidents; they do not replace
this rule, because a guard file cannot stop a tool that was never configured to
read it.

This constraint applies to project maintainers as much as to outside
contributors.

## Adding a language

The framework is open to any nation that wants it. The process:

1. Fork `indigenous-keyboard-pack-template` **as a private repository** owned by
   your nation or its designated authority.
2. Build your layout against the LDML spec. Contribute it publicly to
   `indigenous-keyboard-core` **only if your nation chooses to** — this is
   optional, and packs work fine with a privately held layout.
3. Populate the pack privately. Nothing in that repository is ever pushed here.
4. Distribute the built pack on whatever terms your nation sets, including not
   distributing it at all.

The maintainers of this organization have no claim on, access to, or authority
over any pack but their own. We maintain the machinery. You hold the language.

## Reporting a violation

If language data has been committed to a public repository, treat it as an
incident, not a cleanup task. Email **security@lakotalanguageconsortium.org**
rather than opening a public issue — an issue describing the leak reproduces it.

Deleting the commit is insufficient; the content must be purged from history and
any forks, and the owning nation must be notified regardless of exposure
duration. That notification is their right, not our discretion.
