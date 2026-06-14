---
--QUICK INFO--: --
characters:
setting:
dayStart:
dayEnd:
secDescription:
--TECHNICAL--: --
conflictLabel:
conflictType:
secAct:
secTen:
obsidianUIMode: preview
editTime:
---
#Arc #Section
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Arc Overview]]**\n";
    }    
    tR += last_file  ;
_%>

# `=this.file.name`

> [!info-overview]+ Description
> `=this.secDescription`
### Duration
**Days:** `=this.dayStart`-`=this.dayEnd`
**Detailed Times:** 

### Conflict Type
`BUTTON[act-con]` `BUTTON[dec-con]` `BUTTON[enc-con]` `BUTTON[exp-con]` `BUTTON[fig-con]` `BUTTON[inv-con]` `BUTTON[pre-con]`
> *High level profile of the driving conflict in a section.*
`VIEW[{conflictType}][text(renderMarkdown)]`
### Intensity Levels
> [!warning|collapse] ---Activity---
> *How much movement happens within the section. This is how "dense" or "packed" a section is. Higher activity will typically have shorter durations.*
> >```meta-bind
> > INPUT[progressBar(minValue(0),maxValue(10)):secAct]
> > ```

> [!danger|collapse] ---Tension---
> *How high the stakes are in this section. The outcome serves as a great boon/loss prevention for the winning parties and a great loss for the losers.*
> >```meta-bind
> > INPUT[progressBar(minValue(0),maxValue(10)):secTen]
> > ```
## Scenes

## Quotes
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
