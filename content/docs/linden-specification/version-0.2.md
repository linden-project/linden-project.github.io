---
title: Linden Specification Version 0.2.0
weight: 10
---

# Linden Notes Specification 0.2.0

The official Lindex Notes Specification.


## Application Setups

A complete Linden Notes setup works like a good notetaking app and relational
database. This can be achieved by seperated components or using one complete
application.

### Separate Linden Components

If you use separate compontents you need to configure them so they can work
together. You need the following Linden components.

- Indexer
- Navigator
- Markdown Editor with Linden add-on's

A typical setup with compononent is a Desktop programming editor with a Linden
Plugin installed and configured to work with a headless Linden indexer.

### Monolith Application

If you have a monolith application all components are build in. A typical
monolith application would be a mobile Linden Note app.

## Directories

There are two main directories.

### Root Directory

A Linden system has a root directory where the permanent content and
configurations are stored. Linden apps need to know where this directory is
located.

#### Back-up
The root directory should be part of your back-up.

#### Synchronize
You can synchronize the root directory to use your database on more then one
machine with diffent Linden Clients. Linden Navigator and Indexer can use your
database as long as this directory is available.

#### Linden FileSystem

Inside the root directory is the Linden database filesystem. Directory names
can not be changed. A minimal filesystem looks like this:

/config (here are all configuration files stored)
/wiki (here are all markdown files stored)

### The Index Directory

If you use a stand alone Linden Indexer all Linden components need to know
where the directory with index files is located. 

It's recommended to have the index directory outside the root directory. These
files are constantly regerated, which causes performance problems when using a
sync service or back-up application.

You do not need to backup the index directory.

## Files

### Config Files in /linden-root/wikiConfig

There are three types of Linden Config Files.

| config file                       | description            | mandatory |
|-----------------------------------|------------------------|-----------|
| L1-CONF-TAX-#{tax}.yml            | taxonomy configuration | no        |
| L2-CONF-TAX-#{tax}-TRM-{term}.yml | term configuration     | no        |

#### L1-CONF-TAX-#{tax}.yml

A L1-CONF file is optional. It's a yaml-file that configures one or more views
when showing a taxonomy with it's terms.

##### L1-CONF-TAX Options

| key path       | yaml-type          | description                                                        | mandatory                   | default      |
|----------------|--------------------|--------------------------------------------------------------------|-----------------------------|--------------|
| starred        | boolean            | The singular name of a taxonomy                                    | no                          | taxonony key |
| plural         | string             | The plural name of a taxonomy                                      | no                          | null         |
| description    | string             | Taxonomy description                                               | no                          | null         |
| views          | hash               | containing one or more views                                       | no                          | null         |
| views/group_by | string             | groups all terms by a scalar value in term conf                    | no                          | null         |
| views/only     | array with scalars | only show terms having these scalars or IS_SET or IS_NOT_SET       | no                          | null         |
| views/except   | array with scalars | exclude showing terms having these scalars or IS_SET or IS_NOT_SET | no                          | null         |
| views/sort     | string             | can be: date, az, yaml_key                                         | no                          | null         |
| views/sort_key | string             | if sort = yaml_key, this is the key in l2_conf used for sorting    | yes if sort=frontmatter_key | null         |

##### Example of L1-CONF-TAX-project.yml

Here's an example L1-configuration:

```yaml

---
starred: true
plural: projects
description: Projects private and commercial
views:
  by_type:
    group_by: type
    only:
    - type: IS_SET
    except:
    - archived: true
  private:
    only:
    - type: private
    except:
    - archived: true
  commercial:
    only:
    - type: commercial
    except:
    - archived: true
  archived:
    only:
      - archived: true
```

#### L2-CONF-TAX-#{taxonomy}-TRM-#{term}.yml

A L2-CONF file is optional. It's a yaml-file that configures one or more views, and external locations.
when showing a term with it's values, which are markdown files.

##### L2-CONF-TAX-#{taxonomy}-TRM-#{term}.yml Options

| key path                  | yaml-type          | description                                                        | mandatory                   | default  |
|---------------------------|--------------------|--------------------------------------------------------------------|-----------------------------|----------|
| title                     | string             | The name of a term                                                 | no                          | term key |
| description               | string             | Taxonomy description                                               | no                          | null     |
| starred                   | boolean            | Make this term starred                                             | no                          | false    |
| views                     | hash               | containing one or more views                                       | no                          | null     |
| views/[view_key]/group_by | string             | groups all terms by a scalar value in term conf                    | no                          | null     |
| views/[view_key]/only     | array with scalars | only show terms having these scalars or IS_SET or IS_NOT_SET       | no                          | null     |
| views/[view_key]/except   | array with scalars | exclude showing terms having these scalars or IS_SET or IS_NOT_SET | no                          | null     |
| views/[view_key]/sort     | string             | can be: date, az, frontmatter_key                                  | no                          | null     |
| views/[view_key]/sort_key | string             | if sort = frontmatter_key, this is the key used for sorting        | yes if sort=frontmatter_key | null     |
| locations                 | hash               | containing one or more locations                                   | no                          | null     |
| locations/[location_key]  | string             | URI of the external location, file, dir of webaddress              | no                          | null     |

##### Example of L2-CONF_TAX_project_TRM_linden.yml

Here's an example L2-configuration:

```yaml

---
title: Linden
infotext: The Linden Project
starred: true
locations:
  Linden Spec Repo: file:///Users/mipmip/dev/linden-spec
  gh.com/mipmip/linny.vim: https://github.com/mipmip/linny.vim
  gh.com/mipmip/lindex: https://github.com/mipmip/lindex
type: Software Project
views:
  type:
    group_by: type
    except:
    - archived: true
    - trash: true
  deelpr:
    group_by: sub_project
    except:
      - archived: true
  arch:
    only:
      - archived: true
  man-nl:
    only:
      - sub_project: Linny.vim Handleiding Nederlands
    group_by: hoofdstuk
    sort: frontmatter_key
    sort_key: sortnum
  man-en:
    only:
      - sub_project: Linny.vim Manual Enlish
    group_by: paragraph
    sort: frontmatter_key
    sort_key: sortnum
```

### Markdown files in /linden-root/wiki

All mardown files are stored in the /wiki subdirectory.

### temporary Index Files in de index directory

| index file                                  | datatype             | description                                           | status      |
|---------------------------------------------|----------------------|-------------------------------------------------------|-------------|
| `_index_taxonomies.json`                    | array(string)        | all taxonomies index keys                             |             |
| `_index_docs_starred.json`                  | array(string)        | all starred documents                                 |             |
| `_index_docs_with_props.json`               | hash(string, hash)   | all documents and their properties                    |             |
| `_index_docs_tasks.json`                    | hash(string, hash)   | documents with amounts of open/closed/total tasks     |             |
| `_index_docs_with_title.json`               |                      | all documents and their titles                        | depreciated |
| `_index_terms_starred.json`                 |                      | all starred terms                                     |             |
| `_indexer_info.json`                        | hash(string, string) | meta info about the indexer                           |             |
| `L1-INDEX-TAX-#{taxonomy}.json`             | hash(string, hash)   | hash with names of terms and their properties as hash |             |
| `L2-INDEX-TAX-#{taxonomy}-TRM-#{term}.json` | array(string)        | array with filenames of member documents in this term |             |


## Version History

### 0.1.1

Initial draft.

### 0.1.2

- All index file names added.
- All conf file names added.
- All conf options added.

### 0.2.0

- Removed L0 configuration
- add starred to L1 config file
