# Kotonoha Hán Việt data policy

Policy version: **4.0.0**

Published data license: **CC BY-SA 4.0**

Importer and validation code: **MIT**

Kotonoha keeps character readings, selected display readings, derived word aids,
and exact lexical word forms separate. A value is never presented as a
Vietnamese definition merely because it can be read in Hán Việt.

## Vietnamese meaning shown on kanji pages

The `data/reviewed/kanji-vietnamese.json` file holds AI-assisted editorial
translations checked against the exact pinned KANJIDIC2 English meanings for
the Japanese character. Each record retains the source English list, reviewer,
and review date. The build rejects stale English lists and malformed or duplicate
reviews. These translations are not certified by a human Vietnamese lexicographer.
Where the pinned English gloss is imprecise, a review may also link to a
Japanese dictionary entry; the kanji page displays that additional source.
The current reviewed set covers 3,198 characters, including all 1,026 kanji
taught in Japanese elementary school and all 2,136 kanji with a
KANJIDIC2 grade from 1 through 8. Characters were selected by
Japanese grade and frequency; Japanese–Chinese meaning collision cases such as
机, 芸, 弁, 叶, and 娘 were checked separately.
The audits in `data/reviewed/` record Japanese dictionary checks, corrections,
and known KANJIDIC2 gloss limitations for ambiguous characters.
This is 30.8% of all 10,384 KANJIDIC2 records, 92.6% of records with a
Japanese frequency rank, and 81.1% of kanji appearing in this app's JMdict
spellings. These denominators describe different uses of the source data;
untranslated records must not be silently filled with Hán Việt readings or
Chinese-only glosses.
An additional set of uncommon characters with exact Japanese single-character
headwords was cross-checked against those words' Vietnamese definitions and
KANJIDIC2 meanings. The word definitions remain separate source evidence.
It translates useful Japanese character senses, not every historical
or highly specialized KANJIDIC2 gloss.
Bulk English-to-Vietnamese machine translation was tested and rejected as a
publishable fallback: it mistranslated ordinary kanji senses including 楓
(`maple`) and 卸 (`wholesale`). Machine output may assist drafting, but each
published character translation must be checked against the Japanese-oriented
KANJIDIC2 senses and recorded in the review file.
`npm run data:kanji-vi-queue -- --limit 150 --examples` lists remaining
characters by Japanese frequency, their pinned English meanings, any exact
Japanese-word Vietnamese evidence, and JMdict usage examples. Compound usage
alone does not establish a character meaning. Entries whose Japanese meaning is
unclear stay out of the reviewed file pending more evidence.
The outside-list audit records **987 reviewed** and **7,186 untranslated**
characters among 8,173 outside N5–N1. This includes 476 newly reviewed
single-character Japanese headwords and 278 old Japanese character forms
linked by Unihan `kJapaneseOldVariant`, each checked against its own
KANJIDIC2 senses. Ambiguous old forms were checked in Kanjipedia rather than
inheriting every sense of the modern form. The
[exact-headword evidence](../data/reviewed/off-list-exact-headword-evidence.tsv)
and [old-form evidence](../data/reviewed/off-list-japanese-old-variant-evidence.tsv)
record the comparisons. All exact Japanese single-character headwords in this outside-list queue
now have reviewed meanings. Run
`npm run data:kanji-vi-queue -- --outside-levels --single-headword-only`
to inspect the remaining queue.

When a character has no reviewed translation, one exact, unambiguous Japanese
headword consisting of the kanji alone may supply its independently sourced
Vietnamese word definition. The display labels it **“Meaning as a Japanese
word”** and links to its source. This lexical meaning does not populate the
character's `meanings.vi` field. If neither source exists, the Vietnamese
character meaning remains unavailable; Thiều Chửu glosses are not substituted.

## Sources

- Unicode Unihan 18.0 supplies `kVietnamese` readings and the
  `kJapaneseOldVariant` relationships needed to connect Japanese shinjitai to
  older character forms. Chinese simplified/traditional properties are not
  used for this transfer.
- The pinned CC0 digitization of Thiều Chửu's public-domain *Hán Việt tự điển*
  supplies a separately licensed Vietnamese character-reading record.
- Project-owned editorial decisions may resolve remaining ambiguity, but only
  when they name a reviewer, review date, selected source-backed candidate, and
  supporting evidence.

## Automatic primary rule

The pipeline selects a character primary automatically only when the pinned
Unihan evidence and the pinned Thiều Chửu record produce exactly one combined,
NFC-normalized reading. Source order is never used as preference. Multiple,
conflicting, one-source-only, and missing candidates remain unselected.

## Compact display and derived word rule

Compact character displays show the first reading retained in the local database.
Candidates are deduplicated in Thiều Chửu dictionary-header order, with Unihan-only
readings appended. Alphabetical sorting is not a reading preference. Documented
source-backed display defaults may precede dictionary order: 本 uses BẢN because
its pinned dictionary entry explicitly identifies that as the familiar reading.
会/會 use HỘI before CỐI; 行 uses HÀNH before its alternate readings.
This is a reproducible general-purpose default, not measured frequency or a
guarantee that the resulting reading fits every compound. The default definitions
and supporting notes live in `data/reviewed/han-viet-primary.json`.
Detailed character views keep all candidates and any separately selected primary.

A word-level `Hán Việt (từng chữ)` aid is emitted only when every literal Han
character has a source-backed candidate, using the first retained reading of each.
Kana is ignored. Iteration marks and other
non-kana symbols block derivation. The resulting sequence is a reading aid, not
a translation or an assertion that the sequence is an established Vietnamese
word.

An exact reviewed word form may take display precedence for its exact JMdict
entry and spelling. The character-derived sequence and its components remain
available for provenance.
