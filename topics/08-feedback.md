## Feedback

**Purpose:** Collects user rating and optional feedback after the conversation.

### Key Features
- Five-level rating scale
- Optional free-text comments
- Thanks the user for feedback

### Conversation Flow
1. Assistant asks for rating
2. User selects rating
3. Assistant asks for optional comments
4. Assistant confirms feedback received

### Validation and Guardrails
- Feedback is optional and uses controlled rating options

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: |-
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Global.var_rating
      prompt: |-
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: Question
      variable: Global.var_feedback
      prompt: If you'd like, you can also share any comments or suggestions.
      entity:
        kind: StringPrebuiltEntity
    - kind: SendActivity
      activity: Thanks for your feedback and rating {Global.var_name}. We appreciate your time!
```