# Lakota Language Consortium

*To preserve, promote, and strengthen the Lakota language.*

[lakhota.org](https://lakhota.org)

## What's on this GitHub

The open-source infrastructure behind our work — the tools that make Indigenous
languages typable, searchable, and teachable on modern devices.

We build these in the open so that other nations can use them for their own
languages without asking us, paying us, or waiting for us.

## The principle behind all of it

**A language belongs to the people who speak it.**

Software that handles a language is infrastructure. The language itself is not
infrastructure — it is the collective property of the nation that carries it.
These are different things, and we keep them in different places.

Everything we publish here follows one split:

- **The machinery is public.** Engines, layouts, schemas, build tooling, and the
  keyboard apps themselves. Anyone may use, fork, audit, and contribute.
  Teaching software — learning platforms, practice and assessment apps — is not
  machinery; it is authored instruction, and its terms are its author's.
- **The language is private.** Dictionaries, corpora, recordings, and prediction
  models live in private repositories held by the authority that maintains each
  pack. Where the data
  is not ours, we have no access to it.

This is not a licensing preference. It follows the [CARE Principles for
Indigenous Data Governance](https://www.gida-global.org/care) and it is why our
language packs are deliberately **not** open-source licensed — no standard OSS
license restricts machine-learning ingestion, and that restriction is the point.

**Read the full policy: [DATA-SOVEREIGNTY.md](https://github.com/Lakota-Language-Consortium/.github/blob/main/DATA-SOVEREIGNTY.md)**

## Projects

### 🔤 Native American Keyboard — *active*

Type Lakota — or any Indigenous language — on Android, iOS, Windows, macOS, and
Linux.

**One app. Switch on the languages you speak.** No separate download per
language, no second app to install. On mobile the keys show the actual letters —
`š`, `ǧ`, `ŋ` — so there is nothing to memorize.

Includes predictive text, which has never existed for Lakota or any Siouan
language.

Built on [GiellaLT / Divvun](https://github.com/divvun) (Apache 2.0), the Sámi
language technology stack, whose tools exist because mainstream keyboards ignored
their languages too.

| Repository | Visibility | Contents |
|---|---|---|
| [`indigenous-keyboard`](https://github.com/Lakota-Language-Consortium/native-american-keyboard) | Public | Layouts, builds and releases for every platform |
| [`native-american-keyboard-pack-template`](https://github.com/Lakota-Language-Consortium/native-american-keyboard-pack-template) | Public | Template + guide for building a **private** dictionary pack |
| [`.github`](https://github.com/Lakota-Language-Consortium/.github) | Public | Governance and data sovereignty policy |

Language packs are private and are not listed here.

### 📚 More to come

Learning platforms, dictionary tooling, and other language technology are in
progress and will appear here as they are ready — under the same split. Platform
code public; language content held where it belongs.

## Bringing your language in

The keyboard framework is open to any nation that wants it — Lakota, Crow,
Blackfoot, or otherwise. You keep ownership and control of your language data at
every step, and nothing you build has to pass through us.

Start here: **[native-american-keyboard-pack-template](https://github.com/Lakota-Language-Consortium/native-american-keyboard-pack-template)**

## A note on what's free and what isn't

Two different things are non-public here, for two different reasons, and we'd
rather be plain about it:

- **Language data is private because it isn't ours to publish.** That's
  sovereignty. It applies to our Lakota data and to every other nation's, and it
  is not negotiable or purchasable.
- **Our educational materials are paid because selling them funds this work.**
  That's commerce, and an ordinary one. Building a curriculum — sequencing it,
  writing the exercises, finding out what actually helps a learner — is real
  labor, and it is different work from owning a language.

Those two are not the same claim, and we don't want them confused. Authoring a
Lakota textbook does not make us an owner of Lakota. Our copyright covers the
teaching we built; it stops at the language inside it. Buying our book licenses
you to learn from it — not to redistribute the language in it or feed it to a
model.

**The infrastructure is free and open source, permanently.** The keyboard, the
layouts, the fonts, and the framework require no purchase, no account, and no
permission from us. If you only ever use the free tools and never buy a thing
from us, that is a success by our measure, not a loss.

## License

App code is Apache 2.0 (matching upstream); layouts and tooling are MIT. Fonts are
[SIL OFL 1.1](https://openfontlicense.org). Language packs are not open-source
licensed — see the template repository for why.

## Contact

[lakhota.org](https://lakhota.org) · Data exposure reports:
**security@lakhota.org**
