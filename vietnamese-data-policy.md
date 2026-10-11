# Vietnamese definitions

Kotonoha keeps reviewed Japanese→Vietnamese sense translations separate from
directly sourced Vietnamese dictionary definitions. Independent dictionary
senses are never assigned to JMdict's English sense numbers automatically.

## Broad source layer

Bunchaway's Japanese–Vietnamese `final.csv` is pinned to commit
`6b1e9248c5382949115ccf1f5e8846d0fc85d6ad` and the raw and filtered
SHA-256 hashes in `data/sources.lock.json`. The publisher declares CC BY-SA 4.0.
Its upstream definition sources and editorial process are not documented, so
these entries are clearly recorded as source-provided rather than human-reviewed
Kotonoha translations. This is a provenance limitation and individual meanings
may require correction.

The build imports only literal primary spellings that identify one JMdict entry
across all spellings. No source text is assigned to an English sense. Source
order determines the compact first meaning; it is **not** a measured frequency
ranking. Full definitions remain in the independent Vietnamese list. Search
indexes that list separately from English meanings. The filtered snapshot is
available at [the pinned local source](/data/bunchaway.source.json).

## Free source baseline

The Vietnamese Wiktionary JSONL extract downloaded from Kaikki.org on 2026-09-29
is pinned by SHA-256 in `data/sources.lock.json`. Definitions are attributable to
Vietnamese Wiktionary contributors under CC BY-SA 4.0. Wiktextract / Kaikki.org
provides the extraction. Page history remains available through each source URL;
this snapshot does not claim an individual page revision number.

The filtered source copy is [available here](/data/vietnamese-wiktionary.source.json).
It retains original gloss text and independent source sense IDs. Only Japanese
language entries with direct glosses are eligible. Character readings,
romanizations and inflection/alternate-form references are excluded. Publication
requires a literal displayed-headword match to a unique JMdict entry and compatible
part of speech. The match is recorded as `source-headword`, not `reviewed`.

Compact summaries prefer reviewed Vietnamese wording when available, otherwise
the first Bunchaway definition, then the first Wiktionary definition. Details preserve all imported source
senses in a separate section. Search indexes both layers. Missing entries, kanji
definitions and example translations are not generated from these word definitions.

## Rebuilding

The filtered snapshot ships with the repository; normal `npm run data:build`
does not need network access. To reproduce its filtering, download the raw extract
with the locked input checksum, then run `npm run data:import-vietnamese -- PATH`.
The upstream URL is mutable: if its checksum changes, the importer refuses it.
An intentional refresh must pin and audit a new snapshot and update the manifest.
Filtering/import code is project-authored and MIT licensed.
To rebuild Bunchaway's filtered source, fetch the exact pinned CSV and run
`npm run data:import-bunchaway -- PATH`; the checksum gate rejects altered input.

## CJKI assessment

[CJKI's published data licensing](https://www.cjk.org/licensing/) describes fees
negotiated per use case. Donations are exceptional, not a free public license.
It is therefore not used under this app's no-cost requirement.
