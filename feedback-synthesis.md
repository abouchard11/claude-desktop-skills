---
name: feedback-synthesis
description: This skill should be used when the user shares reviews, feedback, survey responses, customer comments, NPS responses, testimonials, or says "summarize feedback", "what do people think", "common complaints", "sentiment analysis", "aggregate reviews", "feedback themes", "what are customers saying".
---

# Feedback Synthesizer

Transform raw feedback noise into actionable signal through systematic theme extraction, sentiment analysis, and priority ranking.

## Approach

### Phase 1: Feedback Inventory
Before analyzing, catalog the input:

1. **Source Type**:
   - Customer reviews (product, app store, etc.)
   - Survey responses (NPS, CSAT, open-ended)
   - Support tickets/complaints
   - Social media mentions
   - Internal feedback (team, 360 reviews)
   - User interviews/research

2. **Sample Characteristics**:
   - Volume: How many pieces of feedback?
   - Time Range: When was this collected?
   - Representativeness: Who's in this sample? Who's missing?
   - Selection Bias: Why did these people give feedback?

3. **Context Factors**:
   - Recent Changes: Any new releases, pricing changes, etc.?
   - External Events: Industry news, competitor actions?
   - Seasonal Effects: Holiday period, end of quarter?

### Phase 2: Initial Pass - Sentiment Tagging
Categorize each piece of feedback:

**Sentiment Categories**
- **Positive**: Praise, satisfaction, delight
- **Negative**: Complaints, frustration, problems
- **Neutral**: Factual, suggestions without strong sentiment
- **Mixed**: Both positive and negative elements

**Intensity Scale**
- **Strong**: Emotional language, superlatives, all-caps
- **Moderate**: Clear opinion but measured
- **Mild**: Slight preference or concern

### Phase 3: Theme Extraction
Identify recurring patterns:

**Theme Types**

1. **Feature/Functionality Themes**
   - What people love
   - What's missing
   - What's broken
   - What's confusing

2. **Experience Themes**
   - Onboarding issues
   - Learning curve
   - Support interactions
   - Performance/speed

3. **Value Themes**
   - Price/value perception
   - ROI discussions
   - Comparison to alternatives
   - Willingness to recommend

4. **Emotional Themes**
   - Trust/confidence
   - Frustration/friction
   - Delight/surprise
   - Disappointment

### Phase 4: Quantification
Count and weight themes:

**Volume Analysis**
- How many mentions per theme?
- % of total feedback mentioning each theme
- Trend over time (increasing/decreasing)

**Intensity Weighting**
- Strong negative = weight 3x
- Moderate negative = weight 2x
- Mild negative = weight 1x
- (Same scale for positive)

**Impact Assessment**
- Does this affect new users, power users, or all?
- Is this a blocker or an annoyance?
- Does this affect retention or acquisition?

### Phase 5: Signal vs Noise Filtering
Separate actionable insights from noise:

**High Signal** (Act on this)
- Recurring theme (5%+ of feedback)
- Multiple independent sources mention it
- Trend is worsening over time
- Connected to key business metric
- Actionable and within control

**Low Signal** (Note but deprioritize)
- One-off mentions
- Contradicted by majority
- Out of scope/control
- Unlikely to impact business
- Already being addressed

### Phase 6: Priority Ranking
Rank themes by action priority:

**Priority Matrix**

| | High Frequency | Low Frequency |
|---|---|---|
| **High Impact** | P1: Fix immediately | P2: Investigate |
| **Low Impact** | P3: Plan for future | P4: Monitor only |

Consider also:
- Effort to address
- Strategic alignment
- Quick wins available

## Output Structure

### Feedback Analysis Format

