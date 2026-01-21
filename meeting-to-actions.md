---
name: meeting-to-actions
description: This skill should be used when the user shares meeting notes, transcript, agenda, recording summary, or says "extract action items", "meeting summary", "who does what", "follow-ups from", "action items from", "meeting takeaways", or provides text with multiple people and tasks mentioned.
---

# Meeting to Actions Extractor

Transform messy meeting notes into structured commitments with clear ownership, deadlines, and accountability tracking.

## Approach

### Phase 1: Context Identification
Before extracting, understand the meeting:

1. **Meeting Type**:
   - Standup/sync (status updates, blockers)
   - Planning (decisions, resource allocation)
   - Brainstorm (ideas, no immediate actions)
   - Review (feedback, next steps)
   - Decision meeting (commitments made)
   - 1:1 (personal actions, follow-ups)

2. **Participants**: Who was present? Their roles?
3. **Purpose**: What was this meeting supposed to accomplish?
4. **Outcomes**: Did it achieve its purpose?

### Phase 2: Action Item Detection
Scan for explicit and implicit commitments:

**Explicit Commitment Signals**
- "I will...", "I'll...", "I'm going to..."
- "[Name] will...", "[Name] is going to..."
- "Action item:", "TODO:", "Next step:"
- "Can you...", "Could you...", "Would you mind..."
- "Let's...", "We should...", "We need to..."

**Implicit Commitment Signals**
- Problems raised without stated owners → needs owner assigned
- Questions asked without answers → needs follow-up
- Decisions made → may require implementation actions
- Dependencies mentioned → needs tracking
- Deadlines referenced → needs capture

### Phase 3: Commitment Parsing
For each detected action, extract:

1. **WHO**: Clear owner (single person, not "the team")
2. **WHAT**: Specific deliverable or outcome
3. **WHEN**: Deadline (explicit or inferred)
4. **WHY**: Context/purpose (what decision depends on this)
5. **DEPENDENCIES**: What/who is this blocked by?
6. **CONFIDENCE**: How clear was this commitment?

### Phase 4: Ambiguity Flagging
Identify and flag unclear items:

**Ownership Ambiguity**
- "We should do X" → WHO is "we"?
- "Someone needs to..." → WHO specifically?
- "The team will..." → WHO is point person?

**Scope Ambiguity**
- "Look into X" → What does "look into" mean?
- "Follow up on..." → What specifically?
- "Handle the Y situation" → What's the deliverable?

**Timeline Ambiguity**
- "Soon", "ASAP", "when you get a chance"
- No deadline mentioned at all
- Conflicting timeline signals

### Phase 5: Decision Capture
Separate from actions, capture decisions made:

1. **Decision**: What was decided?
2. **Rationale**: Why? (if stated)
3. **Alternatives Rejected**: What wasn't chosen? (if discussed)
4. **Implications**: What does this decision trigger?
5. **Reversibility**: Is this final or provisional?

### Phase 6: Context Preservation
Capture non-action items worth preserving:

- Key discussion points
- Open questions not yet answered
- Concerns raised
- Ideas for future consideration
- Dependencies on external events

## Output Structure

### Meeting Summary Format

```
## Meeting Overview
**Date**: [Date]
**Type**: [Meeting type]
**Participants**: [Names and roles]
**Purpose**: [What was this meeting for]
**Outcome Summary**: [1-2 sentences on what was accomplished]

---

## Action Items

### High Priority

| Owner | Action | Deadline | Context |
|-------|--------|----------|---------|
| @Name | [Specific action] | [Date] | [Why this matters] |

### Standard Priority

| Owner | Action | Deadline | Context |
|-------|--------|----------|---------|
| @Name | [Specific action] | [Date] | [Why this matters] |

### Needs Clarification

| Unclear Item | Ambiguity | Suggested Resolution |
|--------------|-----------|---------------------|
| [Item] | [What's unclear: owner/scope/timeline] | [Proposed clarification] |

---

## Decisions Made

| Decision | Rationale | Owner | Implications |
|----------|-----------|-------|--------------|
| [What was decided] | [Why] | [Who owns implementation] | [What this triggers] |

---

## Dependencies & Blockers

| Item | Blocked By | Expected Resolution | Impact |
|------|------------|--------------------|---------|
| [What's blocked] | [What/who blocks it] | [When/how resolved] | [What's delayed] |

---

## Open Questions
- [Question 1] - Needs answer from [who]
- [Question 2] - To be researched by [who]

## Parking Lot (Future Discussion)
- [Topic 1] - [Brief context]
- [Topic 2] - [Brief context]

---

## Follow-up Meeting Needed?
[Yes/No] - [If yes, purpose and suggested participants]
```

## Quality Checks

Before delivering extraction, verify:

### Completeness Checks
- [ ] All commitments captured (both explicit and implicit)
- [ ] Every action has a clear owner
- [ ] Deadlines captured where mentioned
- [ ] Decisions distinct from actions
- [ ] Ambiguities flagged, not ignored

### Accuracy Checks
- [ ] Owners correctly attributed (not assumed)
- [ ] Actions stated as deliverables, not activities
- [ ] Timelines exactly as stated (no invented deadlines)
- [ ] Context preserved for each action

### Actionability Checks
- [ ] Actions are specific enough to execute
- [ ] Owners can act without further clarification
- [ ] Deadlines are realistic given context
- [ ] Dependencies are trackable

### Honesty Checks
- [ ] Implicit items flagged as inferred
- [ ] Ambiguity acknowledged, not papered over
- [ ] Confidence levels appropriate
- [ ] Not adding actions that weren't committed to

## Anti-Patterns to Avoid

1. **Phantom Ownership**: Assigning owners not mentioned in meeting
2. **Scope Invention**: Making vague items specific without basis
3. **Deadline Invention**: Adding dates not discussed
4. **Action Inflation**: Creating actions from casual comments
5. **Context Stripping**: Actions without why = lost accountability
6. **Decision Amnesia**: Missing decisions buried in discussion
7. **Passive Voice Trap**: "X will be done" without WHO

## Special Handling

### When Ownership Is Unclear
1. Flag explicitly as "NEEDS OWNER"
2. Suggest likely candidates based on context
3. Note: "This requires follow-up to assign"
4. Don't invent owners

### When Timeline Is Missing
1. Flag as "DEADLINE TBD"
2. If meeting had general timeline context, note it
3. Suggest reasonable deadline based on context
4. Mark suggestion as inferred, not committed

### When Scope Is Vague
1. Quote the original language
2. Flag specific ambiguity type
3. Suggest clarifying questions
4. Propose concrete interpretation if reasonable

### Recurring Meeting Patterns
For standups/syncs:
- Focus on changes from last time
- Track blocked items
- Note escalations needed

For planning meetings:
- Capture resource commitments
- Track scope decisions
- Note trade-offs made

For decision meetings:
- Decisions are primary output
- Actions are implementation of decisions
- Capture rationale explicitly

## Invocation Examples

User: [Pastes meeting transcript]
→ Parse participants, extract commitments, flag ambiguities, structure output

User: "What were the action items from that planning meeting?"
→ Focus on WHO/WHAT/WHEN, prioritize by importance, flag missing info

User: "Summarize the key decisions and next steps"
→ Decisions table + action items table, minimal context
