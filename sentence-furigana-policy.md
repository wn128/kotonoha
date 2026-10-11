# Example-sentence readings and Vietnamese translations

Example sentences come from the pinned JMdict-Simplified English-example
release. The Japanese sentence, its linked dictionary word, and English
translation remain unchanged.

## Examples by meaning

The Word tab places an example beneath the exact English JMdict meaning to
which the source attaches it. The importer checks that the example release's
English sense order and glosses match the pinned JMdict release before linking
them. It shows one sourced example per covered meaning; additional examples
remain in Phrases. In this snapshot, 17,091 of 37,160 English meanings have a
linked example. Meanings without one say so instead of borrowing a sentence
from another meaning. Independent Vietnamese dictionary definitions are not
treated as aligned JMdict senses.

## Furigana

Sentence-wide ruby is built offline with SudachiPy 0.7.0 and SudachiDict Core
20260723.1. A kanji-containing token is annotated only when Sudachi's
contextual reading has an exact JmdictFurigana spelling-and-reading record,
and the JmdictFurigana segments reconstruct both the written text and reading.
When that surface has multiple documented readings, the selected pair must
also be a primary headword pair in the imported JMdict dictionary. This
prevents a segmenter's uncommon pronunciation from silently overriding a
common one (for example 私 in a casual sentence).
Out-of-vocabulary or unverifiable readings remain unannotated. These are
machine-derived contextual readings, not human-reviewed transcriptions. The
linked example word separately retains its exact dictionary/conjugation reading.
Accepted ruby is displayed in hiragana even when the source encodes a reading
in katakana.

## Clickable words in examples

Sudachi Core supplies contextual token boundaries, lemmas, and readings in a
pinned [candidate snapshot](/data/example-tokens.source.json). A candidate
becomes a quick-lookup link only if exactly one JMdict entry has the token's
spelling and reading, or if a kanji-containing inflection matches the lemma
and a form produced by the pinned local conjugation engine. A verb stem may
link only when that engine also emits the same stem followed by ます. For
unchanged katakana words, a unique literal spelling may resolve a notation
difference between a source vowel reading and Sudachi's long-vowel mark; this
does not choose between homograph entries. The source-linked
example headword takes precedence. Ambiguous, unmatched, and unsupported
tokens remain plain text. The accepted entry ID and match kind are stored with
each example; no runtime tokenizer or network lookup is needed.

The build uses the pinned dictionary SHA-256 and the JmdictFurigana archive
checksum in `data/sources.lock.json`. Its filtered, reusable result is
[sentence-furigana.source.json](/data/sentence-furigana.source.json). It is a
computed annotation, not a claim that every sentence reading has been
reviewed by a person.

## Vietnamese

Vietnamese sentence text is imported only from Tatoeba's direct Japanese–
Vietnamese links. The importer verifies the Japanese sentence ID **and** exact
Japanese text against Tatoeba's dated Japanese export, then retrieves the
directly linked Vietnamese sentence ID and text from the corresponding
Vietnamese export. It never pivots through English, reuses a word definition,
or machine-translates. Multiple direct translations remain in the filtered
[source snapshot](/data/tatoeba-vietnamese.source.json); the app currently
shows the first sentence-ID-sorted one. Source order is not a quality or
frequency ranking. Missing direct translations remain unavailable.

Tatoeba text is CC BY 2.0 FR; the UI data retains both sentence IDs and a
direct source link. The three raw export checksums and the filtered snapshot
checksum are pinned in `data/sources.lock.json`.

## Rebuilding

After `npm run data:fetch` and an initial `npm run data:build`, use a Python
3.10+ virtual environment with the pinned build-time packages. Then run:

```sh
python3 -m venv .cache/kotonoha-tools
.cache/kotonoha-tools/bin/python -m pip install -r scripts/data/requirements-sentence-furigana.txt
npm run data:import-tatoeba-vietnamese
.cache/kotonoha-tools/bin/python scripts/data/import-sentence-furigana.py
.cache/kotonoha-tools/bin/python scripts/data/import-example-tokens.py
npm run data:build
npm run data:validate
```

If a pinned upstream export changes, the importer rejects its checksum; an
intentional update requires auditing the new snapshot and changing the lock.
