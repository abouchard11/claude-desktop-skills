---
name: research-synthesis
description: This skill should be used when the user says "research", "investigate", "deep dive", "comprehensive analysis", "what do we know about", "explore the topic", "gather information on", or asks complex questions requiring multi-source synthesis with citations and uncertainty tracking.
---

# Deep Research Synthesis

Transform complex questions into systematic research with structured findings, confidence levels, and actionable insights.

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

**Tier 1 - Primary Sources** (Highest reliability)
- Official documentation, peer-reviewed research, authoritative databases
- Direct statements from principals (company announcements, official reports)
- Government/regulatory filings

**Tier 2 - Expert Analysis** (High reliability)
- Domain expert commentary with clear credentials
- Technical analysis from recognized authorities
- Industry reports from established research firms

**Tier 3 - Secondary Reporting** (Moderate reliability)
- Quality journalism with clear sourcing
- Aggregated data from multiple independent sources
- Well-documented case studies

**Tier 4 - Contextual Sources** (Use with caveats)
- Community discussions, forums, social media
- Opinion pieces, editorials
- Unverified claims (flag as such)

### Phase 3: Information Synthesis
For each finding, track:

1. **The Claim**: State it precisely
2. **Source Quality**: Tier 1-4 from above
3. **Confidence Level**:
   - **High** (90%+): Multiple Tier 1-2 sources agree
   - **Medium** (60-89%): Single Tier 1 source OR multiple Tier 2-3 sources
   - **Low** (30-59%): Single Tier 2-3 source OR conflicting information
   - **Speculative** (<30%): Inference, extrapolation, or single Tier 4 source
4. **Contradicting Evidence**: Note any dissenting views or conflicting data
5. **Recency**: How current is this information?

### Phase 4: Knowledge Gap Identification
Explicitly identify:

- **Known Unknowns**: Questions we identified but couldn't answer
- **Data Gaps**: Information that should exist but wasn't found
- **Conflicting Information**: Where sources disagree and why
- **Temporal Gaps**: Information that may be outdated
- **Scope Limitations**: What was outside research scope

### Phase 5: Synthesis and Implications
Connect findings to user's needs:

1. **Key Findings Summary**: 3-5 most important discoveries
2. **Implications**: What do these findings mean for the user's context?
3. **Recommendations**: Concrete next steps based on findings
4. **Further Research Needed**: What additional investigation would add value?

## Output Structure

### Research Report Format

```
## Research Question
[Restated core question with identified sub-questions]

## Executive Summary
[3-5 sentence overview of key findings and confidence level]

## Detailed Findings

### [Finding Category 1]
**Claim**: [Precise statement]
**Confidence**: [High/Medium/Low/Speculative]
**Source(s)**: [Citation with tier]
**Evidence**: [Supporting details]
**Caveats**: [Limitations, contradictions, or uncertainties]

### [Finding Category 2]
[Same structure]

## Knowledge Gaps
- [Gap 1]: [Why this matters and potential sources]
- [Gap 2]: [Why this matters and potential sources]

## Contradictions & Debates
- [Contradiction 1]: [Source A says X, Source B says Y, assessment]

## Implications
[What these findings mean for the user's specific context]

## Recommended Actions
1. [Concrete action with rationale]
2. [Concrete action with rationale]
3. [Concrete action with rationale]

## Further Research Opportunities
- [Topic for deeper investigation]
- [Topic for deeper investigation]

## Sources Referenced
[Numbered list with URLs/citations]
```

## Quality Checks

Before delivering research, verify:

### Completeness Checks
- [ ] All sub-questions addressed (or gaps explicitly noted)
- [ ] Multiple source types consulted where possible
- [ ] Both supporting and contradicting evidence considered
- [ ] Temporal relevance assessed (information recency)

### Accuracy Checks
- [ ] Claims precisely stated (not overgeneralized)
- [ ] Confidence levels appropriate to evidence quality
- [ ] Sources correctly attributed
- [ ] Inferences clearly distinguished from facts

### Usefulness Checks
- [ ] Findings connected to user's actual question/need
- [ ] Recommendations are actionable and specific
- [ ] Knowledge gaps don't undermine core conclusions
- [ ] User can act on this information

### Intellectual Honesty Checks
- [ ] Uncertainty explicitly acknowledged
- [ ] Alternative interpretations noted where relevant
- [ ] Own limitations (search constraints, knowledge cutoff) stated
- [ ] Not presenting speculation as fact

## Anti-Patterns to Avoid

1. **Confirmation Bias**: Don't just find sources that support the expected answer
2. **Authority Fallacy**: Credentials don't make claims true; evaluate the evidence
3. **Recency Bias**: Newer isn't always more accurate
4. **Single Source Dependence**: One source isn't research; it's citation
5. **Hedging to Death**: Excessive caveats that provide no useful signal
6. **False Precision**: "Studies show 73.2%" when the actual confidence is low
7. **Scope Creep**: Going deep on tangents while missing core questions

## Special Handling

### When Sources Conflict
1. Present both positions fairly
2. Evaluate source reliability for each
3. Note methodological differences if apparent
4. Provide assessment of which is more likely accurate and why
5. If unresolvable, state clearly and note what would resolve it

### When Information Is Unavailable
1. State clearly what was sought but not found
2. Explain why it might not be available
3. Suggest alternative approaches to get this information
4. Note if the gap materially affects conclusions

### When Confidence Is Low
1. Be explicit: "This is my best inference with limited data"
2. Explain what would increase confidence
3. Note if the user should wait for better information before acting
4. Provide conditional recommendations: "If X is true, then Y"

## Invocation Examples

User: "Research the current state of battery technology for EVs"
→ Decompose into: chemistry advances, manufacturing scaling, cost curves, recycling, charging infrastructure, timeline projections

User: "What do we know about Company X's financial health?"
→ Decompose into: public financials, industry position, management changes, market sentiment, risk factors, growth indicators

User: "Deep dive on remote work productivity research"
→ Decompose into: quantitative studies, confounding factors, industry variations, long-term effects, management implications
