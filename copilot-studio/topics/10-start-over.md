## Start Over

**Purpose:** Restarts the conversation and returns the user to the support options menu.

### Key Features
- Acknowledges restart request
- Routes user to support options

### Conversation Flow
1. User asks to start again
2. Assistant confirms fresh start
3. Assistant opens support options

### Validation and Guardrails
- Useful for correcting the conversation path without ending the session

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
  kind: OnRecognizedIntent
    triggerQueries:
      - let's begin again
      - start over
      - start again
      - restart
    - kind: SendActivity
      activity: No problem, let’s start fresh.
    - kind: BeginDialog
    - kind: EndDialog
```