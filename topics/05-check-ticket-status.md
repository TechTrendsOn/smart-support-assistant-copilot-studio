## Check Ticket Status

**Purpose:** Retrieves the status of an existing support request by ticket ID or by employee details.

### Key Features
- Supports lookup by Ticket ID
- Supports lookup by company email and issue type
- Validates ticket ID format
- Validates official company email domain
- Retrieves matching records from the ticket log
- Guides the user when a ticket is not found

### Conversation Flow
1. User chooses whether they know the Ticket ID
2. Assistant validates the Ticket ID format
3. Assistant retrieves ticket rows from storage
4. If found, assistant displays ticket status
5. If not found, assistant offers retry, search by email and issue type, raise new request or return to support options

### Validation and Guardrails
- Ticket ID must follow the TKT-12345 format
- Email must use the official demo company domain
- Invalid entries are redirected to retry or alternative lookup

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic retrieves the status of a previously submitted support request.
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Topic.var_check_ticketID
      prompt: "{Global.var_name}, please choose from the following:"
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
            - kind: GotoAction
            - kind: SendActivity
              activity: No worries, {Global.var_name}, I'll help you find your Ticket ID and status using your provided email and issue type.
            - kind: GotoAction
    - kind: Question
      variable: init:Topic.var_ticket_id
      prompt: "{Global.var_name}, please provide your valid ticket ID?"
      entity: StringPrebuiltEntity
    - kind: ConditionGroup
            - kind: SendActivity
              activity: This ticket ID doesn’t match the expected format. The expected format is \*\*TKT‑12345\*\* (TKT + 5 digits).
            - kind: Question
              variable: init:Topic.var_retry_choice
              prompt: Do you want to try again or need help?
              entity:
                kind: EmbeddedEntity
                  kind: ClosedListEntity
            - kind: ConditionGroup
                    - kind: GotoAction
                    - kind: GotoAction
```