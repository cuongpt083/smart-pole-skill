# Logic of the SMART POLE Framework

The SMART POLE framework is designed to eliminate the "guessing" that AI does when faced with vague context. By breaking down "context" into 9 distinct categories, we ensure every "atom" of information is placed exactly where the AI can process it most efficiently.

## Deep Dive into Categories

### 1. S - Style (The AI's Mask)
- **Concept**: The persona the AI wears.
- **Atoms**: "Cynical noir," "Helpful tutor," "Academic paper."
- **Logic**: Sets the vocabulary and syntactic structure of the *response*.
- **God-tier (The Persuasion Scalpel)**: Embed Cialdini's Principles:
  - *Authority*: Cite technical jargon to establish expertise.
  - *Social Proof*: "10,000 users already pre-ordered."
  - *Unity*: Use "we" language for tribal belonging.
- **Persona Specificity**: Not "Be a salesperson" → "Be a **Tech-Evangelist** who is visibly excited."

### 2. M - Mastery (The User's Level)
- **Concept**: Who is the user? What is their cognitive load capacity?
- **Atoms**: "Senior Architect (High context)," "5-year-old child (Low context)," "Intermediate knitter."
- **Logic**: Prevents "average" explanations by locking into a specific expertise tier for the *explanation*.
- **Domain vs Task Mastery (v3.1)**: Always distinguish between:
  - **Domain Mastery**: Expertise in the user's professional field (e.g., "10-year Civil Engineer")
  - **Task Mastery**: Expertise in the specific task being requested (e.g., "first time programming")
  - **The Gap**: A user can have high Domain Mastery but zero Task Mastery. This gap dramatically changes how the AI should respond.
  - *Example*: "Senior DevOps Engineer" (Domain) + "Never written a business plan" (Task) = must explain business concepts using engineering analogies.

### 3. A - Aim (The Objective & Scorecard)
- **Concept**: The specific result and how it will be judged.
- **Atoms**: "Persuade a skeptic," "Summarize for a CEO," "Success = User feels confident."
- **Logic**: Gives the AI a success metric and evaluation criteria.

### 4. R - Resource (The Toolbox)
- **Concept**: What does the AI have to work with?
- **Atoms**: "Use only the attached PDF," "Budget: $0," "Equipment: One laptop."
- **Logic**: Prevents the AI from suggesting impossible or irrelevant solutions.
- **God-tier (The Constraint Clamp)**: Include **Negative Atoms** (what is NOT allowed).
  - *Positive*: "Budget: $500, Tools: CapCut free."
  - *Negative*: "**NO** CGI, **NO** paid ads, **NO** professional studio."
- **Why**: Stops AI from suggesting "pie-in-the-sky" solutions you can't execute.

### 5. T - Time (The Schedule/Era)
- **Concept**: When is this happening, or how long should it take?
- **Atoms**: "Set in 1920s Paris," "Deadline: 2 hours," "Duration: 5-minute read."
- **Logic**: Grounds the response in a temporal context.

### 6. P - People (The Human Variable)
- **Concept**: Who is this for? What do they value? What are their internal beliefs?
- **Atoms**: "Audience: Busy parents," "Value: Efficiency over cost," "Persona: Introverted," "Belief: Sustainability is key."
- **Logic**: Adjusts the empathy and focus of the response to match the user's worldview.

### 7. O - Outline (The Skeleton & Scope)
- **Concept**: The structural constraints and what to *exclude*.
- **Atoms**: "3 acts," "Bullet points followed by a table," "Ignore backyard gardens," "Focus only on balcony."
- **Logic**: Controls the layout and density of the information.

### 8. L - Locale (The Setting)
- **Concept**: The physical or conceptual environment, broken down into 4 sub-dimensions:
    - **L1 - Industry/Domain**: Banking, Healthcare, E-commerce, etc.
    - **L2 - Geography/Region**: Vietnam, EU, USA, etc.
    - **L3 - Legal/Regulatory**: GDPR, HIPAA, PCI-DSS.
    - **L4 - Cultural/Social**: Local customs, user behavior norms.

- **Priority Logic**: The importance of these 4 dimensions shifts based on the Industry context.
    - **Banking**: Legal (L3) > Industry (L1) > Geo (L2) > Cultural (L4).
    - **Healthcare**: Legal (L3) > Industry (L1) > Cultural (L4) > Geo (L2).
    - **E-commerce**: Cultural (L4) > Geo (L2) > Industry (L1) > Legal (L3).
    - *General Rule*: Industry > Geo > Cultural > Legal.
    
