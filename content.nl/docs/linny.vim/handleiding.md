---
title: Linny Vim Handleiding
project: linden
deelproject: Linny.vim Handleiding
type: documentatie
---

# Over deze handleiding

Deze handleiding is de officiële handleiding van Linny Vim. Linny Vim is op het
moment van schrijven zeer actief in ontwikkeling. Deze handleiding tracht alle
officiële functies te documenteren en mee te evalueren bij wijzigingen.

# Wat is Linny & Linny Vim

Linny is een persoonlijk project dat als doel heeft het ideale persoonlijk
documentatie systeem te zijn voor alles, maar dan ook alles.

Technisch gezien is Linny een relationele documenten database. De records van
de database zijn Markdown-bestanden. De relaties tussen de records worden
gelegd met YAML-velden in de Front Matter aan het begin van het Markdown-bestand.

Linny Vim is een Vim-plugin en is momenteel de belangrijkste interface van de
Linny Database. Met Linny Vim kunnen Linny-documenten worden gemaakt, bewerkt en
verwijderd. Daarnaast zorgt Linny Vim voor een een groot aantal functies die
helpen met navigeren, zoeken, het leggen van relaties tussen bestanden en het
configureren van het Linny datamodel.

# Termologie

# Linny Directories

- [[SHELL open ~/.linny_index_files]] - Directory met tijdelijke indexbestanden
- [[SHELL open ~/.linny]] - Directory met overkoepelende Linny configuratie voor deze computer
- [[SHELL open `ruby -rjson -ryaml -e "puts File.expand_path( YAML.load_file(File.expand_path('~/.linny/linny.yml'))['root_path'])"`]] - Stamdirectory met de Linny-data
- [[SHELL open `ruby -rjson -ryaml -e "puts File.expand_path( YAML.load_file(File.expand_path('~/.linny/linny.yml'))['root_path'])"`/wiki]] - Directory met de Linny-markdown-bestanden
- [[SHELL open `ruby -rjson -ryaml -e "puts File.expand_path( YAML.load_file(File.expand_path('~/.linny/linny.yml'))['root_path'])"`/wiki/ARCHIVE]] - Directory met de Linny-markdown-bestanden in ARCHIEF
- [[SHELL open `ruby -rjson -ryaml -e "puts File.expand_path( YAML.load_file(File.expand_path('~/.linny/linny.yml'))['root_path'])"`/wiki/TRASH]] - Directory met de Linny-markdown-bestanden in TRASH
- [[SHELL open `ruby -rjson -ryaml -e "puts File.expand_path( YAML.load_file(File.expand_path('~/.linny/linny.yml'))['root_path'])"`/config]] - Directory met de Linny-config-bestanden voor de 3e niveau's weergaven

# Configuratie Linny Vim

# Configuratie Linny Index

# Configuratie Leafs

```yaml
starred: true
config: true
infotext: Webteksten per onderdeel
frontmatter_template:
  onderwerp: marketing
  project: website lingewoud 2019
  type: webtekst
group_by: onderdeel
locations:
  projectmap: file:///Users/pim/Sys/linny-projects-dirs/website Laurens de Groot
  website: https://website.nl
```

# Uitbreiding van de Markdown syntax


