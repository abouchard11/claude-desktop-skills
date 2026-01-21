# Claude Desktop Skills Collection

This file contains 10 high-leverage skills for Claude. When loaded, Claude will automatically apply the appropriate methodology based on your request.

**Trigger Examples:**
- "Research X" → Deep Research Synthesis
- "Should I X or Y?" → Decision Matrix Builder
- "Extract action items from..." → Meeting to Actions
- "Draft an email to..." → Message Crafter
- "Summarize this feedback..." → Feedback Synthesizer
- "Compare these documents" → Document Diff Analyzer
- "How do I learn X?" → Learning Path Generator
- "Turn this into a..." → Content Transformer
- "Explain X" / "ELI5" → Explain at Level
- "Brainstorm ideas for..." → Structured Brainstorm

---

# Skill 1: Deep Research Synthesis

## Metadata
- **Name**: research-synthesis
- **Triggers**: "research", "investigate", "deep dive", "comprehensive analysis", "what do we know about", "explore the topic", "gather information on"

## Approach

### Phase 1: Question Decomposition
Before researching, decompose the main question into sub-questions:

1. **Core Question**: What is the user actually trying to understand or decide?
2. **Factual Sub-questions**: What objective facts need to be established?
3. **Analytical Sub-questions**: What patterns, causes, or relationships need exploration?
4. **Contextual Sub-questions**: What background or domain knowledge is required?
5. **Practical Sub-questions**: What actionable information does the user need?

### Phase 2: Source Gathering Strategy
Prioritize sources based on reliability hierarchy:

- **Tier 1 - Primary Sources**: Official documentation, peer-reviewed research, authoritative databases
- **Tier 2 - Expert Analysis**: Domain expert commentary, technical analysis from recognized authorities
- **Tier 3 - Secondary Reporting**: Quality journalism with clear sourcing, aggregated data
- **Tier 4 - Contextual Sources**: Community discussions, opinion pieces (use with caveats)

### Phase 3: Information Synthesis
For each finding, track:

1. **The Claim**: State it precisely
2. **Source Quality**: Tier 1-4 from above
3. **Confidence Level**:
   - **High** (90%+): Multiple Tier 1-2 sources agree
   - **Medium** (60-89%): Single Tier 1 source OR multiple Tier 2-3 sources
   - **Low** (30-59%): Single Tier 2-3 source OR conflicting information
   - **Speculative** (<30%): Inference or single Tier 4 source
4. **Contradicting Evidence**: Note any dissenting views
5. **Recency**: How current is this information?

### Phase 4: Knowledge Gap Identification
Explicitly identify:
- Known Unknowns: Questions identified but couldn't answer
- Data Gaps: Information that should exist but wasn't found
- Conflicting Information: Where sources disagree and why
- Scope Limitations: What was outside research scope

### Phase 5: Synthesis and Implications
1. Key Findings Summary: 3-5 most important discoveries
2. Implications: What do these findings mean for the user's context?
3. Recommendations: Concrete next steps based on findings
4. Further Research Needed: What additional investigation would add value?

## Output Format

```
## Research Question
[Restated core question with identified sub-questions]

## Executive Summary
[3-5 sentence overview of key findings and confidence level]

## Detailed Findings
### [Finding Category]
**Claim**: [Precise statement]
**Confidence**: [High/Medium/Low/Speculative]
**Source(s)**: [Citation with tier]
**Caveats**: [Limitations or uncertainties]

## Knowledge Gaps
- [Gap]: [Why this matters]

## Implications
[What these findings mean for user's context]

## Recommended Actions
1. [Concrete action with rationale]

## Sources Referenced
[Numbered list with citations]
```

---

# Skill 2: Decision Matrix Builder

## Metadata
- **Name**: decision-matrix
- **Triggers**: "pros and cons", "should I", "compare options", "which is better", "help me decide", "evaluate alternatives", "trade-offs between", "weighing options"

## Approach

### Phase 1: Decision Framing
1. **Decision Statement**: "I need to decide [X] in order to [achieve Y]"
2. **Decision Type**:
   - **One-way door**: Irreversible or expensive to reverse (high stakes)
   - **Two-way door**: Reversible with manageable cost (can experiment)
3. **Timeline**: When must this decision be made? Why?
4. **Constraints**: What's off the table?

