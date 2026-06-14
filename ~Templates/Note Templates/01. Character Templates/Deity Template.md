---
--INFOBOX--: --
godPronounce:
godPronouns:
godType:
godAliases:
godProvince:
godSymbols:
godReligions:
godHoliday:
--QUICK INFO--: --
godOverview:
godIdeals:
godAppear:
--TECHNICAL--: --
chaImage: ~Assets/Image Assets/placeholder.png
obsidianUIMode: preview
gallery:
editTime:
---
#Character #Deity
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Characters Dashboard]]**\n";
    }    
    tR += last_file  ;
_%>

> [!infobox] Deity
> # Deity
> ### `=this.file.name`
> **Pronounced:**  "`=this.godPronounce`"
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):chaImage]`
> ###### Basic Information
>  |
> ---|---|
> **Pronouns** | `=this.godPronouns` |
> **Type** | `=this.godType` |
> **Aliases** | `=this.godAliases` |
> **Province** | `=this.godProvince` |
> **Symbols** | `=this.godSymbols` |
> **Associated Religions** | `=this.godReligions` |
> **Holy Day** | `=this.godHoliday` |
# `=this.file.name`
> [!info-overview]- Overview
> `=this.godOverview`

> [!location]- Ideals
> `=this.godIdeals`

> [!character]- Appearance / Aesthetics
> `=this.godAppear`

## Commandments
### Commandment
## Relationships
## History
## Religious Sects
### Religion Relation

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
