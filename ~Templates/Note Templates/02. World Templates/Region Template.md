---
--INFOBOX--: --
regPronounce:
regFactions:
regAliases:
regPop:
regLanguages:
regBiomes:
regLandmarks:
--QUICK INFO--: --
regOverview:
regChars:
regResources:
--TECHNICAL--: --
obsidianUIMode: preview
gallery: []
regImage: ~Assets/Image Assets/placeholder.png
editTime:
---
#Region
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Regions Dashboard]]**\n";
    }    
    tR += last_file  ;
_%>

> [!infobox] Region
> # Region
> ### `=this.file.name`
> **Pronounced:**  "`=this.regPronounce`"
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):regImage]`
> ###### Basic Information
>  |
> ---|---|
> **Factions Within** | `=this.regFactions` |
> **Aliases** | `=this.regAliases` |
> **Population** | `=this.regPop` |
> **Languages** | `=this.regLanguages` |
> **Biomes** | `=this.regBiomes` |
> **Key Locations** | `=this.regLandmarks` |

# `=this.file.name`
> [!info-overview]- Overview
> `=this.regOverview`

> [!character]- Characters
> `=this.regChars`

> [!shop]- Resources
> `=this.regResources`

## History

## Sub-regions

## Key Locations & Landmarks

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