### Phase 2: Option Identification
1. **Obvious Options**: What the user already sees
2. **Non-obvious Options**: What might be overlooked?
3. **Hybrid Options**: Combinations of obvious options
4. **Status Quo Option**: Always include "do nothing"
5. **Deferred Option**: "Decide later when X is known"

### Phase 3: Criteria Development
- **Outcome Criteria**: Must-have results, nice-to-have results, outcomes to avoid
- **Process Criteria**: Effort, time, resources, dependencies
- **Risk Criteria**: Probability of failure, severity, recovery options
- **Values Criteria**: Consistency with principles, precedent being set

### Phase 4: Weighting Criteria
Assign weights through forced ranking (total = 100%)

### Phase 5: Option Scoring
Score each option 1-5 against each criterion:
- 5: Excellent - Clearly the best
- 4: Good - Strong, minor drawbacks
- 3: Adequate - Meets requirements
- 2: Poor - Significant concerns
- 1: Unacceptable - Deal-breaker

**Weighted Score** = Sum(criterion_weight × criterion_score)

### Phase 6: Second-Order Analysis
1. **Reversibility**: Can you undo this? At what cost?
2. **Optionality**: Does this open or close future doors?
3. **Learning Value**: What will you know after choosing this?
4. **Regret Minimization**: Which choice would you regret most at 80?
5. **Pre-mortem**: If this fails, why did it fail?

## Output Format

```
## Decision Frame
**Statement**: [I need to decide X to achieve Y]
**Type**: [One-way/Two-way door]
**Timeline**: [Decision deadline]

## Options
| Option | Description | Why Considered |
|--------|-------------|----------------|

## Evaluation Criteria
| Criterion | Weight | Rationale |
|-----------|--------|-----------|

## Decision Matrix
| Criterion (Weight) | Option A | Option B | Option C |
|--------------------|----------|----------|----------|
| **Weighted Total** | **X.X** | **X.X** | **X.X** |

## Second-Order Considerations
- Reversibility, Optionality, Pre-mortem analysis

## Recommendation
**Recommended Option**: [X]
**Rationale**: [Why]
**Confidence Level**: [High/Medium/Low]
**If Wrong, Detect By**: [Signals]
```

---

# Skill 3: Meeting to Actions Extractor

## Metadata
- **Name**: meeting-to-actions
- **Triggers**: "extract action items", "meeting summary", "who does what", "follow-ups from", "action items from", "meeting takeaways", meeting notes/transcripts shared

## Approach

### Phase 1: Context Identification
1. **Meeting Type**: Standup, planning, brainstorm, review, decision meeting, 1:1
2. **Participants**: Who was present? Their roles?
3. **Purpose**: What was this meeting supposed to accomplish?

### Phase 2: Action Item Detection

**Explicit Commitment Signals**
- "I will...", "I'll...", "I'm going to..."
- "[Name] will...", "[Name] is going to..."
- "Action item:", "TODO:", "Next step:"
- "Can you...", "Could you...", "Would you mind..."

**Implicit Commitment Signals**
- Problems raised without stated owners → needs owner
- Questions asked without answers → needs follow-up
- Decisions made → may require implementation
- Dependencies mentioned → needs tracking

### Phase 3: Commitment Parsing
For each action extract:
1. **WHO**: Clear owner (single person, not "the team")
2. **WHAT**: Specific deliverable or outcome
3. **WHEN**: Deadline (explicit or inferred)
4. **WHY**: Context/purpose
5. **DEPENDENCIES**: What/who blocks this?
6. **CONFIDENCE**: How clear was this commitment?

### Phase 4: Ambiguity Flagging
- **Ownership Ambiguity**: "We should do X" → WHO is "we"?
- **Scope Ambiguity**: "Look into X" → What does that mean?
- **Timeline Ambiguity**: "Soon", "ASAP", no deadline

### Phase 5: Decision Capture
1. **Decision**: What was decided?
2. **Rationale**: Why? (if stated)
3. **Implications**: What does this trigger?

## Output Format

```
## Meeting Overview
**Date**: [Date]
**Type**: [Meeting type]
**Participants**: [Names]
**Outcome Summary**: [1-2 sentences]

## Action Items

### High Priority
| Owner | Action | Deadline | Context |
|-------|--------|----------|---------|

### Needs Clarification
| Unclear Item | Ambiguity | Suggested Resolution |
|--------------|-----------|---------------------|

## Decisions Made
| Decision | Rationale | Owner | Implications |
|----------|-----------|-------|--------------|

## Open Questions
- [Question] - Needs answer from [who]

## Follow-up Meeting Needed?
[Yes/No] - [Purpose if yes]
```

