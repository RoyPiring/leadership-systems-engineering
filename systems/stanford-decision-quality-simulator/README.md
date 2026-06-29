# Stanford Decision Quality Simulator

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

This project builds a structured decision simulator designed to apply Stanford GSB's Decision Quality framework and Pfeffer's Power framework to high-stakes business scenarios.

The system is built to move decision-making away from instinct-only reasoning and toward measurable decision quality. Instead of evaluating whether an outcome was successful after the fact, the simulator evaluates whether the decision process itself was structurally sound before execution begins. The focus is on framing, information quality, alternatives, trade-offs, reasoning, and organizational commitment under realistic operational pressure.

The simulator also introduces power dynamics as an execution layer. A technically correct strategy can still fail if stakeholder alignment, influence, and sequencing are ignored. The project combines both frameworks to evaluate not just what decision should be made, but whether the organization can realistically execute it.

The architecture is built across **8 phases**, anchored by **Building a Stanford-Grade Decision Simulator** on the input side and **Proving the Method Generalizes** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Stanford Decision Quality Simulator
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Decider[/Decider: Records Gut Prediction First/]
    Scenario[/Scenario Brief: NorthernTech $400M AI Pivot/]
    Stakeholders[/Stakeholders: Engineering Leads + Board + Targets/]
    Operator[/Operator: 7-Day Live Decision/]

    subgraph Workspace["Cowork Workspace + Three-Persona Simulator"]
        ScenarioFiles[(Scenario Files: Frame, Roles, Constraints)]
        ScoringTemplates[(Scoring Templates: 1-5 per DQ Element)]
        ReferenceCards[(DQ + Power Reference Cards)]
        Coach(Coach Persona: Framework Discipline)
        Skeptic(Skeptic Persona: Stress Tests Reasoning)
        OperatorAgent(Operator Persona: Execution Reality)
    end

    subgraph DQEngine["DQ Engine: Six Elements + Weakest-Link"]
        Frame(Frame: Specificity + Falsifiability)
        Alternatives(Alternatives: Hybrid + Sequencing Options)
        Information(Information: Operational Constraints Surfaced)
        Values(Values + Trade-offs: ESG + Reputation + Cost)
        Reasoning(Reasoning: Defensible Logic Chain)
        Commitment(Commitment: Aligned Execution Will)
        WLGate{{Weakest-Link Gate: min element caps overall score}}
    end

    subgraph PowerOverlay["Pfeffer Power Overlay"]
        Rule1(Out of Way: Be Where Decisions Happen)
        Rule2(Break Rules: Change What Counts)
        Rule3(Show Up Strong: Energy + Presence)
        Rule4(Build Brand: Differentiated Reputation)
        Rule5(Network: Bridge to Resource Holders)
        Rule6(Use Power: Invest Capital Toward Goal)
        Rule7(Success Forgives: Results Reframe Means)
        SeqShift{{Resequence: Internal Comms Before External Negotiation}}
    end

    subgraph GovernanceGate["Board Governance Gate"]
        Risks[(Quantified Risks + Mitigations)]
        Milestones[(Measurable Milestones)]
        ESG[(ESG + Reputation Review)]
        BoardGate{{Board Gate: Defensible to Director Standards}}
    end

    subgraph TransferLoop["Transfer Loop: From Simulation to Operating Discipline"]
        AAR[(After-Action Review: Instinct vs Framework)]
        TeachBack(Teach-Back: Frameworks From Memory)
        Commitment7d[(7-Day Real Decision: AI Readiness Audit GTM)]
        Pattern[(Cross-Scenario Pattern: Power Affects Sequencing, Not Direction)]
    end

    Decider -- "instinct: PARTNER" --> ScenarioFiles
    Scenario -- "load case study" --> ScenarioFiles
    Stakeholders -- "map to roles" --> ScoringTemplates
    ScenarioFiles -- "feed framing" --> Coach
    ReferenceCards -. "ground" .-> Coach
    ReferenceCards -. "ground" .-> Skeptic
    ReferenceCards -. "ground" .-> OperatorAgent

    Coach -- "score 6 elements" --> Frame
    Coach -- "score 6 elements" --> Alternatives
    Coach -- "score 6 elements" --> Information
    Coach -- "score 6 elements" --> Values
    Coach -- "score 6 elements" --> Reasoning
    Coach -- "score 6 elements" --> Commitment

    Skeptic -- "stress-test lowest" --> WLGate
    OperatorAgent -- "surface ops constraints" --> Information

    Frame --> WLGate
    Alternatives --> WLGate
    Information --> WLGate
    Values --> WLGate
    Reasoning --> WLGate
    Commitment --> WLGate
    WLGate -- "weakest = Frame, score 75" --> Rule1

    Rule1 --> SeqShift
    Rule2 --> SeqShift
    Rule3 --> SeqShift
    Rule4 --> SeqShift
    Rule5 --> SeqShift
    Rule6 --> SeqShift
    Rule7 --> SeqShift
    SeqShift -- "PARTNER-to-BUILD with resequenced comms" --> Risks

    Risks --> BoardGate
    Milestones --> BoardGate
    ESG --> BoardGate
    BoardGate -- "passes director standards" --> AAR

    AAR --> TeachBack
    TeachBack --> Commitment7d
    Commitment7d --> Operator
    Commitment7d -. "logged for synthesis" .-> Pattern
    AAR -. "logged for synthesis" .-> Pattern
    class ScenarioFiles,ScoringTemplates,ReferenceCards,Risks,Milestones,ESG,AAR,Commitment7d,Pattern datastore
    class Coach,Skeptic,OperatorAgent,Frame,Alternatives,Information,Values,Reasoning,Commitment,Rule1,Rule2,Rule3,Rule4,Rule5,Rule6,Rule7,TeachBack service
    class WLGate,SeqShift,BoardGate event
    class Decider,Scenario,Stakeholders,Operator io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/stanford-decision-quality-simulator.md`](./documents/stanford-decision-quality-simulator.md).

## Implementation

This system is built across **8 phases**:

1. **Building a Stanford-Grade Decision Simulator**
2. **Mastering the DQ Six Elements and Power Frameworks**
3. **Applying DQ Frameworks to a Real Decision**
4. **Making the $400M NorthernTech AI Pivot Decision**
5. **Layering Pfeffer's Power Rules onto the Decision**
6. **Passing the Board Director Standards Gate**
7. **Teaching Back and Committing to Real-World Transfer**
8. **Proving the Method Generalizes**

For the full walkthrough with screenshots and step-by-step content, see [`documents/stanford-decision-quality-simulator.md`](./documents/stanford-decision-quality-simulator.md).

## Validation

Each build phase below is documented in [`documents/stanford-decision-quality-simulator.md`](./documents/stanford-decision-quality-simulator.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Building a Stanford-Grade Decision Simulator
- ✅ Mastering the DQ Six Elements and Power Frameworks
- ✅ Applying DQ Frameworks to a Real Decision
- ✅ Making the $400M NorthernTech AI Pivot Decision
- ✅ Layering Pfeffer's Power Rules onto the Decision
- ✅ Passing the Board Director Standards Gate
- ✅ Teaching Back and Committing to Real-World Transfer
- ✅ Proving the Method Generalizes
