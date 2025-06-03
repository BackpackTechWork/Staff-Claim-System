# Staff Claim System

A comprehensive Google Apps Script-based system for managing staff claims, expenses, petty cash, and event-related finances.

## Developers
- [@Darkguyaiman](https://github.com/Darkguyaiman)
- [@Ak-ko](https://github.com/Ak-ko)

## Features

- **Claim & Allowance Management**
  - Submit and process staff claims
  - Track allowances
  - Automated approval workflows
  - Support for multiple claim types:
    - Meal allowances
    - Other allowances
    - Stay claims
    - Extra claims
    - Transportation claims
  - Receipt management
  - Status tracking and updates

- **Petty Cash Management**
  - Track petty cash transactions
  - Maintain petty cash balance
  - Transaction history
  - Receipt tracking
  - Balance reconciliation

- **Budget & Expenses Tracking**
  - Monitor department budgets
  - Track expenses against budgets
  - Generate financial reports
  - Budget allocation
  - Expense categorization
  - Real-time budget updates

- **Event Management**
  - Create and manage events
  - Track event-related expenses
  - Post-event expense reconciliation
  - Event status tracking
  - Event budget management
  - Location-based event details

- **Advance Purchase Management**
  - Process advance purchase requests
  - Track purchase status
  - Reconcile purchases with receipts
  - Purchase approval workflow
  - Vendor management
  - Purchase history

- **Dashboard**
  - Overview of all financial activities
  - Quick access to pending items
  - Financial summaries and reports
  - Real-time status updates
  - Customizable views
  - Data visualization

## Prerequisites
- Google Apps Script editor access
- Basic understanding of Google Sheets and Google Apps Script
- Google Maps API key with Places library enabled
- Google Workspace account with appropriate permissions

## Setup Instructions

1. **Clone the Project**
   - Access the [Google Drive Project Folder](YOUR_DRIVE_FOLDER_LINK)
   - Make a copy of the entire project folder
   - Rename it to your preferred project name

2. **Enable Required Google Services**
   - In the Apps Script editor, go to "Services" (+ icon)
   - Add the following services:
     - Drive API (v3)

3. **Configure Project Settings**
   - Open `appsscript.json`
   - Ensure the timezone is set correctly for your region (default: Asia/Singapore)
   - Verify the webapp settings match your requirements:
     ```json
     {
       "webapp": {
         "executeAs": "USER_ACCESSING",
         "access": "ANYONE"
       }
     }
     ```

4. **Multi-Deployment Setup**
   This project requires multiple deployments as each module (tab and form) needs to be deployed independently. Follow these steps for each module:

   a. **Main Directory Deployment**
   - Open `MainDirectory.js`
   - Click "Deploy" > "New deployment"
   - Choose "Web app" as the deployment type
   - Set the following:
     - Execute as: "User accessing the web app"
     - Who has access: "Anyone" (or restrict as needed)
   - Click "Deploy"
   - Copy the deployment URL
   - Save this URL as it will be your main entry point

   b. **Module Deployments**
   Deploy each of the following modules independently:
   - Claim & Allowance Management
   - Petty Cash Management
   - Budget & Expenses
   - Event Creation
   - Advance Purchases Management
   - Settings
   - Dashboard

   For each module:
   1. Open the corresponding .js file
   2. Click "Deploy" > "New deployment"
   3. Choose "Web app" as the deployment type
   4. Set the same execution and access settings
   5. Click "Deploy"
   6. Copy the deployment URL

   c. **Form Deployments**
   Deploy each form independently:
   - Claim & Allowance Form
   - Petty Cash Transaction Form
   - Event Creation Form
   - Advance Purchase Form
   - Post-Event Expenses Form

   For each form:
   1. Open the corresponding .js file
   2. Click "Deploy" > "New deployment"
   3. Choose "Web app" as the deployment type
   4. Set the same execution and access settings
   5. Click "Deploy"
   6. Copy the deployment URL

   d. **Update Deployment URLs**
   After deploying all modules and forms, you need to update the deployment URLs in the following places:
   1. Open `MainDirectory.js`
   2. Locate the URL configuration section
   3. Replace the placeholder URLs with your actual deployment URLs
   4. Save the changes
   5. Redeploy the Main Directory if necessary

   Example URL configuration structure:
   ```javascript
   const DEPLOYMENT_URLS = {
     claimAllowance: 'YOUR_CLAIM_ALLOWANCE_URL',
     pettyCash: 'YOUR_PETTY_CASH_URL',
     budgetExpenses: 'YOUR_BUDGET_EXPENSES_URL',
     eventCreation: 'YOUR_EVENT_CREATION_URL',
     advancePurchases: 'YOUR_ADVANCE_PURCHASES_URL',
     settings: 'YOUR_SETTINGS_URL',
     dashboard: 'YOUR_DASHBOARD_URL',
     forms: {
       claimForm: 'YOUR_CLAIM_FORM_URL',
       pettyCashForm: 'YOUR_PETTY_CASH_FORM_URL',
       eventForm: 'YOUR_EVENT_FORM_URL',
       advancePurchaseForm: 'YOUR_ADVANCE_PURCHASE_FORM_URL',
       postEventForm: 'YOUR_POST_EVENT_FORM_URL'
     }
   };
   ```

5. **Set Up Required Google Sheets**
   Create the following sheets in your Google Spreadsheet:
   - **Claim&Allowance**
     - Main claims tracking
     - Columns: Created Date, Event Status, Application Number, Person of Submission, etc.
   - **Claim&Allowance Stay**
     - Track accommodation claims
     - Columns: Application Number, Stay Type, Stay Cost, Stay Receipt
   - **Claim&Allowance Extra Claims**
     - Track additional claims
     - Columns: Application Number, Claim Description, Claim Amount, Claim Receipt
   - **Claim&Allowance Transportation**
     - Track transportation claims
     - Columns: Application Number, Transportation Type, Car Type, Company Car, etc.
   - **Petty Cash**
     - Track petty cash transactions
   - **Budget & Expenses**
     - Track department budgets and expenses
   - **Events**
     - Track event details and expenses
   - **Advance Purchases**
     - Track advance purchase requests

6. **Configure Google Maps API**
   - Go to Google Cloud Console
   - Enable the Places API
   - Create API credentials
   - Add the API key to your project configuration
   - Enable billing for the project
   - Set up appropriate restrictions for the API key

## API Configuration

The system uses the following Google APIs:

1. **Drive API (v3)**
   - Used for file management
   - Required for handling attachments and documents
   - Required scopes:
     - `https://www.googleapis.com/auth/drive.file`
     - `https://www.googleapis.com/auth/drive.readonly`

2. **Google Maps API**
   - Used for Places library functionality
   - Required for location-based features
   - Required services:
     - Places API
     - Maps JavaScript API
   - Required libraries:
     - Places library
     - Geocoding library

To enable these APIs:
1. Go to Google Cloud Console
2. Enable the required APIs for your project
3. Set up appropriate OAuth consent screen
4. Configure necessary scopes
5. Generate and configure your Google Maps API key
6. Set up API key restrictions:
   - HTTP referrers
   - IP addresses
   - Application restrictions

## File Structure

```
Staff Claim System/
├── HTML Files/
│   ├── CRUDAdvancePurchasesManagement.html
│   ├── CRUDBudget&Expenses.html
│   ├── CRUDClaim&Allowance.html
│   ├── CRUDDashboard.html
│   ├── CRUDEventCreation.html
│   ├── CRUDPettyCashManagement.html
│   ├── CRUDSettings.html
│   ├── MainDirectory.html
│   ├── Claim&AllowanceForm.html
│   ├── Testings.html
│   ├── PettyCashTransaction.html
│   ├── EventCreationForm.html
│   ├── AdvancePurchase.html
│   ├── Post-EventExpensesForm.html
│   └── Unauthorized.html
│
├── JavaScript Files/
│   ├── Petty Cash Transaction.js
│   ├── Event Creation Form.js
│   ├── CRUD Settings.js
│   ├── CRUD Petty Cash Management.js
│   ├── CRUD Budget & Expenses.js
│   ├── CRUD Claim & Allowance.js
│   ├── CRUD Dashboard.js
│   ├── CRUD Event Creation.js
│   ├── Claim & Allowance Form.js
│   ├── Advance Purchase.js
│   ├── CRUD Advance Purchases Management.js
│   ├── Main Directory.js
│   └── Post-Event Expenses Form.js
│
└── Configuration/
    └── appsscript.json
```

## Usage

1. **Access the System**
   - Open the deployed web app URL
   - Log in with your Google Workspace account
   - You'll be redirected to the main directory

2. **Navigation**
   - Use the main directory to access different modules
   - Each module has its own CRUD interface
   - Forms are available for data entry
   - Use the dashboard for quick access to important information

3. **Common Operations**
   - **Submitting Claims**
     1. Navigate to Claim & Allowance Form
     2. Fill in the required information
     3. Attach necessary receipts
     4. Submit for approval
   
   - **Managing Petty Cash**
     1. Access Petty Cash Management
     2. Record transactions
     3. Attach receipts
     4. Update balance
   
   - **Creating Events**
     1. Go to Event Creation module
     2. Fill in event details
     3. Set budget and expenses
     4. Track event status
   
   - **Monitoring Budgets**
     1. Access Budget & Expenses section
     2. View department budgets
     3. Track expenses
     4. Generate reports

## Security Considerations

- Ensure proper access controls are in place
- Regularly review user permissions
- Keep API keys and credentials secure
- Follow Google's security best practices
- Implement proper error handling
- Regular backup of spreadsheet data
- Monitor API usage and quotas
- Implement rate limiting where necessary

## Contributing
1. Fork the repository
2. Create a feature branch
3. Commit your changes
4. Push to the branch
5. Create a Pull Request

## Support
For support, please:
1. Check the documentation
2. Review existing issues
3. Create a new issue if needed

## Acknowledgments
- Google Apps Script team
- Contributors and maintainers
- Users of the system 