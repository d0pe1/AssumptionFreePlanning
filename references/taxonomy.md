# Taxonomy

Every term the roadmap uses, defined once and grounded in an established source. Use these words with exactly these meanings. A plan in which "milestone", "task" and "requirement" mean different things to different readers is itself a hidden assumption.

Sources (marked **v** = checked against the source while writing this file, **m** = taken from the standard from memory, not checked):
- [PMI] PMI Lexicon of Project Management Terms / PMBOK Guide glossary (v)
- [WBS] PMI, *Applying work breakdown structure to project lifecycle*; Haugan 2002 (v)
- [SG] Scrum Guide 2020, scrumguides.org (v)
- [ISTQB] ISTQB Glossary and Foundation Level syllabus §2.2 (v)
- [29148] ISO/IEC/IEEE 29148, requirements engineering (m)
- [INVEST] Bill Wake, "INVEST in Good Stories" (2003) (m)
- [RAID] Risks / Assumptions / Issues / Dependencies log, common PM practice (m)

## The hierarchy

```
Intent (Product Goal)
└── Roadmap
    └── Milestone  ── a checkpoint, reached when its deliverables pass acceptance
        └── Deliverable / Work package  ── a component, or a slice of one
            └── Requirement  ── with acceptance criteria and test level
                └── Task  ── owned by devs, not written by this skill
```

The planner writes everything down to **Requirement**. **Task** and below belong to the people building it.

## Planning terms

| Term | Definition | Source | How this skill uses it |
|---|---|---|---|
| **Intent / Product Goal** | The future state of the product the team is working toward. It is the long-term objective. | [SG] | Phase 0/1. Confirmed by the intent giver in their own words. Everything must trace back to it. |
| **Scope** | All of the work the project includes, and only that work. | [PMI] | The intent plus the explicit **Out of scope** list. |
| **Roadmap** | The ordered set of milestones from today to the intent. | (practice) | `ROADMAP.md`. |
| **Milestone** | "A significant point or event in a project." A schedule milestone **has zero duration**: it marks the completion of a major deliverable or an event that restrains future work. | [PMI] | A milestone is a *checkpoint*, not a bucket of work. Write it as "M2 is reached when …", followed by verifiable conditions. The work leading up to it lives in its deliverables. |
| **Deliverable** | A unique, verifiable product, result or capability that must be produced to complete a process, phase or project. | [PMI] | Usually one component, or a vertical slice of several components. Each milestone lists its deliverables. |
| **WBS** | "A deliverable-oriented hierarchical decomposition of the work to be executed by the project team." | [WBS] | The milestone → deliverable → requirement tree. |
| **100% rule** | The children of a node add up to exactly 100% of the parent's work: no gaps and nothing outside scope. | [WBS] | An integration check in Phase 3. Every part of the intent is covered by some requirement, and no requirement falls outside the intent. |
| **Work package** | The lowest level of the WBS, where cost, effort, duration and resources are estimated and managed. | [PMI] | A deliverable small enough for a dev or team to estimate and own. If a dev can't estimate it, split it or ask more questions. |
| **Planning package** | A WBS element whose scope is known but whose details are not yet. It becomes a work package once the details are defined. | [WBS] | Same as a deliverable that is BLOCKED by an OPEN item. It stays in the tree so the 100% rule holds, but it is not READY. |
| **Dependency** | One element can't start or finish until another one does. | [RAID] | `Depends on:` on milestones. It sets the order of the component loop. |

## Decision and knowledge terms (RAID-aligned)

| Term | Definition | Source | How this skill uses it |
|---|---|---|---|
| **Assumption** | Something taken as true without proof, for planning purposes. | [PMI] | **The thing this skill exists to remove.** At spec level, every assumption must become a Decision (D-n), a Fact (F-n) or an OPEN-n. None may remain in the final roadmap. |
| **Constraint** | A limiting factor that affects how the project is carried out. | [PMI] | A mandate, recorded as a D- item with a cited source. |
| **Decision** (D-n) | A choice made by someone with the authority to make it, with the alternatives recorded. Similar to an ADR. | (practice) | Records who decided it, the date and the options considered. |
| **Fact** (F-n) | A claim about the world, with its evidence. | — | Records the source plus whether it is verified, unverified or inference. |
| **Issue / OPEN-n** | An open question that blocks progress and has an owner. | [RAID] | A question, its owner, what it blocks, and when it was raised. |
| **Risk** | An uncertain event that would affect objectives if it happened. | [PMI] | Phase 4. A risk that needs someone to choose a response becomes a question. |
| **Estimate** | A quantitative assessment of a likely amount or outcome, with a stated accuracy. | [PMI] | Always given as a range with its basis. Never presented as a decision. |

## Requirement terms

| Term | Definition | Source | How this skill uses it |
|---|---|---|---|
| **Requirement** (R-x.y) | A statement of a need that a solution must satisfy. A good one is **necessary, unambiguous, singular, feasible, verifiable, consistent and traceable**. | [29148] | Each one cites the D-/F- items it rests on (that makes it traceable). It says *what*, never *how*: the line between spec and implementation. |
| **Functional / non-functional** | What the system does / how well it does it (performance, availability, security, retention, …). | [29148] | Non-functional numbers are almost always decisions. Never default them. |
| **Acceptance criteria** | The conditions a deliverable must meet to be accepted by the person who asked for it. | [PMI] | Every R- has them. A reviewer who has never seen the planning conversation must be able to check them. |
| **INVEST** | A good backlog item is **I**ndependent, **N**egotiable, **V**aluable, **E**stimable, **S**mall and **T**estable. | [INVEST] | The quality check for a work package before it is marked READY. |
| **Definition of Done (DoD)** | "A formal description of the state of the Increment when it meets the quality measures required for the product." If an item doesn't meet it, it can't be released or even presented. | [SG] | **One DoD for the whole project, decided by a human** (e.g. review required? which test levels? coverage threshold? docs?). It is a spec-level decision, asked once in Phase 3, and it applies to every work package. |
| **Increment** | The moment a backlog item meets the Definition of Done. | [SG] | A deliverable that passes its acceptance criteria and the DoD. |

## Execution terms (the devs' side of the line)

| Term | Definition | Source | How this skill uses it |
|---|---|---|---|
| **Task** | A unit of work the developers use to build a backlog item. Typically "one day or less". How items are broken into tasks is "at the sole discretion of the Developers". | [SG] | **The planner does not write tasks.** It hands over work packages with requirements, acceptance criteria and the DoD. Splitting them into tasks is implementation, the same as naming and code structure. |
| **Activity** | A distinct, scheduled portion of the work needed to complete a work package. | [PMI] | Same as a task here. It belongs to the devs. |

## Test levels

The plan decides **which level must prove each requirement** and **what the DoD demands**. It never writes the tests.

| Level | Definition | Source | Typically proves |
|---|---|---|---|
| **Component (unit) test** | Testing of individual software components in isolation: the smallest testable part. Usually written by developers. | [ISTQB] | Logic inside one component. Usually required through the DoD, not listed per requirement. |
| **Integration test** | Testing that exposes defects in the interfaces and interactions between components or systems. | [ISTQB] | The interface contracts written in Phase 3. |
| **System test** | Testing the integrated system against its specified requirements, functional and non-functional. | [ISTQB] | End-to-end requirements and non-functional numbers. |
| **Acceptance test** | Testing whether the system satisfies the acceptance criteria and whether the stakeholder accepts it. | [ISTQB] | Milestone conditions ("M2 is reached when …"). |

In the requirement table, the `Verified by` column names the level (unit / integration / system / acceptance), so devs know what kind of evidence closes each requirement.
