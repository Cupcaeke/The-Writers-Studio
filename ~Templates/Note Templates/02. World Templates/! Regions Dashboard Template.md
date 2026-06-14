---
--TECHNICAL--: --
fileType: dashboard
dashThumbnail: ~Assets/Image Assets/regions-thumb.jpg
gallery:
obsidianUIMode: preview
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# Overview
> [!column|2 ttl-c nmg s-mg no-i bg-black c-pink txt-c] NOTE: this adds populations from **ALL REGION FILES**. Might be inaccurate if you have subregions
> > [!example|bg-purple c-purple embed] Total Population
> > ```dataviewjs
> > // SUM POP IN ALL REGIONS
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.regPop);
> > const regPop = pages
> >     .map(p => p.regPop)
> >     .sum();
> > 
> > dv.header(1,regPop);
> > ```
> 
> > [!example|bg-purple c-purple embed] Highest Populations
> >```dataview
> > TABLE regPop as "Population"
> > FROM "<% tp.file.folder(true) %>"
> > WHERE regPop
> > SORT regpop DESC
> > LIMIT 3
> > ```
# Regions Database
- **NOTE: Subfolders for subregions must be created manually, as well as moving documents to those folders**
```meta-bind-button
label: + New Landmass Region
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NLR"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/02. World Templates/Region Template.md
    folderPath: <% tp.file.folder(true) %>/Landmasses
    fileName: Landmass
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Island Region
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NIR"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/02. World Templates/Region Template.md
    folderPath: <% tp.file.folder(true) %>/Islands
    fileName: Island
    openNote: true
    openIfAlreadyExists: false
```
`BUTTON[NLR]` `BUTTON[NIR]`
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - '!file.name.endsWith(".canvas")'
    - '!file.name.contains("Dashboard")'
formulas:
  Subfolder: file.folder.replace(/([^]*)\//,"")
properties:
views:
  - type: cards
    name: Cards
    order:
      - file.name
      - formula.Subfolder
    sort:
      - property: file.folder
        direction: ASC
    image: note.regImage
    cardSize: 175

```
# Maps / Gallery
```meta-bind
INPUT[imageListSuggester(optionQuery("~Assets/Image Assets")):gallery]
```
# Tasks
> [!warning|no-t] Tasks
> ```dataview
> TASK 
> FROM "<% tp.file.folder(true) %>"
> GROUP BY file.link
> ```
```meta-bind-button
label: + New Task
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: ""
hidden: false
actions:
  - type: insertIntoNote
    line: selfEnd + 2
    value: "[[New Task]]"
    templater: true

```
---
<%* let path = tp.file.folder(true) %>
<%* await tp.app.vault.createFolder(path + "/Landmasses") %>
<%* await tp.app.vault.createFolder(path + "/Islands") %>