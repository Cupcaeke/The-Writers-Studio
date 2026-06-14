---
--TIMELINE--: For dates, default format is  "YEAR-SEASON(0-4)-DAY"
aat-timelines:
aat-event-start: 0-0-0
aat-event-end: 0-0-0
aat-event-body:
--INFOBOX--: Input as seen within note
eraAKA:
eraStart:
eraEnd:
eraOutcome:
eraLocation:
eraParticipants:
--TECHNICAL--: --
aat-render-enabled: true
obsidianUIMode: preview
gallery: []
eraImage: ~Assets/Image Assets/placeholder.png
editTime:
---
#Timeline #Era
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

> [!infobox] Era
> # Era
> ### `=this.file.name`
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):eraImage]`
> ###### Basic Information
>  |
> ---|---|
> **Other Names** | `=this.eraAKA` |
> **Began** | `=this.eraStart` |
> **Ended** | `=this.eraEnd` |
> **Outcome** | `=this.eraOutcome` |
> **Location** | `=this.eraLocation` |
> **Participants** | `=this.eraParticipants` |
# **`=this.file.name`**
*`=this.aat-event-body`*
## Full Description


### Early `=this.file.name`

### Middle `=this.file.name`

### Late `=this.file.name`

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
