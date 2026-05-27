## Ask Internal Policy Question

**Purpose:** Answers employee questions using only the approved Demo Company Internal Knowledge Base.

### Key Features
- Category selection for HR, IT, Admin, Security, Payroll, Benefits and Onboarding
- Captures the user’s specific policy question
- Searches and summarises only the approved knowledge base
- Uses high moderation and disables general model knowledge
- Asks whether the response answered the question
- Routes unhelpful or unsupported answers to fallback options

### Conversation Flow
1. User selects a policy category
2. User enters a specific question
3. Assistant checks the approved knowledge base
4. Assistant returns a concise answer
5. User confirms whether the answer was helpful
6. Assistant offers another policy question or ends the conversation

### Validation and Guardrails
- If information is not found, the assistant states that it could not find the answer in the approved knowledge base
- The assistant offers support request or human callback as next steps instead of guessing

### Sanitised Logic Snapshot
```yaml
kind: AdaptiveDialog
modelDescription: Answers employee questions about HR Policies, IT Policies & Support, Admin & Facilities, Security & Compliance, Payroll, Benefits, and Onboarding using only the approved Demo Company Internal Knowledge Base.
  kind: OnRecognizedIntent
    - kind: Question
      variable: init:Topic.var_ques_choice
      prompt: "{Global.var_name}, what would you like to know about?"
      entity:
        kind: EmbeddedEntity
          kind: ClosedListEntity
    - kind: Question
      variable: init:Topic.var_userQuestion
      prompt: "{Global.var_name}, what would you like to know about {Topic.var_ques_choice}?"
      entity: StringPrebuiltEntity
    - kind: SendActivity
      activity: Let me check the approved internal knowledge base.
    - kind: SearchAndSummarizeContent
      variable: Topic.Var_policy_ans
      moderationLevel: High
          kind: SearchSpecificFiles
        kind: SearchSpecificKnowledgeSources
      applyModelKnowledgeSetting: false
      responseCaptureType: TextOnly
    - kind: ConditionGroup
            - kind: SendActivity
              activity: "{Global.var_name}, I could not find this information in the approved internal knowledge base."
            - kind: GotoAction
    - kind: Question
      variable: init:Topic.ques_ans
      prompt: "{Global.var_name}, did this answer your question?"
      entity:
```