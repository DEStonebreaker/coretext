# BookContext

BookContext is an experimental semantic indexing tool for large technical sources such as textbooks, specifications, and course materials.


The basic idea is to index a source one, locate relevant ranges through a query, and then read/output. This is to reduce the amount of times a source is read by agents to minimize wasting tokens for reading massive documents.  

AI tools often repeatedly parse, chunk, and search the same large documents in order to answer small questions. BookContext aims to reduce that overhead by creating a reusable index that can tell a human or agent where relevant information is located before the full source needs to be read.

For example, instead of giving an agent a 700-page textbook and asking it to find a concept, BookContext could eventually return something like:

```text
Query: "Where is copy-on-write explained?"

Operating Systems: Three Easy Pieces
Chapter: Process API
Pages: 42–46
```

The agent could then read only that relevant range.

## Project Goals

The initial MVP is focused on:

* ingesting a technical PDF once
* preserving page and source provenance
* supporting keyword and semantic search
* returning small, relevant page ranges
* exposing results in a form that other tools and AI agents can consume

BookContext is intended to work locally first. A future public service could host reusable indexes for openly available technical literature, while self-hosted instances could index private course materials, internal documentation, or proprietary sources.

## Current Status

BookContext is currently in the planning and early development stage.

The first milestone is building a local ingestion pipeline:

```text
PDF
 ↓
text extraction
 ↓
page-preserving representation
 ↓
SQLite
```

Search, embeddings, agent integrations, and public index sharing will come later.


BookContext is not intended to be another general-purpose "chat with a PDF" application.

The project focuses on creating reusable, deterministic source-location metadata that other tools can build on.

The original document remains the source of truth. BookContext's job is to help answer the question of where one should look within a source.