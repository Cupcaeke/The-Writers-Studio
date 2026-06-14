---
--TECHNICAL--: --
fileType: dashboard
dashThumbnail: ~Assets/Image Assets/arcs-thumb.jpg
obsidianUIMode: preview
editTime:
---
**[[<% tp.file.folder(true).split("/")[0] %>/<% tp.file.folder(true).split("/")[0] %> Masterboard|❮❮ Return to Project Masterboard]]**
# At A Glance
> [!column|3 ttl-c nmg s-mg no-i bg-black c-pink txt-c no-t]
> > [!example|bg-purple c-purple embed] Total Sections
> > ```dataviewjs
> > // SUM SECTIONS IN ALL ARCS
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.secTot);
> > const secTot = pages
> >     .map(p => p.secTot)
> >     .sum();
> > 
> > dv.header(3,secTot);
> > ```
> 
> > [!example|bg-purple c-purple embed] Avg. Sections/Arc
> > ```dataviewjs
> > // TOTAL ARCS
> > let arcTot = dv.pages('"<% tp.file.folder(true) %>"').where(p => p.fileType == "overview").length;
> > 
> > // SUM SECTIONS IN ALL ARCS
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.secTot);
> > const secTot = pages
> >     .map(p => p.secTot)
> >     .sum();
> > 
> > // AVG
> > let arcAvg = secTot/arcTot;
> > arcAvg = Math.round(arcAvg);
> > 
> > dv.header(3,arcAvg);
> > ```
> 
> > [!note|bg-green c-green embed] Longest Arc
> > ```dataview
> > TABLE secTot as "Sections"
> > FROM "<% tp.file.folder(true) %>"
> > WHERE contains(filetype, "overview")
> > SORT sectot DESC
> > LIMIT 1
> > ```
> 
> > [!tip|bg-orange c-orange embed] Overall Activity
> > ```dataviewjs
> > // MAXIMUM POTENTIAL ACTIVITY
> > let actMax = (dv.pages('"<% tp.file.folder(true) %>"').where(p => p.fileType == "overview").length) * 100;
> > 
> > // SUM SECTION ACTIVITY
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.arcAct);
> > const actTot = pages
> >     .map(p => p.arcAct)
> >     .sum();
> > 
> > // PERCENT
> > let actPercent = (actTot/actMax)*100;
> > actPercent = Math.round(actPercent);
> > 
> > dv.header(4,actPercent + "%");
> > ```
> 
> > [!tip|bg-orange c-orange embed] Overall Tension
> > ```dataviewjs
> > // MAXIMUM POTENTIAL TENSION
> > let tenMax = (dv.pages('"<% tp.file.folder(true) %>"').where(p => p.fileType == "overview").length) * 100;
> > 
> > // SUM SECTION ACTIVITY
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.arcTen);
> > const tenTot = pages
> >     .map(p => p.arcTen)
> >     .sum();
> > 
> > // PERCENT
> > let tenPercent = (tenTot/tenMax)*100;
> > tenPercent = Math.round(tenPercent);
> > 
> > dv.header(4,tenPercent + "%");
> > ```
> 
> > [!note|bg-green c-green embed] Shortest Arc
> > ```dataview
> > TABLE secTot as "Sections"
> > FROM "<% tp.file.folder(true) %>"
> > WHERE contains(filetype, "overview")
> > SORT sectot ASC
> > LIMIT 1
> > ```
# Arcs
```meta-bind-button
label: + New Arc
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
    templateFile: ~Templates/Note Templates/05. Scripts/New Arc.md

```
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>")
    - fileType == "overview"
formulas:
  Activity: arcAct + "%"
  Tension: arcTen + "%"
properties:
  file.name:
    displayName: Arc
  note.arcDesc:
    displayName: Description
  note.secTot:
    displayName: Sections
views:
  - type: table
    name: Table
    order:
      - file.name
      - arcDesc
      - formula.Activity
      - formula.Tension
      - secTot
    sort: []
    rowHeight: medium
    columnSize:
      file.name: 116
      note.arcDesc: 395
      formula.Tension: 79
      note.secTot: 79

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
