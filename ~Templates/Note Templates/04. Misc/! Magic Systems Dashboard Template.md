---
--TECHNICAL--: --
fileType: dashboard
obsidianUIMode: preview
dashThumbnail: ~Assets/Image Assets/magic-thumb.jpg
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# Magic System Database
```meta-bind-button
label: + New Note
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
    templateFile: ~Templates/Note Templates/04. Misc/Magic Note Template.md
    folderPath: <% tp.file.folder(true) %>
    fileName: Magic Note
    openNote: true
    openIfAlreadyExists: false

```
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - fileType != "dashboard"
formulas:
  Subfolder: if(file.folder.replace(/([^]*)\//,"").startsWith("Magic System"),"",file.folder.replace(/([^]*)\//,""))
views:
  - type: table
    name: Table
    groupBy:
      property: formula.Subfolder
      direction: ASC
    order:
      - file.name
      - formula.Subfolder
      - file.tags
    sort:
      - property: file.tags
        direction: ASC
    indentProperties: false

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
