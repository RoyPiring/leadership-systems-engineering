# Build a Daily Work Catalogue

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

I built the Daily Work Catalogue to stop urgent messages, recent notifications, and loud sources from deciding what I worked on next. Those arrivals could still contain legitimate work, but their timing did not establish priority. I needed one ordered queue that separated collecting a task from choosing when to act on it.

The catalogue became the only place allowed to select my next action. Email, Slack, Notion, meetings, calls, and paper could introduce work, but each ordinary item had to become a pointer and enter the queue in order. I then returned to the action already underway. This system did not prevent every interruption or replace professional judgment. It established a default rule: incoming work waited unless it met the written safety exception. The outcome was a visible decision path that I could review later instead of reconstructing from notifications, memory, or whichever source I happened to open first.

The architecture is built across **7 phases**, anchored by **Choosing What Guides the Next Action** on the input side and **Auditing the Queue on a Busy Day** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Build a Daily Work Catalogue
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Operator[/The person whose next action keeps getting chosen by whatever arrived last/]
    Arrivals[/Email, chat, notes, calendar, meetings, calls, people, paper/]

    subgraph Framing["The problem, named first"]
        Distraction{{Urgent messages and loud sources were deciding the next action}}
        Split{{Collecting a task is separated from choosing when to act on it}}
        OnlyQueue{{One rule: only the queue selects the next action}}
    end

    subgraph Page["One place to look, not one place to keep"]
        Notion[(Daily Work Catalogue page in Notion)]
        Sections[(WHAT IS NEXT, WHERE WORK REACHES ME, sweep rules, rebuild cue, exceptions, cost, review)]
        Routing{{A routing layer, not a replacement inbox: work stays where it arrived}}
    end

    subgraph SourceMap["Every place work can arrive, each with exactly one rule"]
        Visit[("I VISIT IT at a written time: inboxes, chat, calendar, Notion, paper")]
        Reach[("CAN REACH ME under a named condition: meetings, calls, someone in person")]
        NoHidden{{An unlisted channel cannot become a hidden path around the catalogue}}
        NoPriority{{A source can say work exists; it can never choose the next action}}
    end

    subgraph Boundaries["Rules for the day"]
        Cue(Rebuild cue: the end of the daily scrum, present on working days and absent on rest days)
        WhyCue{{An observable transition on the real calendar, not a dismissable reminder}}
        EndOfQueue{{An ordinary arrival gets one pointer at the end of the queue, then work resumes}}
        Exception[(Safety or serious harm may interrupt, every use logged under DATE, WHAT ARRIVED, WHERE IT STAYS)]
        Blank{{The exception log starts blank: no exception had occurred}}
        Above{{Professional, legal and workplace rules stay above this workflow}}
    end

    subgraph Queue["The pointer-only queue"]
        Sweep(Scheduled source visits at 9:00, then the rebuild after the scrum)
        Pointer[("One imperative sentence plus It stays in... and a locator")]
        NoCopy{{No summaries, quotes or background: a pointer that grows into a paragraph is evidence of copied source}}
        Ordered[(WHAT IS NEXT ordered once per rebuild, worked top to bottom)]
    end

    subgraph Precommit["Judged on a date fixed in advance"]
        Review[(One future review scheduled before day one, no daily reminders)]
        Cost[("Setup cost recorded first: five-minute sweep, page repair heavier than the sweep, a displaced gym block")]
        WhyCost{{So review day compares value against real friction, not against the setup-day enthusiasm}}
        KeepDrop{{Keep, revise or drop, decided from logged use}}
    end

    subgraph Audit["The busy-day test"]
        Pressure(Direct messages, meeting requests and spoken asks arriving mid-task)
        Held[(Each received one pointer at the end, none jumped the line, work resumed)]
        Testable{{A day where an unqualified arrival chose the action does not count as compliant}}
        Reviewable{{Adherence is read from queue order and the exception log, not from whether the day felt focused}}
    end

    Operator -- "names" --> Distraction
    Distraction -- "answered by" --> Split
    Split -- "enforced as" --> OnlyQueue
    OnlyQueue -- "lives on" --> Notion
    Notion -- "holds" --> Sections
    Notion -- "designed as" --> Routing
    Arrivals -- "mapped into" --> Visit
    Arrivals -- "mapped into" --> Reach
    Visit -- "with the contact rules closes" --> NoHidden
    Visit -- "bounded by" --> NoPriority
    Reach -- "bounded by" --> NoPriority
    Sections -- "records" --> Cue
    Cue -- "chosen because" --> WhyCue
    Reach -- "governed by" --> EndOfQueue
    EndOfQueue -- "has one exception" --> Exception
    Exception -- "begins as" --> Blank
    Exception -- "sits beneath" --> Above
    Visit -- "drives" --> Sweep
    Cue -- "triggers" --> Sweep
    Sweep -- "produces" --> Pointer
    Pointer -- "held to" --> NoCopy
    Pointer -- "assembled into" --> Ordered
    Routing -- "is what keeps" --> NoCopy
    Ordered -- "handed to" --> Operator
    Sections -- "records" --> Review
    Sections -- "records" --> Cost
    Cost -- "exists so that" --> WhyCost
    Review -- "ends in" --> KeepDrop
    Ordered -- "tested by" --> Pressure
    Pressure -- "under the end-of-queue rule gave" --> Held
    Held -- "graded by" --> Testable
    Testable -- "makes the day" --> Reviewable
    Reviewable -- "feeds" --> KeepDrop
    Blank -- "is checked at" --> KeepDrop

    class Notion,Sections,Visit,Reach,Exception,Pointer,Ordered,Review,Cost,Held datastore
    class Cue,Sweep,Pressure service
    class Distraction,Split,OnlyQueue,Routing,NoHidden,NoPriority,WhyCue,EndOfQueue,Blank,Above,NoCopy,WhyCost,KeepDrop,Testable,Reviewable event
    class Operator,Arrivals io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/daily-work-catalogue.md`](./documents/daily-work-catalogue.md).

## Implementation

This system is built across **7 phases**:

1. **Choosing What Guides the Next Action**
2. **Creating One Place to Look**
3. **Mapping Every Place Work Arrives**
4. **Setting Boundaries for Daily Work**
5. **Building a Pointer-Only Daily Queue**
6. **Precommitting to a Review Decision**
7. **Auditing the Queue on a Busy Day**

For the full walkthrough with screenshots and step-by-step content, see [`documents/daily-work-catalogue.md`](./documents/daily-work-catalogue.md).

## Validation

Each build phase below is documented in [`documents/daily-work-catalogue.md`](./documents/daily-work-catalogue.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Choosing What Guides the Next Action
- ✅ Creating One Place to Look
- ✅ Mapping Every Place Work Arrives
- ✅ Setting Boundaries for Daily Work
- ✅ Building a Pointer-Only Daily Queue
- ✅ Precommitting to a Review Decision
- ✅ Auditing the Queue on a Busy Day
