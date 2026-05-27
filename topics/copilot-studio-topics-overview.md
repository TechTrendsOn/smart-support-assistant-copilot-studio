# Smart Support Assistant: Copilot Studio Topics

This document provides a recruiter-friendly overview of the Microsoft Copilot Studio topics used in the Smart Support Assistant project. It summarises the purpose, flow, validation logic and expected output for each topic. Raw internal identifiers, environment references, flow IDs and file references have been intentionally excluded for public GitHub use.

## Topic Overview

| Topic | Purpose |
|---|---|
| Ask Internal Policy Question | Answers employee questions using only the approved Demo Company Internal Knowledge Base. |
| Check Ticket Status | Retrieves the status of an existing support request by ticket ID or by employee details. |
| End Conversation | Confirms whether the user wants to end or restart the conversation. |
| Escalate to Human Agent | Handles priority-based escalation and urgent callback requests. |
| Fallback | Handles unclear or unsupported requests and redirects users to available support paths. |
| Feedback | Collects user rating and optional feedback after the conversation. |
| Greeting | Welcomes the user, captures an optional preferred name and routes to support options. |
| Raise Support Request | Collects employee support details and creates a structured internal support ticket. |
| Start Over | Restarts the conversation and returns the user to the support options menu. |
| Support Options | Main routing menu for the assistant. |

 The raw export may contain internal implementation references such as generated action IDs, flow IDs, file references, environment prefixes and connection-related identifiers. For public GitHub use, this Markdown file is safer than uploading the raw Copilot Studio export.
