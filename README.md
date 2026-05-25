Teacher Assistant Full – n8n Workflow
Overview

This workflow is an AI-powered teacher assistant system built in n8n. It allows educators to generate structured lesson plans, receive AI assistance via Messenger, automatically populate Google Docs templates, convert outputs to downloadable files, and send them back to users through Facebook Messenger.

It combines:

OpenAI (GPT-4o-mini) for AI generation
Google Docs for document templating
Google Drive for file handling
Google Sheets for optional data retrieval
Facebook Messenger API for delivery
n8n form + webhook triggers for inputs
Workflow Structure
1. Entry Points
lesson_topic (Form Trigger)
Accepts lesson input from a form
Starts lesson plan generation workflow
Webhook (Facebook Messenger)
Receives incoming messages
Handles verification (hub.challenge, verify token)
Routes user messages to AI assistant workflow
2. Lesson Plan Generation Flow
AI Generation (AI Agent)
Uses GPT-4o-mini model
Converts lesson topic into structured JSON
Strict output rules:
Must return valid JSON only
No markdown, no explanation
Structured lesson plan fields:
lessonName
competency
objectives
context
prelesson
flow
resources
integration
assessment
extended
reflections
JSON Parsing
parse_code node
Parses AI output string into JSON array
Splits each lesson object into separate items
3. Google Docs Generation
File Creation
createFile (HTTP Request)
Copies a Google Docs template
Names file using lesson title
Document Update
Update a document (Google Docs node)
Replaces placeholders:
{{lessonName}}
{{competency}}
{{objectives}}
{{context}}
{{prelesson}}
{{flow}}
{{resources}}
{{integration}}
{{assesment}}
{{extended}}
{{reflections}}
4. File Processing
Download File
Downloads updated Google Docs file from Drive
Code Processing
Code in JavaScript1
Sets:
fileName = lessonName.docx
mimeType = Word document format
5. File Delivery (Messenger)
attachment (HTTP Request to Facebook Graph API)
Sends generated .docx file to user via Messenger
Uses sender PSID and entry ID
Delete a file (Google Drive)
Cleans up temporary file after sending
6. AI Chat Assistant Flow (Messenger)
Input Filtering
Filter node
Ensures message text is not empty
AI Agent1
Uses GPT-4o-mini model
Acts as teacher assistant chatbot
Capabilities:
Lesson planning support
Assessment creation
Classroom communication
Curriculum development
Professional development
System behavior:
Always concise (max 2000 characters)
Professional tone
Teacher-focused assistance
Includes lesson plan link when relevant
Memory + Tools
Simple Memory
Stores conversation context per sender ID
Google Sheets Tool
Retrieves stored educational data if needed
Response Handling
If output contains lesson plan link:
link_lessonplan node sends form link to user
Otherwise:
conversation_reply sends AI response back to Messenger
7. Lesson Plan Reminder System
waiting_reply
Sends "Generating..." message to user while processing
If1 condition
Checks if response includes form link
Routes accordingly:
link_lessonplan (send form link)
conversation_reply (send AI answer)
External Integrations
OpenAI API
GPT-4o-mini for text generation
Google Docs API
Template-based document generation
Google Drive API
File copying, download, deletion
Google Sheets API
Optional structured data retrieval
Facebook Messenger Graph API
Sends messages and file attachments
Key Features
Fully automated lesson plan generator
Messenger-based teacher assistant chatbot
Structured JSON-driven document creation
Auto-generated Google Docs → Word export
Temporary file cleanup for efficiency
Conversation memory for contextual replies
Dual workflow (form + chat assistant)
Workflow Behavior Summary
Teacher submits lesson topic OR sends Messenger message
AI generates structured lesson content
System builds formatted Google Docs file
File is converted and sent as .docx
Temporary files are deleted automatically
Chatbot continues assisting teacher in real time
Notes
Requires valid Google OAuth credentials
Requires Facebook Messenger App + Page token
OpenAI API key must support GPT-4o-mini
Google Docs template must contain placeholders exactly matching workflow fields
System depends heavily on strict JSON output from AI
