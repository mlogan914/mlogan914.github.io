```mermaid

flowchart LR
  %% Sources
  subgraph SRC[Sources]
    CRM[(CRM)]
    EHR[(Clinical App)]
    LIMS[(Lab System)]
    Sheets[(Spreadsheets)]
  end

  %% Ingestion / Landing (mixed methods)
  subgraph ING[Ingestion & Landing]
    SFTP[(SFTP Drop)]
    API[[API Pull]]
    Intake[(Landing / S3)]
    NAS[(Shared Drive)]
  end

  %% Processing (split paths)
  subgraph PROC[Processing]
    Legacy[[Legacy ETL]]
    Scripts[[Ad-hoc Scripts]]
  end

  %% Storage (two truths)
  subgraph STORE[Storage]
    OnDW[(On-Prem DW)]
    Cloud[(Cloud DW)]
  end

  %% Serving
  subgraph SERVE[Serving]
    FinMart[(Finance Mart)]
    OpsMart[(Ops Mart)]
  end

  %% Consumption
  subgraph CONS[Consumption]
    BI[[BI Dashboards]]
    XLS[(Excel Reports)]
  end

  %% Flows
  CRM -- nightly --> SFTP --> Intake
  EHR -- API --> API --> Intake
  LIMS -- weekly --> SFTP --> NAS
  Sheets -. ad-hoc .-> NAS

  Intake --> Scripts --> Cloud
  NAS --> Legacy --> OnDW
  Cloud --> OpsMart --> BI
  OnDW --> FinMart --> BI
  OnDW --> XLS

  %% Styling
  classDef manual fill:#f0f0f0,stroke:#888,stroke-dasharray:4 2;
  classDef warn fill:#fff1e6,stroke:#ff9f1c,stroke-width:2px;

  Sheets:::manual
  NAS:::warn
  OnDW:::warn
  ```
