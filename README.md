# InboxGuardian – AI-Powered Email Management Assistant

## Overview

InboxGuardian is an AI-powered email management automation built with **n8n**. It is designed to simplify email management by automatically analysing incoming emails, identifying their importance, generating summaries, and determining the appropriate next action.

The automation integrates Gmail, AI, Telegram, and Google Sheets to help users manage incoming emails more efficiently and stay informed about important messages.

## Problem Statement

Managing a busy email inbox can be time-consuming. Important messages can easily get lost among promotional emails, general correspondence, and other notifications.

InboxGuardian addresses this challenge by using AI and workflow automation to organize incoming emails, highlight urgent messages, and support better email management.

## Project Objectives

- Automate the monitoring of incoming emails.
- Use AI to analyse and classify email messages.
- Identify emails that require urgent attention.
- Generate summaries and suggested replies.
- Send notifications for important emails through Telegram.
- Store email information and AI analysis in Google Sheets.
- Reduce repetitive manual email management tasks.

  ## How It Works

1. **Email Monitoring:** Gmail Trigger detects incoming emails.
2. **Email Analysis:** AI analyses the email content and generates a concise summary.
3. **Email Classification:** Emails are categorized into:
   - Urgent
   - Needs Reply
   - Informational
   - Promotional
   - Personal
   - Uncertain
4. **Priority Assessment:** AI assigns a priority level of High, Medium, or Low.
5. **Conditional Routing:** n8n routes emails according to their assigned categories.
6. **Telegram Notifications:** Urgent emails trigger notifications through a Telegram bot.
7. **Suggested Replies:** AI generates suggested responses for emails requiring replies. These are intended for human review rather than automatic sending.
8. **Google Sheets Logging:** Email details, categories, priorities, summaries, and recommended actions are recorded in Google Sheets.

## Key Features

- Automated Gmail monitoring.
- AI-powered email analysis and classification.
- Email summarization.
- Priority identification.
- Telegram notifications for urgent emails.
- AI-generated suggested replies.
- Conditional workflow routing.
- Centralized email activity logging using Google Sheets.

  ## Technologies Used

- **n8n:** Workflow automation and integration.
- **Gmail:** Incoming email monitoring.
- **AI / LLM:** Email analysis, classification, and summarization.
- **Telegram Bot API:** Urgent email notifications.
- **Google Sheets:** Email records and tracking.

## Workflow Architecture

```text
Gmail Trigger
      |
      v
Extract Email Information
      |
      v
AI Email Analysis
      |
      v
Email Classification
      |
      v
Conditional Routing
      |
      |------ Urgent --------> Telegram Notification
      |
      |------ Needs Reply ---> Suggested Reply
      |
      |------ Informational -> Google Sheets
      |
      |------ Promotional ---> Google Sheets
      |
      |------ Personal ------> Google Sheets
      |
      |------ Uncertain -----> Human Review
      |
      v
Google Sheets Email Log
```


### Part 4: Business value and future improvements

## Business Value

InboxGuardian demonstrates how AI and workflow automation can support everyday business operations by:

- Reducing manual email sorting.
- Improving visibility of important messages.
- Supporting timely responses.
- Organizing email information.
- Reducing repetitive administrative tasks.
- Supporting more structured email management.

## Future Improvements

The automation could be extended with additional n8n integrations and workflow capabilities, including:

- **Google Calendar Integration:** Automatically identify meeting requests and create calendar events.
- **Automated Follow-up Reminders:** Use Schedule Trigger and Gmail nodes to identify emails awaiting responses and send reminders.
- **Human Approval Workflow:** Introduce an approval process before AI-generated replies are sent.
- **Automated Email Responses:** Allow approved AI-generated replies to be sent through Gmail.
- **Performance Reporting:** Connect email records to a reporting dashboard to monitor email categories, priorities, and automation activity.

## Project Structure

```text
ai-email-management-assistant/
│
├── README.md
├── workflow/
│   └── inboxguardian-workflow.json
├── screenshots/
│   ├── complete-workflow.png
│   ├── telegram-notification.png
│   └── google-sheets-log.png
└── sample-data/
    └── sample-emails.csv
```

## Setup Instructions

Follow these steps to set up and run the InboxGuardian workflow.

### Prerequisites

Before getting started, make sure you have:

- An n8n account or self-hosted n8n instance.
- A Gmail account.
- Access to an AI model and its API credentials.
- A Telegram bot created through [BotFather](https://t.me/BotFather).
- A Google account with access to Google Sheets.

### Installation and Configuration

**Step 1: Import the Workflow**

1. Download the exported InboxGuardian workflow JSON file from this repository.
2. Open your n8n workspace.
3. Select **Import from File**.
4. Upload the workflow JSON file.

**Step 2: Configure Gmail**

1. Open the Gmail Trigger node.
2. Create or select your Gmail credentials.
3. Authorize n8n to access your Gmail account.
4. Configure the trigger to monitor incoming emails.

**Step 3: Configure the AI Model**

1. Open the AI node.
2. Add your AI provider credentials.
3. Select your preferred AI model.
4. Review the classification prompt and output structure.

**Step 4: Configure Telegram**

1. Create a Telegram bot using [BotFather](https://t.me/BotFather).
2. Copy your bot token.
3. Open the Telegram node in n8n.
4. Add your Telegram bot credentials.
5. Configure your Telegram Chat ID.
6. Send a test notification to confirm the connection.

**Step 5: Configure Google Sheets**

1. Upload the provided email management template to Google Drive.
2. Open the file using Google Sheets.
3. Connect your Google account to n8n.
4. Open the Google Sheets node.
5. Select your spreadsheet and the `Email Log` worksheet.
6. Map the workflow output fields to their corresponding spreadsheet columns.

**Step 6: Test the Workflow**

1. Send sample emails to your connected Gmail account.
2. Confirm that the AI correctly analyses and classifies the emails.
3. Check that urgent emails generate Telegram notifications.
4. Verify that suggested replies are generated where required.
5. Confirm that processed email information is recorded in Google Sheets.
6. Test different email categories to verify the routing logic.

**Step 7: Activate the Workflow**

After successfully testing all configured nodes and connections, activate the workflow in n8n to begin monitoring incoming emails.

### Important Notes

- Replace all credential placeholders with your own credentials.
- Never upload API keys, bot tokens, passwords, or private account information to GitHub.
- AI-generated replies should be reviewed before sending.
- Test the workflow before activating it for live emails.
