## Raise Support Request

**Purpose:** Collects employee support details and creates a structured internal support ticket.

### Key Features
- Collects full name
- Validates official company email
- Captures issue category
- Captures issue description
- Generates a ticket ID
- Sets ticket status to Open
- Stores ticket details in Excel
- Confirms ticket details to the user

### Conversation Flow
1. Assistant asks for full name
2. Assistant asks for official company email
3. Assistant validates email domain
4. User selects issue type
5. User describes the issue
6. Assistant generates a ticket ID and timestamp
7. Assistant saves the ticket and confirms status

### Validation and Guardrails
- Only official demo company email addresses are accepted
- Ticket ID is generated in TKT format
- New tickets are assigned Open status

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic collects employee details, issue type and issue description to create an internal workplace support ticket.
  kind: OnRecognizedIntent
    - kind: SendActivity
      activity: I can help you {Global.var_name} raise a support request. I’ll just need a few details
    - kind: Question
      variable: init:Topic.var_full_name
      prompt: |
      entity: PersonNamePrebuiltEntity
    - kind: Question
      variable: init:Topic.var_email
      prompt: "{Global.var_name}, what’s the best email to contact you on?"
      entity: EmailPrebuiltEntity
    - kind: ConditionGroup
            - kind: SendActivity
              activity: Please enter your official company email (e.g., name@democompany.com). External or personal emails are not permitted.
            - kind: GotoAction
    - kind: Question
      variable: init:Topic.var_issue_type
      prompt: What type of support request is this?
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
    - kind: SetVariable
      variable: Topic.var_issue_type_text
    - kind: Question
      variable: init:Topic.var_issue
      prompt: "{Global.var_name}, please describe the issue you’re facing."
      entity: StringPrebuiltEntity
```