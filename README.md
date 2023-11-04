# 萌え文dex - Moe Bun-dex Project

## What is this?

An open source word lookup index for Japanese example sentences taken from
various media with a side-by-side curated English translation.

## How do I use it?

TBD

## Soul of the Project

There are certain inalienable qualities that I want this project to focus on.
Take the following bullet points as something like a “constitution" that
describes the “soul" of the project. In case of doubts when making new processes
or guidelines, or when not sure whether to introduce new changes in the process
or any other unpredictable future developments, the constant that must be
maintained is that they must not violate these fundamental tenets.

- The project prioritizes the goal of learning Japanese
- Translations should prioritize making the Japanese understandable
- The project is free to use for anyone
- No Japanese sentences will be accepted if they have been translated from other
  languages
- Quality over quantity, all sentences must be vetted by a human.

## Note for Developers

See the [data format](docs/DATA.md) document for more details.

## Note for Users

As per one of the core principles of this project, please make use of this
however you please. However if you plan to build tools on top of the data from
this project, we recommend keeping in mind the following:

- The sentences are chosen for the purpose of learning Japanese. If you are
  building a corpus or collection of data to provide statistical analysis, this
  is not the right dataset for you. The data is intentionally biased.
- The sentences put the focus on a single entry (vocab, expression, etc). Unlike
  other projects like tatoeba corpus, we don't recommend indexing these
  sentences using a different entry or key than the one provided as the quality
  of the results will likely drop.
- The project focuses on manual curation of entries, if you are looking for an
  extensive coverage of a lot of different expressions, this will likely not be
  the right dataset for you.
- Our sentences prioritize fictional and scripted media, so they might not
  necessarily reflect how Japanese is used in real life.
- The authoritative source in these samples should always be the Japanese
  sentence. The English translations are made just as an example/explanation to
  understand the Japanese. If you plan to provide English -> Japanese queries
  (like reverso) or are going to translate these sentences into other languages,
  we recommend starting from the original Japanese and ignoring the English.

## Contributing

See the [CONTRIBUTING.md](docs/CONTRIBUTING.md) page for details on how to
contribute new sentences.
