# Indigenous Keyboard Project

Open infrastructure for typing Indigenous languages on every platform —
built so that **the machinery is shared and the language stays home.**

## What this is

A keyboard and font framework for North American Indigenous languages. Install
it on Windows, macOS, Linux, Android, iOS, or in a browser, add the languages you
speak, and switch between them the way you would on any modern phone keyboard.

It is built on [Keyman](https://keyman.com) (MIT, SIL Global) with layouts
written to the [Unicode CLDR LDML keyboard
standard](https://unicode-org.github.io/cldr/ldml/tr35-keyboards.html).

## The design constraint

Indigenous language data is the property of the nation that carries it. It is
not ours to publish, and it is not anyone's to scrape.

So this project is split in two:

- **The machinery is public.** Engine, compilers, layouts, fonts, schemas,
  documentation. Anyone may use, fork, audit, and contribute to it.
- **The language is private.** Dictionaries, corpora, and prediction models live
  in private repositories owned by individual nations. This organization has no
  access to them.

The engine builds and runs with zero language packs installed. That is enforced
in CI, because a seam that isn't tested isn't a seam.

Read the full policy: **[DATA-SOVEREIGNTY.md](../DATA-SOVEREIGNTY.md)**

## Repositories

| Repository | Visibility | Contents |
|---|---|---|
| `indigenous-keyboard-core` | Public | LDML layouts, build pipeline, validation |
| `indigenous-keyboard-fonts` | Public | Font package (SIL OFL 1.1) |
| `indigenous-keyboard-pack-template` | Public | Template + guide for building a **private** language pack |
| `.github` | Public | Governance, data sovereignty policy, contribution guide |

Language packs themselves are private and are not listed here.

## Bringing your language in

The framework is open to any nation that wants it — Lakota, Crow, Blackfoot, or
otherwise. You keep ownership and control of your language data at every step;
the template repository walks through building a pack that never leaves your
nation's hands.

Start here: **[indigenous-keyboard-pack-template](https://github.com/Lakota-Language-Consortium/indigenous-keyboard-pack-template)**

## A note on scope

The Lakota Language Consortium maintains this framework and sells Lakota
educational materials. Those are separate things. **The keyboard, the fonts, and
the framework are free and open source, permanently.** Nothing here requires a
purchase, and no nation needs our permission to use it.

## License

Code is MIT. Fonts are [SIL OFL 1.1](https://openfontlicense.org). Language packs
are **not** open-source licensed — see the template repository for why.
