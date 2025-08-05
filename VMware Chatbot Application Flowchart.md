graph TD
    subgraph User Interaction (Frontend)
        A[User Types Query in Chat Interface] --> B{Is it a direct question or needs data?};
        B -- Direct Question --> C[Display "Thinking..." Loader];
        B -- Needs Data --> C;
        C --> D[Send Query to Backend (Flask app.py)];
    end

    subgraph Backend Processing (app.py)
        D --> E[Receive Query at /chat Endpoint];
        E --> F{LLM Decision: Tool Call or Direct Response?};
        F -- Tool Call Indicated --> G[Identify Tool Name & Parameters];
        F -- Direct Response --> P[Generate Natural Language Response (LLM)];

        G --> H[Authenticate API Call (OAuthHandler)];
        H -- Token Acquired/Refreshed --> I[Execute API Call (MCPServer)];
        H -- Authentication Failed --> J[Generate Error Response (LLM)];

        I --> K{API Call Successful?};
        K -- Yes, Data Received --> L[Summarize Raw API Data (app.py)];
        K -- No, API Error --> J;

        L --> M[Generate Natural Language Response with Data (LLM)];

        J --> N[Add Bot Response to Chat History];
        M --> N;
    end

    subgraph Frontend Rendering (index.html)
        N --> O[Receive Bot Response & Message Index];
        O --> P[Remove "Thinking..." Loader];
        P --> Q[Render Bot Message in Chat Interface];
        Q -- If Tabular Data Detected --> R[Add CSV/PDF Download Buttons];
        Q --> S[Auto-scroll to Latest Message];
    end

    style A fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;
    style B fill:#d0eef5,stroke:#007CBB,stroke-width:2px,color:#333333;
    style C fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
    style D fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;

    style E fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;
    style F fill:#d0eef5,stroke:#007CBB,stroke-width:2px,color:#333333;
    style G fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
    style H fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;
    style I fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
    style J fill:#f8d7da,stroke:#dc3545,stroke-width:2px,color:#721c24;
    style K fill:#d0eef5,stroke:#007CBB,stroke-width:2px,color:#333333;
    style L fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
    style M fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;
    style N fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;

    style O fill:#e0f2f7,stroke:#007CBB,stroke-width:2px,color:#333333;
    style P fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
    style Q fill:#d0eef5,stroke:#007CBB,stroke-width:2px,color:#333333;
    style R fill:#d4edda,stroke:#28a745,stroke-width:2px,color:#155724;
    style S fill:#f5f5f5,stroke:#cccccc,stroke-width:1px,color:#666666;