---

# Skill 4: Professional Message Crafter

## Metadata
- **Name**: message-crafter
- **Triggers**: "draft email", "write message", "respond to", "professional reply", "help me say", "how should I phrase", "compose a message", "write to", "reach out to"

## Approach

### Phase 1: Context Analysis
1. **Relationship Context**: Who are they? Role, seniority, history, power dynamic
2. **Purpose Analysis**: Primary goal, secondary goals, anti-goals, call to action
3. **Constraints**: Medium, length, timing, potential forwarding

### Phase 2: Tone Calibration

| Dimension | Low ←→ High |
|-----------|-------------|
| Formality | Casual ←→ Formal |
| Warmth | Professional distance ←→ Personal warmth |
| Directness | Diplomatic ←→ Blunt |
| Urgency | Relaxed ←→ Time-sensitive |
| Authority | Requesting ←→ Directing |

**Common Tone Profiles**
- Executive Update: High formality, low warmth, high directness
- Team Collaboration: Low formality, high warmth, medium directness
- Client Communication: Medium-high formality, medium warmth
- Difficult Conversation: Medium formality, medium warmth, high directness

### Phase 3: Structure Selection

**Request Message**: Context → Clear ask → Why it matters → Timeline → Close
**Update Message**: Bottom-line first → Key details → Next steps → Questions
**Response Message**: Acknowledge → Address points → New info → Next steps
**Difficult Message**: Acknowledge situation → State position → Reasoning → Path forward → Open door

### Phase 4: Drafting Principles

**Opening**: No "I hope this email finds you well" - lead with purpose
**Body**: One idea per paragraph, front-load key info, use bullets
**Closing**: Clear call to action, specific next step

### Anti-Patterns to Avoid
- Burying the lede
- Passive aggression
- Hedge overload ("I was just wondering if maybe...")
- Wall of text
- Vague CTAs ("Let me know what you think")

## Output Format

```
## Context Analysis
**Recipient**: [Who, relationship]
**Purpose**: [What this must accomplish]
**Tone**: [Profile selection]

## Draft Message
**Subject**: [Compelling, specific]

[Message body]

## Alternative Version
[Different tone/approach if useful]

## Notes
- [Caveats, follow-up suggestions]
```

---

# Skill 5: Feedback Synthesizer

## Metadata
- **Name**: feedback-synthesis
- **Triggers**: "summarize feedback", "what do people think", "common complaints", "sentiment analysis", "aggregate reviews", "feedback themes", "what are customers saying", reviews/survey responses shared

## Approach

### Phase 1: Feedback Inventory
1. **Source Type**: Customer reviews, surveys, support tickets, social media, internal feedback
2. **Sample Characteristics**: Volume, time range, representativeness, selection bias
3. **Context Factors**: Recent changes, external events, seasonal effects

### Phase 2: Sentiment Tagging
- **Positive/Negative/Neutral/Mixed**
- **Intensity**: Strong, Moderate, Mild

### Phase 3: Theme Extraction

1. **Feature/Functionality**: What people love, what's missing, broken, confusing
2. **Experience**: Onboarding, learning curve, support, performance
3. **Value**: Price perception, ROI, comparison to alternatives
4. **Emotional**: Trust, frustration, delight, disappointment

### Phase 4: Quantification
- Volume: Mentions per theme, % of total, trend over time
- Intensity Weighting: Strong = 3x, Moderate = 2x, Mild = 1x
- Impact Assessment: Who affected, blocker vs annoyance, retention impact

### Phase 5: Signal vs Noise

**High Signal** (Act on this)
- Recurring theme (5%+ of feedback)
- Multiple independent sources
- Trend worsening
- Connected to key metric

**Low Signal** (Deprioritize)
- One-off mentions
- Contradicted by majority
- Out of control
- Already being addressed

### Phase 6: Priority Ranking

| | High Frequency | Low Frequency |
|---|---|---|
| **High Impact** | P1: Fix immediately | P2: Investigate |
| **Low Impact** | P3: Plan for future | P4: Monitor only |

## Output Format

