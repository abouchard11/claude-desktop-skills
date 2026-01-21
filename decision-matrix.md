---
name: decision-matrix
description: This skill should be used when the user says "pros and cons", "should I", "compare options", "which is better", "help me decide", "evaluate alternatives", "trade-offs between", "weighing options", or describes a dilemma with multiple possible paths forward.
---

# Decision Matrix Builder

Transform ambiguous choices into structured decisions through multi-criteria analysis, risk assessment, and second-order thinking.

## Approach

### Phase 1: Decision Framing
Before evaluating options, establish the decision frame:

1. **Decision Statement**: "I need to decide [X] in order to [achieve Y]"
2. **Decision Type**:
   - **One-way door**: Irreversible or expensive to reverse (high stakes)
   - **Two-way door**: Reversible with manageable cost (can experiment)
3. **Timeline**: When must this decision be made? Why?
4. **Stakeholders**: Who is affected? Who has veto power?
5. **Constraints**: What's off the table? Budget/time/values limits?

### Phase 2: Option Identification
Ensure complete option space:

1. **Obvious Options**: What the user already sees
2. **Non-obvious Options**: What might be overlooked?
3. **Hybrid Options**: Combinations of obvious options
4. **Status Quo Option**: Always include "do nothing" as explicit choice
5. **Deferred Option**: "Decide later when X is known"

### Phase 3: Criteria Development
Develop evaluation criteria:

**Outcome Criteria** (What success looks like)
- Primary outcomes: Must-have results
- Secondary outcomes: Nice-to-have results
- Negative outcomes: What we're trying to avoid

**Process Criteria** (How we get there)
- Effort required
- Time to implement
- Resources needed
- Dependencies on others

**Risk Criteria** (What could go wrong)
- Probability of failure
- Severity of failure
- Detectability of problems
- Recovery options

**Values Criteria** (Alignment with principles)
- Consistency with stated values
- Precedent being set
- Stakeholder impact

### Phase 4: Weighting Criteria
Assign weights through forced ranking:

1. List all criteria
2. For each pair, ask: "If I could only optimize one, which?"
3. Assign relative weights (total = 100%)
4. Validate: Do the weights feel right? Adjust if needed.

### Phase 5: Option Scoring
Score each option against each criterion:

**Scoring Scale**
- 5: Excellent - Clearly the best on this criterion
- 4: Good - Strong performance, minor drawbacks
- 3: Adequate - Meets requirements, nothing special
- 2: Poor - Significant concerns
- 1: Unacceptable - Deal-breaker level

**Weighted Score** = Sum(criterion_weight × criterion_score)

### Phase 6: Second-Order Analysis
Beyond the matrix, consider:

1. **Reversibility**: Can you undo this? At what cost?
2. **Optionality**: Does this choice open or close future doors?
3. **Learning Value**: What will you know after choosing this?
4. **Regret Minimization**: Which choice would you regret most at 80?
5. **Pre-mortem**: If this fails, why did it fail?
6. **Inversion**: What would make each option clearly wrong?

### Phase 7: Synthesis and Recommendation
Integrate all analysis:

1. **Quantitative Winner**: Highest weighted score
2. **Qualitative Check**: Does this feel right? Why/why not?
3. **Red Flags**: Any deal-breakers the matrix missed?
4. **Confidence Level**: How sure are we about inputs?
5. **Recommended Action**: Clear recommendation with rationale

## Output Structure

### Decision Analysis Format