```
## Analysis Overview
**Feedback Volume**: [N pieces analyzed]
**Sources**: [Where feedback came from]
**Time Period**: [Date range]
**Overall Sentiment**: [X% positive, Y% negative, Z% neutral]

---

## Executive Summary
[3-5 sentences: Top themes, overall health, key concerns]

---

## Sentiment Breakdown

### Positive Themes (What's Working)

| Theme | Mentions | % of Total | Representative Quote |
|-------|----------|------------|---------------------|
| [Theme] | [N] | [X%] | "[Verbatim quote]" |

### Negative Themes (What Needs Attention)

| Theme | Mentions | % of Total | Severity | Representative Quote |
|-------|----------|------------|----------|---------------------|
| [Theme] | [N] | [X%] | [H/M/L] | "[Verbatim quote]" |

### Neutral/Suggestions

| Theme | Mentions | Actionability | Representative Quote |
|-------|----------|--------------|---------------------|
| [Theme] | [N] | [High/Med/Low] | "[Verbatim quote]" |

---

## Priority Recommendations

### P1: Address Immediately
1. **[Theme]**: [Why it's urgent, suggested action]

### P2: Plan to Address
1. **[Theme]**: [Why it matters, timeline suggestion]

### P3: Future Consideration
1. **[Theme]**: [Low urgency but track]

### Monitor Only
1. **[Theme]**: [Why not acting now]

---

## Notable Outliers
[Individual feedback pieces that don't fit themes but are noteworthy]

## Confidence & Caveats
- [Sample size limitations]
- [Selection bias concerns]
- [Themes that need more data]

## Recommended Follow-ups
- [What to investigate further]
- [Who to talk to for more context]
- [Data to collect going forward]
```

## Quality Checks

Before delivering analysis, verify:

### Data Quality
- [ ] Sufficient sample size for conclusions
- [ ] Sources documented
- [ ] Time period clear
- [ ] Selection bias acknowledged

### Theme Quality
- [ ] Themes are distinct (not overlapping)
- [ ] Each theme backed by multiple mentions
- [ ] Themes are actionable (not too vague)
- [ ] Contradicting feedback noted

### Quantification Quality
- [ ] Counts are accurate
- [ ] Percentages add up reasonably
- [ ] Weighting logic is consistent
- [ ] Outliers identified

### Analysis Quality
- [ ] Signal distinguished from noise
- [ ] Priority rankings justified
- [ ] Recommendations are actionable
- [ ] Confidence levels appropriate

## Anti-Patterns to Avoid

1. **Cherry-Picking**: Only highlighting feedback that confirms priors
2. **Volume Bias**: Loud minority drowning out quiet majority
3. **Recency Bias**: Over-weighting recent feedback
4. **Anecdote Elevation**: Treating one vivid story as a trend
5. **Theme Inflation**: Creating themes with only 1-2 mentions
6. **False Precision**: "42.7% mention X" with N=23
7. **Ignoring Context**: Missing that spike correlates with outage
8. **Actionability Blindness**: Themes without path to improvement

## Special Handling

### Small Sample Sizes (N < 30)
1. Note limitation explicitly
2. Focus on qualitative patterns, not percentages
3. Identify what questions need more data
4. Be tentative in conclusions

### Highly Negative Feedback Sets
1. Look for survivor bias (who left without feedback?)
2. Separate systemic issues from individual incidents
3. Identify any positive signals (often overlooked)
4. Prioritize ruthlessly (can't fix everything)

### Mixed/Contradictory Feedback
1. Segment by user type (power users vs new users)
2. Look for context differences
3. Identify if it's preference vs problem
4. Note genuinely unresolvable trade-offs

### Feedback Over Time
1. Track trend direction per theme
2. Note inflection points and correlate with changes
3. Identify improving vs worsening areas
4. Distinguish seasonal from structural patterns

## Invocation Examples

User: [Pastes 50 app store reviews]
→ Sentiment breakdown, feature requests, complaints ranked by frequency, actionable recommendations

User: "What are the main complaints in these support tickets?"
→ Focus on negative themes, severity ranking, common root causes

User: "Summarize this NPS feedback - what's driving detractors?"
→ Segment by promoter/passive/detractor, focus on detractor themes, identify fixable issues
