---
--TECHNICAL--: --
fileType: dashboard
dashThumbnail: ~Assets/Image Assets/timeline-thumb.jpg
obsidianUIMode: preview
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# At a Glance
> [!column|3 ttl-c s-mg no-i bg-black c-pink txt-c no-t]
> > [!example|bg-yellow c-yellow embed] Total Timelines
> > ```dataviewjs
> > // SUM EVENTS
> > let timelineTot = dv.pages('"<% tp.file.folder(true) %>"').where(p => p.fileType == "overview").length;
> > 
> > dv.header(3,timelineTot);
> > ```
> 
> > [!example|bg-yellow c-yellow embed] Total Events
> > ```dataviewjs
> > // SUM EVENTS
> > let eventTot = dv.pages('"<% tp.file.folder(true) %>"').where(p => !p.fileType).length;
> > 
> > dv.header(3,eventTot);
> > ```
> 
> > [!example|bg-yellow c-yellow embed] Avg. Events/Timeline
> > ```dataviewjs
> > // TOTAL TIMELINES
> > let timelineTot = dv.pages('"<% tp.file.folder(true) %>"').where(p => p.fileType == "overview").length;
> > 
> > // SUM SECTIONS IN ALL ARCS
> > let eventTot = dv.pages('"<% tp.file.folder(true) %>"').where(p => !p.fileType).length;
> > 
> > // AVG
> > let eventAvg = eventTot/timelineTot;
> > eventAvg = Math.round(eventAvg);
> > 
> > dv.header(3,eventAvg);
> > ```
# Timeline Database
```meta-bind-button
label: + New Timeline
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: ""
hidden: false
actions:
  - type: runTemplaterFile
    templateFile: ~Templates/Note Templates/05. Scripts/New Timeline.md

```
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - fileType == "overview"
properties:
  note.timelineDesc:
    displayName: Description
views:
  - type: cards
    name: Cards
    order:
      - file.name
      - timelineDesc
    sort: []
    indentProperties: true

```
# Master Timeline
> [!metadata|txt-s wsmall subt]- *List Timeline Keys*
> ```dataview
> LIST 
> FROM "<% tp.file.folder(true) %>"
> WHERE aat-timelines
> SORT aat-timelines ASC
> GROUP BY aat-timelines
> ```
```meta-bind-button
label: Master Timeline Settings
icon: ""
style: default
class: ""
cssStyle: ""
backgroundImage: ""
tooltip: ""
id: ""
hidden: false
actions:
  - type: replaceInNote
    fromLine: 103
    toLine: 103
    replacement: "~Templates/Note Templates/05. Scripts/Master Timeline Settings.md"
    templater: true

```
```aat-vertical

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
