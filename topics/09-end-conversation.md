## End Conversation

**Purpose:** Confirms whether the user wants to end or restart the conversation.

### Key Features
- Offers end conversation or start over
- Routes completed conversations to feedback
- Allows restart through support options

### Conversation Flow
1. Assistant asks whether the user wants to end
2. User selects end conversation or start over
3. Assistant collects feedback or restarts the support menu

### Validation and Guardrails
- Provides controlled ending rather than abruptly stopping the conversation

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
  kind: OnRecognizedIntent
    triggerQueries:
      - Bye
      - Bye for now
      - Bye now
      - Good bye
      - No thank you. Goodbye.
      - See you later
    - kind: Question
      variable: Topic.EndConversationChoice
      prompt: Would you like to end our conversation?
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
            - kind: BeginDialog
            - kind: CancelAllDialogs
            - kind: BeginDialog
    - kind: EndDialog
```