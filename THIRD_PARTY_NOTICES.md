# Third-party data notices

## JPDB frequency ranks

The user-supplied JPDB rank-based archive has revision
`JPDB_by-frequency-global_2022-05-10T03:27:02.930Z`. Its ZIP SHA-256 and the
checksum of the joined entry-rank mapping are recorded in
`data/frequency/jpdb-entry-ranks.json` and `data/sources.lock.json`. The archive
does not specify a licence. The app uses the ranks only for result ordering;
it does not publish the original frequency bank.

- https://jpdb.io

Kotonoha Jisho's generated dictionary read model is built only from the pinned
assets in `data/sources.lock.json`. The generated artifact retains source
versions and record identifiers. It does not publish unreviewed Wiktionary
translations or invented Hán Việt selections.

## JMdict and JMdict examples

JMdict data is the property of the Electronic Dictionary Research and
Development Group and is used under the JMdict/EDRDG licence. The JSON
conversion is provided by `scriptin/jmdict-simplified`. Example records retain
their source sentence IDs. Tatoeba sentence text is attributed to Tatoeba and
is available under CC BY 2.0 FR. Direct Japanese–Vietnamese example translations
use the pinned 2026-09-26 Tatoeba Japanese/Vietnamese sentence and link exports;
the filtered snapshot preserves both sentence IDs and the direct link. No
indirect or automatically translated sentence is published.

- https://www.edrdg.org/edrdg/licence.html
- https://github.com/scriptin/jmdict-simplified
- https://tatoeba.org/
- https://tatoeba.org/en/downloads

## KANJIDIC2

KANJIDIC2 JSON is provided by JMdict-Simplified and distributed under
CC BY-SA 4.0 with EDRDG attribution.

## Unicode Unihan

Unicode Unihan data is used under the Unicode License v3. The Unicode
copyright and permission notice is available at:
https://www.unicode.org/license.txt

## Thiều Chửu Hán Việt tự điển

Hán Việt character-reading records also use the public-domain Thiều Chửu
dictionary as digitized by `catusf/tudien` under CC0 1.0. The build pins commit
`a7dd918ecc67de8c2d15034f885d919b9295eba4` and retains record identifiers.

- https://github.com/catusf/tudien
- https://creativecommons.org/publicdomain/zero/1.0/

## KanjiVG

KanjiVG is copyright Ulrich Apel and contributors and is distributed under
CC BY-SA 3.0. Kotonoha retains the ordered SVG path data and attributes the
project at https://kanjivg.tagaini.net/.

## Selected Yomitan dictionaries

The compiled word-detail page may show Japanese–English definitions from
研究社 新和英大辞典 第５版, falling back to JMdict where the full edition lacks an exact
spelling-and-reading pair. Japanese–Japanese definitions come from 旺文社国語辞典
第十一版, 明鏡国語辞典 第二版, or 実用日本語表現辞典 in that order. Pitch positions come from
アクセント辞典v2. The exact local revisions and input checksums are recorded in
`data/dicts/selected-sources.lock.json` and the generated source manifest.
Publisher attribution and reuse terms vary by source; the source manifest
states when a dictionary index does not provide terms.

## Kanji Alive native-speaker audio

Exact-matched example-word recordings are by Kanji Alive and its native
Japanese speakers, licensed CC BY 4.0. The word index is derived from
`ka_data.csv` at commit `f83e18664f5ffe2312f468010c528c08a88456c7`.
Kotonoha matches only an identical displayed spelling and reading. MP3 files
are streamed from Kanji Alive's media server and are not modified or bundled.
See https://kanjialive.com/credits/ and
https://github.com/kanjialive/kanji-data-media.

## Tofugu and WaniKani native-speaker audio

Where Kanji Alive has no exact match, Kotonoha uses an identical spelling and
reading from Tofugu's older WaniKani vocabulary recordings. The source files
are licensed CC BY-SA 4.0 by Tofugu and WaniKani. The recording index is pinned
to repository commit `9725e0e7d628ab616e8b14e126d3daa33eba8d36`.
MP3 files are streamed unchanged from that repository and are not bundled.
The collection includes Tokyo and Kansai accents; a recording may differ from
the displayed pitch diagram. See
https://github.com/tofugu/japanese-vocabulary-pronunciation-audio and
https://creativecommons.org/licenses/by-sa/4.0/.

## JmdictFurigana

Ruby segmentation comes from JmdictFurigana release `2.3.1+2026-09-25` and
retains its JMdict/EDRDG provenance. Project code is MIT licensed.

## Sudachi sentence analysis

SudachiPy 0.7.0 and SudachiDict Core 20260723.1 are Apache-2.0 build tools.
The Core dictionary SHA-256 is pinned in the source manifest. Published
sentence ruby requires agreement with exact JmdictFurigana word data; no
Sudachi source code or dictionary binary is shipped in the app.
Example quick-lookup candidates also use Sudachi word boundaries and lemmas;
published links require an unambiguous JMdict pair or a locally generated
conjugation match.

- https://github.com/WorksApplications/sudachi.rs
- https://github.com/WorksApplications/SudachiDict

## WanaKana

WanaKana 5.3.1 is MIT licensed and is used only for query normalization.

## Wiktionary

Direct Vietnamese definitions also use the Vietnamese Wiktionary extract
downloaded from Kaikki.org on 2026-09-29, raw SHA-256
`10e62bccdf3d85fc9e7472c1f85b2149602f97c75177b09523f4762c57ef7d3d`.
Credit Vietnamese Wiktionary contributors and Wiktextract / Kaikki.org.
Definitions are CC BY-SA 4.0; extraction/filtering code is MIT. Source senses
remain independent of JMdict senses. The filtered source snapshot remains local;
each definition retains
its Wiktionary page URL and snapshot-specific record ID. It is a downloaded
snapshot, not a claim of individually pinned page revision IDs.
Source: https://kaikki.org/dictionary/rawdata.html

Reviewer-approved Vietnamese sense mappings use pinned Wiktionary revisions
under CC BY-SA 4.0. Each published mapping retains its edition, page revision,
source-sense identifier, reviewer, and review date. The `辞書 → từ điển`
mapping uses Japanese Wiktionary revision `2179683`:
https://ja.wiktionary.org/w/index.php?title=辞書&oldid=2179683

## Bunchaway Japanese–Vietnamese dictionary

Independent Vietnamese word definitions use a filtered copy of Bunchaway's
`final.csv` at commit `6b1e9248c5382949115ccf1f5e8846d0fc85d6ad`.
The source publisher states CC BY-SA 4.0. Kotonoha credits Bunchaway and retains
the raw CSV SHA-256, filtered snapshot SHA-256, source record number, and exact
headword join. The publisher has not documented where its underlying definitions
originated or how they were reviewed; these are source-provided, **not**
Kotonoha-reviewed translations. They are not mapped to JMdict English senses.
No definition from an ambiguous spelling is imported.

- https://github.com/bunchaway/tu-dien-nhat-viet
- https://creativecommons.org/licenses/by-sa/4.0/

## Kotonoha conjugation engine

The versioned conjugation rules are project-authored and MIT licensed. They do
not copy a third-party conjugation table.
