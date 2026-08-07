# Gemini Directives for this Codebase

This document contains a set of standing orders and best practices for me, Gemini, to follow while working in this directory. My primary goal is to produce robust, maintainable, and correct solutions while minimizing unnecessary trial-and-error. There are many diverse sub-projects here, so I should not assume requirements for one task will apply to others, though general principles are more likely to persist.

## Core Directives

### 1. Analyze the Output Format Before Choosing Tools

**Directive:** Before selecting a particular solution (e.g. templating engine), I must first analyze its suitability for the exact task in hand.

**Checklist:**
-   **Identify special characters:** Does the format use characters that are common in templating languages (e.g., `{}`, `\`, `%`, `&`, `$`)?
-   **Assess syntax complexity:** Is the syntax complex and sensitive to whitespace or special characters?
-   **Anticipate parsing conflicts:** Based on the above, I will anticipate potential parsing conflicts with standard templating engines.

**Action:**
-   If high risk of conflict is identified (e.g., with LaTeX), I will immediately prioritize a more robust generation strategy. This means:
    1.  **First, attempt a templating engine with custom delimiters** that do not conflict with the target syntax.
    2.  **If custom delimiters are not supported or fail, immediately pivot to a code-only generation approach.** I will not get stuck in a loop trying to fix a failing templating engine.

### 2. Prioritize Robustness over "Standard" Tooling

**Directive:** I must recognize that "popular" or "standard" tools are not always the best fit for every problem. When a standard tool proves to be a poor fit, I will pivot to a more suitable, even if more verbose, solution.

**Action:**
-   If a templating engine fails more than twice on the same fundamental parsing issue, I will immediately abandon it and switch another approach which would avoid the problem (either a different tool of the same type, or a new approach entirely), clearly explaining to the user why I am making this change.

### 3. Handle Format-Specific Quirks Proactively

**Directive:** I must proactively handle any known quirks of the target output format.

**Checklist:**
-   **Character Escaping:** Have I identified and correctly escaped all necessary characters for the target format (e.g., `&` to `\&` in LaTeX)?
-   **Whitespace and Newlines:** Am I controlling whitespace and newlines precisely, as required by the target format?

**Action:**
-   I will incorporate the necessary escaping and formatting logic directly into my generation code. I will not assume that a templating engine will handle this correctly by default.

### 4. Deconstruct Complex Prompts into a Clear Plan

**Directive:** For any multi-step task, I will first deconstruct the user's request into a clear, actionable plan. I will then share a concise version of this plan with the user before I begin.

**Checklist:**
-   **Identify the core goal:** What is the user's ultimate objective (e.g., "make the CV easier to maintain")?
-   **Identify the technical steps:** What are the necessary technical steps to achieve this goal?
-   **Identify potential roadblocks:** What are the likely points of failure or difficulty (e.g., syntax conflicts)?
-   **Formulate a primary strategy and a fallback plan.**

**Action:**
-   I will always start my response to a complex request with a brief summary of my plan, including my chosen tools and fallback strategy. This will give the user an opportunity to correct my course before I begin a long and potentially flawed implementation.

### 5. Learning from experience

**Directive:** Once the project is confirmed to be complete, I shall update this document with any learnings that are generalizable.

**Checklist:**
-   **Improvements:** Was there anything that could have been achieved more efficiently by taking a different approach?
-   **Principles:** Can this improvements be generalized to underlying principles which are more generally applicable?

**Action:**
-   I will always review the work I did at the end of the project, and incorporate my learnings in this document in the most useful form I can to help with future work.

By adhering to these directives, I will improve the quality and efficiency of my work in future projects.
