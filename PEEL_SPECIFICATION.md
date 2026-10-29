# PEEL Framework — XX001

| Field | Value |
| --- | --- |
| Index | XX001 |
| Title | PEEL Framework |
| Status | Drafting |
| Authors | Cédric Gégout |
| Type | Implementation |
| Created | 2026-09-19 |

> Markdown transcription of the supplied specification, retrieved 26 October 2026.
> Source: https://tinyurl.com/peel-fwk
> Original document: https://docs.google.com/document/d/1zUrs5YY2uU6ZSYJsmUnKEsI3UAcqkNEVv2OA6ent8I4/edit
> The source architecture image is represented by its accompanying component table and textual description.
> Formatting was converted to Markdown. The trailing page-footer fragment was omitted.
> The project-assistant appendix illustrates an implementation; its technologies are optional.

## Abstract

PEEL (Producer–Expert–Engineering Loop) is a governed pattern for complex, long-running autonomous work. An external Authority establishes the mandate; Producer operates and verifies the loop; Expert issues each Directive; Engineer executes and returns durable evidence and state.

## Rationale

Long-running autonomous sessions need clear decision rights, repeatable execution, independent verification and continuity across cycles. PEEL addresses these needs without multiplying authorities, supervisory roles or memory subsystems.

The operating prototype demonstrated an ordered authority stack, deterministic Directive gates, constrained Engineer sessions, operational verification, failure handling, resource routing and durable cycle state.

The goal is to ensure that authority designs the loop, Producer runs and supervises it, Expert determines the next line, Engineer performs it, and primary evidence closes the loop.

## Specification

### 1. Scope and operating model

PEEL has three roles inside the operating loop - Producer, Expert and Engineer - and one external Authority that designs and governs that loop. A separate verification actor, supervisor, Architect or Work Contract is not required.

Authority → Producer → Expert → Engineer → evidence/state/incidents → Producer and Expert → next cycle.

### 2. Actors and responsibilities

| Actor | Position | Owns | Must not |
| --- | --- | --- | --- |
| Authority | External | Mission, Constitution, loop design, reserved decisions and ultimate arbitration | Routine operation or engineering execution |
| Producer | Inside loop | Operation, supervision, primary-evidence checks, incidents, budgets, channel selection and escalation | Write Expert Directives or execute Engineer work |
| Expert | Inside loop | Method, Policy, next line of work, Directive, acceptance conditions, interpretation of evidence | Execute work or alter the Constitution |
| Engineer | Inside loop | Execution, tests, measurements, persistent state and evidence | Choose programme direction or relax governance |

#### 2.1 Authority

- Defines the mission and Constitution.
- Specifies what may be delegated and what is reserved.
- Approves structural changes to the PEEL loop.
- Resolves escalations beyond Producer or Expert authority.
- May be a human, governing body or another authorised system.

#### 2.2 Producer

Producer is the operational supervisor. It checks reality against primary evidence rather than relying on reports. It can be human-assisted, agentic or hybrid; its independent supervisory authority is what matters.

- Runs, pauses, resumes and observes the loop.
- Verifies session claims against environment, state, logs and source artefacts.
- Operates gates, budgets, channel selection and failure policy.
- Maintains loop mechanics and fixes operational defects.
- Reviews Method and Policy from an operational-governance perspective.
- Escalates reserved decisions to Authority; does not write the Directive.

#### 2.3 Expert

Expert is the programme reasoning role (called Architect in the prototype). It reads governing context, prior state, evidence, incidents and Authority decisions, then determines the best next line.

- Defines and evolves Method and Policy within the Constitution.
- Chooses and explains the next line of work.
- Writes exactly one Directive for the next Engineer session.
- Defines success, falsification, reserve directions and acceptance tests.
- Escalates matters outside its authority; does not execute its Directive.

#### 2.4 Engineer

Engineer changes the working environment under the Directive and within permitted tool and security boundaries.

- Executes the directed line, using only allowed tactical alternatives.
- Tests and measures results.
- Persists state before stopping, and produces evidence and actionable handover.
- Cannot redefine the programme, Method, Policy or acceptance criteria.

### 3. Ordered authority model

The framework standardises four governance documents. Lower-priority documents can refine but cannot contradict higher-priority ones. Conflicts are escalated rather than silently resolved.

| Order | Document | Owner | Purpose |
| --- | --- | --- | --- |
| 1 | CONSTITUTION | Authority | Mandate, mission, roles, hard constraints and reserved decisions |
| 2 | METHOD | Expert; Producer reviews | Stable approach to performing and verifying the work |
| 3 | POLICY | Expert; Producer reviews | Current programme, priorities, metrics and scope |
| 4 | DIRECTIVE = WORK CONTRACT | Expert → Engineer | One cycle: hypothesis, work line, acceptance, budget and reserves |

