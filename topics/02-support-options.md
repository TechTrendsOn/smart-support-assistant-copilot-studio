## Support Options

**Purpose:** Main routing menu for the assistant.

### Key Features
- Routes to policy questions
- Routes to support ticket creation
- Routes to ticket status lookup
- Routes to human escalation

### Conversation Flow
1. User asks for help or support options
2. Assistant displays available support paths
3. User selects a path
4. Assistant begins the selected topic

### Validation and Guardrails
- Uses structured options to reduce ambiguity and keep the conversation guided

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic routes employees to the correct internal support pathway by presenting structured support options and directing them to policy knowledge lookup, support ticket creation, ticket status checking, or priority‑based escalation to a human agent.
  kind: OnRecognizedIntent
    triggerQueries:
      - I need help
      - I need support
      - Show support options
      - What can you help me with
      - I want to ask a policy question
      - I want to raise a support request
      - I need help with HR policy
      - I need IT support
      - I need help with workplace policy
      - I have an internal support issue
      - Support options
      - Help menu
    - kind: Question
      variable: init:Topic.Var_option
      prompt: "{Global.var_name}, please select from the following options:"
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
            - kind: BeginDialog
            - kind: BeginDialog
            - kind: BeginDialog
            - kind: BeginDialog
    - kind: EndDialog
```
