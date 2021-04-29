# Contributing

To contribute to the Linden Project documentation, please read the following. Pull
requests that do not meet the criteria described below will not be merged.
Before submitting a PR:

This will improve the chances of your contribution being accepted quickly.

## Contents

- [Style Guide](#style-guide)
- [Submitting Changes](#submitting-changes)

## Style Guide

This style guide outlines the standards for contributing to the Handbook. The
manual on <https://linden-project.github.io/> is generated from an
[hugo-book](https://github.com/alex-shpak/hugo-book) site stored in the
[linden-project.github.io](https://github.com/linden-project/linden-project.github.io/) repository.

### General

Although there will always be cases where command listings are appropriate, the
contents of the Handbook should be written in American English.

### Formatting

For markdown formatting, this project uses the default Hugo markdown format.
Most valid markdown is accepted by the formatter. Read more about [Hugo
markdown formatting)[https://www.markdownguide.org/tools/hugo/].

#### Placeholders

Placeholders indicate where the user should substitute the appropriate
information. They should use square brackets (`[` and `]`) and contain only
lower-case text, with words separated by underscores. For example:

```
$ cat ~/Sukoh/config.<site_name>.json
```

and not:

```
$ cat ~/Sukoh/config.[site_name].json
```

### Links

Link text should not include sentence-level punctuation. For example:

```
[Visit this site](https://example.org).
```

and not:

```
[Visit this site.](https://example.org)
```

#### Internal links

Links to other sections of the Handbook use the Hugo [`ref` shortcode](https://gohugo.io/content-management/shortcodes/#ref-and-relref).

For example:

```
[example]({{< ref "document#anchor" >}})

```

and not:

```
[example](./example.md#heading-text)
```

When referring literally to a Handbook section, the section title should be
placed in double-quotes. Otherwise, double-quotes are not required. For example:

```
For more information, please read the "[Site workspace configuration]({{< ref "../1-workspace-conf/" >}})" section.
```

and

```
Some utility automatically creates a [Site workspace configuration]({{< ref "../1-workspace-conf/" >}}).
```


#### Auto Links

Auto links (links with the same title as URL) should use the following notation:

```
this is an autolink https://www.example.com/ and you should not do anything else.
```

They should not be formatted like this:

```
[https://www.example.com/](https://www.example.com/)
```

#### Redirects

When changing a section name, or moving a section to a different part of the
Handbook, a [Hugo `alias`](https://gohugo.io/content-management/urls/#aliases)
must be added to the `frontmatter` section in the moved document., e.g.

```
---
title: page with new name
aliases:
  - "/docs/page-with-old-name/"
---
```

### Case

Proper nouns outside of code blocks should use the casing of official
information sources: e.g. 'Hugo' not 'hugo', 'GDPR' not 'gdpr', 'twitter' not
'Twitter', etc. In general, abbreviations should be upper-cased: 'CPU'
for central processing unit, 'SSD' for solid state drive, 'UI' for user
interface, etc.

Handbook filenames and directories should use [kebab
case](https://en.wikipedia.org/wiki/Kebab_case) when splitting words. For
example the filename should be `post-install.md` not `postinstall.md`.

### Voice

Prefer the active imperative voice when writing documentation. Consider the
following examples:

> Now we need to install the Electron and and test it.

This version is conversational and friendlier, but contains unnecessary language
that may not be as clear to an ESL reader.

> Install the Electron, then test if it works correctly.

This version contains a clear command to act, and a follow up that shows what
will be done next. It is clear both to native English speakers, ESL readers, and
to translators.

### Warnings

Warnings should begin with `**Warning**:`, and should not be block-quoted with
`>`. For example, the Markdown should look like:

```
**Warning**: Selecting the wrong option will detroy your old WordPress website.
```

and not:

```
> WARNING: Selecting the wrong option will destroy your old WordPress website.
```

### Notes

Notes should only be used sparingly, and for non-critical information. They
should begin with a phrase such as "Note that ..." or "It should be noted that
... ", and not be block-quoted with `>`. For example, the Markdown should look
like:

```
Note that you can also use Linden utility X for this purpose.
```

and not:

```
> You can also use Linden utility X for this purpose.
```

### Block quotes

Block quotes (i.e. `>`) should only be used to quote text from an external
source.

## Submitting Changes

Proposed changes should be submitted as pull requests to the
[Linden Book](https://github.com/linden-project/linden-project.github.io) repository on
[GitHub](https://github.com/). Please note that, unlike a wiki, submissions will
be reviewed before they are merged. If any changes are required they will need
to be made before the pull request is accepted. This process is in place to
ensure the quality and standards of the Linden Project are sustained.

### Requirements

You can use the _edit this page_ link at the bottom of each page to use the
online GitHub editing tools to create a fork, create a modification and send a
pull request.

To clone the repository locally and push changes, git is required. It can be
installed via the `git` package.

Building the Linden Project Documentation locally requires a recent version of [Hugo
extended](https://github.com/gohugoio/hugo/releases/latest).

### Forking

To fork the repository a [GitHub account](https://github.com/join) is needed.
Once you have an account, follow GitHub's
[guide](https://help.github.com/en/articles/fork-a-repo) on setting up a fork.

Clone the repository onto your computer, enter it, and create a new branch:

```
$ git clone https://github.com/<your_username>/linden-project.github.io.git
$ cd linden-project.github.io
$ git checkout -b <branch_name>
```

You can then edit the repository files as appropriate.

### Making changes

To serve the docs locally and view your changes, run `hugo server --minify` from the
root of the repository.

If `hugo server` runs without errors, push your changes to your forked
repository:

```
$ git add <edited_file(s)>
$ git commit -m "<commit_message>"
$ git push --set-upstream origin <branch_name>
```

The commit message should be in the form `<filename>: <description_of_changes>`.

Pull requests should only contain a single commit. If a change is made after the
initial commit, `git add` the changed files and then run `git commit --amend`.
The updated commit will need to be force-pushed: `git push --force`.

If multiple commits are made they will need to be squashed into a single commit
with `git rebase -i HEAD~X`, where `X` is the number of commits that need to be
squashed. An editor will appear to choose which commits to squash. A second
editor will appear to choose the commit message. See
[git-rebase](https://git-scm.com/docs/git-rebase) for more information.
The updated commit will need to be force-pushed: `git push --force`.
