## Fallback

**Purpose:** Handles unclear or unsupported requests and redirects users to available support paths.

### Key Features
- Offers support request creation
- Offers internal policy question flow
- Offers human escalation
- Prevents dead-end conversations

### Conversation Flow
1. Assistant explains available options
2. User selects a next step
3. Assistant routes to the selected topic

### Validation and Guardrails
- Unsupported queries are not answered by guessing

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic handles unclear or unsupported user messages and redirects employees to available support options, including internal policy questions, support ticket creation, ticket status checking, or human escalation.
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Topic.var_fallback_choice
      prompt: "**{Global.var_name},** I can help you raise a support request, request a human-agent callback if the matter is urgent, or ask another policy question. What would you like to do next?"
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
            - kind: BeginDialog
            - kind: BeginDialog
            - kind: BeginDialog
    - kind: EndDialog
```