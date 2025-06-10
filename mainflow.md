'''
flowchart TD
  %% Client Management
  subgraph Client Management
    A1[Client Registration Screen] --> DS_Client[(Client Table)]
    A2[Branch Registration Screen] --> DS_Branch[(Branch Table)]
    A3[Admin Registration Screen] --> DS_Admin[(Admin Table)]
  end

  %% Project Management
  subgraph Project Management
    B1[Project Creation Screen] --> DS_Project[(Project Table)]
    B2[Lead Entry]               --> DS_Lead[(Lead Table)]
    DS_Client                    --> DS_Project
    DS_Branch                    --> DS_Project
    DS_Lead                      --> DS_Project
  end

  %% Scan & Inspection
  subgraph Scan & Inspection
    C1[LiDAR Scan Execution]     --> DS_Scan[(Scan Table)]
    C2[AI Detection Processing]  --> DS_Inspection[(Inspection Table)]
    C3[Rescan Marker Read]       --> DS_Scan
  end

  %% Plan & Estimate
  subgraph Plan & Estimate
    D1[Plan Creation]            --> DS_Plan[(Plan Table)]
    D2[Simple Estimate]          --> DS_EstimateSimple[(Estimate Simple Table)]
    D3[Detailed Estimate]        --> DS_Estimate[(Estimate Table)]
    DS_Plan                      --> DS_EstimateSimple
    DS_EstimateSimple            --> DS_Estimate
  end

  %% Invoice & Financial Planning
  subgraph Invoice & Financial Planning
    E1[Invoice Issuance]         --> DS_Invoice[(Invoice Table)]
    E2[Financial Plan Creation]  --> DS_FinPlan[(Financial Plan Table)]
    DS_Estimate                  --> DS_Invoice
  end
