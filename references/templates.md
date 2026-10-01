# Templates

## ROADMAP.md skeleton

```markdown
# <Project> Roadmap

Status: <Phase 0–5> · Review: <GREEN | RED | not yet> · Last updated: <date>

## Intent
<Outcome, for whom, success signal, in the user's words. Confirmed by <name> on <date>.>

## Out of scope
- <explicit non-goals, incl. adjacent/future systems → boundary only>

## Mandates and decision authority
| Area | Mandate / owner | Source |
|---|---|---|
| Secrets management | Org mandate: <X> | <policy / email / person, date> |
| Hosting | Decided by <role/name> | <source> |

## Decisions
| ID | Decision | Options considered | Decided by | Evidence | Date |
|---|---|---|---|---|---|
| D-1 | <choice> | <A, B, C> | <name or mandate> | <verbatim quote / doc link> | <date> |

## Facts
| ID | Fact | Source | Status |
|---|---|---|---|
| F-1 | <statement> | <URL / doc / command> | verified · unverified · inference (from …) |

## OPEN
| ID | Question | Owner | Blocks | Raised |
|---|---|---|---|---|
| OPEN-1 | <bounded question> | <person/role> | M2, R-3.1 | <date> |

## Definition of Done (applies to every work package)
Decided by <name>, <date> (D-n):
- <e.g. code reviewed by 1 other dev>
- <e.g. unit tests for new logic; integration tests for every interface contract touched>
- <e.g. docs updated>

## Milestones
### M1 — <name>  · READY | BLOCKED by OPEN-n
M1 is reached when: <verifiable conditions = acceptance test>
Depends on: <M-ids or none>
Deliverables: <C-ids / slices>   (devs split these into tasks themselves)

## Components
### C1 — <name>
Purpose: <one line>
Interfaces: <inputs/outputs, contract to other components>

| ID | Requirement | Acceptance criteria | Verified by | Rests on |
|---|---|---|---|---|
| R-1.1 | <what, not how> | <how a reviewer verifies it> | unit · integration · system · acceptance | D-2, F-1 |

## Estimates (not decisions)
| What | Range | Basis |
|---|---|---|
```

## Options table (one per decision)

```markdown
### Decision needed: <question>  (component C<n>)
Why it matters: <what downstream depends on it>
Excluded by mandate: <option — reason, source> (or "none")

| Option | Pros | Cons | Touches / forces |
|---|---|---|---|
| A | | | |
| B | | | |
| C | | | |

Facts used: F-3 (verified), F-4 (unverified)
→ Which one, or is this someone else's call?
```

No "Recommended" column. Add a separate, labelled "Agent recommendation, not a decision" line only when asked.

## Example: declared assumptions for one component

Intent: "I want to be a CVE watchdog." Component C5, Notification:

1. Who is notified: a single person, an on-call rotation, or the owner of the affected asset? (decision)
2. Which events trigger a notification: every match, only above a severity, only actively exploited (KEV)? (decision)
3. Which severity model: CVSS v3.1, v4.0, EPSS, or a combination? (decision; F: which feeds expose which, to be researched)
4. Channel: email, Teams, Slack, Signal, SMS, pager service? (decision)
5. Protocol or integration per channel: SMTP, webhook, Graph API, vendor API? (decision; F: what each supports)
6. Urgency tiers, and what each tier means in response time? (decision)
7. Escalation if nobody acknowledges: after how long, and to whom? (decision)
8. Quiet hours and on-call times? (decision)
9. Deduplication and re-notification when a CVE is updated? (decision)
10. Audit trail: must notifications be retained, and for how long? (decision, possibly a mandate)

Each one becomes an options table, then a D-n or an OPEN-n, and only then an R-5.x.
