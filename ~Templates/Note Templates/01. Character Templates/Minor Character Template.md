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
chaStake:
obsidianUIMode: preview
gallery: []
editTime:
---
#Character #Minor-Character
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

> [!infobox] Minor Character
> # Minor Character
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
### Strengths
> *Adaptable Ambitious Assertive Charismatic Compassionate Courageous Creative Decisive Diligent Disciplined Energetic Empathetic Humble Inspirational Intuitive Loyal Patient Resilient Self-Confident Strategic Tenacious Visionary Witty ETC.*

### Weaknesses
> *Impulsive Indecisive Inflexible Insecure Intolerant Irresponsible Lazy Naïve Neglectful Nervous Obstinate Overbearing Overcritical Perfectionist Pessimistic Procrastinator Reactive Rigid Self-Centered Sensitive Shy Stubborn Timid Unfocused Vague ETC.*

## Background

## Quotes

## Trivia

## Image Gallery
```meta-bind
INPUT[imageListSuggester(optionQuery("~Assets/Image Assets")):gallery]
```
## Task
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
