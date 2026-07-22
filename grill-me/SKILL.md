---
name: grill-me
description: Interview the user before beginning any new project, feature, workflow, automation, system, campaign, migration, or substantial change. Uncover incomplete requirements, assumptions, contradictions, risks, dependencies, permissions, integrations, constraints, success criteria, and edge cases; then produce an approval-gated plan. Do not use for trivial factual questions or simple edits that do not constitute a project.
---

# Grill Me

Conduct a rigorous discovery interview before any implementation begins. Convert an incomplete project request into an explicit, reviewable plan that the user must approve.

## Non-negotiable rules

1. Ask exactly one substantive question per turn.
2. Never combine several questions into one sentence, list, checklist, or set of alternatives.
3. Do not write code, commands, patches, schemas, configuration files, implementation artifacts, or production copy during the interview.
4. Do not begin implementation, modify files, run write actions, or delegate implementation until the user explicitly approves the final plan.
5. Challenge vague, contradictory, incomplete, or overly broad answers instead of silently filling gaps.
6. Separate confirmed requirements from assumptions. Never treat an assumption as confirmed without explicit user validation.
7. Preserve the user's terminology, constraints, and stated priorities. Do not reframe them into a different objective without confirmation.
8. Follow the user's language. Keep questions concise, direct, and easy to answer.
9. Do not repeat a question that the user has already answered unless a contradiction or material ambiguity remains.
10. Continue until the readiness gate is satisfied. Do not stop merely because a fixed number of questions has been asked.

## Working requirement ledger

Maintain an internal ledger throughout the interview. Classify every material statement as one of:

- `CONFIRMED`: explicitly stated or explicitly accepted by the user.
- `ASSUMPTION`: inferred, proposed, conventional, or not yet validated.
- `PENDING`: a decision or fact still required.
- `CONTRADICTION`: two requirements or answers that cannot both be true as stated.
- `RISK`: an event or condition that could harm delivery, quality, security, adoption, cost, schedule, or compliance.
- `DEPENDENCY`: a person, system, vendor, approval, dataset, credential, environment, or external event required for success.
- `EDGE CASE`: an exceptional, failure, boundary, misuse, recovery, or low-frequency scenario that requires defined behavior.

Do not expose the entire ledger after every answer. Use it to select the next highest-value question. Briefly state the ambiguity or conflict before asking the next question when doing so helps the user answer accurately.

## Interview method

### 1. Establish the project frame

Clarify, one question at a time:

- The problem to solve and why it matters now.
- The desired outcome.
- In-scope and explicitly out-of-scope work.
- The sponsor, decision-maker, operator, administrator, and end users.
- The current process or baseline.

### 2. Examine the operating workflow

Clarify the normal flow from trigger to completion:

- Entry conditions and triggers.
- User actions and system actions.
- Handoffs, approvals, notifications, and escalation paths.
- Outputs and downstream use.
- Cancellation, retries, reversals, recovery, and manual fallback.

When a workflow is described only at a high level, choose the most consequential unclear step and ask about it next.

### 3. Examine data

Clarify:

- Required inputs, sources, owners, formats, volumes, and update frequency.
- Data quality expectations and validation rules.
- Sensitive, personal, confidential, regulated, or proprietary data.
- Storage, retention, deletion, auditability, and export requirements.
- Source of truth and conflict-resolution rules.

Do not assume sample data represents production data.

### 4. Examine access and permissions

Clarify:

- Roles and permission boundaries.
- Authentication and authorization expectations.
- Who may view, create, edit, approve, export, delete, or administer.
- Segregation of duties, audit logs, and approval requirements.
- Credentials, environments, and access that must exist before implementation.

### 5. Examine integrations and dependencies

Clarify:

- External systems, APIs, connectors, vendors, files, devices, or human dependencies.
- Direction and frequency of data exchange.
- Ownership and availability of documentation or credentials.
- Rate limits, quotas, costs, version constraints, and service-level expectations.
- Behavior when an integration is slow, unavailable, duplicated, or inconsistent.

### 6. Examine constraints and quality attributes

Clarify:

- Budget, deadline, team capacity, approved technologies, environments, and procurement limits.
- Security, privacy, legal, compliance, accessibility, localization, and brand constraints.
- Performance, scale, reliability, availability, maintainability, observability, and support expectations.
- Compatibility, migration, rollout, rollback, and business-continuity requirements.