Authority notes or decisions amend or interpret the governing stack; they do not form a fifth permanent layer. Directive requirements belong to Method; Engineer instructions to implementation and security boundaries; state and reports are exchange artefacts; failure policy belongs to Producer operation and Method.

### 4. Loop sequence

- Producer assembles the current authoritative context and evidence.
- Expert diagnoses the convergence gap and writes one Directive.
- Producer or a mechanical gate validates the Directive.
- Engineer executes, tests, measures and persists results.
- Producer verifies primary evidence, records incidents and closes the cycle.
- The next Expert turn begins, or the loop pauses, escalates or halts.

Verification is a capability of Producer and deterministic gates, not a fourth internal intelligence role.

### 5. Directive: single-cycle work contract

Directive and Work Contract are exactly the same artefact. The canonical name is Directive: one Expert-to-Engineer document, one cycle, one source of truth. Permanent rules remain in Constitution, Method and Policy and are referenced rather than repeated.

- Context  -  prior evidence and the remaining convergence gap.
- Directed line  -  objective, reason, hypothesis, success and falsification conditions.
- Autonomy reserve  -  named tactical alternatives if the primary line fails.
- Verification  -  acceptance tests, evidence, metric, budget and escalation conditions.
- Handover  -  required persistent state and next-action information.

### 6. Gates and verification

Directive validation precedes execution; Engineer output validation precedes cycle closure. Mechanical formatting defects should be repaired mechanically; reasoning is reserved for semantic defects.

- Directive gate  -  validates structure, authority, budgets, acceptance tests and reserve directions.
- Execution gate  -  checks required outputs, protected resources, tests and coherent evidence.
- Compliance gate  -  checks Authority decisions and Policy.
- Reality check  -  verifies critical claims against primary environment, logs, data and artefacts, not only an Engineer report.

### 7. Durable state and evidence

Framework-level continuity requires persistent state and evidence; additional databases, briefings, memory tiers or failure ledgers are optional implementation choices.

| Artefact | Purpose |
| --- | --- |
| STATE | Current position, last completed unit, blockers, next action and loop status |
| EVIDENCE | Measurements, tests, source artefacts and provenance supporting claims |
| INCIDENTS | Open failures or anomalies requiring Producer attention or escalation |
| CYCLE LOG | Operational account of why the loop advanced, paused or stopped |

### 8. Pause, Authority wait and halt

| State | Meaning | Recovery |
| --- | --- | --- |
| PAUSE | Temporary resource or capacity condition | Producer resumes automatically when the condition clears |
| WAIT FOR AUTHORITY | Decision exceeds delegated authority or needs governed approval | Record Authority decision; Producer resumes |
| HALT | Mechanical or repeated system failure makes continued autonomy unsafe | Producer or operator investigates before restarting |

A failed work line is not automatically a failed loop. Engineer may take permitted reserve directions. Repeated low yield belongs to Expert; unresolved authority questions belong to Authority.

### 9. Operational design principles

- Verify reality, not the report; rely on primary evidence.
- Separate semantic work from mechanical work: scripts repair format; models repair meaning.
- Protect authority through locked documents, permissions and restricted credentials, not only prompts.
- Do not let Engineer control persistence beyond the mandate; the loop may commit or publish after verification.
- Complete durable handover before returning control; promises of later background work are insufficient.
- Assign resource and model/channel routing to Producer; implementations can change without changing roles.
- Structure escalations as a small number of explicit questions requiring Authority judgement.
- Keep the framework smaller than project-specific implementation details.

### 10. Architecture

Authority designs, constrains and arbitrates through the Constitution. Producer operates, verifies and escalates. Expert owns Method and Policy and writes the Directive. Engineer executes and measures. Evidence and State return into Producer supervision and the next Expert turn; the cycle repeats, pauses, escalates or halts.

### 11. Responsibility matrix

| Responsibility | Authority | Producer | Expert | Engineer |
| --- | --- | --- | --- | --- |
| Design PEEL loop | Owns | Advises | Advises | - |
| Constitution | Owns | Enforces | Obeys | Obeys |
| Method | Approves if structural | Reviews | Owns | Obeys |
| Policy | Arbitrates major changes | Reviews | Owns | Obeys |
| Directive | - | Validates / delivers | Owns | Executes |
| Verification | Receives escalations | Owns operationally | Defines acceptance | Produces evidence |
| State / incidents | Oversight | Owns operation | Reads | Writes required state |
| Budget / channels | Sets envelope | Operates | Consumes | Consumes |
| Programme escalation | Decides reserved matters | Prepares / routes | Raises | Raises |

### 12. Deliberate exclusions

