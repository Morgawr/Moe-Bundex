# Data Format

The database is divided in entries, keyed on a word or expression. Each indexed
key can have multiple example sentences connected to it.

Here is a loose pseudocode representation of the data format:

```javacript
// Top level entry
{
  // This is the expression that will be keyed on by the database
  "expression": <str>,
  // All possible readings of the expression, including alternative kanji
  "readings": [<str>],
  // List of all example sentence entries (see below) that use said expression
  "entries": [<Entry>]
}
```

```javascript
// Entry
{
  // Original Japanese sentence including furigana
  "sentence_jp": <str>,
  // Translated English sentence
  "sentence_en": <str>,
  // Individual word or expression in "plain" form in the same script as it shows up in the sentence (kana, kanji, etc)
  "expression": <str>,
  // Type of source the sentence was taken from (see below)
  "source_type": SOURCE_TYPE,
  // Title of the work the sentence was taken from (see below)
  "source_title": <str>,
  // Whether the sentence contains sensitive content (sex, gore, violence, etc)
  "sensitive": <bool>
  // Additional free-flow notes, can be used to explain translation choices or cultural contexts
  "notes": optional<str>,
  // If there is and audio-visual source, it can be linked as external URL
  "media": optional<url>,
  // Person who submitted the sentence
  "submitter": optional<str>,
  // If the sentence has been verified, bug tracker number of the issue where it was verified
  "verified": optional<str>,
  // True if the sentence was submitted without verification
  "break_glass": <bool>
}
```

The `SOURCE_TYPE` data type is used to track what kind of media the sentence has
been taken from.

Here are the possible options:

- Anime
- Manga
- Book (this includes light novels)
- Visual Novel
- Videogame
- Other (Audiovisual)
- Other (Written)

NOTE: The distinction between Visual Novel and Videogame is clear in most cases,
however there are corner cases where it is ambiguous and submitters may
disagree. In such situations, always default to using the Videogame type.

The source title should ideally also contain specific details like which anime
episode or light novel / manga volume a certain sentence was taken from, if
possible. The actual page number or timestamped minute should be left out.

The Japanese sentence should keep the same furigana as in the original source.
To encode furigana use the format `[kanji;furigana]okurigana`, for example: 食べる
-> \[食;た\]べる

The expression entry should keep the same style (katakana, hiragana, kanji, etc)
as the original sentence, however it has to be deconjugated as it would appear
in a dictionary like jmdict, etc.

For example:

- いかない -> いく
- 物足りない -> 物足りない (not 物足りる because the expression itself takes ない)
- ちょっとウケたみたいだ。-> ウケる (not 受ける)

The top level entry should be keyed on the most common representation of the
word/expression with the alternative readings provided in the `readings` list.
For example, the word 聞く should have `[聞く, きく]` as readings. In case of 異字同訓
words with clearly different usages (聞く vs 聴く vs 訊く) should have different
entries in the database. The database does not distinguish example sentences
based on meaning, that is up to users and dictionary creators to separate
individual meanings if necessary.

In case of words that can be written with multiple kanji but maintain the same
meaning or not distinguish between usage differences, they should go into a
single entry. This includes 旧字体 forms. For example: 答え should match:
`[答え, 応え, 報え, こたえ]`.
