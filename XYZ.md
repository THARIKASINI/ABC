# AcademicIntel AI -- System Architecture & Flow

## Overview

AcademicIntel AI is a modern AI-powered academic intelligence platform
designed for universities to analyze classroom engagement, student
stress, assignment workloads, and academic performance.

Built with: - Next.js 14 (App Router) - TailwindCSS - Glassmorphism UI -
Lucide Icons - Recharts / Chart.js - Ollama (Local AI Models)

------------------------------------------------------------------------

# High Level Architecture

User (Student / Teacher) \| v Next.js Frontend (App Router) \| v API
Layer (Next.js Server Actions / API Routes) \| v Database Layer
(PostgreSQL / MySQL / Prisma) \| v AI Engine (Local Ollama Model --
Mistral) \| v Analytics Engine \| v Dashboards & Graph Visualizations

------------------------------------------------------------------------

# Application Page Flow

## 1. Landing Page

Purpose: Introduce the AcademicIntel AI platform.

Sections: - Hero Section - Feature Cards - Platform Overview - Dashboard
Preview - Call To Action

User Actions: - Explore platform - Navigate to login

Navigation:

Landing Page \| v Login Page

------------------------------------------------------------------------

# 2. Authentication Flow

User selects role:

Student Teacher

Login Fields: - Student ID / Email - Password - Role Selection

Flow:

User Login \| v Role Verification \| \|---- Student → Student Dashboard
\| \|---- Teacher → Teacher Dashboard

------------------------------------------------------------------------

# 3. Student Dashboard Flow

Main Modules:

1.  Mood Feedback System
2.  Assignment Submission Portal
3.  Workload Analyzer
4.  Personal Stress Analysis
5.  Anonymous Doubt Exchange
6.  Smart Attendance System

------------------------------------------------------------------------

# Mood Feedback System Flow

Student selects mood:

Confused Bored Interested Too Fast Too Slow

Flow:

Student → Select Mood \| v IP Address Validation \| v Check Lecture
Session \| v Allow One Submission \| v Store Data in Database \| v
Update Mood Graph

Stored Fields:

-   student_id
-   ip_address
-   lecture_id
-   mood_type
-   timestamp

------------------------------------------------------------------------

# Assignment Submission Flow

Student uploads assignment file.

Flow:

Student Upload \| v Deadline Validation \| v File Storage \| v
Submission Logging

Stored Fields:

-   student_id
-   ip_address
-   timestamp
-   deadline
-   delay_time
-   submission_status

System Features:

Deadline Detector If deadline \< 24 hours → Warning Notification

------------------------------------------------------------------------

# Workload Analyzer Flow

Input Data:

-   assignments_per_week
-   late_submissions
-   missed_assignments

Workload Score Formula:

workload_score = (assignments_per_week \* 2) + (late_submissions \* 3) +
(missed_assignments \* 5)

Flow:

Assignment Data \| v Workload Calculator \| v Score Generation \| v
Progress Meter Visualization

------------------------------------------------------------------------

# Personal Stress Analysis Flow

Stress Score Factors:

-   Mood Feedback History
-   Assignment Delays
-   Workload Score
-   Academic Decline

Flow:

Student Data \| v Stress Evaluation Engine \| v Stress Level
Classification

Levels:

Low Stress Moderate Stress High Stress Burnout Risk

Charts:

-   Stress Timeline
-   Trend Analysis

------------------------------------------------------------------------

# Anonymous Doubt Exchange Flow

Student posts doubt anonymously.

Flow:

Post Question \| v Abusive Language Filter \| \|---- Clean Message →
Post Anonymously \| \|---- Abusive Message → Reveal Student Identity
Send to Teacher

Students can:

-   Answer questions
-   Upvote answers
-   Tag subjects

When upvotes reach threshold:

Question → Marked as Solved

------------------------------------------------------------------------

# Smart Attendance System Flow

Attendance Process:

Student opens camera page.

Flow:

Camera Capture \| v Face Recognition Engine \| v Match with Student
Dataset \| v IP Verification (College WiFi) \| v Attendance Marked

Restrictions:

-   One attendance per IP
-   Must match registered face
-   Must be inside campus network

------------------------------------------------------------------------

# Teacher Dashboard Flow

Teacher Dashboard Modules:

1.  Classroom Mood Analytics
2.  Student Stress Monitoring
3.  Assignment Analytics
4.  Doubt Monitoring
5.  AI Teaching Suggestions

------------------------------------------------------------------------

# Classroom Mood Analytics Flow

Data Source:

Student mood submissions.

Flow:

Mood Data \| v Analytics Engine \| v Graph Visualization

Charts:

-   Pie Chart (Mood Distribution)
-   Timeline Engagement Graph

------------------------------------------------------------------------

# AI Teaching Suggestion System

Rule Based Logic:

If confusion \> 40%

Suggestion: Review previous concept

If boredom \> 50%

Suggestion: Increase lecture pace

If "Too Fast" responses increase

Suggestion: Slow down explanation

Flow:

Mood Analytics \| v Suggestion Engine \| v Teacher Notification

------------------------------------------------------------------------

# Student Stress Alert System

Flow:

Student Analytics \| v Stress Threshold Detection \| v Teacher Alert

Example Alert:

Student ID: STU104 Stress Level: High

Reasons:

-   Multiple late assignments
-   High confusion mood
-   Increasing workload score

------------------------------------------------------------------------

# Assignment Analytics Flow

Teacher View:

Assignment completion rates Late submissions Workload distribution

Visualization:

Bar Charts Pie Charts Trend Graphs

------------------------------------------------------------------------

# AI Architecture

Local AI Model:

Ollama

Example Model:

Mistral

Processing Flow:

User Query \| v Local Ollama Model \| v Generated Response \| v
Displayed in Dashboard

------------------------------------------------------------------------

# Data Security System

Security Controls:

-   One mood submission per IP per lecture
-   One attendance per IP per class
-   Doubt post spam detection
-   Abuse monitoring
-   Teacher log review

Logs Stored:

-   IP address
-   student_id
-   action_type
-   timestamp

------------------------------------------------------------------------

# Graph System

Graphs used across platform:

-   Mood Distribution
-   Stress Trends
-   Assignment Workload
-   Submission Rate
-   Class Engagement Timeline

Visualization Libraries:

-   Recharts
-   Chart.js

------------------------------------------------------------------------

# UI Design System

Design Style:

Glassmorphism

Features:

-   Frosted glass cards
-   Soft purple gradients
-   Baby pink highlights
-   Blur backgrounds
-   Smooth hover animations

Components:

Navbar Floating Cards Analytics Panels Charts Interactive Buttons

------------------------------------------------------------------------

# Final Platform Flow

Landing Page \| v Login Page \| v Role Authentication \| \|---- Student
Dashboard \| \| \|-- Mood Feedback \| \|-- Assignment Portal \| \|--
Workload Analyzer \| \|-- Stress Analysis \| \|-- Doubt Exchange \| \|--
Smart Attendance \| \| \|---- Teacher Dashboard \| \|-- Classroom Mood
Analytics \|-- Stress Alerts \|-- Assignment Analytics \|-- Doubt
Monitoring \|-- AI Teaching Suggestions

------------------------------------------------------------------------

# End of Architecture Flow