```
## Decision Frame
**Statement**: [I need to decide X to achieve Y]
**Type**: [One-way/Two-way door]
**Timeline**: [Decision deadline and rationale]
**Key Constraints**: [Hard limits]

## Options Under Consideration

| Option | Brief Description | Why Considered |
|--------|------------------|----------------|
| A      | [Description]    | [Rationale]    |
| B      | [Description]    | [Rationale]    |
| C      | [Description]    | [Rationale]    |
| Status Quo | [Current state] | [Baseline]  |

## Evaluation Criteria

| Criterion | Weight | Rationale |
|-----------|--------|-----------|
| [Criterion 1] | X% | [Why this matters] |
| [Criterion 2] | Y% | [Why this matters] |
| Total | 100% | |

## Decision Matrix

| Criterion (Weight) | Option A | Option B | Option C | Status Quo |
|--------------------|----------|----------|----------|------------|
| Crit 1 (X%) | 4 | 3 | 5 | 2 |
| Crit 2 (Y%) | 3 | 4 | 2 | 3 |
| **Weighted Total** | **X.X** | **X.X** | **X.X** | **X.X** |

## Second-Order Considerations

### Reversibility Analysis
| Option | Reversibility | Cost to Reverse | Time to Reverse |
|--------|--------------|-----------------|-----------------|
| A | [High/Med/Low] | [Cost] | [Time] |

### Optionality Impact
- **Option A**: [Opens/closes what future possibilities]
- **Option B**: [Opens/closes what future possibilities]

### Pre-Mortem (If This Fails...)
- **Option A fails because**: [Likely failure mode]
- **Option B fails because**: [Likely failure mode]

## Risk Assessment

| Option | Key Risks | Probability | Impact | Mitigation |
|--------|-----------|-------------|--------|------------|
| A | [Risk] | [H/M/L] | [H/M/L] | [Strategy] |
| B | [Risk] | [H/M/L] | [H/M/L] | [Strategy] |

## Recommendation

**Recommended Option**: [X]

**Rationale**: [Why this option, integrating quantitative scores and qualitative factors]

**Confidence Level**: [High/Medium/Low] because [reasons]

**Key Assumptions**: [What must be true for this to be right]

**If Wrong, Detect By**: [Signals that this was the wrong choice]

**Recommended Next Steps**:
1. [Immediate action]
2. [Follow-up action]
3. [Checkpoint/review point]
```

## Quality Checks

Before delivering analysis, verify:

### Frame Quality
- [ ] Decision statement is specific and actionable
- [ ] Timeline pressure is understood (real vs artificial)
- [ ] Stakeholders and constraints identified
- [ ] Option space is complete (including non-obvious options)

### Criteria Quality
- [ ] Criteria are independent (not double-counting)
- [ ] Weights reflect user's actual priorities
- [ ] No hidden criteria smuggled into scoring
- [ ] Deal-breakers identified separately from scoring criteria

### Scoring Quality
- [ ] Scores are based on evidence, not vibes
- [ ] Uncertainty in scores is acknowledged
- [ ] Scores are comparable across options
- [ ] Outlier scores explained

### Analysis Quality
- [ ] Second-order effects considered
- [ ] Risks assessed for each option
- [ ] Reversibility evaluated
- [ ] Recommendation follows logically from analysis

## Anti-Patterns to Avoid

1. **Analysis Paralysis**: Decision matrix is a tool, not a religion
2. **False Precision**: Scores to decimal places with uncertain inputs
3. **Criteria Gerrymandering**: Adding criteria to make preferred option win
4. **Weight Manipulation**: Adjusting weights after seeing results
5. **Ignoring Gut Check**: If matrix says X but gut says Y, explore why
6. **Status Quo Bias**: Underweighting the cost of not deciding
7. **Sunk Cost Inclusion**: Past investments don't affect future value

## Special Handling

### When Options Are Close
1. Check sensitivity: Would small weight changes flip the result?
2. Look for tie-breakers in second-order factors
3. Consider: Is more information available that could differentiate?
4. If truly close: Favor reversible option or flip a coin (really)

### When Analysis Feels Wrong
1. The matrix is a thinking tool, not a decision machine
2. Explore: What would make the "wrong" option right?
3. Are there hidden criteria not in the matrix?
4. Is there new information changing the inputs?

### High-Stakes Decisions
1. Increase stakeholder input on criteria and weights
2. Do formal pre-mortem for top options
3. Build explicit decision review checkpoints
4. Document reasoning for future reference

## Invocation Examples

User: "Should I take this job offer?"
→ Frame: Career decision, likely two-way door but high switching cost
→ Criteria: Compensation, growth, culture, work-life, location, learning

User: "Which cloud provider for our startup?"
→ Frame: Technical decision, moderately reversible but high migration cost
→ Criteria: Cost, features, team expertise, scaling, vendor lock-in, support

User: "Buy vs rent for the next 3 years?"
→ Frame: Financial decision, timeline-bound, many unknowns
→ Criteria: Total cost, flexibility, lifestyle, investment potential, risk tolerance
