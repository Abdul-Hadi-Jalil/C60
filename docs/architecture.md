# Architecture

```mermaid
flowchart TB
    subgraph Sources
      S1[Marketplace API]
      S2[Advertising API]
      S3[Inventory API]
      S4[Controlled file inputs]
    end
    subgraph Azure
      FN[Scheduled ingestion functions]
      RT[Retry queue]
      LAKE[(Raw and state data lake)]
      DB[(Private PostgreSQL warehouse)]
      KV[Key Vault]
      MON[Logs and alerts]
    end
    BI[Business intelligence]
    S1 --> FN
    S2 --> FN
    S3 --> FN
    S4 --> LAKE
    KV --> FN
    FN --> LAKE --> DB --> BI
    FN <--> RT
    FN -.-> MON
    DB -.-> MON
```

Every source implements a client, adapter, orchestration unit, schedule, and retry policy. Raw data lands first. The warehouse loads validated captures and rebuilds facts and marts in a single controlled model run.
