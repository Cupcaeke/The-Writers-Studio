---
--DESCRIPTION--: --
projElevatorPitch:
projSummary:
projType:
projSynopsis:
--TECHNICAL--: --
obsidianUIMode: preview
fileType: masterboard
banner: ~Assets/Image Assets/placeholder.png
fcount:
editTime:
---
**[[Home|❮❮ Return to Homepage]]**
# `=this.file.name`
> [!info|txt-s wsmall subt]- *Select Cover Image*
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):banner]`

> [!info-overview]+ Summary & Description
> **Elevator Pitch:**
> `=this.projElevatorPitch`
> 
> **Summary/Teaser:**
> `=this.projSummary`
> 
> **Project Type:**
> `=this.projType`

> [!info-overview]+ Synopsis
> `=this.projSynopsis`
# At A Glance
> [!column|3 ttl-c nmg s-mg no-i bg-black c-pink txt-c no-t]
> > [!example|bg-red c-red embed] Total Project Files
> > ```dataviewjs
> > // CALL METAEDIT API
> > const {update} = this.app.plugins.plugins["metaedit"].api;
> > 
> > // TOTAL FILES IN PROJECT
> > let fileCount = dv.pages('"<% tp.file.folder(true) %>"').length;
> > dv.header(4, fileCount + " files");
> > update("fcount", fileCount, "<% tp.file.path(true) %>");
> > ```
> 
> > [!example|bg-orange c-orange embed] Creation Date
> > ⠀
> > #### `=this.file.cday` 
> 
> > [!example|bg-yellow c-yellow embed] Total Worktime
> > ```dataviewjs
> > // SUM TIME WORKED
> > const pages = dv.pages('"<% tp.file.folder(true) %>"')
> >     .where(p => p.editTime);
> > const hoursWork = pages
> >     .map(p => p.editTime)
> >     .sum() / 3600;
> > dv.header(4, hoursWork + "hrs");
> > ```
---
> [!metadata|ttl-c nmg s-mg bg-blue c-blue txt-c embed] Recently Modified
>```dataview
>TABLE file.mtime AS "Last Modified"
>FROM "<% tp.file.folder(true) %>"
>SORT file.mtime DESC
>LIMIT 3
>```
# Plotting
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>/Plotting")
    - fileType == "dashboard"
views:
  - type: cards
    name: Cards
    order:
      - file.name
    cardSize: 400
    image: note.dashThumbnail
    imageAspectRatio: 0.4

```

> [!warning|ttl-c no-i txt-s] **Plotting Tasks**
> ```dataview
> TASK 
> FROM "<% tp.file.folder(true) %>/Plotting"
> GROUP BY file.link
> ```
# Wiki
```base
filters:
  and:
    - file.inFolder("<% tp.file.folder(true) %>/Wiki")
    - fileType == "dashboard"
views:
  - type: cards
    name: Cards
    order:
      - file.name
    cardSize: 260
    image: note.dashThumbnail
    imageAspectRatio: 0.4

```

> [!warning|ttl-c no-i txt-s] **Worldbuilding Tasks**
> ```dataview
> TASK 
> FROM "<% tp.file.folder(true) %>/Wiki"
> GROUP BY file.link
> ```
# Tasks
> [!metadata|bg-pink no-t]
> ```dataview
> TASK 
> FROM "<% tp.file.folder(true) %>"
> GROUP BY (file.folder + "/" + file.link)
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
