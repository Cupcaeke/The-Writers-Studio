---
--DESCRIPTION--: --
arcDesc:
--TECHNICAL--: --
obsidianUIMode: preview
fileType: overview
arcAct:
arcTen:
secTot:
editTime:
---
#Arc
**[[<% tp.file.folder(true).split("/")[0] %>/Plotting/Arcs/Arcs Dashboard|❮❮ Return to Arcs Dashboard]]**
# `=this.file.name`

> [!info-overview]+ Description
> `=this.arcDesc`
# At A Glance
> [!column|no-t collapse]
> > [!info|ttl-c collapse] Characters
> > ```dataview
> > TABLE 
> >     length(rows) as "Appearances",
> > 	join(rows.file.link, ", ") as "Notes"
> > FROM "<% tp.file.folder(true) %>"
> > WHERE 
> >     characters
> > FLATTEN
> >     characters
> > GROUP BY
> >     join(characters, ", ") as "Characters"
> > ```
> 
> > [!note|ttl-c collapse] Section Variance
> > ```dataview
> > TABLE 
> >     length(rows) as "Instances",
> > 	join(rows.file.link, ", ") as "Notes"
> > FROM "<% tp.file.folder(true) %>"
> > WHERE 
> >     conflictLabel
> > FLATTEN
> >     conflictLabel
> > GROUP BY
> >     join(conflictLabel, ", ") as "Conflict"
> > ```
---
> [!column|2 ttl-c nmg s-mg no-i bg-black c-pink txt-c] Intensity
> > [!tip|bg-gray c-red embed] Arc Activity
> > ```dataviewjs
> > // CALL METAEDIT API
> > const {update} = this.app.plugins.plugins["metaedit"].api;
> > 
> > // MAXIMUM POTENTIAL ACTIVITY
> > let actMax = (dv.pages('"<% tp.file.folder(true) %>/Sections"').length) * 10;
> > 
> > // SUM SECTION ACTIVITY
> > const pages = dv.pages('"<% tp.file.folder(true) %>/Sections"')
> >     .where(p => p.secAct);
> > const actTot = pages
> >     .map(p => p.secAct)
> >     .sum();
> > 
> > // PERCENT
> > let actPercent = (actTot/actMax)*100;
> > actPercent = Math.round(actPercent);
> > 
> > // UPDATE & DISPLAY
> > update("arcAct", actPercent, "<% tp.file.path(true) %>");
> > dv.header(5, actPercent + "%");
> > ```
> 
> > [!warning|bg-gray c-yellow embed] Arc Tension
> > ```dataviewjs
> > // CALL METAEDIT API
> > const {update} = this.app.plugins.plugins["metaedit"].api;
> > 
> > // MAXIMUM POTENTIAL ACTIVITY
> > let tenMax = (dv.pages('"<% tp.file.folder(true) %>/Sections"').length) * 10;
> > 
> > // SUM SECTION ACTIVITY
> > const pages = dv.pages('"<% tp.file.folder(true) %>/Sections"')
> >     .where(p => p.secTen);
> > const tenTot = pages
> >     .map(p => p.secTen)
> >     .sum();
> > 
> > // PERCENT
> > let tenPercent = (tenTot/tenMax)*100;
> > tenPercent = Math.round(tenPercent);
> > 
> > // UPDATE & DISPLAY
> > update("arcTen", tenPercent, "<% tp.file.path(true) %>");
> > dv.header(5, tenPercent + "%");
> > ```
```dataviewjs
// CALL METAEDIT API
const {update} = this.app.plugins.plugins["metaedit"].api;

// UPDATE SECTION COUNT
let secCount = dv.pages('"<% tp.file.folder(true) %>/Sections"').length;
update("secTot", secCount, "<% tp.file.path(true) %>");
```
# Sections
```meta-bind-button
label: + New Section
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
    templateFile: ~Templates/Note Templates/00. Plotting Templates/Section Template.md
    folderPath: <% tp.file.folder(true) %>/Sections
    fileName: New Section
    openNote: true
    openIfAlreadyExists: false
```
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>/Sections")
properties:
  file.name:
    displayName: Section
  note.secDescription:
    displayName: Description
  note.characters:
    displayName: Characters
  note.setting:
    displayName: Setting
  note.dayStart:
    displayName: Day Starts
  note.dayEnd:
    displayName: Day Ends
  note.conflictLabel:
    displayName: Conflict Type
  note.secAct:
    displayName: Activity (0-10)
  note.secTen:
    displayName: Tension (0-10)
views:
  - type: table
    name: Table
    order:
      - file.name
      - secDescription
      - characters
      - setting
      - dayStart
      - dayEnd
      - conflictLabel
      - secAct
      - secTen
    sort:
      - property: file.name
        direction: ASC
    columnSize:
      file.name: 80
      note.secDescription: 327
      note.characters: 117
      note.dayStart: 52
      note.dayEnd: 58
      note.conflictLabel: 83
      note.secAct: 52
      note.secTen: 52
    rowHeight: medium
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
<%* await tp.app.vault.createFolder(path + "/Sections") %>