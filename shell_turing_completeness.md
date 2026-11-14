mermaid

```mermaid
flowchart TD
    CTSS["CTSS<br/>N/A"]
    RUNCOM["RUNCOM<br/>NTC<br/>Louis Pouzin"]
    STRACHEY["Strachey's macro-generator<br/>NTC<br/>Christopher Strachey"]
    MULTICS["Multics shell<br/>TC<br/>Glenda Schroeder and GE collaborator"]
    THOMPSON["Thompson shell<br/>NTC<br/>Ken Thompson"]
    PWB["PWB / Mashey shell<br/>TC<br/>John Mashey"]
    BOURNE["Bourne shell<br/>TC<br/>Stephen Bourne"]
    BASH["Bash<br/>TC<br/>Brian Fox"]

    CTSS --> RUNCOM
    RUNCOM --> MULTICS
    STRACHEY --> MULTICS
    MULTICS --> THOMPSON
    THOMPSON --> PWB
    THOMPSON --> BOURNE
    PWB -.-> BOURNE
    BOURNE --> BASH
```

Legend:

- TC = Turing Complete
- NTC = Not Turing Complete
- CTSS = Operating system; TC/NTC distinction does not apply.
- Solid arrow = Major inspiration.
- Dashed arrow = Minor inspiration.
