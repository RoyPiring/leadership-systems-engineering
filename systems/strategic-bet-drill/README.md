# Set the Bet: Strategic Leadership

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

In this build, I applied the strategic leadership drill to a real decision about where the organization should place its next bet. The work was not about making a better plan or adding more activity. It was about choosing a customer, moving resources, and naming what had to stop.

The real decision was whether to keep spreading effort across multiple directions or commit to a focused strategic bet. The drill forced the choice out of vague strategy language and into a funded trade-off.

This mattered because strategy is only real when money, people, and trust move. A plan that funds every option is not a bet. It is a delay with better formatting.

The architecture is built across **8 phases**, anchored by **The Strategic Bet I Chose to Own** on the input side and **Forcing the Kill Decision** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Set the Bet, Strategic Leadership Drill
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Leader[/Leader: Brings One Real Strategic Decision/]
    Scenario[/Scenario: Mid-Market vs Enterprise Bet/]
    OrgContext[/Org Context: Sub-Scale Across Segments/]
    Operator[/Operator: 90-Min Session + Re-Score/]

    subgraph Foundation["Principles + Vault Foundation"]
        Principles[(principles.md: Drill Governance)]
        Vault[(Obsidian Vault Skeleton)]
        Guide[(guide.md: Plain-Language System)]
        ValueClaim(Value Claim: Design Estimate, Not Guarantee)
        Tickets[(10 Linear Tickets: Tracked Delivery)]
    end

    subgraph Architecture["Decision Architecture: Four Records"]
        ADR1(Four-Persona Configuration)
        ADR2(Iterative Refusal Rules)
        ADR3(Resource-Allocation Tests)
        ADR4(Dependency-Based Workflow)
        Topology[(Agent Topology in Mermaid)]
    end

    subgraph Patterns["Three Patterns: The Floor"]
        Diagnose(Diagnose Before You Decide)
        SeparateVoices(Separate the Voices)
        FundOrNot(Fund It or It Is Not Real)
    end

    subgraph Personas["Four-Persona Boot Prompt"]
        Strategist(Strategist: Honest Diagnosis + Pressure)
        BoardChair(Board Chair: Funding Reality)
        Frontline(Frontline Voice: Who Carries It)
        DQVoice(Decision-Quality Voice: Judgment)
    end

    subgraph Phases["Eight Phased Steps: 90-Minute Run"]
        P12(Phase 1-2: Name the Real Problem)
        P3(Phase 3: Choose the Bet + Customer)
        P4(Phase 4: Name the Real Trade-Off)
        P5(Phase 5: Human Cost + Funding Source)
        P6(Phase 6: Seven-Field Decision Brief)
        P78(Phase 7-8: Capstone Scoring)
    end

    subgraph Refusals["Refusal Rules: Stop the Evasion"]
        R3{{Phase 3: Reject Flattering Diagnosis}}
        R5{{Phase 5: Reject Funding via Efficiency}}
        Floor{{Refusal Floor: Force the Honest Move}}
    end

    subgraph Artifacts["Worksheets + Templates + Instruments"]
        Worksheets[(3 Worksheets: Problem, Bet, Trade-Off)]
        BriefTemplate[(7-Field Decision-Brief Template)]
        Variants[(Operational Variants)]
    end

    subgraph Scoring["Capstone Scorecard: 8 of 12"]
        Rubric[(Per-Step Rubric: Runtime Enforcement)]
        Item3{{Item 3 Real Trade-Off: min 1 or Fail}}
        Item5{{Item 5 Human Cost + Trust: min 1 or Fail}}
        PassBar{{Capstone Gate: Stops Nothing = Fail}}
    end

    subgraph KillMission["Secret Mission: The Kill Decision"]
        Kill(Kill One Defensible Bet: End Enterprise Push)
        HumanCost[(Human Cost: Marcus T, VP Sales + Hires)]
        Trust(Own the Loss, Spend the Trust)
    end

    subgraph ReScore["30 / 90-Day Re-Score Loop"]
        Day30{{Day 30: Allocation Still Moved?}}
        Day90{{Day 90: Target Metric First Result?}}
        Reality[(Scores Reality, Not Intent)]
    end

    Brief[/Decision Brief: Funded Bet + Named Trade-Off/]

    Leader -- "one funded choice" --> Principles
    Scenario -- "load the case" --> Vault
    OrgContext -. "ground the diagnosis" .-> Guide
    Principles -- "rules before runtime" --> ValueClaim
    Vault --> Tickets
    Guide --> ValueClaim

    ValueClaim --> ADR1
    Tickets --> ADR4
    ADR1 --> Topology
    ADR2 --> Topology
    ADR3 --> Topology
    ADR4 --> Topology

    Principles -- "encode the floor" --> Diagnose
    Principles --> SeparateVoices
    Principles --> FundOrNot
    Diagnose -. "governs" .-> Strategist
    SeparateVoices -. "governs" .-> BoardChair
    FundOrNot -. "governs" .-> DQVoice

    Topology --> Strategist
    Topology --> BoardChair
    Topology --> Frontline
    Topology --> DQVoice

    Strategist --> P12
    P12 --> P3
    P3 --> P4
    P4 --> P5
    P5 --> P6
    P6 --> P78

    Strategist -- "blocks execute-faster answer" --> R3
    BoardChair -- "blocks efficiency-gains funding" --> R5
    R3 --> Floor
    R5 --> Floor
    Floor -- "no dodge moves forward" --> P3
    Floor --> P5
    Frontline -. "surfaces who pays" .-> P5

    Worksheets --> P12
    Worksheets --> P4
    BriefTemplate --> P6
    Variants -. "context fit" .-> P78

    P78 --> Rubric
    Rubric --> Item3
    Rubric --> Item5
    Item3 --> PassBar
    Item5 --> PassBar
    DQVoice -- "judges the brief" --> PassBar

    P5 --> Kill
    Kill --> HumanCost
    HumanCost --> Trust
    Trust -- "records the real cost" --> P6

    PassBar -- "8 of 12, trade-off funded" --> Brief
    Brief --> Operator
    Operator --> Day30
    Day30 --> Day90
    Day90 --> Reality
    Reality -. "revert = strategy failed" .-> PassBar

    class Principles,Vault,Guide,Tickets,Topology,Worksheets,BriefTemplate,Variants,Rubric,HumanCost,Reality datastore
    class ValueClaim,ADR1,ADR2,ADR3,ADR4,Diagnose,SeparateVoices,FundOrNot,Strategist,BoardChair,Frontline,DQVoice,P12,P3,P4,P5,P6,P78,Kill,Trust service
    class R3,R5,Floor,Item3,Item5,PassBar,Day30,Day90 event
    class Leader,Scenario,OrgContext,Operator,Brief io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/strategic-bet-drill.md`](./documents/strategic-bet-drill.md).

## Implementation

This system is built across **8 phases**:

1. **The Strategic Bet I Chose to Own**
2. **Running the Drill: Decision Brief and Capstone Results**
3. **Shipping the Complete System to GitHub**
4. **Building the Principles and Vault Foundation**
5. **Designing the Agent Topology and Decision Architecture**
6. **Building the Four-Persona Drill and Scoring System**
7. **Worksheets, Templates, and Validation Instruments**
8. **Forcing the Kill Decision**

For the full walkthrough with screenshots and step-by-step content, see [`documents/strategic-bet-drill.md`](./documents/strategic-bet-drill.md).

## Validation

Each build phase below is documented in [`documents/strategic-bet-drill.md`](./documents/strategic-bet-drill.md), with screenshots, configuration, and notes as captured during the build:

- ✅ The Strategic Bet I Chose to Own
- ✅ Running the Drill: Decision Brief and Capstone Results
- ✅ Shipping the Complete System to GitHub
- ✅ Building the Principles and Vault Foundation
- ✅ Designing the Agent Topology and Decision Architecture
- ✅ Building the Four-Persona Drill and Scoring System
- ✅ Worksheets, Templates, and Validation Instruments
- ✅ Forcing the Kill Decision
