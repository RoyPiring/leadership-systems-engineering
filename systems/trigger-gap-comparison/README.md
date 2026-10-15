# Build a Trigger Gap Page

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

I created a small habit comparison to test whether noticeable if-then triggers helped me complete actions I had been postponing. The comparison used ten actions I genuinely intended to finish. Five would keep only their written dates, while five preselected actions would keep their dates and receive triggers tied to specific moments.

The result would be one subtraction: completed dated items without triggers subtracted from completed items with triggers. I fixed the cutoff at 2 before collecting results. A gap meeting that boundary would support keeping the trigger-writing habit during the later review. Fixing the calculation and cutoff first prevented the outcome from changing the rule used to judge it.

The architecture is built across **7 phases**, anchored by **Defining My Response to Postponement** on the input side and **Refining Triggers With Critical Judgment** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Build a Trigger Gap Page
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Operator[/The operator, who keeps the final say on which moments are real/]
    Fresh[/The day 66 fresh gap, the only one allowed to decide the habit/]

    subgraph Design["The comparison, written before anything was added"]
        Split{{Ten intended actions, split five with dates only and five with dates plus an if-then trigger}}
        Formula[(One signed result: completed with triggers minus completed with dates alone)]
        Cutoff[(The cutoff fixed at 2 before any result existed)]
        OneNumber{{One subtraction rather than several competing measurements}}
        RuleFirst{{Fixing the formula and the boundary first stops the outcome from choosing the rule that judges it}}
    end

    subgraph Intention["The filter applied before anything was dated"]
        Gate(One question asked of every candidate: do I mean to do this)
        Struck[("Four entries answered No and were struck through rather than quietly dropped")]
        Replaced[("Four replacements that each answered Yes: a hallway bulb, a photo backup, a returned drill, a cleared car trunk")]
        Visible{{Striking them through keeps the selection rule and the reason the list changed on the page}}
        FairBase{{An action never meant to be done cannot count as evidence that a date or a trigger failed}}
    end

    subgraph Ready["A clean starting state, predicted then checked"]
        Predict(Predicted that mail and calendar would show the same account)
        Confirmed[(Prediction confirmed, with no calendar entries for this work and a blank page body)]
        Attributable{{A clean start means later reminders and source messages cannot be split across two identities}}
    end

    subgraph Dates["Dates to both halves, before any trigger"]
        AllTen[(Target dates added to all ten actions, 11 to 16 October)]
        NotScheduling{{The test is dates against dates plus a noticeable cue, not scheduled work against unscheduled work}}
        Audit(The whole page reread top to bottom against a prediction of ten dated actions and no if-then text)
        Order[(Gap definition, the example block, the value 2 and the cutoff sentence all confirmed present and in order)]
    end

    subgraph Triggers["Cues judged by when they fire"]
        Added(If-then triggers added to the five selected actions, with every date left in place)
        Timing{{Each trigger tested by asking when its cue would fire, not whether its wording read clearly}}
        Collision[("Two cues found competing for the same moment: bins to the curb and the dishwasher, both just after dinner")]
        Moved[(One cue moved to the start of an afternoon walk so the pairs point at separate moments)]
        Lesson{{Two well-written triggers can still weaken each other when they depend on the same moment}}
    end

    subgraph Judgment["Assistant proposals, accepted and refused"]
        Proposed(An assistant asked for alternative cues)
        RejectVague[("Rejected: finish my last task before lunch, because it names no dependable event")]
        RejectAbsent[("Rejected: see the drill by the front door, because the drill might not be there")]
        Weaker[(Three others acceptable but weaker than the wording already written, so the originals were kept)]
        Final{{An assistant can propose a clear sentence but cannot know which events are stable in this routine, so the human choice stays the control}}
    end

    subgraph Returns["Two return points with different jobs"]
        Day7[(Day 7, 17 October: write the first gap)]
        Observation{{The first gap is an observation and decides nothing}}
        Day66[(Day 66, 15 December: start a fresh comparison)]
        Decides{{Only the fresh gap is judged against the cutoff, so one small early result cannot become the conclusion}}
        Notified[(Both carry 30-minute notifications, scheduled in advance so neither can be skipped or moved once an outcome is visible)]
    end

    subgraph Bounds["What a result of this size can say"]
        Small{{A personal comparison of five against five proves little beyond its own setting}}
        NoUniversal{{It can guide one habit choice and cannot establish that triggers work for every task, person or workflow}}
        Drift{{The open question is whether the cues stay attached to stable moments as the routine changes, and whether collisions return}}
    end

    Operator -- "defines" --> Split
    Split -- "resolved by" --> Formula
    Formula -- "bounded by" --> Cutoff
    Formula -- "deliberately" --> OneNumber
    Cutoff -- "written first, giving" --> RuleFirst
    Operator -- "filters through" --> Gate
    Gate -- "rejected" --> Struck
    Struck -- "answered by" --> Replaced
    Struck -- "kept on the page, giving" --> Visible
    Gate -- "is what delivers" --> FairBase
    FairBase -- "is the precondition for" --> Formula
    Operator -- "opens with" --> Predict
    Predict -- "verified as" --> Confirmed
    Confirmed -- "gives" --> Attributable
    Replaced -- "dated by" --> AllTen
    AllTen -- "applied to both halves, giving" --> NotScheduling
    AllTen -- "checked by" --> Audit
    Audit -- "confirmed" --> Order
    Order -- "protects" --> RuleFirst
    Audit -- "only then permitting" --> Added
    Added -- "each tested under" --> Timing
    Timing -- "exposed" --> Collision
    Collision -- "resolved by" --> Moved
    Collision -- "taught" --> Lesson
    Added -- "challenged by" --> Proposed
    Proposed -- "refused as" --> RejectVague
    Proposed -- "refused as" --> RejectAbsent
    Proposed -- "accepted but set aside as" --> Weaker
    RejectVague -- "establishes" --> Final
    Final -- "returns authority to" --> Operator
    Moved -- "read at" --> Day7
    Day7 -- "held as" --> Observation
    Day7 -- "separated from" --> Day66
    Day66 -- "is what carries" --> Decides
    Day7 -- "both carry" --> Notified
    Cutoff -- "applied only at" --> Day66
    Decides -- "produces" --> Fresh
    Fresh -- "returns to" --> Operator
    Fresh -- "bounded by" --> Small
    Small -- "stated as" --> NoUniversal
    Lesson -- "leaves open" --> Drift
    Day66 -- "is the first check on" --> Drift

    class Formula,Cutoff,Struck,Replaced,Confirmed,AllTen,Order,Collision,Moved,RejectVague,RejectAbsent,Weaker,Day7,Day66,Notified datastore
    class Gate,Predict,Audit,Added,Proposed service
    class Split,OneNumber,RuleFirst,Visible,FairBase,Attributable,NotScheduling,Timing,Lesson,Final,Observation,Decides,Small,NoUniversal,Drift event
    class Operator,Fresh io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/trigger-gap-comparison.md`](./documents/trigger-gap-comparison.md).

## Implementation

This system is built across **7 phases**:

1. **Defining My Response to Postponement**
2. **Creating a Reliable Project Home**
3. **Filtering for Ten Meaningful Actions**
4. **Designing a Fair Dated Comparison**
5. **Adding Noticeable Triggers Without Losing Dates**
6. **Preparing the Delayed Reading and Fresh Review**
7. **Refining Triggers With Critical Judgment**

For the full walkthrough with screenshots and step-by-step content, see [`documents/trigger-gap-comparison.md`](./documents/trigger-gap-comparison.md).

## Validation

Each build phase below is documented in [`documents/trigger-gap-comparison.md`](./documents/trigger-gap-comparison.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Defining My Response to Postponement
- ✅ Creating a Reliable Project Home
- ✅ Filtering for Ten Meaningful Actions
- ✅ Designing a Fair Dated Comparison
- ✅ Adding Noticeable Triggers Without Losing Dates
- ✅ Preparing the Delayed Reading and Fresh Review
- ✅ Refining Triggers With Critical Judgment
