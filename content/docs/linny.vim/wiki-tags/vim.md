---
title: VIM
---

# VIM wikitag

## Description

Runs Vim Ex command

## Usage

```markdown

# Some vim commands embedded as Wiki Command Tags

[[VIM :help 42]]

[[VIM :smile]]

[[VIM :set background=light]]

[[VIM :set background=dark]]

[[VIM: %s/\\(MARKSTART\\n\\)\\@<=\\_.*\\(\\nMARKEND\\)\\@=/\\=substitute(system('date'),'\\n','','g')/g]]

MARKSTART
za  8 feb 2020 18:49:11 CET
MARKEND

```


