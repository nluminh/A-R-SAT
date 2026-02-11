```mermaid
flowchart TD
    A[Data Collection] --> B[Data Cleaning]
    B --> C[Data Exploration]
    C -->|Check Correlations| D[Model Building]
    C -->|Visualize Data| E[Reporting]
    D --> F[Model Evaluation]
    F -->|Reiterate|D
    E -->|Share Findings| G[Stakeholders]
    G --> H[Decision Making]
```