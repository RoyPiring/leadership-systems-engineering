# Schedule Time for Important Work

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

My delayed item was updating my resume. It mattered to me, but it had remained unscheduled and was repeatedly left for spare time. I reduced that broad item to one visible piece that could be completed in a single sitting: rewriting the resume summary paragraph and producing at least its first new sentence.

Defining the smallest piece gave the weekly appointment a concrete starting point. I would not need to decide whether to revise the entire resume when the reminder appeared. I could open the file, find the summary, and begin one named change. This reduced the distance between seeing the cue and creating visible evidence that the work had started.

The architecture is built across **7 phases**, anchored by **Choosing the Work That Deserves a Weekly Appointment** on the input side and **Applying the Rule Without Changing the Measure** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Schedule Time for Important Work
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Operator[/The operator, deciding now what a later result will be allowed to mean/]
    ReviewSelf[/The same operator on 16 December, reading a total against a cutoff written before any week was counted/]

    subgraph Piece["The work, cut down to something a session can finish"]
        Broad[(The delayed item: updating a resume, repeatedly left for spare time)]
        Small[("One visible piece: rewrite the summary paragraph and produce at least its first new sentence")]
        NoDecision{{Naming the smallest piece removes the question of whether to revise the whole resume when the reminder appears}}
    end

    subgraph Home["One page that holds the whole practice"]
        Page(A single Notion page carrying the baseline, the schedule, the session one plan, the movement rule, the boundary sentence, the cost note and the review)
        Together{{One continuing record, rather than rules and results spread across memory, email and separate notes}}
    end

    subgraph Identity["The setup error checked before it could happen"]
        Tabs(Google Calendar and Gmail opened side by side and the profile checked in each)
        Same[(Both show the same name and the same personal Gmail address)]
        Traceable{{A cue made under one account and a notification checked under another makes a working reminder look missing, so the shared identity is confirmed first}}
    end

    subgraph Baseline["Four weeks, judged only on what the calendar can show"]
        Search(The four weeks before the first session searched for resume-related entries)
        None[(No entries found, so all four weeks recorded as No, with the calendar noted as silent)]
        SilenceRule{{Calendar silence counts as No. Missing evidence is not replaced by intention or memory}}
        Conservative{{Counting a silent week as Yes would shrink the neglect without support, so the baseline is deliberately the harsher reading}}
        Separate{{Recording it before the recurring event exists keeps earlier neglect apart from later sessions}}
    end

    subgraph Cue["The hour, given its own place"]
        Event(A recurring appointment every Sunday from 3 to 4 PM, named for the work itself)
        Attached[("Pop-up reminder, email reminder, the page link and the session one instruction, all carried in the event")]
        OwnHour{{The work gets an hour of its own rather than competing for whatever is left}}
    end

    subgraph FirstFive["The first five minutes, decided in advance"]
        Steps(Open the page, read the session one line, open the file)
        Sentence[(Type the first new sentence of the summary before five minutes have passed)]
        Starting{{The response is scoped to starting, not to finishing the resume}}
        Crossed{{A first visible sentence is the evidence of crossing from preparation into action}}
        NoNegotiate{{It also removes the window in which the session could be reconsidered or postponed while deciding where to begin}}
    end

    subgraph Pressure["Written before anyone pushed against it"]
        Boundary[("A prepared sentence: something at 3 PM on Sunday, free any time after 4")]
        NoApology{{The hour is protected without an apology or an explanation of what the work is}}
        Movement[(A moved session has to stay inside the same week rather than disappearing)]
        Cost[(A cost line left deliberately blank until after the fourth session)]
        TooEarly{{Leaving the cost blank prevents an early judgment about what protecting the hour actually takes}}
    end

    subgraph Review["A review date fixed before any result existed"]
        Date[("First session October 11, one-time review December 16, 66 days later")]
        OwnCue[(The review carries its own pop-up and email, separate from the weekly reminders)]
        NotInformal{{Keeping it separate stops a routine weekly reminder from turning into an informal judgment point}}
        NoDrift{{Scheduling it first removes the chance of delaying it or picking a kinder date once results are visible}}
    end

    subgraph Frozen["The verdict, written before the first week was counted"]
        Keep[(A total of 3 or 4 keeps the Sunday appointment)]
        Drop[(A total of 2 or fewer removes it)]
        Fixed{{The cutoff is stated as unable to move after the results are known}}
        Mechanical{{The December decision is a reading rather than an argument, which is what separates the evidence from a later preference}}
    end

    subgraph Bounds["What the build does not claim"]
        Pending{{The review date has not arrived, so the appointment's future is undecided and no outcome is reported}}
        OneMeasure{{Nothing new may be measured afterwards; the total and the cutoff are the only inputs}}
    end

    Operator -- "names" --> Broad
    Broad -- "reduced to" --> Small
    Small -- "is what delivers" --> NoDecision
    Small -- "recorded on" --> Page
    Page -- "held under" --> Together
    Page -- "depends on" --> Tabs
    Tabs -- "confirmed" --> Same
    Same -- "is what gives" --> Traceable
    Page -- "opens with" --> Search
    Search -- "returned" --> None
    None -- "recorded under" --> SilenceRule
    SilenceRule -- "chosen because" --> Conservative
    None -- "timed to give" --> Separate
    Separate -- "only then creating" --> Event
    Event -- "carries" --> Attached
    Event -- "is what gives" --> OwnHour
    Traceable -- "is why" --> Attached
    Attached -- "triggers" --> Steps
    Steps -- "ends in" --> Sentence
    Sentence -- "scoped by" --> Starting
    Sentence -- "evidences" --> Crossed
    Starting -- "also delivers" --> NoNegotiate
    Page -- "prepares" --> Boundary
    Boundary -- "gives" --> NoApology
    Page -- "prepares" --> Movement
    Page -- "prepares" --> Cost
    Cost -- "left blank because" --> TooEarly
    Movement -- "keeps weeks countable for" --> Date
    Page -- "schedules" --> Date
    Date -- "carries" --> OwnCue
    OwnCue -- "exists so that" --> NotInformal
    Date -- "set first, giving" --> NoDrift
    Date -- "paired with" --> Keep
    Date -- "paired with" --> Drop
    Keep -- "held under" --> Fixed
    Drop -- "held under" --> Fixed
    Fixed -- "makes the decision" --> Mechanical
    Crossed -- "is what the weekly total counts toward" --> Keep
    Mechanical -- "read by" --> ReviewSelf
    ReviewSelf -- "bounded by" --> Pending
    Mechanical -- "bounded by" --> OneMeasure
    Conservative -- "is the floor the total is measured against" --> Mechanical

    class Broad,Small,None,Attached,Boundary,Movement,Cost,Date,OwnCue,Keep,Drop,Same,Sentence datastore
    class Page,Tabs,Search,Event,Steps service
    class NoDecision,Together,Traceable,SilenceRule,Conservative,Separate,OwnHour,Starting,Crossed,NoNegotiate,NoApology,TooEarly,NotInformal,NoDrift,Fixed,Mechanical,Pending,OneMeasure event
    class Operator,ReviewSelf io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/weekly-protected-hour.md`](./documents/weekly-protected-hour.md).

## Implementation

This system is built across **7 phases**:

1. **Choosing the Work That Deserves a Weekly Appointment**
2. **Creating a Home for the Practice**
3. **Establishing an Honest Baseline**
4. **Turning a Calendar Event into a Weekly Cue**
5. **Protecting the Hour Before Pressure Arrives**
6. **Scheduling a Fair 66-Day Review**
7. **Applying the Rule Without Changing the Measure**

For the full walkthrough with screenshots and step-by-step content, see [`documents/weekly-protected-hour.md`](./documents/weekly-protected-hour.md).

## Validation

Each build phase below is documented in [`documents/weekly-protected-hour.md`](./documents/weekly-protected-hour.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Choosing the Work That Deserves a Weekly Appointment
- ✅ Creating a Home for the Practice
- ✅ Establishing an Honest Baseline
- ✅ Turning a Calendar Event into a Weekly Cue
- ✅ Protecting the Hour Before Pressure Arrives
- ✅ Scheduling a Fair 66-Day Review
- ✅ Applying the Rule Without Changing the Measure
