---
--INFOBOX--: --
chaPronounce:
chaPronouns:
chaRace:
chaAge:
chaNick:
chaAffil:
chaJob:
chaLanguage:
--QUICK INFO--: --
chaOverview:
chaAppear:
chaWeb: "![[placeholderWeb]]"
--TECHNICAL--: --
chaImage: ~Assets/Image Assets/placeholder.png
chaArc:
chaStake:
obsidianUIMode: preview
gallery: []
editTime:
---
#Character #Major-Character
<%*
    let last_file = ""
    let recent_leaf = this.app.workspace.getMostRecentLeaf();
    let back_history = recent_leaf.history.backHistory;
    //skip when there is no back history 
    //this can happen when the file gets created directly from the GUI
    if(back_history.length > 0) {
        // the last entry is the most recent file
        last_file = "**[[" + back_history[back_history.length - 1].title + "|❮❮ Return to Characters Dashboard]]**\n";
    }    
    tR += last_file  ;
_%>

> [!infobox] Major Character
> # Major Character
> ### `=this.file.name`
> **Pronounced:**  "`=this.chaPronounce`"
> `INPUT[imageSuggester(optionQuery("~Assets/Image Assets")):chaImage]`
> ###### Basic Information
>  |
> ---|---|
> **Pronouns** | `=this.chaPronouns` |
> **Race/Species** | `=this.chaRace` |
> **Age** | `=this.chaAge` |
> **Nicknames/Titles** | `=this.chaNick` |
> **Affiliations** | `=this.chaAffil` |
> **Occupation** | `=this.chaJob` |
> **Languages** | `=this.chaLanguage` |
# `=this.file.name`

> [!info-overview]- Overview
> `=this.chaOverview`

> [!character]- Appearance
> `=this.chaAppear`

> [!location]- Relationship Web
> `=this.chaWeb`

## Attributes
### Character Arc
`BUTTON[cor-arc]` `BUTTON[dis-arc]` `BUTTON[fal-arc]` `BUTTON[fla-arc]` `BUTTON[pos-arc]`
> *How the character grows and evolves during the story.*
`VIEW[{chaArc}][text(renderMarkdown)]`
### Ghost
> *An important event in the character's past that defines their beliefs. The ghost is highly likely a turning point, highly positive or highly negative and may have shaped their view of the world as a lie.*

### Lie
> *What the character believes about the world to be true that is false.*

### Beliefs
> *What the character accepts to be true in the world, even if they are wrong.*

### Need
> *What a character truly needs, even if it is unknown to them.*

### Behaviour
> *The normal way the character does things, the way the reader sees them.*

### Want
> *What the character thinks they want to achieve, even if it is not what they really need. This often determines their behaviour.*

### Stake
> *The Stake defines a value of how much the character is invested in their occupation, wants and behaviours. This helps defining how much effort they will put into achieving them.*

> [!info|no-t]
> ```meta-bind
> INPUT[progressBar(minValue(0),maxValue(10)):chaStake]
> ```
### Opposition
> *Forces that stop the character from getting what they want.*

### Strengths
> *Adaptable Ambitious Assertive Charismatic Compassionate Courageous Creative Decisive Diligent Disciplined Energetic Empathetic Humble Inspirational Intuitive Loyal Patient Resilient Self-Confident Strategic Tenacious Visionary Witty ETC.*

### Weaknesses
> *Impulsive Indecisive Inflexible Insecure Intolerant Irresponsible Lazy Naïve Neglectful Nervous Obstinate Overbearing Overcritical Perfectionist Pessimistic Procrastinator Reactive Rigid Self-Centered Sensitive Shy Stubborn Timid Unfocused Vague ETC.*

## Gotham Character Questionnaire
> This questionnaire is found in Gotham Writers Workshop’s ***Writing Fiction***. 
> *It is recommended to answer them clearly, but in character.*
##### What is your character’s name? Does the character have a nickname?

##### What is your character’s hair color? Eye color?

##### What kind of distinguishing facial features does your character have?

##### Does your character have a birthmark? Where is it? What about scars? How did he get them?

##### Who are your character’s friends and family? Who does she surround herself with? Who are the people your character is closest to? Who does he wish he were closest to? 

##### Where was your character born? Where has she lived since then? Where does she call home? 

##### Where does your character go when he’s angry? 

##### What is her biggest fear? Who has she told this to?  Who would she never tell this to? Why?

## Background

## Quotes

## Trivia

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