- **Logic**: Ensures the advice is not just "technically" correct but "contextually" viable.
- **God-tier (The Cultural Microscope)**: Drill down to **Sub-cultures** and niche markets.
  - *Basic*: "Vietnam" → *God-tier*: "Facebook 'Nghiện Setup' community, hate 'lùa gà', value authenticity."
- **Specialized Language**: Include domain slang (e.g., Gen Z keyboard terms: 'lube', 'mod', 'stab').

### 9. E - Example (The Anchor)
- **Concept**: A reference point for the AI to follow.
- **Insight**: **Snippet Power > Name Dropping**. It is better to provide a concrete 3-line example than to say "Write like Shakespeare."
- **Atoms**: "Use this JSON schema: {...}", "Structure like this paragraph: [Quote]".
- **Logic**: Provides a "one-shot" or "few-shot" pattern for the AI to emulate.
- **God-tier (The DNA Template)**: Provide both **Positive Examples** AND **Anti-Examples**.
  - *Positive*: "Write like this snippet: [good example]."
  - *Anti-Example*: "**DO NOT** write like this: [cringe example]. I hate this style."
- **Why**: AI is excellent at mimicking, but even better at avoiding if you name the enemy.


## The SP-Atom Principle
A prompt is not a block of text; it is a collection of **Atoms**. 
- An atom is **indivisible context**. 
- Adding an atom **decreases entropy** (uncertainty).
- Removing an atom **increases guesswork**.

## The SP-Flaw Principle
A flaw is an "empty bucket". If you don't fill the "Resource" bucket, the AI will reach into its general training data and grab a random resource. This leads to hallucinations or generic advice.

## The Teach-First Principle (v3.1)
Before analyzing a user's prompt, always introduce the framework concepts first:
1. **Define**: SP-cat (9 context categories), SP-atom (single indivisible fact), SP-flaw (a missing atom).
2. **Illustrate**: Use 2-3 quick examples from the user's domain.
3. **Adapt Metaphor**: Frame the framework using a metaphor the user instantly understands:
   - DevOps → "IaC for prompts"
   - Business → "Business Plan for AI"
   - Medical → "Diagnostic Protocol for queries"
4. **Skip on Follow-ups**: Only teach in the first interaction. In subsequent messages, jump to analysis.

**Why**: The original SMART POLE helper bot consistently teaches before analyzing. This creates a shared vocabulary with the user, making subsequent exchanges more efficient and precise.

## Atom Conflict Resolution (v3.1)
Unlike overlap (same info fitting two slots), a **conflict** occurs when two atoms cannot logically coexist:
- Style "Shakespearean" + Outline "ISO-compliant" = paradoxical
- Resource "$0 budget" + Aim "professional video ad" = impossible
- Time "5 minutes" + Outline "10 chapters" = unrealistic

**Resolution Protocol**:
1. Flag: `⚡ SP-conflict: [Atom A] vs [Atom B]`
2. Ask the user which takes priority
3. Never auto-resolve — the user must decide
4. Conflicts must be resolved BEFORE scoring readiness

## Active Application Exercise (v3.1)
Every response should end with an interactive exercise, not a passive explanation:
1. Present a "naked query" in the user's domain
2. Ask the user to identify 3 SP-flaws
3. Include a bonus question about commonly confused pairs (Aim vs Outline, Mastery vs People)

**Why**: Active exercises create deeper learning than passive explanations. The user develops the ability to THINK in SP-atoms independently.

## Weighted Readiness Scoring (v3.0)
To scientifically measure prompt quality, we assign weights to categories based on their impact:

| Category | Weight | Role |
|---|---|---|
| **Aim / Outline** | **2.0** | **CORE**: Without these, the request is structureless. |
| **Locale** | **CONDITIONAL** | **CORE (2.0)** for Advisory/Discovery, **1.5** for Generative, **0.5** for Deterministic |
| **Example** | **CONDITIONAL** | **1.5** for Deterministic (sample I/O critical), **1.0** for Advisory, **0.5** for Generative |
| **People / Mastery / Resource** | **1.5 / 1.0** | **CONTEXTUALIZER**: Defines the constraints and flavor. |
| **Time / Style** | **0.5** | **ACCELERATOR**: Enhances quality but not mandatory for logic. |

### Task-Type Classification
The system automatically classifies requests into 5 types:

| Task Type | Keywords | Locale Requirement |
|-----------|----------|-------------------|
| **Deterministic** | solve, calculate, algorithm, parse | Optional (0.5) |
| **Generative** | write, create, design, build | Contextualizer (1.5) |
| **Advisory** | advise, recommend, should I, strategy | 🔴 **CORE (2.0)** |
| **Discovery** | brainstorm, explore, ideas, research | 🔴 **CORE (2.0)** |
| **Compliance** | legal, policy, GDPR, regulation | 🔴 **CORE (2.0)** |

