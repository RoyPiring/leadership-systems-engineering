# Coach Anyone From Stuck to Action

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

A coaching operating system that engineers the **ICF (International Coach Federation)** core competencies and **iPEC** energy-coaching framework into a measurable, repeatable workflow inside Claude Code + an Obsidian vault. Where Stanford Decision Quality (the lens's other system) treats decisions as structured artifacts, this system treats coaching conversations the same way — turning subjective interaction into scored, documented practice.

The vault scaffolds three personas (a Master Coach Mentor, a resistant coachee named Marcus, and an ICF/iPEC Standards Gate that scores every session), a Self-ELI energy-baseline assessment, and the **4-Step Shift Arc** as the coaching engine. A scored live session with Marcus produced a documented 9/10 ICF competency rating, with presence, active listening, and awareness generation as the strongest competencies. The protocol then transfers out of simulation into seven days of calendared real conversations, and a Day-1-vs-Day-3 progression check.

The architecture below shows the operating loop: Self-ELI baseline → 4-Step Shift Arc + powerful-questions engine → live session with Marcus → ICF competency scoring gate → reusable protocol artifacts → 7-day real-world transfer.

## Architecture

```mermaid
---
title: Coaching Shift Protocol — ICF and iPEC Operating System
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Coach[/Coach: Self in Operator Role/]
    Marcus[/Marcus: Simulated Coachee with Resistance/]
    RealPerson[/Real Coachee: 7-Day Calendared Conversations/]
    Outcome[/Self-Generated Insight + Documented Energy Shift/]

    subgraph Workspace["Workspace: Claude Code + Obsidian Vault (shift-protocol)"]
        Assessments[(assessments/: Self-ELI Baselines)]
        Sessions[(sessions/: Live Transcripts + Scores)]
        Protocols[(protocols/: Reusable Operating Patterns)]
        Transfer[(transfer/: 7-Day Application Workflows)]
        Templates[(templates/: Session Scaffolds)]
        Prompts[(prompts/: Persona + Question Library)]
    end

    subgraph Personas["Three Personas: Role Separation"]
        Mentor(Master Coach Mentor: Teaches + Evaluates)
        MarcusPersona(Marcus Persona: Resistance + Triggers)
        StandardsGate(ICF or iPEC Standards Gate: Quality Control)
    end

    subgraph Baseline["Pre-Session Baseline: Self-ELI Assessment"]
        NormalEnergy[(Normal-Conditions Profile: Level 4 Concern + Responsibility)]
        StressEnergy[(Stress-Conditions Profile: Frustration + Self-Criticism)]
        Pattern{{Energy Pattern Recognized: Stress Redirects to Internal Resistance}}
    end

    subgraph Engine["Coaching Engine: 4-Step Shift Arc"]
        PowerfulQ(Powerful Questions: Expand Exploration)
        AdviceTrap{{Advice Trap: Closes Exploration}}
        Lockwords(Lock-Words: Reveal Emotional Context)
        Silence(Disciplined Silence: Tolerate Incomplete Thoughts)
        ShiftArc(4-Step Shift Arc: Resistance to Self-Generated Insight)
    end

    subgraph LiveSession["Live Session + ICF Scoring Gate"]
        ThirtyMin(30-Min Coaching Session With Marcus)
        BestWorkQ(Most-Effective Question: What does your best work mean to you?)
        Breakthrough(Breakthrough: Identity Pattern Surfaced Independently)
        ICFEval{{ICF Competency Evaluation: 9 of 10}}
        Strongest[(Strongest Competencies: Presence + Listening + Awareness)]
    end

    subgraph Transfer["Transfer Loop: Simulation to Real Operating Discipline"]
        Protocol[(Reusable Protocol Artifacts)]
        Teachback(Teach-Back Exercise: Frameworks From Memory)
        SevenDay[(7-Day Calendar: 3 Real Conversations)]
        D1vsD3[(Day 1 vs Day 3 Skill Progression)]
        SilenceWin(Keep Going Prompt: Returns Ownership to Coachee)
    end

    Coach -- "configure environment" --> Assessments
    Coach -- "complete assessment" --> NormalEnergy
    Coach -- "complete assessment" --> StressEnergy
    NormalEnergy --> Pattern
    StressEnergy --> Pattern
    Pattern -- "informs presence" --> ShiftArc

    Mentor -. "grounds" .-> Engine
    Templates -. "scaffold" .-> ThirtyMin
    Prompts -. "library for" .-> Mentor
    Prompts -. "library for" .-> MarcusPersona

    PowerfulQ --> ShiftArc
    AdviceTrap -. "blocked by" .-> PowerfulQ
    Lockwords --> PowerfulQ
    Silence --> ShiftArc

    ShiftArc -- "drives" --> ThirtyMin
    Marcus -- "presents resistance" --> ThirtyMin
    MarcusPersona -. "simulates" .-> Marcus
    ThirtyMin -- "asks" --> BestWorkQ
    BestWorkQ -- "unlocks" --> Breakthrough
    Breakthrough -- "logged to" --> Sessions

    Sessions --> ICFEval
    StandardsGate -. "scores against" .-> ICFEval
    ICFEval -- "9 of 10" --> Strongest
    ICFEval -- "feedback into" --> Protocols

    Protocols -- "synthesized as" --> Protocol
    Protocol -- "rehearsed via" --> Teachback
    Teachback -- "calendared as" --> SevenDay
    SevenDay -- "applied to" --> RealPerson
    RealPerson -- "produces" --> Outcome
    Outcome -. "compared via" .-> D1vsD3
    SilenceWin -. "key transfer move" .-> SevenDay
    D1vsD3 -. "evidence stored in" .-> Sessions

    class Assessments,Sessions,Protocols,Transfer,Templates,Prompts,NormalEnergy,StressEnergy,Strongest,Protocol,SevenDay,D1vsD3 datastore
    class Mentor,MarcusPersona,PowerfulQ,Lockwords,Silence,ShiftArc,ThirtyMin,BestWorkQ,Breakthrough,Teachback,SilenceWin service
    class Pattern,AdviceTrap,ICFEval,StandardsGate event
    class Coach,Marcus,RealPerson,Outcome io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/coaching-shift-protocol.md`](./documents/coaching-shift-protocol.md).

## Implementation

This system is built across **8 phases**:

1. **Setting Up the Coaching Skills Environment**
2. **Building the Shift Protocol Vault**
3. **Establishing Your Energy Baseline: Self-ELI Assessment**
4. **Mastering Powerful Questions vs. Advice-Giving**
5. **Conducting a Live Coaching Session with Marcus**
6. **Scoring the Session: ICF Competency Evaluation**
7. **Building a Reusable Protocol and 7-Day Transfer System**
8. **Deploying the Protocol on a Real Person**

For the full walkthrough with screenshots and step-by-step content, see [`documents/coaching-shift-protocol.md`](./documents/coaching-shift-protocol.md).

## Validation

Build outcomes verified end-to-end. Each phase below is captured with screenshots, configuration, and observable behavior in [`documents/coaching-shift-protocol.md`](./documents/coaching-shift-protocol.md):

- ✅ Setting Up the Coaching Skills Environment
- ✅ Building the Shift Protocol Vault
- ✅ Establishing Your Energy Baseline: Self-ELI Assessment
- ✅ Mastering Powerful Questions vs. Advice-Giving
- ✅ Conducting a Live Coaching Session with Marcus
- ✅ Scoring the Session: ICF Competency Evaluation
- ✅ Building a Reusable Protocol and 7-Day Transfer System
- ✅ Deploying the Protocol on a Real Person
