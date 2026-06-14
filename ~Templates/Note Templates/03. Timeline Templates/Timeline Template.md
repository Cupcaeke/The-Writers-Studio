---
--OVERVIEW--: --
timelineDesc:
--TECHNICAL--: --
fileType: overview
obsidianUIMode: preview
editTime:
---
#Timeline
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Timeline]]**\n";
    }    
    tR += last_file  ;
_%>

# Info
>
*`=this.timelineDesc`*
> 
### Notes

# Timeline
```meta-bind-button
label: + New Era
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NEra"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/03. Timeline Templates/Era Template.md
    folderPath: <% tp.file.folder(true) %>/Eras
    fileName: New Era
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Major Event
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NMaE"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/03. Timeline Templates/Major Event Template.md
    folderPath: <% tp.file.folder(true) %>/Events
    fileName: New Major Event
    openNote: true
    openIfAlreadyExists: false
```
```meta-bind-button
label: + New Minor Event
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: "NMiE"
hidden: true
actions:
  - type: templaterCreateNote
    templateFile: ~Templates/Note Templates/03. Timeline Templates/Minor Event Template.md
    folderPath: <% tp.file.folder(true) %>/Events
    fileName: New Minor Event
    openNote: true
    openIfAlreadyExists: false
```
`BUTTON[NEra]` `BUTTON[NMaE]` `BUTTON[NMiE]`
```aat-vertical
<% await tp.system.prompt("Please enter a timeline name (or names, separated by commas)") %>
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
<%* await tp.app.vault.createFolder(path + "/Eras") %>
<%* await tp.app.vault.createFolder(path + "/Events") %>