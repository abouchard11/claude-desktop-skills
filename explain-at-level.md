---
name: explain-at-level
description: This skill should be used when the user says "explain", "help me understand", "ELI5", "explain like I'm 5", "technical deep dive", "break down", "simplify", "what is", "how does X work", or asks for concept explanation with an implied or specified expertise level.
---

# Explain at Level

Deliver calibrated explanations that match the audience's expertise, using appropriate analogies and building from their existing knowledge.

## Approach

### Phase 1: Audience Calibration
Determine explanation level needed:

1. **Explicit Level Indicators**
   - "ELI5" → Child-friendly, no jargon
   - "I'm a beginner" → Foundation building
   - "I have some background in X" → Build on that
   - "Technical deep dive" → Expert level
   - "For my team" → Match team expertise

2. **Implicit Level Indicators**
   - Vocabulary they use in question
   - Context of their question
   - What they're trying to do
   - What they've already tried

3. **Expertise Levels**
   - **Layperson**: No domain knowledge, needs analogies
   - **Beginner**: Some exposure, building foundation
   - **Intermediate**: Working knowledge, filling gaps
   - **Advanced**: Deep knowledge, nuance and edge cases
   - **Expert**: Peer-level, technical precision

### Phase 2: Knowledge Foundation Mapping
Identify what to build on:

1. **What they likely already know**
   - Common knowledge at their level
   - Related concepts they've mentioned
   - Prerequisites for their question

2. **What they need to understand first**
   - Foundational concepts
   - Key terminology
   - Mental models

3. **Common misconceptions to address**
   - What people at this level often get wrong
   - Intuitions that mislead
   - Oversimplifications to correct

### Phase 3: Explanation Architecture

**Structure Options**

**Bottom-Up** (Build foundation first)
- Start with fundamentals
- Add layers progressively
- Build to full understanding
- Best for: Beginners, complex topics

**Top-Down** (Start with big picture)
- Overview first
- Then zoom into details
- Connect details to whole
- Best for: Intermediate+, time-constrained

**Analogy-First** (Familiar bridge)
- Start with familiar comparison
- Map concept to analogy
- Note where analogy breaks down
- Best for: Abstract concepts, laypersons

**Problem-Solution** (Motivation first)
- Why does this exist?
- What problem does it solve?
- How does it solve it?
- Best for: Technical topics, practical learners

### Phase 4: Explanation Execution

**Language Calibration by Level**

| Level | Jargon | Sentence Length | Analogies |
|-------|--------|-----------------|-----------|
| Layperson | None | Short, simple | Essential |
| Beginner | Introduced & defined | Moderate | Frequent |
| Intermediate | Expected, explained if advanced | Moderate | Occasional |
| Advanced | Expected | Can be complex | For new concepts |
| Expert | Full precision | As needed | Rare |

**Depth Calibration**

| Level | Details | Edge Cases | Nuance |
|-------|---------|------------|--------|
| Layperson | Core only | Skip | Skip |
| Beginner | Important | Skip | Skip |
| Intermediate | Most | Common ones | Some |
| Advanced | All relevant | Most | Yes |
| Expert | Full precision | All | Complete |

### Phase 5: Understanding Verification
Check comprehension through:

1. **Prediction Questions**: "What would happen if...?"
2. **Application Questions**: "How would you use this to...?"
3. **Teaching Test**: "How would you explain this to...?"
4. **Misconception Probes**: "Is it true that...?"

### Phase 6: Next Steps
After explanation, provide:

1. What to learn next
2. Resources for deeper exploration
3. How to apply this knowledge
4. Common next questions

## Output Structure

### Explanation Format

```
## Quick Answer
[1-2 sentence summary at their level]

## The Explanation

### [Analogy/Context Hook - if appropriate]
[Relatable comparison or framing]

### How It Works
[Core explanation at calibrated level]

[Use progressive sections if needed:]

#### Foundation
[Prerequisites and basics]

#### The Key Concept
[Central mechanism/idea]

#### Why It Matters
[Implications and applications]

### Common Misconceptions
- **Misconception**: [What people get wrong]
- **Reality**: [The correct understanding]

### Check Your Understanding
[1-2 questions to verify comprehension]

## Going Deeper
- [Next concept to learn]
- [Resource for more detail]
- [Related topic to explore]
```

## Level-Specific Templates

### Layperson (ELI5)
```
Think of [concept] like [everyday analogy].

[Explanation using only common words, <100 words]

The key thing to remember: [One sentence takeaway]
```

### Beginner
```
## What is [Concept]?
[Simple definition]

## How It Works (Simply)
[Core mechanism, ~200 words]

## Key Terms
- **[Term 1]**: [Simple definition]
- **[Term 2]**: [Simple definition]

## Why It Matters
[Practical relevance]
```

### Intermediate
```
## [Concept]: The Essentials

### Definition
[Precise but accessible]

### How It Works
[Full mechanism with technical vocabulary]

### Key Considerations
- [Point 1]
- [Point 2]

### Common Pitfalls
- [Pitfall 1]
- [Pitfall 2]

### In Practice
[Application examples]
```

### Advanced/Expert
```
## [Concept]

[Precise technical explanation assuming domain knowledge]

### Technical Details
[Specifics, edge cases, nuances]

### Trade-offs and Alternatives
[When to use, when not to, alternatives]

### Current Developments
[Latest thinking, open questions]
```

## Quality Checks

Before delivering explanation, verify:

### Level Appropriateness
- [ ] Vocabulary matches audience level
- [ ] Depth appropriate (not too shallow, not too deep)
- [ ] Analogies resonant for this audience
- [ ] Assumptions about prior knowledge correct

### Accuracy
- [ ] Technically correct
- [ ] Simplifications don't mislead
- [ ] Analogies break down points noted
- [ ] Edge cases appropriate to level

### Completeness
- [ ] Core concept fully explained
- [ ] Key questions answered
- [ ] Misconceptions addressed
- [ ] Path forward provided

### Effectiveness
- [ ] Builds on what they know
- [ ] Addresses what they asked
- [ ] Actionable for their context
- [ ] Can verify understanding

## Anti-Patterns to Avoid

1. **Curse of Knowledge**: Forgetting what it's like not to know
2. **Jargon Dumping**: Using terms without defining
3. **Analogy Overreliance**: Analogy becomes the concept
4. **Depth Mismatch**: Too shallow or too deep
5. **Information Dump**: Everything at once
6. **Assumption Error**: Wrong starting point for audience
7. **Missing Motivation**: What without why
8. **Dead End**: No path to deeper understanding

## Special Handling

### Abstract Concepts
1. Start with concrete manifestations
2. Use multiple analogies
3. Build up to abstraction
4. Return to concrete applications

### Counter-Intuitive Topics
1. Acknowledge the intuition
2. Explain why it's wrong
3. Build correct understanding
4. Verify the shift

### Highly Technical Topics
1. Establish need-to-know level
2. Progressive disclosure
3. Signpost what's skippable
4. Provide reference for details

### Contested/Evolving Topics
1. Present mainstream view first
2. Note areas of debate
3. Indicate confidence levels
4. Avoid false certainty

## Invocation Examples

User: "Explain machine learning to me" [no level specified]
→ Assume intermediate layperson, use strong analogies, focus on practical understanding

User: "ELI5 how the stock market works"
→ Maximum simplification, everyday analogies, core mechanism only

User: "I understand SQL basics but what's a subquery?"
→ Intermediate level, build on SQL knowledge, practical examples

User: "Technical deep dive on transformer architecture"
→ Expert level, full precision, mathematical notation acceptable
