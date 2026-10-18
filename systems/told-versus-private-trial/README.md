# Tell One Person: Six Dated Actions

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

I ran a private comparison using six personal plans with fixed completion dates to see whether telling one person supported my follow-through. Date order assigned three plans to TOLD and three to PRIVATE, which prevented me from placing easier or more appealing actions in the group I wanted to perform better. The activity measured my own behavior and did not involve plans that other people expected me to complete.

Before recording any result, I wrote the rule that would determine whether I kept or stopped the practice. The final decision depended on the difference between the TOLD and PRIVATE completion counts, but only if my listener checked in on every TOLD date. Fixing this process first prevented me from changing the assignment method, completion standard, or decision rule after learning which plans I finished.

The architecture is built across **7 phases**, anchored by **Committing to a Private Accountability Practice** on the input side and **Following the Decision Written in Advance** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: "Tell One Person: Six Dated Actions"
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Listener[/Sam, who hears three actions and their dates and nothing else from the page/]
    NextTrial[/The untested half: whether each action had enough protected time reserved to be finished/]

    subgraph Rules["Rules fixed while every field was still empty"]
        Blank[("Ten empty fields: Listener, Plan list, Identity line, TOLD or PRIVATE, Told, Mark, Listener asked, Difference, COST LINE, Review date")]
        Telling(The telling rule and the boundary keeping identity lines private, written at the top)
        Keep[("The keep-or-stop sentence, the review-date rule and the research passage, all entered before a plan existed")]
        NoReshape{{With no plan, mark or listener answer recorded yet, the method cannot be reshaped to suit a result}}
        Gated{{The decision depends on the difference, but only if the listener checked in on every TOLD date}}
    end

    subgraph Setup["Paths tested, then cleared"]
        Notion(A Notion page named Tell-or-Keep Practice created under Private)
        Tested[("One calendar event with a 30-minute notification and one unsent Gmail draft, both verified")]
        Deleted[("Both test items deleted, leaving only the blank page for the real record")]
        Available{{Verifying the reminder and the backup telling path first keeps a missing path from surfacing after a plan depends on it}}
        NotProof{{A working path proves access, never that any of the six plans would be finished}}
    end

    subgraph Assign["Assignment taken out of the author's hands"]
        Six(Six personal plans written with fixed completion dates, then sorted by date)
        Odd[("Positions 1, 3 and 5 became TOLD: the door hinge, the new recipe, the library book")]
        Even[("Positions 2, 4 and 6 became PRIVATE: the garage, the photos, the bulbs")]
        NoFavour{{Date order prevents the more appealing or easier actions being placed in the group expected to perform better}}
        SelfOnly{{Only self-directed plans qualified, so no outside expectation could drive a completion}}
    end

    subgraph Disclosure["What was said, and what stayed on the page"]
        Spoken(Each TOLD action and its date told to the listener in person)
        Withheld[("Identity lines never shared, because the listener needs the action and the date to check in")]
        Seven[("Seven Google Calendar events: one per action date and one for the review")]
        Minimum{{Disclosure is limited to what the practice requires while the full personal record stays in one private place}}
        Equal{{Every plan received the same calendar support, so reminders are not what separates the two groups}}
    end

    subgraph Marks["One mark per plan, entered on its own date"]
        OnDate(Each plan checked when its evening reminder appeared, with no date moved afterwards)
        Done[("Plans 1, 2 and 3 marked Done on time")]
        NotDone[("Plans 4, 5 and 6 marked Not done on time")]
        Late[("The library book finished one day late and still marked Not done on time")]
        SameBar{{Completion is measured against the original date, so a late finish cannot become a success through rescheduling}}
        Comparable{{One boundary applied to all six keeps the two working counts comparable}}
    end

    subgraph Checkins["The condition that had to hold before the counts could speak"]
        Asked(The Listener asked field recorded for each TOLD plan on its scheduled date)
        Three[("Yes for the door hinge on October 21, the recipe on October 28 and the book on November 4")]
        Occurred{{Telling once would not establish that dated follow-up happened, which is what the TOLD condition actually claims}}
        NoField{{PRIVATE plans carry no such field, because the listener was never told about them}}
    end

    subgraph Counts["Working values, kept inspectable"]
        Told[("TOLD count 2, from plans 1 and 3")]
        Private[("PRIVATE count 1, from plan 2")]
        Diff[("Difference: 2 minus 1 is 1, written directly beneath the working counts")]
        OneNumber{{The difference is the only outcome, so neither group count can be quoted on its own to suit a conclusion}}
        CostWords[("The COST LINE written in words, adding no further rating or score")]
        Inspectable{{Placing the counts above the arithmetic lets the result be checked without rereading all six entries}}
    end

    subgraph Verdict["The action that was already written down"]
        Gate(The listener answers checked first, and all three read Yes)
        Above[("A difference above zero, matching the TOLD is better branch of the sentence written in advance")]
        Preference[("Recorded as keeping the practice, described as a preference rather than proof")]
        Unchanged{{No date, mark, listener answer, count or threshold was altered on the way to the decision}}
        Narrow{{Six plans of one person, grouped by date without balancing difficulty, cannot establish a cause}}
    end

    subgraph Cost["What the practice cost"]
        First[("About 75 minutes for the page, the six plans, the assignment, the telling and seven events")]
        Daily[("About one minute per plan date, 20 minutes to count, 10 minutes for the decision")]
        Scarce{{The hardest part was finding six plans nobody else already expected to be completed}}
    end

    Blank -- "topped by" --> Telling
    Blank -- "followed by" --> Keep
    Blank -- "is what gives" --> NoReshape
    Keep -- "makes the decision" --> Gated
    Telling -- "needs a home, so" --> Notion
    Notion -- "paths proven by" --> Tested
    Tested -- "then" --> Deleted
    Tested -- "establishes" --> Available
    Available -- "bounded by" --> NotProof
    NoReshape -- "only then writing" --> Six
    Six -- "sorted into" --> Odd
    Six -- "and into" --> Even
    Odd -- "assigned under" --> NoFavour
    Even -- "assigned under" --> NoFavour
    Six -- "restricted by" --> SelfOnly
    Odd -- "told through" --> Spoken
    Spoken -- "kept clear of" --> Withheld
    Withheld -- "delivers" --> Minimum
    Six -- "scheduled as" --> Seven
    Seven -- "gives" --> Equal
    Deleted -- "leaves Seven as the only live events" --> Seven
    Seven -- "drives" --> OnDate
    OnDate -- "produced" --> Done
    OnDate -- "produced" --> NotDone
    NotDone -- "includes" --> Late
    Late -- "held under" --> SameBar
    SameBar -- "gives" --> Comparable
    Spoken -- "followed on each date by" --> Asked
    Asked -- "returned" --> Three
    Three -- "proves" --> Occurred
    Asked -- "limited by" --> NoField
    Done -- "counted within TOLD as" --> Told
    Done -- "counted within PRIVATE as" --> Private
    Comparable -- "is what lets Told and Private be compared" --> Told
    Told -- "minus" --> Private
    Private -- "yields" --> Diff
    Diff -- "held as" --> OneNumber
    Diff -- "accompanied by" --> CostWords
    Told -- "placed above the arithmetic, giving" --> Inspectable
    Occurred -- "checked first at" --> Gate
    Gated -- "is the order Gate follows" --> Gate
    Gate -- "then reads" --> Above
    Diff -- "supplies the value for" --> Above
    Above -- "produced" --> Preference
    Preference -- "earned by" --> Unchanged
    Preference -- "bounded by" --> Narrow
    Notion -- "cost" --> First
    OnDate -- "cost" --> Daily
    SelfOnly -- "is what made the first session hard, through" --> Scarce
    Three -- "read by" --> Listener
    Minimum -- "is all that reached" --> Listener
    Narrow -- "leaves open" --> NextTrial
    Preference -- "carried into" --> NextTrial

    class Blank,Keep,Tested,Deleted,Odd,Even,Withheld,Seven,Done,NotDone,Late,Three,Told,Private,Diff,CostWords,Above,Preference,First,Daily datastore
    class Telling,Notion,Six,Spoken,OnDate,Asked,Gate service
    class NoReshape,Gated,Available,NotProof,NoFavour,SelfOnly,Minimum,Equal,SameBar,Comparable,Occurred,NoField,OneNumber,Inspectable,Unchanged,Narrow,Scarce event
    class Listener,NextTrial io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/told-versus-private-trial.md`](./documents/told-versus-private-trial.md).

## Implementation

This system is built across **7 phases**:

1. **Committing to a Private Accountability Practice**
2. **Creating a Private Home for the Practice**
3. **Establishing Rules Before Results**
4. **Assigning Plans by Date and Telling a Listener**
5. **Recording Each Dated Outcome**
6. **Comparing TOLD and PRIVATE Results**
7. **Following the Decision Written in Advance**

For the full walkthrough with screenshots and step-by-step content, see [`documents/told-versus-private-trial.md`](./documents/told-versus-private-trial.md).

## Validation

Each build phase below is documented in [`documents/told-versus-private-trial.md`](./documents/told-versus-private-trial.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Committing to a Private Accountability Practice
- ✅ Creating a Private Home for the Practice
- ✅ Establishing Rules Before Results
- ✅ Assigning Plans by Date and Telling a Listener
- ✅ Recording Each Dated Outcome
- ✅ Comparing TOLD and PRIVATE Results
- ✅ Following the Decision Written in Advance
