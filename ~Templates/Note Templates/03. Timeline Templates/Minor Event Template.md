---
--TIMELINE--: For dates, default format is  "YEAR-SEASON(0-4)-DAY"
aat-timelines:
aat-event-start: 0-0-0
aat-event-end: 0-0-0
aat-event-body:
--INFOBOX--: Input as seen within note
eveAKA:
eveStart:
eveEnd:
eveOutcome:
eveLocation:
eveParticipants:
--TECHNICAL--: --
aat-render-enabled: true
obsidianUIMode: preview
gallery: []
eveImage:
facImage: ~Assets/Image Assets/placeholder.png
editTime:
---
#Timeline #Event #Minor-Event
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

> [!infobox] Minor Event
> # Minor Event
> ### `=this.file.name`
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):facImage]`
> ###### Basic Information
>  |
> ---|---|
> **Other Names** | `=this.eveAKA` |
> **Began** | `=this.eveStart` |
> **Ended** | `=this.eveEnd` |
> **Outcome** | `=this.eveOutcome` |
> **Location** | `=this.eveLocation` |
> **Participants** | `=this.eveParticipants` |
# **`=this.file.name`**
*`=this.aat-event-body`*
## Full Description


### Cultural Impact

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
