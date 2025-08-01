# Refactoring with IDGL: A Strategic, Spec-Driven Approach

## The Human-AI Partnership in Refactoring

In the IDGL framework, refactoring is a strategic, human-led activity, not a blind, automated process. The AI serves as a powerful and efficient tool for executing changes, but the IDGL Practitioner is the architect who directs the process. This partnership has a clear division of labor:

*   **The IDGL Practitioner (The Strategist):** Identifies the need for refactoring, defines the precise goal in a high-quality **Spec** (`intent.md`), and serves as the ultimate validator of the result.
*   **The AI (The Tool):** Analyzes the codebase for potential improvements and executes the tedious, large-scale changes defined in the practitioner's spec with speed and precision.

## Two Scales of Refactoring

The IDGL provides two distinct, formal processes for handling refactoring, depending on the scope and risk of the change. The practitioner must strategically decide which process is appropriate for the task at hand.

```mermaid
graph TD
    A["Practitioner Identifies<br/>Need for Refactoring"] --> B{Assess Scope & Risk};
    B -->|Shallow / Low-Risk| C["Handle as a Sustaining Task"];
    B -->|Deep / High-Risk| D["Handle as a Re-Generation Phase"];

    subgraph "Lifecycle 2: Sustaining"
        C
    end

    subgraph "Lifecycle 1: Initial Generation (Again)"
        D
    end

    classDef blue fill:#e0e7ff,stroke:#5a79e0,color:#000
    classDef green fill:#e0ffe0,stroke:#5ae05a,color:#000
    
    class A,B blue
    class C,D green
```

### 1. Shallow Refactoring (as a Sustaining Task)

This process is used for localized, low-risk changes that improve the health of a specific component without altering the system's architecture.

*   **Examples:** Renaming a variable for clarity, extracting a complex function, converting a single module to a new pattern (e.g., `async/await`).
*   **Process:** A shallow refactoring is treated as an ad-hoc **Generative Task** and is registered within the **Sustaining Lifecycle**.
*   **Directory Structure:** A new task folder is created within the `sustaining/` directory of the relevant feature.
    ```
    .idgl/sustaining/authentication/refactor-login-function-for-clarity/
    ```

### 2. Deep Refactoring (as a Re-Generation Phase)

This process is reserved for large-scale, high-risk, architectural changes that fundamentally reshape a part of the system.

*   **Examples:** Migrating a backend framework, breaking a monolith into microservices, changing a core database paradigm.
*   **Process:** A deep refactoring **must be escalated to a formal Re-Generation Phase**. This is a full **Development Phase** with a specific `Main Goal` of rebuilding a decayed or outdated part of the system.
*   **Key Step:** The `01_system_design` task for this phase is critical. It must use the entire maintenance history from the `sustaining/` folder as a primary input, ensuring that the new architecture is explicitly informed by the documented problems of the old one.
*   **Directory Structure:** A new, numbered `Development Phase` folder is created at the root of the `.idgl` directory.
    ```
    .idgl/04-refactor-backend-to-microservices-phase/
    ```

By providing distinct, formal processes for both shallow and deep refactoring, the IDGL ensures that every change, from a simple renaming to a full architectural overhaul, is a deliberate, spec-driven, and traceable activity, safeguarding the long-term health and maintainability of the project. 