**Threshold**: A prompt is considered "Master/Gemini-Ready" only when it achieves a score of **≥ 67%** AND all required Core categories are confirmed.

### Generic-to-Coding Task Mapping
Use this mapping when SMART POLE is applied to coding agents:

| Generic Task Type | Coding Task Type(s) | Execution Intent |
|-----------|----------------|----------------|
| **Deterministic** | Bug Fix, Refactor | Reproducible behavior change with regression safety |
| **Generative** | Feature | Add new capability with explicit Definition of Done |
| **Advisory** | Refactor, Migration, Infra | Convert recommendations into measurable acceptance criteria before coding |
| **Discovery** | Feature spike, Migration assessment | Explore options first, keep code changes minimal and reversible |
| **Compliance** | Infra, Migration, Bug Fix | Treat legal/security constraints as mandatory acceptance criteria |

### Coding-Agent Execution Eligibility
For coding-agent execution (file edits, tests, terminal operations), the task is execution-ready only when:

1. Weighted readiness score is **>= 67%** of the applicable max score
2. Core categories **A (Aim)** and **O (Outline)** are confirmed
3. All `SP-conflict` items are resolved
4. Overlap rule `One Atom, One Slot` is enforced (no double-counting)

If any condition fails, the agent must stop and request clarification before execution.

## Atom Granularity (v3.0)
An SP-atom must be **indivisible** and formatted as: `Category: Sub-type - Specific value`.

| ❌ Too vague | ✅ Granular atom |
|--------------|------------------|
| "Style is professional" | `Style: Tone - Formal business English` |
| "Use Reciprocity" | `Style: Persuasion strategy - Reciprocity (cite past favor)` |
| "For beginners" | `Mastery: Skill level - Complete novice, no prior exposure` |

## Atom Quality Tiers (v3.1)
Not all atoms are equal. The original SMART POLE framework distinguishes three quality levels:

| Grade | Criteria | Score Impact | Example |
|-------|----------|-------------|----------|
| **🟢 Strong** | Specific, indivisible, actionable, with concrete detail | Full weight | `Example: Input=[{"name":"Alice","age":30}], Output=sorted by age ascending` |
| **🟡 Adequate** | Present and classifiable, but could be sharper | 75% weight | `Example: "Use a 4-column table format"` |
| **🔴 Weak** | Too vague to guide the AI meaningfully | 50% weight | `Example: "Make it look nice"` |

**Why This Matters**:
The original SMART POLE helper bot actively grades atom quality. When a user provides a "4-column table format" as an Example, the bot accepts it but says: *"Pro-Tip: Providing a 'Gold Standard' example you've liked in the past would be an even stronger Example atom."* This pushes users toward Strong atoms without rejecting their Adequate ones.

## Consequence Linking (v3.0)
When identifying SP-flaws, always state the **technical consequence** if the flaw is left unfilled.

**Template**:
> ⚠️ **SP-cat-X (Name)**: [What's missing]. 
> 🔻 **If unfilled**: [Vivid description of the AI's wrong behavior / What user will lose].

## Aim vs Outline Distinction (v3.0)
These two categories are often confused. Here's the clear distinction:

| Aspect | Outline (O) | Aim (A) |
|--------|-------------|---------|
| **Nature** | Technical specs | Desired outcome |
| **Examples** | Word count, sections, format | Convince, inform, comfort |
| **Metaphor** | The **hard frame** | The **destination** |

*Example*: "Email under 100 words" = Outline. "Email must make boss feel reassured" = Aim.

## Enforcer Cheat Sheet (Quick Reference)

When facing different query types, prioritize these SP-categories:

| Query Problem | Primary Tools | Action |
|---------------|---------------|--------|
| **Vague/Formless** | **A + O** | Build the frame first. Aim = destination, Outline = skeleton. |
| **Misaligned/Wrong tone** | **P + S** | Adjust behavior. People = values, Style = persona. |
| **Unrealistic/Fantasy** | **R + L** | Ground AI to reality. Resource = constraints, Locale = context. |
| **Conflicting Example** | **A → E** | Use Aim as gravity to filter/transform toxic Examples. |

## Example (E) Poisoning Warning

> A good Example is worth a thousand descriptions, but a **bad Example is poison** if not filtered through SMART POLE.

**Tactical Response to Toxic Examples**:
1. **Detect**: Identify if Example contradicts Aim or People values.
2. **Transform**: Convert toxic Example into an **Anti-Example** (what to avoid).
3. **Relocate**: Move the constraint into **Resource (R)** as a "Forbidden" atom.