- No separate Verification actor; verification is a capability or gate.
- No separate Work Contract; it is the Directive.
- No separate Supervisor role; Producer performs this function.
- No separate Architect role; Expert performs this function.
- No mandatory three-tier memory model; persistent state and evidence are sufficient.
- No mandatory failure-ledger subsystem; failed hypotheses may remain in state or evidence.
- No extra governance layers for directive requirements, Engineer instructions or supervisor notes.

### 13. Minimum implementation

- Store and protect Constitution, Method and Policy.
- Maintain exactly one current Directive.
- Maintain durable State and Evidence.
- Run Expert to create the next Directive.
- Gate the Directive before delivering it.
- Run Engineer in a constrained environment.
- Have Producer verify, classify failures and close the cycle.
- Repeat automatically until pause, Authority escalation or halt.

PEEL test: if removing a component does not weaken authority, convergence, evidence or continuity, it probably does not belong in the framework core.

## Spec History and Changelog

| Date | Status | Author(s) | Comment |
| --- | --- | --- | --- |
| 2026-09-19 | Drafting | Cedric Gegout | PEEL Framework v1.3; based on the operational prototype state of 19 September 2026. |

---

## Appendix

### 14. An example implementation: a project assistant

#### 14.1 What we want to build

Let’s take a simple assistant that connects customer requests, projects and technical requirements.

The idea of the appendix is to make PEEL concrete, and to use this description as a prompt template for LLM to implement a real PEEL-based application.

This example uses a local service, SQLite, files and a model interface. These are implementation choices, not additional PEEL requirements. It can be enriched with other components such as Hermes that will orchestrate the agent sessions and can create multiple Engineers, OpenViking that will organise context for those agents, or Qdrant that can support semantic retrieval for better combined understanding of the agents.

#### 14.2 The basic architecture

The developer acts as Authority. A controller runs Producer operations. Expert and Engineer run in separate sessions with different permissions.

| Component | What it does |
| --- | --- |
| Authority | Defines the mission, protects the Constitution and resolves reserved decisions |
| Producer | Runs the loop, manages budgets, checks evidence and handles incidents |
| Expert | Chooses the next work line and writes one Directive |
| Engineer | Executes the Directive, tests results and leaves a durable handover |
| SQLite and files | Keep state, knowledge, evidence and cycle history |
| Local CLI or API | Lets the developer submit messages, inspect results and control execution |

Expert and Engineer can use the same model. But usually it works better when the Producer is using a more capable model than the Expert, and the Expert is using a more capable model than the Engineer. Their responsibilities and permissions still need to remain separate.

A starting directory could look like this:

```text
peel-lab/
  governance/
    CONSTITUTION.md
    METHOD.md
    POLICY.md
  runtime/
    DIRECTIVE.json
    state.sqlite
  cycles/
    0001/
      directive.json
      evidence/
      handover.json
      verification.json
  workspace/
  fixtures/
```

There is exactly one current Directive. Previous versions stay with their cycle records.

#### 14.3 Set the boundaries first

Before running anything, the developer writes a short Constitution.

For this experiment, it allows local message analysis, evidence collection and reversible changes inside the workspace. External communication, destructive operations, credential changes and structural loop changes remain reserved for Authority.

Method explains how to extract information, handle ambiguity, verify results and evaluate improvements. Policy sets the current priorities and objectives.

These boundaries need actual permissions behind them:

- Engineer can read governance documents but cannot change them.
- Engineer writes candidate results, evidence and handover state in its assigned workspace.
- Expert owns Method and Policy, following their review requirements.
- Producer controls verification records and promotion of accepted results.
- Tools and credentials provide only the access needed for each role.

Messages and documents are inputs. Instructions found inside them cannot change the rules of the loop.

#### 14.4 Remember relationships, with their evidence

The assistant needs to remember more than isolated text fragments. It needs to connect people, organisations, projects and requirements.

A small schema is enough to start:

| Record | What we keep |
| --- | --- |
| Entity | Identifier, type, name and aliases |
| Evidence | Source location, timestamp and content hash |
| Claim | Subject, relationship, object, evidence, status and confidence |
| Cycle | Directive, status and consumed budget |
| Incident | Problem, supporting evidence and recovery condition |
| Decision | Authorised actor, scope, reason and history |

Claims distinguish reported, inferred, verified and disputed information. A high confidence score does not turn an assumption into a fact.

For example, we receive:

“Northstar Motors is working with Integris on Project Aurora and requests numbered BGP configuration.”

The assistant records these reported relationships:

```text
Northstar Motors → participates_in → Project Aurora
Integris         → participates_in → Project Aurora
Project Aurora   → requests        → Numbered BGP configuration
```