```
## Analysis Overview
**Volume**: [N pieces]
**Sources**: [Where from]
**Overall Sentiment**: [X% positive, Y% negative, Z% neutral]

## Executive Summary
[Top themes, overall health, key concerns]

## Positive Themes
| Theme | Mentions | % | Representative Quote |
|-------|----------|---|---------------------|

## Negative Themes
| Theme | Mentions | % | Severity | Quote |
|-------|----------|---|----------|-------|

## Priority Recommendations
### P1: Address Immediately
### P2: Plan to Address
### P3: Monitor

## Confidence & Caveats
```

---

# Skill 6: Document Diff Analyzer

## Metadata
- **Name**: document-diff
- **Triggers**: "compare these", "what changed", "difference between", "track changes", "version comparison", "diff these documents", two document versions shared

## Approach

### Phase 1: Document Characterization
1. **Document Type**: Contract, policy, technical spec, proposal, code
2. **Comparison Context**: Why comparing? What changes matter most?
3. **Version Information**: Which is before/after?

### Phase 2: Change Detection Layers

- **Surface Changes**: Added, removed, moved, substituted text
- **Structural Changes**: Reordering, hierarchy changes, format changes
- **Semantic Changes**: Definition, scope, obligation, timeline, party changes
- **Implied Changes**: Risk exposure, rights/obligations shifts, liability

### Phase 3: Materiality Assessment

**Material Changes** (High importance)
- Alters rights, obligations, liabilities
- Changes financial terms
- Modifies timelines/deadlines
- Shifts risk allocation

**Significant Changes** (Medium)
- Clarifies ambiguous language
- Standardizes terminology
- Updates references

**Cosmetic Changes** (Low)
- Formatting, typos, punctuation, style

### Phase 4: Risk Flagging

- **Red Flags**: Rights reduced, obligations increased, terms less favorable
- **Yellow Flags**: Meaning unclear, needs clarification
- **Green Flags**: Rights expanded, better protections

## Output Format

```
## Comparison Overview
**Document Type**: [Type]
**Version A**: [Description]
**Version B**: [Description]
**Overall Assessment**: [Summary]

## Material Changes (Require Attention)

### 1. [Change Description]
**Location**: [Section]
| Before | After |
|--------|-------|
| "[Original]" | "[New]" |
**Implication**: [What this means]
**Flag**: [Red/Yellow/Green]

## Significant Changes
| # | Location | Summary | Before → After |
|---|----------|---------|----------------|

## Risk Assessment
### Red Flags
### Yellow Flags
### Green Flags

## Recommended Actions
```

---

# Skill 7: Learning Path Generator

## Metadata
- **Name**: learning-path
- **Triggers**: "learn", "understand", "get started with", "master", "study", "build skills in", "become proficient in", "how do I learn", "roadmap to learn"

## Approach

### Phase 1: Learner Assessment
1. **Current State**: What do they know? Adjacent knowledge? Learning style? Time available?
2. **Target State**: What does "learned" mean? Practical or theoretical? What level?
3. **Constraints**: Time, budget, tools access, context
4. **Motivation**: Why learn this? Stakes?

### Phase 2: Knowledge Mapping
1. Core Concepts: Essential building blocks
2. Prerequisites: What must be known first
3. Dependencies: What unlocks what
4. Common Misconceptions: What trips people up

### Phase 3: Path Architecture

**Levels of Learning**
1. Exposure: Basic awareness
2. Comprehension: Understand how it works
3. Application: Can use in guided contexts
4. Analysis: Can solve novel problems
5. Synthesis: Can combine with other knowledge
6. Mastery: Can teach others

**Path Structure**
- Foundation Phase: Prerequisites and core concepts
- Core Learning Phase: Main content and skills
- Practice Phase: Application and reinforcement
- Integration Phase: Connecting to real work
- Deepening Phase: Advanced topics

### Phase 4: Milestone Design
- Knowledge Check: Can explain concept
- Skill Check: Can perform task
- Project Check: Can complete meaningful project
- Teaching Check: Can explain to someone else

### Phase 5: Resource Curation
Types: Courses, documentation, tutorials, books, videos, practice platforms, projects, communities

Selection criteria: Quality, fit, accessibility, currency

## Output Format

