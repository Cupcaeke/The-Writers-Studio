---
--TECHNICAL--: --
fileType: dashboard
dashThumbnail: ~Assets/Image Assets/fac-thumb.webp
obsidianUIMode: preview
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# Factions Database
```meta-bind-button
label: + New City
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NCity"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/02. World Templates/Faction Template.md
    folderPath: <% tp.file.folder(true) %>/Cities
    fileName: City
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Organization
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NOrg"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/02. World Templates/Faction Template.md
    folderPath: <% tp.file.folder(true) %>/Organizations
    fileName: Organization
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Religion
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NRel"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/02. World Templates/Faction Template.md
    folderPath: <% tp.file.folder(true) %>/Religions
    fileName: Religion
    openNote: true
    openIfAlreadyExists: false
```
`BUTTON[NCity]` `BUTTON[NOrg]` `BUTTON[NRel]`
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - '!file.name.endsWith(".canvas")'
    - '!file.name.contains("Dashboard")'
formulas:
  Untitled: if(file.inFolder("<% tp.file.folder(true) %>/Cities"),"⌂ City",if(file.inFolder("<% tp.file.folder(true) %>/Organizations"),"∴ Organization",if(file.inFolder("<% tp.file.folder(true) %>/Religions"),"灵 Religion")))
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
    image: note.facImage
    cardSize: 175

```

> [!column|3 ttl-c nmg s-mg no-i bg-black c-pink embed] By Type
> > [!metadata|bg-gray c-yellow] Cities
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Cities"
> > SORT file.name ASC
> > ```
> 
> > [!metadata|bg-gray c-red embed] Organizations
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Organizations"
> > SORT file.name ASC
> > ```
> 
> > [!metadata|bg-gray c-purple embed] Religions
> > ```dataview
> > LIST
> > FROM "<% tp.file.folder(true) %>/Religions"
> > SORT file.name ASC
> > ```
# Affinity Webs
- **NOTE: Canvases must be created manually. To create a new canvas, right click on the "Relationship Webs" subfolder of the current project and click "New Canvas"**
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>/Affinity Webs")
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
<%* await tp.app.vault.createFolder(path + "/Cities") %>
<%* await tp.app.vault.createFolder(path + "/Organizations") %>
<%* await tp.app.vault.createFolder(path + "/Religions") %>
<%* await tp.app.vault.createFolder(path + "/Affinity Webs") %>