---
name: clutchpower-jira-ticket
description: Create Jira tickets following the ClutchPower team's standard format. Use this skill whenever the user asks to create, write, draft, or format a Jira ticket, issue, or task — even if they just describe a piece of work and say "make a ticket for this" or "write this up as a Jira issue". Output is text ready to paste into Jira, with a title and structured description.
---

# Jira Ticket Skill

## Output Format

Produce two clearly separated parts:

### 1. Title
A concise, imperative summary of the work (e.g. "Migrate Matomo authentication from Keycloak to SAML Entra ID").

### 2. Label
Infer the correct Team Coordination label from the ticket content:
- `backend_platform` — backend services, APIs, infrastructure, databases, auth, DevOps
- `frontend` — web UI implementation, components, client-side code
- `ux_ui` — design, wireframes, user research, UX flows
- `content_localization` — copy, translations, content management
- *(no label)* — cross-cutting, process, or anything that doesn't fit the above

If the ticket could plausibly belong to more than one subteam, pick the most dominant concern, or note the ambiguity and ask the user to confirm.

### 3. Description
Structured in this exact order, using these exact section headers:

```
As a [role], I want to [action] to [goal].

Acceptance Criteria
* [Functional/business-level check — verifiable from a user or product perspective]
* ...

Technical Criteria
* [Implementation-level check — verifiable from a developer or ops perspective]
* ...

Technical Notes
* [Freeform context, constraints, gotchas, contacts, environment details]
* [Group into sub-sections with bold headers if there are distinct clusters, e.g. **Access**, **Environment**]
* ...
```

**Section rules:**
- **User story**: Always follows "As a [role], I want to [action] to [goal]." format.
- **Acceptance Criteria**: Required. Functional/business checks. Written as verifiable statements starting with "Verify that...".
- **Technical Criteria**: Include if there are implementation-specific checks (documentation, config, data migration, etc.). Omit the section entirely if not applicable.
- **Technical Notes**: Include if there is useful context for the engineer picking up the ticket. Omit if there's nothing to add. Group related notes under a bold sub-header if there are 4+ notes or distinct clusters (e.g. `**Access**`, `**Environment**`, `**Contacts**`).

---

## Workflow

1. **Gather information.** Before drafting, review what the user has provided and identify any gaps that would improve the ticket. Ask all clarifying questions in a single batch — never one at a time. Consider asking about:
   - Who benefits and why (if the user story role or goal is unclear)
   - What "done" looks like (if acceptance criteria are vague or missing)
   - Technical constraints, dependencies, or environment details (if relevant but unmentioned)
   - Access or permissions requirements
   - Relevant contacts or prior work to be aware of
   - Edge cases or rollback considerations (for riskier changes)

   Only ask questions that would meaningfully improve the ticket — don't ask for the sake of it. If the user has provided enough to write a solid ticket, draft it straight away.

2. **Infer the subteam label** from the content. If ambiguous, state your best guess and ask the user to confirm.

3. **Draft the ticket** with Title, Label, and Description.

4. **Present the output** as rendered markdown in the chat (not in a code block), so the user can read it clearly and copy-paste the relevant parts into Jira's WYSIWYG editor. Use standard markdown: `##` for section headers, `*` bullet lists, `**bold**` for sub-headers in Technical Notes.

---

## Example Output

Render the ticket like this (no wrapping code block — use real markdown so it renders in chat):

---

**Title:** Migrate Matomo authentication from Keycloak to SAML Entra ID

**Label:** `backend_platform`

---

As an engineer, I want to migrate the Matomo authentication method from Keycloak to SAML Entra ID to remove the dependency on the self-hosted Keycloak instance.

## Acceptance Criteria
* Verify that the login for Matomo is handled by Entra ID.
* Verify that the Keycloak client is removed from Keycloak.

## Technical Criteria
* Verify that the SAML setup is documented in Kernel.
* Verify that roles for users are transferred correctly.
* Verify that the necessary groups are created in Entra ID (if needed).

## Technical Notes
* Matomo is hosted in its own cluster.
* Needs admin privilege.
* Kresten might know how the authentication is currently set up.
* The clutchpower account has super user access. If that doesn't work, ask one of the "owners".

---
