# AI-Powered Smart Support Assistant using Microsoft Copilot Studio

## Overview

Smart Support Assistant is a low-code AI-powered prototype designed to help employees with internal workplace support needs using Microsoft Copilot Studio, Power Automate, Excel Online, and Outlook V2 email workflows.

The prototype demonstrates how employees can access knowledge-grounded policy guidance, create support tickets, check ticket status, and escalate urgent issues to human support teams through callback notification workflows.

The assistant relies only on approved internal knowledge sources and follows safety, privacy, compliance, validation, and fallback guardrails.

---

## Project Demo

[View Working Demo PDF](demo/AI-Powered Smart Support Assistant for Internal Organisational Support Working Demo.pdf)

---

## Project Objectives

The project was designed to demonstrate:

- Conversational internal workplace support workflows
- Knowledge-grounded policy assistance
- Structured ticket generation workflows
- Ticket status retrieval workflows
- Human-agent escalation handling
- Multi-turn conversational experiences
- Validation and fallback handling
- Internal workplace support automation using Microsoft Copilot Studio and Power Automate

---

## Workplace Support Areas

The assistant currently supports employee queries related to:

- HR Policies
- IT Policies & Support
- Payroll Support
- Benefits
- Admin & Facilities
- Security & Compliance
- Onboarding

---

## Core Functionality

### Internal Policy Assistance

The assistant answers internal workplace policy questions using an uploaded Demo Company Internal Knowledge Base.

To ensure grounded and compliant responses:

- External web search is disabled
- General knowledge responses are restricted
- Responses are generated only from approved internal documents
- Unsupported queries trigger fallback guidance and alternative support options

---

### Raise Support Request Workflow

The assistant helps employees raise structured support requests by collecting:

- Employee name
- Official company email
- Issue type
- Issue description

The workflow includes:

- Official company email validation
- Structured ticket ID generation
- Automatic ticket status assignment
- Excel Online ticket storage for later retrieval

---

### Ticket Status Lookup Workflow

Employees can check the status of previously submitted support requests using:

- Ticket ID
- Official employee email and Issue type

The assistant validates ticket information before retrieving matching ticket records from Excel Online.

Validation handling includes:

- Incorrect ticket ID format detection
- No-match handling
- Retry guidance for employees

---

### Human Escalation Workflow

Urgent issues can be escalated to human support teams.

The escalation workflow includes:

- Priority selection
- Callback request handling
- Callback detail collection
- Power Automate integration
- Outlook V2 email notification workflow

The support team receives escalation notification emails and the employee receives confirmation that the callback request was submitted successfully.

---

### Multi-Turn Conversational Support

The assistant supports:

- Context-aware conversations
- Follow-up handling
- Clarification prompts
- Guided next steps
- Start-over workflows
- End-conversation workflows
- Feedback collection after support interactions

---

### Personalised Greeting Workflow

The assistant personalises conversations by asking employees for an optional preferred name at the beginning of the interaction.

If the user chooses not to share a preferred name, the assistant assigns a neutral conversational reference such as:

`Team member`

---

## Safety, Privacy, and Compliance Guardrails

The assistant follows strict conversational and compliance rules, including:

- Using only approved internal knowledge sources
- Never guessing policy details
- Clearly informing users when information is unavailable
- Avoiding legal, medical, or financial advice
- Redirecting unsupported requests to support workflows
- Protecting employee privacy
- Applying validation and fallback handling where required

---

## Key Features

- AI-powered workplace support assistant
- Knowledge-grounded internal policy responses
- Multi-turn conversational workflows
- Structured support ticket generation
- Ticket status lookup workflows
- Human-agent escalation through Outlook V2 callback email notification workflows
- Excel Online integration
- Validation and fallback handling
- Feedback and conversation closure workflows
- Personalised greeting experience
- Conversation-based evaluation testing

---

## Demonstration Workflows Included

The project demonstrations cover:

1. Internal policy question workflow
2. Knowledge-base answer retrieval
3. Fallback handling for unsupported questions
4. Support ticket generation
5. Email validation handling
6. Ticket status lookup
7. Ticket validation workflows
8. Human escalation and callback workflows
9. Outlook V2 email notifications
10. Conversation feedback and closure workflows

The repository also includes topic-level Copilot Studio workflow documentation, evaluation summaries, sample ticket records, architecture diagrams, and demonstration files.

---

## Evaluation Results

The Smart Support Assistant prototype was evaluated using Microsoft Copilot Studio conversation-based evaluation testing.

### Evaluation Coverage

| Test Case | Result |
|---|---|
| Ask Internal Policy Question | 100% |
| Raise Support Request | 100% |
| Find Ticket ID and Check Status | 100% |
| Incorrect Ticket ID Validation | 100% |
| Urgent Callback Escalation via Email | 100% |

All evaluated workflows achieved a 100% general quality score during prototype testing.

Refer to the included project demonstration presentation and PDF documentation for workflow screenshots, architecture diagrams, and evaluation evidence.

---

## Technologies Used

- Microsoft Copilot Studio
- Power Automate
- Excel Online
- Outlook V2 Email Workflows
- Conversational AI
- Low-Code Automation
- Knowledge-Grounded AI Assistance

---

## Repository Structure

```text
assets/
copilot-studio/
evaluation/
knowledge-base/
sample-data/
demo/
```

---

## Important Note

This repository contains a recruiter-friendly and sanitised demonstration version of the project.

Raw implementation references such as:

- Environment identifiers
- Flow IDs
- Connection references
- Generated action identifiers
- Internal configuration details

have been intentionally excluded for public GitHub sharing.

All uploaded ticket records, screenshots, email addresses, and support data are demonstration-only sample data.

---

## Author

Ruchika Arora

GitHub: TechTrendsOn
