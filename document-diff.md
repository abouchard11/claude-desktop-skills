---
name: document-diff
description: This skill should be used when the user says "compare these", "what changed", "difference between", "track changes", "version comparison", "diff these documents", "changes from version", "what's different", or pastes two versions of text, contracts, policies, agreements, or documents.
---

# Document Diff Analyzer

Identify material changes between document versions with semantic understanding, not just text comparison.

## Approach

### Phase 1: Document Characterization
Before comparing, understand what you're comparing:

1. **Document Type**:
   - Contract/legal agreement
   - Policy/terms of service
   - Technical specification
   - Business proposal
   - Code/configuration
   - Meeting notes/records
   - General text

2. **Comparison Context**:
   - Why is user comparing these?
   - What changes would matter most?
   - Who cares about the differences?
   - Are there known areas of concern?

3. **Version Information**:
   - Which is "before" and which is "after"?
   - Time between versions if known
   - Author of changes if known
   - Context of changes if known

### Phase 2: Change Detection Layers
Analyze at multiple levels:

**Surface Changes** (Easy to spot)
- Added text/sections
- Removed text/sections
- Moved text/sections
- Word/phrase substitutions

**Structural Changes** (Organization)
- Section reordering
- Hierarchy changes (headers, nesting)
- Format changes (lists to paragraphs, etc.)
- Reference changes (cross-references, links)

**Semantic Changes** (Meaning)
- Definition changes
- Scope expansions/reductions
- Obligation changes
- Timeline/deadline changes
- Party/role changes
- Condition changes

**Implied Changes** (Consequences)
- Risk exposure changes
- Rights/obligations shifts
- Enforcement implications
- Liability impacts

### Phase 3: Materiality Assessment
Not all changes matter equally:

**Material Changes** (High importance)
- Alters rights, obligations, or liabilities
- Changes financial terms
- Modifies timelines or deadlines
- Shifts risk allocation
- Adds or removes parties
- Changes governing terms

**Significant Changes** (Medium importance)
- Clarifies ambiguous language
- Standardizes terminology
- Updates references
- Improves specificity
- Reorganizes for clarity

**Cosmetic Changes** (Low importance)
- Formatting only
- Typo fixes
- Punctuation changes
- Style consistency
- Minor rewording without meaning change

### Phase 4: Change Cataloging
For each material change, document:

1. **Location**: Where in document
2. **Before**: Exact original text
3. **After**: Exact new text
4. **Change Type**: Add/remove/modify/move
5. **Category**: Which phase 3 category
6. **Implication**: What this change means

### Phase 5: Pattern Analysis
Look for systematic changes:

- Consistent terminology shifts
- Repeated structural patterns
- One-sided modifications (all favor one party)
- Areas of heavy revision vs stability
- Changes that work together

### Phase 6: Risk/Opportunity Flagging
Highlight items needing attention:

**Red Flags** (Negative for user)
- Rights reduced
- Obligations increased
- Liability expanded
- Terms less favorable

**Yellow Flags** (Ambiguous)
- Meaning unclear
- Could go either way
- Needs clarification
- Depends on interpretation

**Green Flags** (Positive for user)
- Rights expanded
- Obligations reduced
- Terms more favorable
- Better protections

## Output Structure

### Document Comparison Format