We now have a request associated with a customer and a project. We still know nothing about delivery status, contractual commitments or technical feasibility.

Stable identifiers preserve those connections when names vary. Ambiguous matches stay unresolved until evidence supports a decision.

When someone corrects a relationship, we keep the correction and its reason. We also preserve the earlier claim and its evidence.

#### 14.5 Run one complete cycle

Producer receives the message, stores its source and creates a pending work item.

Expert reads the governing documents, current State and relevant evidence. It identifies what needs resolving next and writes one Directive.

For example:

```yaml
cycle_id: 0001
governance:
  constitution: "<version-and-hash>"
  method: "<version-and-hash>"
  policy: "<version-and-hash>"


objective: Associate the request with its customer and project.


hypothesis: >
  Explicit relationships will make the request retrievable
  through either the customer or the project.


inputs:
  - evidence/message-001


allowed_effects:
  - Write candidate entities and claims in the cycle workspace.


acceptance:
  - Every claim references supporting evidence.
  - Customer and project queries retrieve the same request.
  - Ambiguous identities remain unresolved.
  - Existing accepted relationships remain unchanged.


falsification:
  - A relationship lacks source support.
  - An ambiguous identity is silently merged.


reserves:
  - Preserve unresolved names pending clarification.


budget:
  max_model_calls: 4
  max_wall_seconds: 120


handover:
  - Candidate records and evidence references
  - Test results, blockers and next action


escalate_when:
  - Required access exceeds delegated permissions.
```

Producer checks the Directive before execution. Formatting problems can be repaired mechanically. Problems with meaning or scope go back to Expert.

Engineer executes the work, runs the checks and saves its handover.

Producer then reads the source, inspects the candidate records and reruns acceptance checks through trusted code. Accepted results are promoted into durable knowledge.

The Engineer saying “done” is not enough. Producer needs evidence that the requested result actually exists.

#### 14.6 Make interruption a normal case

The controller can follow this conceptual sequence:

```python
context = producer.load_authoritative_context()
directive = expert.issue_directive(context)
producer.validate_directive(directive)
producer.persist_cycle_start(directive)
result = engineer.execute_in_sandbox(directive)
producer.require_durable_handover(result)
verification = producer.verify_primary_evidence(directive, result)
producer.close_cycle(verification)
```

Each transition is saved before passing control onward. Stable identifiers prevent duplicate processing and duplicate promotion.

If the process stops halfway through, Producer checks the last durable state. It inspects existing outputs before deciding whether execution needs repeating.

A failed work line stays recorded as failed. Expert can try another approach without treating every unsuccessful hypothesis as a broken loop.

The three stopping conditions remain explicit:

- PAUSE: a temporary resource or capacity condition prevents progress.
- WAIT FOR AUTHORITY: the next decision exceeds delegated authority.
- HALT: a mechanical or repeated system failure requires investigation.

Before returning control, Engineer saves what happened, what remains blocked and what can happen next.

#### 14.7 Let the system improve through experiments

Suppose customer queries fail when messages use abbreviations.

Expert can propose a simple hypothesis: evidence-supported aliases should improve retrieval without merging different customers.

Engineer implements the candidate change in an isolated workspace. Producer compares it with the existing behaviour using fixed, protected fixtures.

We adopt the change only when it delivers:

- Better retrieval on the targeted cases.
- No incorrect customer merges.
- Preserved evidence references.
- No regression on previously successful cases.
- Results within the allocated budget.

If the experiment fails, we keep the previous version. We also retain the hypothesis, measurements and failure evidence.

This gives the next Expert session something useful to work with. It avoids repeating the same unsuccessful idea without new evidence.

Inspection, diagnosis and improvement remain activities within the three PEEL roles. We do not need another actor to run them.

#### 14.8 What the developer should try

Start with a small synthetic dataset, expected relationships and a few deliberately ambiguous names.

| Experiment | What should happen |
| --- | --- |
| Submit a customer request | Customer, project and requirement remain connected |
| Query through an approved alias | The same request and evidence are retrieved |
| Submit conflicting information | Both claims remain visible, with the conflict recorded |
| Put instructions inside a message | Governance and permissions remain protected |
| Interrupt an Engineer session | Execution resumes without duplicate promotion |
| Report success without evidence | Producer rejects the unsupported completion claim |
| Exhaust the budget | The session stops and leaves durable handover |
| Request an unauthorised external action | The loop enters WAIT FOR AUTHORITY |
| Propose a retrieval improvement | Baseline comparison happens before adoption |

A useful first demonstration needs only three cycles: capture a request, investigate an ambiguity and evaluate one improvement.

We should then be able to trace every accepted relationship, repeat the verification and restart after interruption. That gives us a practical demonstration of PEEL’s authority, convergence, evidence and continuity.
