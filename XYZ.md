flowchart LR

%% ENTRY
A[User] --> B[Landing Page]

B --> C{Login Role}

C --> D[Student Login]
C --> E[Teacher Login]

D --> F[Auth System]
E --> F

F --> G{Verified Role}

G --> H[Student Dashboard]
G --> I[Teacher Dashboard]

%% STUDENT MODULES
subgraph Student Dashboard
H --> S1[Mood Feedback]
H --> S2[Assignments]
H --> S3[Workload Analyzer]
H --> S4[Stress Analysis]
H --> S5[Doubt Exchange]
H --> S6[Smart Attendance]
end

%% TEACHER MODULES
subgraph Teacher Dashboard
I --> T1[Mood Analytics]
I --> T2[Stress Alerts]
I --> T3[Assignment Stats]
I --> T4[Doubt Monitoring]
I --> T5[AI Teaching Suggestions]
end

%% AI SYSTEM
subgraph AI Engine
AI1[User Query] --> AI2[Ollama]
AI2 --> AI3[Mistral Model]
AI3 --> AI4[AI Insight]
end

%% DATABASE
subgraph Database
DB1[(Users)]
DB2[(Mood Data)]
DB3[(Assignments)]
DB4[(Stress Records)]
DB5[(Attendance)]
DB6[(Doubts)]
DB7[(Security Logs)]
end

%% DATA STORAGE
S1 --> DB2
S2 --> DB3
S4 --> DB4
S6 --> DB5
S5 --> DB6
F --> DB1