Treat words such as “fast,” “secure,” “simple,” “scalable,” “intuitive,” or “automatic” as ambiguous until they have an observable definition.

### 7. Define success and acceptance

Clarify:

- Business outcome and measurable success indicators.
- Baseline, target, measurement method, owner, and evaluation period.
- Functional acceptance criteria.
- Non-functional acceptance thresholds.
- Required evidence, testing, sign-off, and launch conditions.
- What would make the project unsuccessful even if it is delivered.

### 8. Probe exceptions and adversarial scenarios

Actively test the proposed requirements against:

- Empty, missing, malformed, stale, duplicated, conflicting, or unusually large inputs.
- Unauthorized, accidental, abusive, or concurrent actions.
- Partial completion, timeout, interruption, retry, rollback, and recovery.
- New users, inactive users, deleted users, changed roles, and orphaned records.
- Time zones, languages, currencies, date boundaries, and localization where relevant.
- Integration outages, delayed events, reordered events, and duplicate events.
- Capacity spikes and degraded performance.
- Human error and unavailable approvers.

Ask only about edge cases that are materially relevant to the project.

## How to challenge ambiguity

When an answer is ambiguous:

1. State the ambiguity in one concise sentence.
2. Explain the decision it affects only when necessary.
3. Ask one focused question that resolves the highest-impact uncertainty.

Do not present a large questionnaire. Do not offer more than a small number of mutually exclusive options unless options materially reduce ambiguity. Even when options are offered, ask only one question.

## Prioritization rule

Choose the next question using this order:

1. Contradictions that block the project objective.
2. Decisions with high impact and high irreversibility.
3. Security, privacy, legal, compliance, or financial exposure.
4. Unknown users, workflows, data, permissions, or integrations.
5. Dependencies that could block delivery.
6. Success criteria and acceptance evidence.
7. Lower-impact refinements and edge cases.

## Readiness gate

The interview is sufficiently clear only when all applicable items below are either confirmed or explicitly documented as pending assumptions with an owner and resolution path:

- Objective, desired outcome, scope, and non-goals.
- Stakeholders, users, roles, and decision authority.
- Current state and intended end-to-end workflow.
- Inputs, outputs, data sources, ownership, quality, and lifecycle.
- Permissions, security, privacy, and compliance requirements.
- Integrations, dependencies, and failure behavior.
- Constraints, quality attributes, rollout, rollback, and support model.
- Measurable success criteria and testable acceptance criteria.
- Material risks, contradictions, and edge cases.
- Remaining decisions are visible and do not make the plan misleading.

If a missing answer is not blocking, record it as an assumption or pending decision rather than prolonging the interview unnecessarily. If it is blocking, continue asking one question at a time.

## Final deliverable

When the readiness gate is satisfied, stop interviewing and produce a structured plan with exactly these sections:

1. **Objetivo del proyecto**
2. **Requisitos confirmados**
3. **Suposiciones**
4. **Decisiones pendientes**
5. **Riesgos**
6. **Casos límite**
7. **Arquitectura recomendada**
8. **Plan de implementación**
9. **Criterios de aceptación**

Requirements for the final deliverable:

- Make confirmed requirements and assumptions visibly distinct.
- Trace important architecture and implementation choices back to confirmed requirements or clearly labeled assumptions.
- For each pending decision, state its owner, impact, and the point by which it must be resolved when known.
- For each risk, include likelihood, impact, mitigation, and contingency in concise form.
- Make acceptance criteria observable and testable.
- For non-software projects, interpret “arquitectura” as the recommended operating model, system structure, channel structure, governance model, or solution design appropriate to the domain.
- Do not include implementation code or execute any action.

End with exactly one approval question equivalent to:

**¿Apruebas este plan para comenzar la implementación?**

## After the plan

- If the user explicitly approves the plan, acknowledge approval and allow the implementation workflow to begin.
- If the user requests changes, update the ledger, resume the interview with one question at a time when clarification is needed, and issue a revised plan.
- If approval is conditional, treat the stated conditions as pending decisions and do not implement until they are resolved or explicitly accepted as assumptions.
- Silence, topic changes, partial agreement, or phrases such as “se ve bien” do not count as approval when material decisions remain unresolved.
