## Escalate to Human Agent

**Purpose:** Handles priority-based escalation and urgent callback requests.

### Key Features
- Captures urgency level
- Confirms whether high-priority issues require callback escalation
- Collects phone number for urgent callback
- Invokes a Power Automate flow to notify support
- Routes non-urgent cases to ticket creation or policy retry

### Conversation Flow
1. User selects urgency level
2. For high priority, assistant confirms whether callback is required
3. Assistant collects callback number
4. Assistant sends details to the support team through automation
5. Assistant confirms escalation and ends or redirects

### Validation and Guardrails
- Escalation is only performed after the user confirms urgency
- Phone number is collected using a phone number entity

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: This topic manages the full escalation workflow by assessing priority, confirming urgency, and coordinating internal support actions. It handles urgent cases through callback requests and manages other queries through ticket creation or by offering the user the option to try the assistant again.
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Topic.var_choice_priority
      prompt: How urgent is your query, {Global.var_name}?
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: ConditionGroup
            - kind: Question
              variable: init:Topic.var_choice_further
              prompt: Since you selected High priority {Global.var_name}, I can email the support team to request an urgent callback. Is this issue urgent enough to escalate now?
              entity:
                kind: EmbeddedEntity
                  kind: ClosedListEntity
            - kind: ConditionGroup
                    - kind: SendActivity
                      activity: Got it, {Global.var_name}. I’ll handle that for you.
                    - kind: BeginDialog
                    - kind: EndDialog
                    - kind: SendActivity
                      activity: Got it, {Global.var_name}. Let me try again.
                    - kind: BeginDialog
                    - kind: EndDialog
                    - kind: SendActivity
                      activity: Got it, {Global.var_name}. I’ll handle that for you.
                    - kind: Question
                      variable: init:Global.var_phone
                      prompt: Please share the best phone number for our team to call you back.
```