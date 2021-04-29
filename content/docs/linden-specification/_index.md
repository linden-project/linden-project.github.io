---
title: Linden Specification
bookFlatSection: true
weight: 10
---

# Linden Specification

Linden is a personal database standard created with plain text files. The
Specification is a standard describing how all Linden Clients and
Linden Indexers should communicate.

- Records are made of markdown files.
- Relations are declared in front matter.
- The Schema grows organically utilizing simple yaml configuration files.
- And indexes are made of plain json files.

# Taxonomies

Linden Notes is inspired by the Hugo static website engine, and it's way of
using front matter to create user defined taxonomies.

A taxonomy is a way of grouping content and by grouping content the therefor
creating relation between content. Linden specifies the usage of front
matter to classify markdown documents in term of a taxonomy.

# Implementation

Linden is not a software itself but a way working. If you want to take notes
the Linden way you can use the existing tools that implement the Linden
Specification.

You need an Linden Menu Interface in your editor, Wiki Tags in your editor and a Linden Indexer.

# Linden Notes Tools and Applications

| Name                   | Type       | Software-onderdeel                                                    | github project or short name                           | Status        |
|------------------------|------------|-----------------------------------------------------------------------|--------------------------------------------------------|---------------|
| Linden Specification   | spec       | Specification of the Linden Markdown Database, index en configuration | https://linden-project.github.io                       | alpha release |
| Lindex                 | cli-app    | Implentation of a Linden Indexer written in Crystal                   | https://github.com/linden-project/lindex               | alpha release |
| Fred                   | cli-app    | Command line Front Matter Editor                                      | https://github.com/linden-project/fred                 | alpha release |
| Linny.vim              | vim-plugin | Vim Plugin that works with the Linden Notes                           | https://github.com/linden-project/linny.vim            | alpha release |
| Linny Wiki Github tags | vim-plugin | Linny.vim markup extension adding github-repo tags                    | https://github.com/linden-project/linny-wikitag-github | alpha release |
