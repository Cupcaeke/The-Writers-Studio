---
--TECHNICAL--: --
fileType: dashboard
dashThumbnail: ~Assets/Image Assets/characters-thumb.jpg
obsidianUIMode: preview
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# Character Database
```meta-bind-button
label: + New Major Character
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NMaC"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/01. Character Templates/Major Character Template.md
    folderPath: <% tp.file.folder(true) %>/Major Characters
    fileName: Major Character
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Minor Character
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NMiC"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/01. Character Templates/Minor Character Template.md
    folderPath: <% tp.file.folder(true) %>/Minor Characters
    fileName: Minor Character
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Deity
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NDe"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/01. Character Templates/Deity Template.md
    folderPath: <% tp.file.folder(true) %>/Deities
    fileName: Deity
    openNote: true
    openIfAlreadyExists: false
```
`BUTTON[NMaC]` `BUTTON[NMiC]` `BUTTON[NDe]`
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - '!file.name.endsWith(".canvas")'
    - fileType != "dashboard"
formulas:
  Untitled: if(file.inFolder("<% tp.file.folder(true) %>/Deities"),"✪ Deity",if(file.inFolder("<% tp.file.folder(true) %>/Major Characters"),"✦ Major Character",if(file.inFolder("<% tp.file.folder(true) %>/Minor Characters"),"✧ Minor Character")))
properties:
  formula.Untitled:
    displayName: Type
views:
  - type: cards
    name: Cards
    order:
      - file.name
      - formula.Untitled
    sort: []
    image: note.chaImage
    cardSize: 175

```

> [!column|3 ttl-c nmg s-mg no-i bg-black c-pink embed] By Type
> > [!kith|bg-gray c-red] Major Characters
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Major Characters"
> > SORT file.name ASC
> > ```
> 
> > [!kith|bg-gray c-blue embed] Minor Characters
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Minor Characters"
> > SORT file.name ASC
> > ```
> 
> > [!kith|bg-gray c-yellow embed] Deities
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Deities"
> > SORT file.name ASC
> > ```
# Relationship Webs
- **NOTE: Canvases must be created manually. To create a new canvas, right click on the "Relationship Webs" subfolder of the current project and click "New Canvas"**
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>/Relationship Webs")
views:
  - type: cards
    name: Cards
    order:
      - file.basename
      - file.backlinks
    cardSize: 150
    imageAspectRatio: 2.5

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
<%* await tp.app.vault.createFolder(path + "/Major Characters") %>
<%* await tp.app.vault.createFolder(path + "/Minor Characters") %>
<%* await tp.app.vault.createFolder(path + "/Deities") %>
<%* await tp.app.vault.createFolder(path + "/Relationship Webs") %>