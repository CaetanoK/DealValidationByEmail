# Email Validation and Deal Update Workflow in N8N

This repository contains a workflow for N8N that automates email validation, updates deals in Pipedrive, and logs data in a Google Sheets spreadsheet. The workflow consists of multiple connected steps to perform the following tasks:

1. **Receive Deal Data:**
   - A webhook is configured to receive deal data from Pipedrive.

2. **Get Deal Information:**
   - Using the deal ID received from the webhook, the workflow fetches detailed deal information from Pipedrive.

3. **Email Validation:**
   - The workflow sends the email associated with the deal to the Snov.io API for validation.
   - The email validation status is periodically checked until the validation process is complete.

4. **Set Variables:**
   - The validation results are stored in variables, including the email status and deal information.

5. **Conditional Check:**
   - The workflow checks if the email is invalid (`not_valid`) and if the deal is in the "Lead in" stage.
   - If both conditions are met, the deal is marked as lost with the reason "Invalid Email."

6. **Update Deal in Pipedrive:**
   - Deals with invalid emails are updated in Pipedrive to reflect the lost status and the reason.

7. **Log Data to Google Sheets:**
   - The workflow appends or updates a Google Sheets spreadsheet with the deal data, including email validation status.

### Workflow Steps Overview

1. **Webhook:**
   - Receives deal data from Pipedrive.
2. **Pipedrive Get Deal:**
   - Retrieves detailed information about the deal using the deal ID.
3. **Email Validation:**
   - Sends the deal's email to Snov.io for validation.
4. **Check Validation Status:**
   - Periodically checks the validation status of the email.
5. **Set Variables:**
   - Stores email validation results and deal information in variables.
6. **Conditional Logic:**
   - Checks if the email is invalid and if the deal is in the "Lead in" stage.
7. **Update Deal Status:**
   - Updates the deal in Pipedrive to mark it as lost if the email is invalid.
8. **Log to Google Sheets:**
   - Logs deal data and validation results to a Google Sheets spreadsheet.

### Nodes Description

- **Pipedrive (Get Deal):** Fetches deal details using the deal ID.
- **Merge (Combine Data):** Combines data from multiple sources.
- **If (Conditional Check):** Checks if email is invalid and deal stage.
- **Pipedrive (Update Deal):** Updates the deal status in Pipedrive.
- **Google Sheets (Append/Update):** Logs deal data to a Google Sheets spreadsheet.
- **HTTP Request (Email Validation):** Sends email for validation and checks the status.

### Usage

1. **Configure Webhook:**
   - Set up a webhook in Pipedrive to send deal data to the N8N webhook node.

2. **Set Credentials:**
   - Ensure that your Pipedrive and Snov.io API credentials are correctly configured in N8N.

3. **Google Sheets Setup:**
   - Ensure that the Google Sheets document and sheet are correctly configured to receive the logged data.

4. **Run Workflow:**
   - Start the workflow in N8N and let it handle the automation process.

This workflow helps automate the process of validating emails associated with deals, updating deal statuses based on email validity, and maintaining a log of these actions in Google Sheets.
