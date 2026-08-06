# Data Sovereignty

How we handle language data: what we publish, what stays private, and why.

This describes our principles and our practice. It is not a contract and creates
no obligations on anyone else. What binds a recipient of a language pack is the
licence on that pack.

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

Every artifact is **machinery**, **language**, or **pedagogy**.

> **Could someone reconstruct meaning in the language from this file?**
> No → **machinery**. Public.
> Yes → **language**. Private.
>
> **Is it someone's authored work of teaching?**
> Yes → **pedagogy**. Its author decides its terms.

Machinery and language are the split that matters most. Pedagogy is separate
because teaching a language is authored labor with an owner who is not
necessarily the owner of the language.

**Language and pedagogy stack.** A textbook is pedagogy *and* it contains
language. Both sets of rights apply to the same file at once, and the stricter
governs.

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

All of the following live in a private repository held by the authority that
maintains that language pack:

- Wordlists, dictionaries, lexicons
- Corpora, text collections, transcriptions
- N-gram models, frequency data, trained weights
- Morphological analyzers, FSTs, grammar rules
- Autocorrect and prediction data
- Audio, recordings, speaker data

Frequency data is included deliberately. A frequency-ranked wordlist is a corpus
with the sentences removed; it is still the language.

### Proprietary — pedagogy

| Artifact | Held by |
|---|---|
| Curriculum, scope and sequence, lesson plans | Its author |
| Textbooks, workbooks, exercises, assessments | Its author |
| Illustrations and recordings produced for instruction | Its author |
| Teacher guides and training materials | Its author |
| Learning platforms, courseware, lesson-delivery software | Its author |
| Vocabulary, practice, and assessment applications | Its author |
| Teacher dashboards and classroom management tools | Its author |

**Software can be pedagogy.** "Machinery is public" is not "all software is
public." A keyboard engine is infrastructure; a learning platform is authored
teaching that happens to be software. The test is whether it is infrastructure
or instruction — not whether it compiles.

**Teaching a language is not the same as owning it.** Designing a sequence of
lessons, writing exercises, commissioning artwork, and testing what actually
helps a learner — that is authored work, and its author may hold it, license it,
or sell it. The Lakota Language Consortium does exactly that, and the revenue
funds the open infrastructure in this organization.

This is an ordinary copyright and commercial matter. It is **not** a sovereignty
claim, and it must never be dressed up as one.

#### The two rights stack; neither overrides the other

- **Owning the teaching effort does not grant ownership of the language it
  teaches.** LLC's copyright in a Lakota textbook does not make LLC an owner of
  Lakota. No amount of authorship, funding, or institutional history converts
  into a claim on the language itself.

- **A nation's authority over its language does not entitle it to another
  party's curriculum** — while that nation does retain authority over the
  language content inside that curriculum.

The practical consequence, which is easy to get wrong:

> **A proprietary textbook still contains language data.**
> Purchasing it does not license the language inside it for redistribution,
> corpus-building, or machine-learning use. Commercial terms and sovereignty
> terms apply to the same file simultaneously, and the stricter one governs any
> given use.

A publisher may sell its book. It may not sell the language in the book.

## How we structure it

1. **One private repository per language pack, held by the authority that
   maintains it.** Not per-organization. That authority controls the pack,
   including the right to revoke it. Where more than one authority maintains a
   pack for the same language, each holds its own.

2. **We do not make private packs submodules of public repositories.**
   A submodule reference in a public repo is a public pointer to private content
   and leaks the existence, name, and commit history of the pack. Packs are
   consumed as **built, signed binary artifacts** loaded at runtime.

3. **The engine builds and runs with zero packs installed.**
   If a build ever needs a language pack, the seam has been breached.

4. **Illustrative examples are fine. Collections are not.**

   Showing a few words to document what a key produces, how a glyph renders, or
   how a bug reproduces is fine. That is teaching, and nations publish exactly
   this kind of example in their own primers, dictionaries' front matter, and
   keyboard guides. A policy that forbade it would make the software
   undocumentable and would not protect anything.

   What we keep out is **systematic** language data: wordlists, lexicons,
   corpora, frequency tables, paradigm sets, sentence collections, or anything
   assembled to be comprehensive.

   The distinction is *purpose and completeness*, not word count:

   | Fine | Not |
   |---|---|
   | "`R` produces `š`, as in `šúŋka`" | A list of words containing `š` |
   | A sentence showing mixed-script rendering | A collection of sentences |
   | A bug report quoting the word that breaks | A file of test words |

   Ask: *would this help someone reconstruct the language, or only help someone
   understand the software?* If the former, it belongs in the private pack.

   When in doubt on a specific case, the maintaining authority decides — not the
   maintainers, and not the contributor.

## Machine learning and automated ingestion

This policy binds this organization. Recipients are bound by the licence on the
pack they receive — see `LICENSE` in the pack template. Standard open-source
licences do not restrict machine-learning use, which is why language packs are
**not** open-source licensed.

**We do not sell, license, or provide language data to anyone for training,
fine-tuning, evaluating, or conditioning a model.**

**A maintaining authority may train models on the data it maintains** and
distribute them on its own terms.

Any other use requires that authority's specific, written, revocable consent.
Absence of a refusal is not consent.

What we do on a private pack repository:

- Repository visibility **private**; organization-level fork policy disabled
- Code-indexing integrations **disabled** at the organization level
- `.aiexclude`, `.cursorignore`, `.codeiumignore`, and `CLAUDE.md` guard files
  committed at the repository root
- `noindex` headers and `robots.txt` denial on any hosted build artifact
- Signing keys held by the maintaining authority

These reduce exposure; none of them is complete. Organization settings cannot
reach a contributor's personally licensed AI tooling, and guard files bind only
software configured to read them. Access control — keeping the list of people
with repository access short — does more than any of the above.

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

1. Fork `native-american-keyboard-pack-template` **as a private repository** owned by
   your nation's designated authority.
2. Build your layout against the LDML spec. Contribute it publicly to
   `native-american-keyboard` **only if your authority chooses to** — this is
   optional, and packs work fine with a privately held layout.
3. Populate the pack privately. Nothing in that repository is ever pushed here.
4. Distribute the built pack on whatever terms your authority sets, including not
   distributing it at all.

The maintainers of this organization have no claim on, access to, or authority
over any pack but their own. We maintain the machinery. You hold the language.

## Reporting a violation

If language data has been committed to a public repository, treat it as an
incident, not a cleanup task. Email **security@lakhota.org**
rather than opening a public issue — an issue describing the leak reproduces it.

Deleting the commit is not enough. We rewrite the content out of the
repository's history and tell **the authority that contributed the affected
material**, however brief the exposure was. That notification is their right, not
our discretion.

Copies already taken cannot be recalled. Forks, clones, caches and mirrors are
outside our control; we can ask GitHub to purge caches and contact fork owners,
and we say what we could not reach rather than implying the exposure was undone.
