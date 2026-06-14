---
--TECHNICAL--: --
fileType: dashboard
obsidianUIMode: preview
editTime:
dashThumbnail: ~Assets/Image Assets/items-thumb.jpg
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# At A Glance
```dataview
TABLE 
    length(rows) as "Count",
	join(rows.file.link, ", ") as "Items"
FROM "<% tp.file.folder(true) %>"
WHERE 
    objType
FLATTEN
    objType
GROUP BY
    join(objType, ", ") as "Type"
```
# Items Database
```meta-bind-button
label: + New Item/Artifact
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: ""
hidden: false
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/04. Misc/Item Template.md
    folderPath: <% tp.file.folder(true) %>
    fileName: Item
    openNote: true
    openIfAlreadyExists: false
```
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - '!file.name.endsWith(".canvas")'
    - '!file.name.contains("Dashboard")'
properties:
  note.objType:
    displayName: Type
views:
  - type: cards
    name: Cards
    order:
      - file.name
      - objType
    sort:
      - property: objType
        direction: ASC
    image: note.objImage
    cardSize: 175

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
