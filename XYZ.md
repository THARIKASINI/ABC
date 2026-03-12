# AcademicIntel AI -- Full System Flow & Architecture

This document describes the **complete functional flow** of the
AcademicIntel AI platform.

------------------------------------------------------------------------

# High-Level Platform Flow

``` mermaid
flowchart TD

A[User Opens Platform] --> B[Landing Page]

B --> C{User Chooses Login}
C -->|Student| D[Student Login]
C -->|Teacher| E[Teacher Login]

D --> F[Authentication System]
E --> F

F --> G{Role Verification}

G -->|Student| H[Student Dashboard]
G -->|Teacher| I[Teacher Dashboard]

%% STUDENT SIDE

subgraph Student_System

H --> S1[Mood Feedback System]
H --> S2[Assignment Portal]
H --> S3[Workload Analyzer]
H --> S4[Stress Analysis Engine]
H --> S5[Anonymous Doubt Exchange]
H --> S6[Smart Attendance]

%% Mood System
S1 --> S1A[Student Selects Mood]
S1A --> S1B[Check IP Address]
S1B --> S1C{Already Submitted?}
S1C -->|No| S1D[Store Mood in Database]
S1C -->|Yes| S1E[Reject Submission]

S1D --> S1F[Update Mood Graph]
S1F --> S1G[Send Data to Teacher Dashboard]

%% Assignment Portal
S2 --> S2A[Upload Assignment]
S2A --> S2B[Deadline Check]
S2B --> S2C{Late Submission?}
S2C -->|Yes| S2D[Calculate Delay Time]
S2C -->|No| S2E[Normal Submission]

S2D --> S2F[Store Submission Data]
S2E --> S2F

S2F --> S2G[Update Submission History]
S2G --> S2H[Update Assignment Analytics]

%% Workload Analyzer
S3 --> S3A[Fetch Assignment Data]
S3A --> S3B[Count Assignments Per Week]
S3A --> S3C[Count Late Submissions]
S3A --> S3D[Count Missed Assignments]

S3B --> S3E[Workload Formula Engine]
S3C --> S3E
S3D --> S3E

S3E --> S3F[Generate Workload Score]
S3F --> S3G[Display Progress Meter]

%% Stress Analysis
S4 --> S4A[Collect Mood History]
S4 --> S4B[Collect Assignment Delays]
S4 --> S4C[Collect Workload Score]
S4 --> S4D[Collect Academic Trend]

S4A --> S4E[Stress Calculation Engine]
S4B --> S4E
S4C --> S4E
S4D --> S4E

S4E --> S4F{Stress Level}

S4F -->|Low| S4G[Low Stress]
S4F -->|Moderate| S4H[Moderate Stress]
S4F -->|High| S4I[High Stress]
S4F -->|Critical| S4J[Burnout Risk]

%% Doubt Exchange
S5 --> S5A[Student Posts Doubt]
S5A --> S5B[Abusive Language Filter]

S5B -->|Clean| S5C[Post Anonymously]
S5B -->|Abusive| S5D[Reveal Identity]

S5D --> S5E[Send Report to Teacher]

S5C --> S5F[Students Answer]
S5F --> S5G[Upvote System]

S5G --> S5H{Upvotes Threshold}

S5H -->|Reached| S5I[Mark Doubt Solved]

%% Smart Attendance
S6 --> S6A[Open Camera]
S6A --> S6B[Capture Face]
S6B --> S6C[Face Recognition]
S6C --> S6D{Face Match}

S6D -->|Yes| S6E[Verify IP Address]
S6D -->|No| S6F[Reject Attendance]

S6E --> S6G{College WiFi?}

S6G -->|Yes| S6H[Mark Attendance]
S6G -->|No| S6I[Reject]

end

%% TEACHER SIDE

subgraph Teacher_System

I --> T1[Classroom Mood Dashboard]
I --> T2[Student Stress Monitor]
I --> T3[Assignment Analytics]
I --> T4[Doubt Monitoring]
I --> T5[AI Teaching Suggestions]

%% Mood Dashboard
T1 --> T1A[Collect Student Mood Data]
T1A --> T1B[Generate Pie Chart]
T1A --> T1C[Generate Timeline Graph]

%% Stress Alerts
T2 --> T2A[Fetch Stress Scores]
T2A --> T2B{Stress Threshold}

T2B -->|High| T2C[Generate Alert]
T2C --> T2D[Notify Teacher]

%% Assignment Analytics
T3 --> T3A[Fetch Submission Data]
T3A --> T3B[Completion Rate Graph]
T3A --> T3C[Late Submission Graph]
T3A --> T3D[Workload Distribution]

%% Doubt Monitoring
T4 --> T4A[Monitor Doubt Activity]
T4A --> T4B[Detect Abusive Posts]
T4B --> T4C[Reveal Student Identity]

%% AI Suggestions
T5 --> T5A[Analyze Mood Data]
T5A --> T5B{Confusion > 40%}
T5B -->|Yes| T5C[Suggest Review Concept]

T5A --> T5D{Boredom > 50%}
T5D -->|Yes| T5E[Suggest Increase Pace]

T5A --> T5F{Too Fast Feedback}
T5F -->|Yes| T5G[Suggest Slow Down]

end

%% AI SYSTEM

subgraph AI_System

AI1[User Query]
AI1 --> AI2[Send to Ollama]
AI2 --> AI3[Local Model - Mistral]
AI3 --> AI4[Generate AI Insight]
AI4 --> AI5[Return Suggestion]

end

%% DATA LAYER

subgraph Database

DB1[(Users)]
DB2[(Mood Logs)]
DB3[(Assignments)]
DB4[(Stress Scores)]
DB5[(Attendance)]
DB6[(Doubts)]
DB7[(Security Logs)]

end

S1D --> DB2
S2F --> DB3
S4E --> DB4
S6H --> DB5
S5A --> DB6
S1B --> DB7
```

------------------------------------------------------------------------

# Technology Stack

Frontend - Next.js 14 (App Router) - TailwindCSS - Lucide Icons -
Recharts / Chart.js

Backend - Next.js API Routes

AI Layer - Ollama - Mistral Model

Database - PostgreSQL / MySQL - Prisma ORM

------------------------------------------------------------------------

# Security Rules

• One mood submission per IP per lecture\
• One attendance per IP per class\
• Doubt spam prevention\
• Abusive language detection\
• Teacher review logs

------------------------------------------------------------------------

# End of System Flow
