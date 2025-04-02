Gmail Automation with CrewAI 📧✨

Gmail Automation with CrewAI is an intelligent email management system that leverages AI agents to categorize, organize, respond to, and clean up your Gmail inbox automatically.



✨ Features

📋 Email Categorization: Automatically categorizes emails into specific types (newsletters, promotions, personal, etc.)

🔔 Priority Assignment: Assigns priority levels (HIGH, MEDIUM, LOW) based on content and sender with strict classification rules

🏷️ Smart Organization: Applies Gmail labels and stars based on categories and priorities

💬 Automated Responses: Generates draft responses for important emails that need replies

📱 Slack Notifications: Sends creative notifications for high-priority emails

🧹 Intelligent Cleanup: Safely deletes low-priority emails based on age and category

🎬 YouTube Content Protection: Special handling for YouTube-related emails

🗑️ Trash Management: Automatically empties trash to free up storage space

🧵 Thread Awareness: Recognizes and properly handles email threads

🚀 Installation

# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate  # On Windows: .venv\Scripts\activate

# Install dependencies
crewai install

⚙️ Configuration

Create a .env file in the root directory with the following variables:

# Choose your LLM provider
# OpenAI (Recommended)
MODEL=openai/gpt-4o-mini
OPENAI_API_KEY=your_openai_api_key

# Gmail credentials
EMAIL_ADDRESS=your_email@gmail.com
APP_PASSWORD=your_app_password

# Optional: Slack notifications
SLACK_WEBHOOK_URL=your_slack_webhook_url

Go to your Google Account settings at myaccount.google.com

Select Security from the left navigation panel

Under "Signing in to Google," find and select 2-Step Verification (enable it if not already enabled)

Scroll to the bottom and find App passwords

Select Mail from the "Select app" dropdown

Select Other (Custom name) from the "Select device" dropdown

Enter Gmail CrewAI as the name

Click Generate

Copy the 16-character password that appears (spaces will be removed automatically)

Paste this password in your .env file as the APP_PASSWORD value

Click Done

Note: App passwords can only be created if you have 2-Step Verification enabled on your Google account.

Go to api.slack.com/apps

Click Create New App

Select From scratch

Enter Gmail Notifications as the app name

Select your workspace and click Create App

In the left sidebar, find and click on Incoming Webhooks

Toggle the switch to Activate Incoming Webhooks

Click Add New Webhook to Workspace

Select the channel where you want to receive notifications

Click Allow

Find the Webhook URL section and copy the URL that begins with https://hooks.slack.com/services/

Paste this URL in your .env file as the SLACK_WEBHOOK_URL value

📧 How It Works

This application uses the IMAP (Internet Message Access Protocol) to securely connect to your Gmail account and manage your emails. Here's how it works:

Secure Connection: The application establishes a secure SSL connection to Gmail's IMAP server (imap.gmail.com).

Authentication: It authenticates using your email address and app password (not your regular Google password).

Mailbox Access: Once authenticated, it can access your inbox and other mailboxes to:

Read unread emails

Apply labels

Move emails to trash

Save draft responses

Safe Disconnection: After each operation, the connection is properly closed to maintain security.

IMAP allows the application to work with your emails while they remain on Google's servers, unlike POP3 which would download them to your device. This means you can still access all emails through the regular Gmail interface.

🔍 Usage

Run the application with:

crewai run

You'll be prompted to enter the number of emails to process (default is 5).

The application will:

📥 Fetch your unread emails

🔎 Categorize them by type and priority

⭐ Apply appropriate labels and stars

✏️ Generate draft responses for important emails

🔔 Send Slack notifications for high-priority items

🗑️ Clean up low-priority emails based on age

🧹 Empty the trash to free up storage space

🌟 Special Features

📅 Smart Deletion Rules:

Promotions older than 2 days are automatically deleted

Newsletters older than 7 days (unless HIGH priority) are deleted

Shutterfly emails are always deleted regardless of age

Receipts and important documents are archived instead of deleted

🎬 YouTube Protection: All YouTube-related emails are preserved and marked as READ_ONLY (you'll respond directly on YouTube)

✍️ Smart Response Generation: Responses are tailored to the email context and include proper formatting

💡 Creative Slack Notifications: Fun, attention-grabbing notifications for important emails

🧵 Thread Handling: Properly tracks and manages email threads to maintain conversation context

👥 Contributing


