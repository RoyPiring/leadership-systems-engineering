# Audit Claude Household Privacy

> Inside the [Leadership Systems Engineering](../../README.md) portfolio · *Leadership frameworks from formal coursework, engineered as working systems.*

## Overview

I created a local audit workspace before reviewing Claude settings, Memory, chats, or account data. The lab folder became the private location for complete records, including household roles, consent decisions, account observations, research evidence, timestamps, and the pending export. This established the privacy boundary before any sensitive information was collected.

The audit followed a local-first rule: full household details remained on my computer, while Claude could receive only a cleaned Settings Record when needed. I also retained control over every account change and chat deletion rather than asking Claude to act on my behalf. This setup allowed me to examine privacy behavior without exposing the family map or treating an online account as the primary home for audit evidence.

The architecture is built across **6 phases**, anchored by **Establishing a Privacy-First Audit Workspace** on the input side and **Demonstrating Least-Disclosure Practices** at the end. Each phase is listed in the Implementation section below.

## Architecture

```mermaid
---
title: Audit Claude Household Privacy
---
%%{init: {"theme":"base","themeVariables": {"primaryColor":"#1B4332","primaryTextColor":"#F4D03F","primaryBorderColor":"#F4D03F","secondaryColor":"#264653","tertiaryColor":"#2F5233","lineColor":"#F4D03F","fontFamily":"ui-monospace, SFMono-Regular, Menlo, Consolas, monospace","fontSize":"13px"}}}%%
flowchart TD
    classDef datastore fill:#264653,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef service fill:#1B4332,stroke:#F4D03F,stroke-width:2px,color:#F4D03F
    classDef event fill:#7B42BC,stroke:#F4D03F,stroke-width:2px,color:#FFFFFF
    classDef io fill:#0d1117,stroke:#F4D03F,stroke-width:1.5px,color:#F4D03F,font-style:italic

    Absent[/The household member who was unavailable, and therefore consented to nothing/]
    Export[/The account export, requested and still pending, which never becomes evidence until it arrives/]

    subgraph Boundary["The rule set before anything was collected"]
        LocalFirst{{Complete household detail stays on the laptop; only a cleaned record may ever enter a Claude Project}}
        Folder[(A local lab folder opened empty, so every complete audit file has one private home)]
        Human{{Every account change and every deletion is made by the operator rather than asked of the tool}}
        Default{{Privacy by default: the tool receives what it needs to explain a setting, and nothing of the household context behind the decision}}
    end

    subgraph Consent["Consent recorded by role, not by name"]
        Log[("A five-row log: item, role, consent, action, reason")]
        Roles{{Roles replace names, which lowers the identifying detail the audit itself has to store}}
        NoConsent[(The absent member marked no consent, with every related item left unchanged)]
        NotApproval{{Absence does not count as approval, and shared access to a household does not authorize changing another person's information}}
        StopRule{{A clear stop condition whenever the person attached to the data cannot speak for themselves}}
    end

    subgraph Observed["Settings read, not assumed"]
        Controls(The account controls reviewed one by one: whether conversations are used for model training, Memory, past-chat search, retention clocks, incognito chats and data export)
        AsSeen[(Each recorded as observed, with its source and the time it was observed)]
        NotPlan{{Plan type and default behavior are not treated as evidence of any particular level of household privacy}}
        Reduces{{A control reduces one defined risk. It does not make the account private, and the record says so}}
        Sources(Official provider pages and cited research kept separate from direct observation)
        Apart{{The record stays clear about what was seen, what the provider documents, and what is still pending or unknown}}
    end

    subgraph Fixture["A real boundary tested with invented data"]
        Invent[("An invented pet and an invented town, carrying no household information at all")]
        DeleteChat(The fixture chat deleted, then past-chat search run again)
        Gone[("At 11:06 PM the chat result is gone, yet the separate Memory topic still returns the invented town")]
        Split{{Deleting a chat does not delete the Memory topic built from it. The two are separate locations needing separate action}}
        DeleteTopic(Only the invented Memory topic then deleted, and the question asked once more)
        Unknown[("At 11:11 PM the answer becomes I do not know")]
        Safe{{The sequence proves the behavior without putting one real family detail at risk}}
    end

    subgraph Records["Two records, one of them shareable"]
        Complete[(The complete local record: settings, sources, observation clocks, fixture proof, export status and chat counts, beside the consent log and the family map)]
        Redacted[(A redacted copy for the Claude Project, with the family list, roles and consent details removed)]
        Table[("A four-column table tying each setting or finding to its state, its evidence and the decision it produced")]
        Pending{{The table keeps observed settings apart from actions that are pending or deliberately not taken}}
        Followable{{A later reviewer can follow the reasoning without ever needing the family map}}
    end

    subgraph Check["The disclosure check, line by line"]
        NinetyNine(All 99 lines of the shareable copy read for household information)
        Clean[(No family role, no personal name and no consent detail found, so nothing further was removed)]
        Kept[(Settings, sources, timestamps, fixture evidence and export status all still present after redaction)]
        Limited{{The claim is limited to what the line-by-line review showed about this copy, and is not a statement that the account or platform is private}}
    end

    subgraph Owed["Held open on purpose"]
        Requested(The export requested through the settings path, with the download link not yet arrived)
        NotClaimed{{Recorded as pending rather than marked complete, and its contents are not described before it exists}}
        WillStay{{When it arrives it is opened while signed in and saved only in the local folder, because an export can carry private chats and household material}}
    end

    Absent -- "is the reason for" --> LocalFirst
    LocalFirst -- "realised as" --> Folder
    LocalFirst -- "paired with" --> Human
    LocalFirst -- "expressed as" --> Default
    Folder -- "holds" --> Log
    Log -- "written with" --> Roles
    Log -- "records" --> NoConsent
    NoConsent -- "governed by" --> NotApproval
    NotApproval -- "gives" --> StopRule
    Absent -- "protected by" --> StopRule
    Default -- "then permits" --> Controls
    Controls -- "recorded" --> AsSeen
    AsSeen -- "held under" --> NotPlan
    AsSeen -- "bounded by" --> Reduces
    Controls -- "set beside" --> Sources
    Sources -- "kept" --> Apart
    Controls -- "tested by" --> Invent
    Invent -- "used in" --> DeleteChat
    DeleteChat -- "returned" --> Gone
    Gone -- "reveals" --> Split
    Split -- "answered by" --> DeleteTopic
    DeleteTopic -- "returned" --> Unknown
    Invent -- "is what makes the test" --> Safe
    Human -- "performed" --> DeleteChat
    Human -- "performed" --> DeleteTopic
    AsSeen -- "written into" --> Complete
    Unknown -- "recorded in" --> Complete
    Complete -- "reduced to" --> Redacted
    Complete -- "structured as" --> Table
    Table -- "separates through" --> Pending
    Table -- "gives" --> Followable
    Redacted -- "verified by" --> NinetyNine
    NinetyNine -- "found" --> Clean
    NinetyNine -- "confirmed" --> Kept
    Clean -- "supports only" --> Limited
    Reduces -- "is why" --> Limited
    Log -- "never enters" --> Redacted
    Controls -- "opened" --> Requested
    Requested -- "recorded under" --> NotClaimed
    NotClaimed -- "governed by" --> WillStay
    WillStay -- "keeps it out of" --> Redacted
    Requested -- "leaves" --> Export
    Pending -- "is where Export sits" --> Export

    class Folder,Log,NoConsent,AsSeen,Invent,Gone,Unknown,Complete,Redacted,Table,Clean,Kept datastore
    class Controls,Sources,DeleteChat,DeleteTopic,NinetyNine,Requested service
    class LocalFirst,Human,Default,Roles,NotApproval,StopRule,NotPlan,Reduces,Apart,Split,Safe,Pending,Followable,Limited,NotClaimed,WillStay event
    class Absent,Export io
```

The diagram shows the topology and data flow of the system as built. The full architectural narrative, with screenshots and prose, lives in [`documents/household-privacy-audit.md`](./documents/household-privacy-audit.md).

## Implementation

This system is built across **6 phases**:

1. **Establishing a Privacy-First Audit Workspace**
2. **Planning Consent and Research Evidence**
3. **Verifying Settings, Memory, and Privacy Boundaries**
4. **Recording Export and Chat Review Decisions**
5. **Completing a Redacted, Evidence-Based Settings Record**
6. **Demonstrating Least-Disclosure Practices**

For the full walkthrough with screenshots and step-by-step content, see [`documents/household-privacy-audit.md`](./documents/household-privacy-audit.md).

## Validation

Each build phase below is documented in [`documents/household-privacy-audit.md`](./documents/household-privacy-audit.md), with screenshots, configuration, and notes as captured during the build:

- ✅ Establishing a Privacy-First Audit Workspace
- ✅ Planning Consent and Research Evidence
- ✅ Verifying Settings, Memory, and Privacy Boundaries
- ✅ Recording Export and Chat Review Decisions
- ✅ Completing a Redacted, Evidence-Based Settings Record
- ✅ Demonstrating Least-Disclosure Practices
