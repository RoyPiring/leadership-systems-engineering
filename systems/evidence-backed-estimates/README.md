# Look Back Before You Put a Time on a Job

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

I built one Notion page to estimate recurring work from jobs I had already completed. The focus was my weekly operations and administration load, including status reports, invoice runs, server patching, code reviews, and backup checks. These jobs often ran beyond the time I expected, making the remembered estimates difficult to plan around.

The practice separated estimates supported by past work from estimates written as one unsupported number. I would later compare how often each group finished inside its estimate. The purpose was not to predict every job perfectly. It was to test whether looking backward at completed work produced a planning time that held up more often than relying on memory alone.

The architecture is built across **6 phases**, anchored by **Choosing a Recurring Job to Estimate Better** on the input side and **Rebuilding the Baseline with Checked Typical Times** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Look Back Before You Put a Time on a Job
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Planner[/The operator planning a week of recurring operations and administration work/]
    Owed[/The gap, which does not exist until both groups hold their first 20 countable jobs/]

    subgraph Question["What is actually being tested"]
        Compare{{Does an estimate with a visible past-work trail finish inside its time more often than an estimate written as one unsupported number}}
        NotPredict{{The aim is not to estimate every job correctly, only to test whether looking backward plans better than memory}}
    end

    subgraph Home["One page, one source of truth"]
        Notion(A single Notion page holding the baseline table, the weekly list, the estimates, the actuals, the counting rules, the gap and the verdict)
        CalOnly[(Google Calendar carries only the day 7, day 28 and day 66 checkpoints and never a copy of the jobs)]
        NoForks{{One evolving record and one set of return points, so the practice cannot split into two copies with different numbers}}
    end

    subgraph Setup["A check that changed nothing"]
        Account(Inbox and calendar opened side by side and the account confirmed the same in both)
        Untouched[(No label created, no message sent and no event added until the rules were written)]
        Attributable{{A clean setup boundary means every later event belongs to this practice, and no reminder lands somewhere unwatched}}
    end

    subgraph Remembered["The baseline being challenged"]
        Table[("Eight recurring job types with the times memory would have used, such as patching at 1h and code review at 30 min")]
        NotEvidence{{The remembered table is the existing baseline, explicitly not verified duration evidence}}
    end

    subgraph Order["Ten jobs, in the order they arrived"]
        Ten[(Ten jobs for the week, numbered 1 to 10 in first-thought order)]
        Unsorted{{Not sorted by duration, urgency, difficulty or how easy a job would be to support with evidence}}
        Blank[(Estimates left blank at this stage, so naming work and defending a time for it stay visibly separate)]
        NoGaming{{Because the order decides the odd and even split, fixing it first prevents favorable jobs being steered into either group}}
    end

    subgraph Method["Two estimate formats, one list"]
        Odd(Odd-numbered jobs get three lines: what the table says, a sentence of relevant completed work, and the estimate)
        Even(Even-numbered jobs get one line: the estimate alone)
        Worked[("A worked example: table says 1h, past patch nights ran 1h 30 once reboot checks are counted, estimate 1h 30")]
        Plain[("Against a bare entry: estimate 30 min, usable for planning, with no trail behind it")]
        Visible{{A reader can tell which estimates carry a past-work trail and which do not, without either being claimed correct in advance}}
    end

    subgraph Counting["What counts, decided before any actual existed"]
        Countable{{A job becomes countable only once it has an actual time}}
        Exact{{Finishing exactly on the estimate counts as inside, not over}}
        Never{{A job that never started is excluded, because it produced no timing evidence}}
        Unfinished{{A started but unfinished job counts as over only once the time already spent passes its estimate}}
        Frozen[(Counting rules, limits, cost rule and verdict boundary copied onto the page before any actual could influence them)]
        ThenDates(The three reminders created only after those rules were written)
    end

    subgraph Patience["The count that refuses to arrive early"]
        Twenty{{The gap is calculated only when the odd and even groups each hold their first 20 countable jobs}}
        Readiness[(Day 28 is a readiness check, not a guaranteed calculation date)]
        Slip[(If either group is short, the check moves forward one week and recording continues under the same rules)]
        NoPartial{{No partial gap is computed, so an early imbalance cannot decide the outcome while one group has more usable evidence}}
        Boundary[("The prewritten boundary: does the odd inside count exceed the even inside count by 4 or more")]
    end

    subgraph Typical["Rebuilding the baseline, middle not mean"]
        Three[("Three supplied actuals: 2h 20, 2h 40 and 2h 30")]
        Sorted(The operator sorted them personally, shortest to longest)
        Model(A model asked for the typical time returned 2h 30 with the three source values and no average)
        Middle{{The returned value had to match the middle completed time, which is the check rather than the model's answer}}
        Rule{{On day 66 the same check runs before any real table row is replaced, so one unusual job cannot move the baseline}}
    end

    subgraph Bounds["What is not claimed"]
        NoResult{{No result is reported. Neither method has been shown better, and the comparison has not been run}}
        Uncomfortable[(The page already shows patch nights and migration reviews running longer than memory said, which is the baseline being wrong rather than the method working)]
    end

    Planner -- "asks" --> Compare
    Compare -- "scoped by" --> NotPredict
    Compare -- "recorded on" --> Notion
    Notion -- "paired with" --> CalOnly
    CalOnly -- "together give" --> NoForks
    Notion -- "preceded by" --> Account
    Account -- "left" --> Untouched
    Untouched -- "gives" --> Attributable
    Notion -- "opens with" --> Table
    Table -- "labelled as" --> NotEvidence
    Table -- "challenged by" --> Ten
    Ten -- "written under" --> Unsorted
    Ten -- "carries" --> Blank
    Unsorted -- "is what delivers" --> NoGaming
    NoGaming -- "allows the split into" --> Odd
    NoGaming -- "allows the split into" --> Even
    Odd -- "shown by" --> Worked
    Even -- "shown by" --> Plain
    Worked -- "set against Plain, giving" --> Visible
    Table -- "is the line Worked departs from" --> Worked
    Odd -- "scored under" --> Countable
    Even -- "scored under" --> Countable
    Countable -- "refined by" --> Exact
    Countable -- "refined by" --> Never
    Countable -- "refined by" --> Unfinished
    Countable -- "written into" --> Frozen
    Frozen -- "only then scheduling" --> ThenDates
    Frozen -- "sets" --> Twenty
    ThenDates -- "reaches" --> Readiness
    Readiness -- "short, so" --> Slip
    Slip -- "repeats under" --> NoPartial
    Twenty -- "resolves against" --> Boundary
    NoPartial -- "defers" --> Owed
    Boundary -- "awaits" --> Owed
    Notion -- "also tests" --> Three
    Three -- "ordered by" --> Sorted
    Three -- "put to" --> Model
    Sorted -- "is what validates" --> Middle
    Model -- "checked against" --> Middle
    Middle -- "becomes" --> Rule
    Rule -- "will rebuild" --> Table
    Owed -- "returns to" --> Planner
    Boundary -- "bounded by" --> NoResult
    Table -- "already contradicted by" --> Uncomfortable

    class CalOnly,Untouched,Table,Ten,Blank,Worked,Plain,Frozen,Readiness,Slip,Boundary,Three,Uncomfortable datastore
    class Notion,Account,Odd,Even,ThenDates,Sorted,Model service
    class Compare,NotPredict,NoForks,Attributable,NotEvidence,Unsorted,NoGaming,Visible,Countable,Exact,Never,Unfinished,Twenty,NoPartial,Middle,Rule,NoResult event
    class Planner,Owed io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/evidence-backed-estimates.md`](./documents/evidence-backed-estimates.md).

## Implementation

This system is built across **6 phases**:

1. **Choosing a Recurring Job to Estimate Better**
2. **Creating a Home for the Recording Practice**
3. **Establishing the Remembered Baseline**
4. **Estimating New Jobs from Past Work**
5. **Protecting the Practice with Rules and Reminders**
6. **Rebuilding the Baseline with Checked Typical Times**

For the full walkthrough with screenshots and step-by-step content, see [`documents/evidence-backed-estimates.md`](./documents/evidence-backed-estimates.md).

## Validation

Each build phase below is documented in [`documents/evidence-backed-estimates.md`](./documents/evidence-backed-estimates.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Choosing a Recurring Job to Estimate Better
- ✅ Creating a Home for the Recording Practice
- ✅ Establishing the Remembered Baseline
- ✅ Estimating New Jobs from Past Work
- ✅ Protecting the Practice with Rules and Reminders
- ✅ Rebuilding the Baseline with Checked Typical Times
