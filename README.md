# 📬 Gmail to Notion Job Tracker

This project helps automate the tracking of your job applications directly from Gmail into a Notion database. By using Google Apps Script, it extracts important details from job-related emails (like company, job title, status) and syncs them to a Notion board for easier job search management.

## 🚀 Features

- Job Status Tracking: Categorize emails into `Applied`, `Interview`, `Offer`, `Rejected`, and `Follow-up` statuses.
- Automatic Data Extraction: Extracts company name, job title, email sender, email subject, snippet, and date from job-related emails.
- Prevents Duplicates: Skips already processed emails to avoid redundant entries in the Notion database.
- Notion Integration: Easily integrates Gmail with Notion via Notion's API to store job application data.
- Daily Automation: Optionally set up a daily trigger to automatically run the script every day.

## 🛠 Tech Stack

- [Google Apps Script](https://developers.google.com/apps-script) for Gmail and Notion API interactions.
- [Notion API](https://developers.notion.com/) to create, update, and query Notion pages and databases.
- Gmail Integration via Google Apps Script.
- Google Apps Script Services like `PropertiesService`, `UrlFetchApp`, etc.

## 🔧 How to Use

### Step 1: Set Up Your Notion Database

1. Create a Notion Database where you will track job applications.
   - Example of fields for the Notion Database:
     - Company (Title)
     - Job Title (Rich Text)
     - Status (Select: `Applied`, `Interview`, `Rejected`) and choose color as per your preferences.
     - Email Subject (Rich Text)
     - Snippet (Rich Text)
     - Date (Date)
     - From (Email)

2. Get your Notion API Key: Follow the instructions on the [Notion API documentation](https://developers.notion.com/) to create an integration and get your API key.

3. Get your Notion Database ID: You can find this in the URL of your database (after `/` in the URL).

### Step 2: Set Up Google Apps Script

1. Create a Google Apps Script Project:
   - Go to [Google Apps Script](https://script.google.com) and create a new project.
   
2. Paste the Script:
   - Copy and paste the provided script into your Apps Script project. This script connects your Gmail account and the Notion database.

3. Store Notion API Key and Database ID:
   - Go to the "Script Properties" in Google Apps Script (under File → Project Properties → Script Properties) and add:
     - `NOTION_API_KEY` = Your Notion API Key
     - `DATABASE_ID` = Your Notion Database ID

4. Run the Script:
   - You can run the script manually for the first time or set a trigger to run it daily. 
   - For the first run, the script will clear the Notion database (if you set it to), then fetch emails related to job applications and sync them to Notion.
   
### Step 3: Optional (Set Up a Daily Trigger)

1. Set Up Automatic Daily Runs:
   - You can set a trigger to run the script daily by running the `createDailyTrigger()` function in the Google Apps Script UI. This will check for new emails every day and update your Notion database automatically.

### Step 4: View Your Job Applications in Notion

- After running the script, check your Notion database, and you'll see the job application data automatically populated with details such as company name, job title, status, and more!

## ⚙️ Configurations

- The script searches for job-related emails based on a predefined query, such as:
  - "subject:(application OR interview OR 'job offer' OR 'thank you' OR rejected OR declined OR 'follow-up' OR 'follow up' OR 'job opportunity' OR 'position')"
  - The script then categorizes the status based on keywords in the email's subject and body.

## 📝 Customization

- Change the email query: Modify the `processGmailEmails` function to suit your specific needs. For example, you can add more keywords or adjust the time filter.
- Change Notion database fields: If your Notion database has different fields, simply update the `createNotionEntry` function to match your database's schema.
- Adjust job status detection: The `determineJobStatus` function uses simple string matching to categorize emails. You can tweak the logic to match more precise patterns.

## 💡 Tips & Troubleshooting

- Google Apps Script Authorization: The first time you run the script, you'll need to authorize it to access your Gmail and Notion accounts.
- Rate Limiting: If you have a large number of emails, Google Apps Script may hit API rate limits. Consider modifying the script to handle pagination or throttle requests.

## 📄 Example of Notion Database

| Company      | Job Title     | Status  | Email Subject | Snippet      | Date          | From               |
|--------------|---------------|---------|---------------|--------------|---------------|--------------------|
| Google       | Software Engineer | Interview | Invitation to Interview | "We are pleased to inform you..." | 2025-05-10 | john.doe@gmail.com |
| Microsoft    | Data Analyst | Offer   | Job Offer from Microsoft | "We're excited to offer..." | 2025-05-05 | recruiter@microsoft.com |

## 📅 Set Up and Run

1. Clone the repository to your GitHub or directly download the script.
2. Set your Notion API credentials as explained above.
3. Customize the script if needed.
4. Run the script manually or set up an automatic trigger.

## 🔗 Links

- [Notion API Documentation](https://developers.notion.com/)
- [Google Apps Script Documentation](https://developers.google.com/apps-script/)
- [Gmail API Documentation](https://developers.google.com/gmail/api)

---

### 🚀 Future Enhancements (Optional)

- Add email content parsing to better extract details like job description or interview dates.
- Improve the email status detection to support more scenarios (e.g., interview rescheduled).
- Create an interface for the user to manually edit the status or details within Notion.

---

## 👏 Contributing

If you’d like to contribute to this project, feel free to fork it, make changes, and submit a pull request. Your contributions are welcome!

---

### 📝 License

This project is licensed under the MIT License – see the [LICENSE](LICENSE) file for details.