```
## Learning Objective
**Topic**: [What to learn]
**Target Level**: [Awareness → Mastery]
**Timeframe**: [Duration at X hours/week]
**Outcome**: [What they'll be able to do]

## Prerequisite Check
**Required**: [Prerequisites with verification]
**Helpful**: [Nice-to-haves]

## Learning Path Overview
Phase 1: Foundation (Week X-Y)
Phase 2: Core Skills (Week X-Y)
Phase 3: Practice (Week X-Y)
Phase 4: Integration (Week X-Y)

## Detailed Path

### Phase 1: Foundation
**Duration**: [X hours]
**Objective**: [What you'll know after]
**Topics**: [List]
**Resources**: [Table with type, time, notes]
**Milestone**: [Checkboxes]

## Common Pitfalls
## Success Indicators
```

---

# Skill 8: Content Transformer

## Metadata
- **Name**: content-transform
- **Triggers**: "turn this into", "repurpose", "convert to", "make this a", "adapt for", "reformat as", "transform into", "summarize as", "expand into"

## Approach

### Phase 1: Source Analysis
1. **Content Audit**: Core message, supporting points, evidence, structure, tone, length
2. **Purpose Assessment**: Original purpose, what worked
3. **Asset Extraction**: Key quotes, data points, unique insights, memorable examples

### Phase 2: Target Definition
1. **New Format**: Conventions, constraints, opportunities
2. **New Audience**: What they know, what they care about, how they consume
3. **New Context**: Where it appears, what surrounds it, desired action

### Phase 3: Gap Analysis
- **Keep**: Core message, key evidence, universal insights
- **Adapt**: Structure, tone, examples, depth
- **Add**: Format-specific elements, audience context, CTAs
- **Remove**: Irrelevant details, length excess, outdated references

### Phase 4: Format-Specific Transformation

**Blog → Twitter Thread**: Hook first, one idea per tweet, engagement hooks, CTA
**Report → Executive Summary**: Conclusion first, bullets over paragraphs, clear next steps
**Long-form → Slides**: One concept per slide, headlines that make the point
**Technical → Non-Technical**: Plain language, analogies, focus on outcomes
**Formal → Casual**: Shorter sentences, contractions, conversational

### Format Reference

| Platform | Constraints | Best Practices |
|----------|-------------|----------------|
| Twitter/X | 280 char | Hooks, threads |
| LinkedIn | ~3000 char | Professional, stories |
| Email | 500-1000 words | Personal, CTA |
| Slides | 10-15 | One point/slide |

## Output Format

```
## Transformation Summary
**Source**: [Original format, length]
**Target**: [New format, constraints]
**Audience Shift**: [Original → New]

## Transformed Content
[The actual transformed content]

## Notes
**Preserved**: [What kept]
**Adapted**: [What changed]
**Added**: [New elements]

## Alternative Angles
[Options for different emphasis]
```

---

# Skill 9: Explain at Level

## Metadata
- **Name**: explain-at-level
- **Triggers**: "explain", "help me understand", "ELI5", "explain like I'm 5", "technical deep dive", "break down", "simplify", "what is", "how does X work"

## Approach

### Phase 1: Audience Calibration

**Explicit Indicators**
- "ELI5" → Child-friendly, no jargon
- "I'm a beginner" → Foundation building
- "Technical deep dive" → Expert level

**Expertise Levels**
- Layperson: No domain knowledge, needs analogies
- Beginner: Some exposure, building foundation
- Intermediate: Working knowledge, filling gaps
- Advanced: Deep knowledge, nuance and edge cases
- Expert: Peer-level, technical precision

### Phase 2: Knowledge Foundation Mapping
- What they likely already know
- What they need to understand first
- Common misconceptions to address

### Phase 3: Explanation Architecture

**Bottom-Up**: Start with fundamentals, add layers (best for beginners)
**Top-Down**: Overview first, then details (best for intermediate+)
**Analogy-First**: Familiar comparison, map concept, note where it breaks down
**Problem-Solution**: Why it exists, what problem, how it solves (best for technical)

### Phase 4: Calibration

| Level | Jargon | Analogies | Details |
|-------|--------|-----------|---------|
| Layperson | None | Essential | Core only |
| Beginner | Introduced & defined | Frequent | Important |
| Intermediate | Expected | Occasional | Most |
| Advanced | Expected | For new concepts | All |
| Expert | Full precision | Rare | Complete |

## Output Format by Level

**Layperson (ELI5)**
```
Think of [concept] like [everyday analogy].
[Explanation <100 words using common words]
Key thing to remember: [One sentence]
```

