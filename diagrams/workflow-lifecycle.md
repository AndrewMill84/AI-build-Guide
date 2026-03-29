# Workflow Lifecycle Diagram

The complete 9-stage workflow with decision points, feedback loops, and artifact outputs.

```mermaid
flowchart TD
    START(("🚀 New\nProject")) --> S1

    subgraph DISCOVER["📋 Discovery"]
        S1["Stage 1\nIdea Capture"]
        S2["Stage 2\nClarification"]
        S3["Stage 3\nSpecification"]
    end

    subgraph DESIGN["🔧 Design"]
        S4["Stage 4\nTechnical Plan"]
        S5["Stage 5\nTask Breakdown"]
    end

    subgraph BUILD["⚡ Build"]
        S6["Stage 6\nImplementation"]
        S7["Stage 7\nReview & Validation"]
    end

    subgraph CLOSE["📦 Close"]
        S8["Stage 8\nDocumentation"]
        S9["Stage 9\nHandoff"]
    end

    S1 -->|"01-idea.md"| S2
    S2 -->|"02-clarification.md"| S3
    S3 -->|"03-spec.md ✅"| S4
    S4 -->|"04-plan.md ✅"| S5
    S5 -->|"05-tasks.md"| S6
    S6 -->|"06-impl-log.md"| S7
    S7 -->|"07-review.md ✅"| S8
    S8 -->|"08-report.md"| S9
    S9 -->|"09-handoff.md"| DONE

    DONE(("✅ Complete"))

    S2 -.->|"idea unclear"| S1
    S4 -.->|"spec gap"| S3
    S6 -.->|"plan update"| S4
    S7 -.->|"issues found"| S6

    S9 -.->|"next phase"| START

    style START fill:#4a90d9,color:#fff,stroke:#3a7bc8
    style DONE fill:#27ae60,color:#fff,stroke:#1a9e50
    style DISCOVER fill:#e8f0fe,stroke:#4a90d9
    style DESIGN fill:#f3e8ff,stroke:#7b68ee
    style BUILD fill:#fff3e0,stroke:#e67e22
    style CLOSE fill:#e8f5e9,stroke:#27ae60
```

## Reading the Diagram

- **Solid arrows** → Normal forward flow with the artifact name produced at each stage
- **Dashed arrows** → Feedback loops when issues are discovered
- **✅ marks** → Stages where human approval is required before proceeding
- **Subgroups** → The four phases: Discovery, Design, Build, Close
- **"next phase" loop** → When a project hands off to a follow-up phase, it starts a new project at Stage 1