```
## Comparison Overview
**Document Type**: [Type]
**Version A**: [Description/date]
**Version B**: [Description/date]
**Overall Assessment**: [Summary of change scope and direction]

---

## Executive Summary
**Total Changes**: [N changes identified]
**Material Changes**: [N] | **Significant Changes**: [N] | **Cosmetic Changes**: [N]

**Key Takeaway**: [1-2 sentences on what matters most]

---

## Material Changes (Require Attention)

### 1. [Change Description]
**Location**: [Section/paragraph]
**Category**: [Obligation/Right/Liability/Timeline/etc.]

| Before | After |
|--------|-------|
| "[Exact original text]" | "[Exact new text]" |

**Implication**: [What this means in practical terms]
**Flag**: [Red/Yellow/Green]

### 2. [Change Description]
[Same format]

---

## Significant Changes (Worth Noting)

| # | Location | Change Summary | Before → After |
|---|----------|----------------|----------------|
| 1 | [Loc] | [Summary] | "[Key phrase]" → "[New phrase]" |
| 2 | [Loc] | [Summary] | "[Key phrase]" → "[New phrase]" |

---

## Cosmetic Changes (For Completeness)
- [X formatting/style changes in Section Y]
- [N typo corrections throughout]
- [Other cosmetic items grouped]

---

## Pattern Analysis
**Systematic Changes Observed**:
- [Pattern 1]: [Description and occurrences]
- [Pattern 2]: [Description and occurrences]

**Areas of Heavy Revision**:
- [Section X]: [N changes, nature of changes]

**Unchanged Areas**:
- [Section Y]: [No changes, significance if any]

---

## Risk Assessment

### Red Flags
1. **[Issue]**: [Why concerning, where to find it]

### Yellow Flags (Ambiguous)
1. **[Issue]**: [What's unclear, questions to ask]

### Green Flags (Improvements)
1. **[Issue]**: [What's better, why it matters]

---

## Recommended Actions
1. [Specific action re: specific change]
2. [Question to ask counterparty]
3. [Clause to negotiate]

## Questions to Resolve
- [Ambiguity needing clarification]
- [Missing information]
```

## Quality Checks

Before delivering comparison, verify:

### Accuracy Checks
- [ ] Before/after versions correctly identified
- [ ] All changes captured (nothing missed)
- [ ] Exact text quoted accurately
- [ ] Change type correctly categorized

### Completeness Checks
- [ ] All sections compared
- [ ] Both additions and deletions noted
- [ ] Moved content tracked (not marked as delete+add)
- [ ] Implicit changes identified

### Materiality Checks
- [ ] Material vs cosmetic appropriately distinguished
- [ ] Implications accurately assessed
- [ ] Flags appropriate to severity
- [ ] Patterns identified

### Usefulness Checks
- [ ] User can act on this comparison
- [ ] Key changes highlighted appropriately
- [ ] Recommended actions are specific
- [ ] Nothing important buried in cosmetic changes

## Anti-Patterns to Avoid

1. **False Equivalence**: Treating minor and major changes equally
2. **Surface-Only**: Missing semantic changes with same words
3. **Missing Context**: Changes without explaining implications
4. **Alarm Fatigue**: Flagging everything as important
5. **Cosmetic Inflation**: Making formatting changes seem significant
6. **Interpretation Overreach**: Stating implications as fact when uncertain
7. **Pattern Blindness**: Missing systematic one-sided changes
8. **Version Confusion**: Mixing up which is before/after

## Special Handling

### Legal/Contract Documents
1. Pay extra attention to:
   - Defined terms and definitions section
   - Limitation of liability clauses
   - Indemnification provisions
   - Termination rights
   - Governing law/jurisdiction
2. Flag any:
   - New obligations
   - Reduced rights
   - Liability caps changed
   - Notice period changes
3. Recommend legal review for material changes

### Technical Specifications
1. Focus on:
   - Requirement changes (shall/must)
   - Acceptance criteria
   - Performance metrics
   - API/interface definitions
2. Track:
   - Breaking vs non-breaking changes
   - Backward compatibility impacts
   - Dependency implications

### Policy Documents
1. Watch for:
   - Scope changes (who's affected)
   - Process changes (how things work)
   - Enforcement changes (consequences)
   - Exception changes (what's allowed)

### When Documents Are Very Different
1. Note that this is a major revision, not incremental change
2. Consider structural comparison over line-by-line
3. Focus on what's kept vs what's new
4. May be more useful to characterize each separately

## Invocation Examples

User: [Pastes two versions of employment contract]
→ Focus on compensation, responsibilities, IP assignment, termination, non-compete changes

User: "What changed in version 2 of the API spec?"
→ Focus on endpoint changes, breaking changes, new/deprecated features

User: "Compare these two proposals and tell me what's different"
→ Focus on pricing, scope, timeline, terms differences
