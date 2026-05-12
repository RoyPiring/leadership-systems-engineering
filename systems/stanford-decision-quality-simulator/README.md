# Stanford Decision Quality Simulator

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

-T-h-i-s- -p-r-o-j-e-c-t- -b-u-i-l-d-s- -a- -s-t-r-u-c-t-u-r-e-d- -d-e-c-i-s-i-o-n- -s-i-m-u-l-a-t-o-r- -d-e-s-i-g-n-e-d- -t-o- -a-p-p-l-y- -S-t-a-n-f-o-r-d- -G-S-B-'-s- -D-e-c-i-s-i-o-n- -Q-u-a-l-i-t-y- -f-r-a-m-e-w-o-r-k- -a-n-d- -P-f-e-f-f-e-r-'-s- -P-o-w-e-r- -f-r-a-m-e-w-o-r-k- -t-o- -h-i-g-h---s-t-a-k-e-s- -b-u-s-i-n-e-s-s- -s-c-e-n-a-r-i-o-s-.-
-
-T-h-e- -s-y-s-t-e-m- -i-s- -b-u-i-l-t- -t-o- -m-o-v-e- -d-e-c-i-s-i-o-n---m-a-k-i-n-g- -a-w-a-y- -f-r-o-m- -i-n-s-t-i-n-c-t---o-n-l-y- -r-e-a-s-o-n-i-n-g- -a-n-d- -t-o-w-a-r-d- -m-e-a-s-u-r-a-b-l-e- -d-e-c-i-s-i-o-n- -q-u-a-l-i-t-y-.- -I-n-s-t-e-a-d- -o-f- -e-v-a-l-u-a-t-i-n-g- -w-h-e-t-h-e-r- -a-n- -o-u-t-c-o-m-e- -w-a-s- -s-u-c-c-e-s-s-f-u-l- -a-f-t-e-r- -t-h-e- -f-a-c-t-,- -t-h-e- -s-i-m-u-l-a-t-o-r- -e-v-a-l-u-a-t-e-s- -w-h-e-t-h-e-r- -t-h-e- -d-e-c-i-s-i-o-n- -p-r-o-c-e-s-s- -i-t-s-e-l-f- -w-a-s- -s-t-r-u-c-t-u-r-a-l-l-y- -s-o-u-n-d- -b-e-f-o-r-e- -e-x-e-c-u-t-i-o-n- -b-e-g-i-n-s-.- -T-h-e- -f-o-c-u-s- -i-s- -o-n- -f-r-a-m-i-n-g-,- -i-n-f-o-r-m-a-t-i-o-n- -q-u-a-l-i-t-y-,- -a-l-t-e-r-n-a-t-i-v-e-s-,- -t-r-a-d-e---o-f-f-s-,- -r-e-a-s-o-n-i-n-g-,- -a-n-d- -o-r-g-a-n-i-z-a-t-i-o-n-a-l- -c-o-m-m-i-t-m-e-n-t- -u-n-d-e-r- -r-e-a-l-i-s-t-i-c- -o-p-e-r-a-t-i-o-n-a-l- -p-r-e-s-s-u-r-e-.-
-
-T-h-e- -s-i-m-u-l-a-t-o-r- -a-l-s-o- -i-n-t-r-o-d-u-c-e-s- -p-o-w-e-r- -d-y-n-a-m-i-c-s- -a-s- -a-n- -e-x-e-c-u-t-i-o-n- -l-a-y-e-r-.- -A- -t-e-c-h-n-i-c-a-l-l-y- -c-o-r-r-e-c-t- -s-t-r-a-t-e-g-y- -c-a-n- -s-t-i-l-l- -f-a-i-l- -i-f- -s-t-a-k-e

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
8. **Proving the Method Generalizes**, -.

For the full walkthrough with screenshots and step-by-step content, see [`documents/stanford-decision-quality-simulator.md`](./documents/stanford-decision-quality-simulator.md).

## Validation

Build outcomes verified end-to-end. Each phase below is captured with screenshots, configuration, and observable behavior in [`documents/stanford-decision-quality-simulator.md`](./documents/stanford-decision-quality-simulator.md):

- ✅ Building a Stanford-Grade Decision Simulator
- ✅ Mastering the DQ Six Elements and Power Frameworks
- ✅ Applying DQ Frameworks to a Real Decision
- ✅ Making the $400M NorthernTech AI Pivot Decision
- ✅ Layering Pfeffer's Power Rules onto the Decision
- ✅ Passing the Board Director Standards Gate
- ✅ Teaching Back and Committing to Real-World Transfer
- ✅ Proving the Method Generalizes
