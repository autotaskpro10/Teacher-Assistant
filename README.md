Teacher Assistant Full

An AI-powered teacher assistant workflow built with n8n, OpenAI API, Google Docs API, Google Drive API, Google Sheets API, and Meta Messenger Platform.

This workflow allows teachers to generate AI-powered lesson plans directly from Facebook Messenger, automatically create formatted Google Docs, send downloadable .docx files back to Messenger users, and provide educational assistant features.

Features
AI Lesson Plan Generator
Generates structured lesson plans using OpenAI
Produces competency-based outputs
Creates:
Objectives
Lesson flow
Assessment questions
Reflections
Integration activities
Extended tasks
Messenger Chatbot
Facebook Messenger integration
Responds automatically to teacher requests
Sends lesson plan form links
Sends generated lesson plan documents directly in chat
Google Docs Automation
Uses Google Docs as a lesson plan template
Automatically replaces placeholders
Creates downloadable .docx lesson plans
Google Sheets Integration
Reads spreadsheet data as a knowledge source
Supports curriculum/resource lookup
Temporary File Management
Creates Google Drive copies dynamically
Deletes generated files automatically after sending
Workflow Overview
Messenger User
      ↓
Webhook Trigger
      ↓
AI Assistant Chat
      ↓
Lesson Plan Request
      ↓
n8n Form Submission
      ↓
OpenAI Lesson Generator
      ↓
Google Docs Template Copy
      ↓
Placeholder Replacement
      ↓
Export DOCX
      ↓
Send File to Messenger
      ↓
Delete Temporary File
Technologies Used
Service	Purpose
n8n	Workflow automation
OpenAI GPT-4o Mini	AI content generation
Google Docs API	Document editing
Google Drive API	File handling
Google Sheets API	Spreadsheet integration
Meta Messenger Platform	Messenger chatbot
Main Workflow Components
1. Messenger Webhook

Handles incoming Facebook Messenger messages.

Nodes
Webhook
If
Filter
Respond to Webhook
2. Conversational AI Assistant

Acts as a teaching assistant for educators.

Features
Lesson plan requests
Assessment creation
Curriculum support
Professional communication
Educational best practices
Nodes
AI Agent1
OpenAI Chat Model1
Simple Memory
3. Lesson Plan Form System

Provides teachers with a form for lesson topic submission.

Nodes
lesson_topic
waiting_reply
link_lessonplan
4. AI Lesson Plan Generation

Generates structured JSON lesson plans.

Output Includes
Competency
Objectives
Context
Pre-lesson activity
Lesson flow
Resources
Integration
Assessment
Extended activity
Reflections
Nodes
AI Agent
OpenAI Chat Model
parse_code
