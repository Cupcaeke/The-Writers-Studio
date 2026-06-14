---
--INFOBOX--: --
objType:
objPronounce:
objAliases:
objOrigin:
objPossession:
objEffects:
--QUICK INFO--: --
objOverview:
--TECHNICAL--: --
objImage: ~Assets/Image Assets/placeholder.png
gallery:
obsidianUIMode: preview
editTime:
---
#Item
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Items Dashboard]]**\n";
    }    
    tR += last_file  ;
_%>

> [!infobox] Object
> # Item/Artifact
> ### `=this.file.name`
> **Pronounced:**  "`=this.objPronounce`"
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):objImage]`
> ###### Basic Information
>  |
> ---|---|
> **Aliases** | `=this.objAliases` |
> **Type** | `=this.objType` |
> **Origin/Creator** | `=this.objOrigin` |
> **Owner(s)** | `=this.objPossession` |
> **Effects/Purpose** | `=this.objEffects` |
# `=this.file.name`

> [!info-overview]+ Overview
> `=this.objOverview`
## Effects/Usage

## History

## Trivia

## Image Gallery
```meta-bind
INPUT[imageListSuggester(optionQuery("~Assets/Image Assets")):gallery]
```
## Tasks
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
