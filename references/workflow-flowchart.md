# Carousel for IG — Workflow Flowchart

This is the operating map for turning a raw idea into a publish-ready Instagram carousel. A failed decision returns only to the nearest relevant stage, so approved work stays intact.

```mermaid
flowchart TD
    A["Raw idea or trend"] --> B["Build brief"]
    B --> C{"Audience and learning outcome clear?"}
    C -- "No" --> B
    C -- "Yes" --> D["Research and source check"]
    D --> E{"Angle distinct and useful?"}
    E -- "No" --> F["Reframe or remove overlap"]
    F --> D
    E -- "Yes" --> G["Storyboard and visual system"]
    G --> H["Create DRAFT"]
    H --> I{"User approval?"}
    I -- "Revise" --> J["Scoped revision"]
    J --> H
    I -- "Approve" --> K["Final QA"]
    K --> L{"QA passed?"}
    L -- "No" --> M["Fix failed checks"]
    M --> K
    L -- "Yes" --> N["Final package"]
    N --> O{"Publish approved?"}
    O -- "Not yet" --> P["READY TO PUBLISH"]
    O -- "Yes" --> Q["Publish"]
    Q --> R["Measure saves, shares, reach"]
    R --> S["Feed lessons into next brief"]
    S --> B
```

## Approval gates

| Gate | Pass condition | If it fails |
|---|---|---|
| Brief | Audience and learning outcome are explicit | Clarify the brief |
| Angle | Distinct, useful, sourceable and visually viable | Reframe or remove overlap |
| Draft | User approves the concept, narrative and requested visuals | Revise only the requested scope |
| QA | Copy, crop, sequence, dimensions and files pass inspection | Fix failed checks and re-run QA |
| Publish | User explicitly approves publishing | Hold as READY TO PUBLISH |

## State labels

Use one unambiguous status at a time:

`NEW → RESEARCHING → STRATEGY_READY → DRAFT_READY → REVISION or APPROVED → READY_TO_PUBLISH → PUBLISHED`
