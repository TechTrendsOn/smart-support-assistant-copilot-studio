## Greeting

**Purpose:** Welcomes the user, captures an optional preferred name and routes to support options.

### Key Features
- Captures preferred name
- Allows user to continue without sharing a name
- Defaults to Team member if no name is provided
- Routes to support options

### Conversation Flow
1. Assistant asks what to call the user
2. User provides name or chooses to continue
3. Assistant stores display name
4. Assistant opens support options

### Validation and Guardrails
- If the user types Continue or leaves the name blank, a neutral fallback name is used

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic welcomes the user, captures their preferred name (optional), and routes them to the support options menu.
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Global.var_name
      prompt: I am here to help. What should I call you during this conversation? Please provide your first name, or type Continue if you prefer not to share it.
      entity: PersonNamePrebuiltEntity
    - kind: SetVariable
      variable: Global.var_name
    - kind: SendActivity
      activity: Thanks, I will refer to you as {Global.var_name} during the conversation.
    - kind: BeginDialog
    - kind: EndDialog
```