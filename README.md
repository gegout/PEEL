# PEEL — Producer–Expert–Engineering Loop

PEEL is a governed pattern for complex, long-running autonomous work.

An external **Authority** sets the mandate. **Producer** runs and verifies the loop.
**Expert** writes one Directive per cycle. **Engineer** executes it and returns durable evidence and state.

```
Authority → Producer → Expert → Engineer → evidence / state / incidents → Producer & Expert → next cycle
```

## Why PEEL

Long-running autonomous sessions need four things:

- Clear decision rights
- Repeatable execution
- Independent verification
- Continuity across cycles

PEEL provides them without multiplying authorities, supervisory roles or memory subsystems.

## The four roles

| Role | Position | Owns | Must not |
| --- | --- | --- | --- |
| Authority | External | Mission, Constitution, loop design, reserved decisions | Routine operation or execution |
| Producer | Inside loop | Operation, supervision, primary-evidence checks, budgets, incidents | Write Directives or execute work |
| Expert | Inside loop | Method, Policy, next line of work, the Directive | Execute work or alter the Constitution |
| Engineer | Inside loop | Execution, tests, measurements, state and evidence | Choose direction or relax governance |

## Ordered authority stack

Lower documents refine but never contradict higher ones. Conflicts are escalated, not silently resolved.

1. **CONSTITUTION** — owned by Authority
2. **METHOD** — owned by Expert, reviewed by Producer
3. **POLICY** — owned by Expert, reviewed by Producer
4. **DIRECTIVE** — one cycle, Expert → Engineer (this *is* the Work Contract)

## Key principles

- Verify reality, not the report. Rely on primary evidence.
- Scripts repair format; models repair meaning.
- Protect authority with locked documents and restricted credentials, not only prompts.
- Complete a durable handover before returning control.
- Keep the framework smaller than any project-specific implementation.

**The PEEL test:** if removing a component does not weaken authority, convergence, evidence or continuity, it probably does not belong in the core.

## What is in this repository

| Path | Purpose |
| --- | --- |
| `PEEL_Framework_XX001_specification.docx` | The full specification (XX001, v1.3), with the project-assistant appendix |
| `PEEL_kicker/IMPLEMENTATION_PROMPT.md` | Entry point: interview, implementation and validation instructions |
| `PEEL_kicker/PRODUCER.md` | Role template: operations, gates, verification, budgets, escalation |
| `PEEL_kicker/EXPERT.md` | Role template: Method, Policy, hypotheses, the single current Directive |
| `PEEL_kicker/ENGINEER.md` | Role template: constrained execution, tests, evidence, handover |
| `PEEL_kicker/PEEL_SPECIFICATION.md` | Markdown version of the specification |

## Quick start — the PEEL kicker

The `PEEL_kicker` folder bootstraps a PEEL-based application with a coding agent.

1. Open Codex, Claude Code, Antigravity, OpenCode or a similar orchestration tool.
2. Load the five files from `PEEL_kicker/` into a new project.
3. Send this startup message:

> Read every Markdown file in the PEEL kicker, starting with IMPLEMENTATION_PROMPT.md.
> Interview me to define my application and fill every project placeholder across the four templates.
> Use PEEL_SPECIFICATION.md as the framework reference. Show me the completed mandate and implementation plan.
> After I approve their scope, build and test a working PEEL application within that scope.

4. Answer the interview questions. The tool fills the templates; no manual editing is needed.
5. Review the proposed mandate, permissions, budgets and acceptance checks. Approve their scope.
6. Let the tool build and test the application. Stay available for reserved Authority decisions.

The four templates are implementation inputs, not governance layers.
The generated governance stack is always Constitution > Method > Policy > Directive.

## Status

- Index: XX001
- Status: Drafting (v1.3, based on the operational prototype of 19 September 2026)
- Author: Cédric Gégout
