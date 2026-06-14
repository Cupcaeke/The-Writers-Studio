---
--TECHNICAL--: --
banner: ~Assets/Image Assets/homepage-thumb.jpg
obsidianUIMode: preview
editTime:
---
> [!faq]- Help | FAQ | User Manual
> **Welcome to the Writer's Studio. Here, you can track and plan all your stories and worlds with ease.**
> ## What is this?
> - This Obsidian vault is a tool for writers to help plan and manage all of their major projects. It was made lovingly by **[Cupcaeke](https://cupcaeke.carrd.co)** over many months of finishing their Creative Writing degree. She wanted something free and easy to use that would work with her more loose workflow. Click their name above to see how you can support them!
> - In the **Writer's Studio**, you can:
> 	- Develop your story section by section.
> 	- Define and plan each story arc.
> 	- Plot relevant points of history within the world/story by separated timelines, eras, and events.
> 	- Develop character pages along with their character arcs.
> 	- Develop factions and communities and their intricacies.
> 	- Showcase and track specific items and artifacts relevant to the world and story.
> 	- Build your own magic system.
> 	- Plan and worldbuild regions and locations.
> 	- Anything else you decide to add!
> ## What about drafting?
> - That one is on you! As so many people have such different drafting processes (or may not wish to write prose at all), this vault functions independent from drafting, yet still tracks all relevant information. **Cupcaeke** personally uses [Freewrite](https://getfreewrite.com) for her own distraction-free drafting. If Freewrite seems interesting, try out their word processor, [Sprinter/Postbox](https://getfreewrite.com/pages/sprinter).
> ## How do I use this vault?
> - It should usually be self-explanatory! Almost everything is automatic, and will tell you when you need to do things yourself. Each dashboard has buttons for creating new notes from templates, so don't worry about creating anything from the File Explorer (unless otherwise stated). Most features should be accessible to edit even through Reading Mode.
> - In almost every note template, there are adjustable Properties in the frontmatter (at the top). This is where much of the user-input happens. Watch it all render with a page refresh!
> 	- **Unless something is broken, DO NOT touch or edit any properties below the `--TECHNICAL--` property. This is where most of the automation comes in. If you accidentally change something here, please look through the corresponding Note Template's properties for help resetting it.**
> - Feel free to adjust or add any features you like!
> ## Can I use different themes?
> - Yes! Most formatting is done through CSS snippets, so the vault should be mostly theme-independent.
> ## Help! Something broke!!
> - Most cases, this is just a cache error. Simply reload the vault (`ctrl+p` "reload" OR close Obsidian and re-open). Sometimes, a toast notification will pop up from Templater saying there is an error after pressing a button, but you can ignore this if new files are created nonetheless.
> - Changing file names and paths too much can lead to errors. If you need to do this, be sure to check in `source mode` for any file paths in the code and adjust accordingly.
> - Sometimes files don't backlink properly. If something links up wrong in any of the **Return to \[dashboard\]** buttons, just go ahead and adjust the link to fit the link text.
> - If you have another issue, please contact **Cupcaeke** on github or elsewhere.
> ## Thanks
> - Hi! It's me, Cupcaeke. Thank you for using my Writer's Studio vault! I've put a lot of hard work into this project; so I hope you find it helpful. This started out as just a simple management system for my own creative works, but simply evolved into something huge that I wanted to share in the world. If you want to support me in any way (monetarily or otherwise), click [here](https://cupcaeke.carrd.co).
>   
>   Have fun with your creative endeavors!
# At A Glance
> [!column|3 ttl-c nmg s-mg no-i bg-black c-pink txt-c no-t]
> > [!example|bg-purple c-purple embed] Total Project Files
> > ```dataviewjs
> > // TOTAL FILES IN PROJECTS
> > let fileCount = dv.pages('-"~Templates"').length - dv.pages('"~Assets"').length - 1;
> > dv.header(4, fileCount + " files");
> > ```
> 
> > [!example|bg-purple c-purple embed] Total Worktime
> > ```dataviewjs
> > // SUM TIME WORKED
> > const pages = dv.pages()
> >     .where(p => p.editTime);
> > const hoursWork = pages
> >     .map(p => p.editTime)
> >     .sum() / 3600;
> > dv.header(4, hoursWork + "hrs");
> > ```
> 
> > [!example|bg-pink c-pink embed] Top 3 Projects
> > ```dataview
TABLE fcount AS "File Count"
WHERE fcount AND fileType = "masterboard"
SORT fcount DESC
LIMIT 3
> > ```
---
> [!metadata|ttl-c nmg s-mg bg-blue c-blue txt-c embed] Recently Modified
>```dataview
>TABLE file.mtime AS "Last Modified"
>SORT file.mtime DESC
>LIMIT 3
>```
# Project Database
```meta-bind-button
label: + New Project
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
    templateFile: ~Templates/Note Templates/05. Scripts/New Project.md

```
```base
filters:
  and:
    - fileType == "masterboard"
    - '!file.folder.contains("~Templates")'
properties:
  file.ctime:
    displayName: Created
views:
  - type: cards
    name: Cards
    order:
      - file.name
      - file.ctime
    image: note.banner
    cardSize: 230
    imageAspectRatio: 0.7

```
# Tasks
> [!metadata|nmg ttl-s txt-s txt-c embed collaps no-t clear wfull c-p-sm]
> ```dataview
> TASK 
> FROM -"~Templates"
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