**Beginner**
```
## What is [Concept]?
[Simple definition]
## How It Works
[Core mechanism ~200 words]
## Key Terms
## Why It Matters
```

**Intermediate**
```
## [Concept]: The Essentials
### Definition
### How It Works
### Key Considerations
### Common Pitfalls
### In Practice
```

**Advanced/Expert**
```
## [Concept]
[Technical explanation assuming domain knowledge]
### Technical Details
### Trade-offs and Alternatives
### Current Developments
```

---

# Skill 10: Structured Brainstorm

## Metadata
- **Name**: structured-brainstorm
- **Triggers**: "brainstorm", "ideas for", "creative options", "possibilities", "what could we", "generate alternatives", "think of ways to", "explore options", "creative solutions"

## Approach

### Phase 1: Problem Definition
1. **Core Challenge**: What are we solving for?
2. **Success Criteria**: What makes an idea "good"?
3. **Constraints**: What's off the table?
4. **Current State**: What's been tried?

### Phase 2: Divergent Exploration

**Conventional Ideas**: Standard approach, safe, proven
**Unconventional Ideas**: Opposite approach, naive outsider view, remove constraints
**Combinatorial Ideas**: Combine approaches, borrow from adjacent domains
**Constraint-Flipping Ideas**: Turn weakness into advantage
**Wild Ideas**: No limits, magic thinking

### Phase 3: Idea Forcing Techniques

**SCAMPER Framework**
- Substitute: What can be replaced?
- Combine: What can merge?
- Adapt: What can be borrowed?
- Modify: What can change scale/form?
- Put to other uses: What else could this do?
- Eliminate: What can be removed?
- Reverse: What can be flipped?

**Other Techniques**
- Analogical: How does nature/other industries solve this?
- Reversal: What if we wanted the opposite?
- Random Stimulus: Force connection to unrelated domain

### Phase 4: Idea Clustering
Group by: theme, resource requirements, risk level, time to implement, innovation level

### Phase 5: Evaluation

| | High Frequency | Low Frequency |
|---|---|---|
| **High Impact** | Must Do | Should Do |
| **Low Impact** | Could Do | Won't Do |

Criteria: Impact, feasibility, cost, time, risk, alignment, novelty, reversibility

### Phase 6: Idea Development
For promising ideas:
1. Concrete Next Step
2. Key Assumption to validate
3. Quick Test approach
4. Potential Blocker
5. Who would champion this

## Output Format

```
## Challenge Definition
**Core Question**: [What we're solving]
**Success Criteria**: [What good looks like]
**Constraints**: [What's fixed]

## Ideas Generated

### Conventional Approaches
| # | Idea | Description |
|---|------|-------------|

### Unconventional Approaches
| # | Idea | Description | Why Unconventional |
|---|------|-------------|-------------------|

### Wild Cards
| # | Idea | What Would Enable It |
|---|------|---------------------|

### Combinations
| # | Idea | Components Combined |
|---|------|-------------------|

## Evaluation Matrix
| Idea | Impact | Feasibility | Cost | Time | Total |
|------|--------|-------------|------|------|-------|

## Recommended Actions

### Pursue Now
1. **[Idea]**: Why, first step, test with

### Investigate Further
1. **[Idea]**: Key question, how to learn

### Quick Wins
### Park for Later

## Patterns Observed
```

---

# Quick Reference Card

| Need | Say This | Skill Activated |
|------|----------|-----------------|
| Research a topic | "Research...", "Deep dive on...", "What do we know about..." | Research Synthesis |
| Make a decision | "Should I...", "Compare...", "Which is better..." | Decision Matrix |
| Process meeting notes | "Action items from...", "Who does what..." | Meeting to Actions |
| Write professional message | "Draft email...", "Help me say...", "Respond to..." | Message Crafter |
| Analyze feedback | "Summarize feedback...", "Common complaints...", "What do people think..." | Feedback Synthesizer |
| Compare documents | "What changed...", "Compare these...", "Diff..." | Document Diff |
| Create learning plan | "How do I learn...", "Roadmap for...", "Master..." | Learning Path |
| Repurpose content | "Turn this into...", "Convert to...", "Adapt for..." | Content Transform |
| Get explanation | "Explain...", "ELI5...", "Help me understand..." | Explain at Level |
| Generate ideas | "Brainstorm...", "Ideas for...", "What could we..." | Structured Brainstorm |
