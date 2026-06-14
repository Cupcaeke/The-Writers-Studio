---
--INFOBOX--: ---
facPronounce:
facPop:
facAliases:
facLocation:
facBeliefs:
facLanguages:
facSubgroups:
facType:
--QUICK INFO--: ---
facOverview:
facLocations:
facLandmarks:
facShops:
facChars:
facAffinityWeb: "![[placeholder]]"
--TECHNICAL--: --
facImage: ~Assets/Image Assets/placeholder.png
obsidianUIMode: preview
gallery: []
editTime:
---
#Faction
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Factions Dashboard]]**\n";
    }    
    tR += last_file  ;
_%>

> [!infobox] Faction
> # Faction
> ### `=this.file.name`
> **Pronounced:**  "`=this.facPronounce`"
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):facImage]`
> ###### Basic Information
>  |
> ---|---|
> **Population** | `=this.facPop` |
> **Aliases** | `=this.facAliases` |
> **Languages** | `=this.facLanguages` |
> **Location** | `=this.facLocation` |
> **Belief System** | `=this.facBeliefs` |
> **Subgroups** | `=this.facSubgroups` |
> **Type** | `=this.facType` |

# **`=this.file.name`**
> [!info-overview]- Overview
> `=this.facOverview`

> [!location]- Locations
> `=this.facLocations`

> [!landmark]- Landmarks
> `=this.facLandmarks`

> [!shop]- Shops
> `=this.facShops`

> [!character]- Characters
> `=this.facChars`

## Culture
### Mission


### Conduct & Customs


### Recruitment & Training


### Ranks & Family Structure


### Uniforms, Equipment, and Appearances


## Acquaintances
> [!info|nmg ttl-c txt-c]- Affinity Web
> `=this.facAffinityWeb`
### Allies:


### Rivals:


### Contacts:


## History


## Notes

### General Notes

### Economy and Resources

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