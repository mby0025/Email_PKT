PAYRUPIK EMAIL EXECUTIVE ASSESSMENT PORTAL – SEPARATE SUBMISSION VERSION

FILES
1. index.html – upload this file to the root of GitHub repository Email_PKT (replace the old index.html).
2. Code.gs – replace the complete code in the existing Google Apps Script project named Email Assessment Backend.

IMPORTANT EXISTING SETTINGS
- Keep the existing Script Properties SPREADSHEET_ID and ADMIN_PASSWORD. Do not delete or change them.
- Keep using the existing Google spreadsheet. The updated backend creates two new tabs in that same spreadsheet:
  * Individual Assessments
  * Email Writing
- The old tab named Email Assessment is left untouched as historical data.
- Do not create a new Apps Script project or a new spreadsheet.

DEPLOYMENT
1. Open the existing Google Apps Script project.
2. Replace all Code.gs content with the supplied Code.gs and Save.
3. Select function setup and Run once. Approve permissions if Google asks. This creates the two new tabs in the existing spreadsheet.
4. Click Deploy > Manage deployments > Edit (pencil) on the existing Web App deployment.
5. Select New version, keep Execute as: Me and Who has access: Anyone, then Deploy.
6. The frontend is already configured with the current Web App URL recorded for this project. If Apps Script gives a different URL, replace BACKEND_URL in index.html with the current /exec URL.
7. In GitHub repo mby0025/Email_PKT, replace the root index.html with this new index.html and commit the change.
8. Open https://mby0025.github.io/Email_PKT/ and test with a test email ID before sharing it with executives.

HOW IT WORKS
- Same email ID can submit Assessment 1, 2 and 3 separately, in any order.
- Each assessment is saved immediately and permanently locked for that email ID.
- Each MCQ score is calculated on the server and shown after that assessment is submitted. Correct answers are not shown to executives.
- Final Email Writing Task becomes available only after all three MCQ assessments are submitted.
- Executive selects ONE of five topics and submits one email. It is locked after submission.
- Trainer dashboard lists each executive, all individual MCQ scores, the selected email topic and response. Trainer assigns 0–25 marks and feedback; final score is calculated out of 100.

TEST CHECKLIST
- Submit Assessment 1 with a test email; verify score appears and status changes to Submitted.
- Refresh/re-enter using same email; Assessment 1 should be locked while Assessments 2 and 3 remain available.
- Submit Assessments 2 and 3 separately; verify all three scores.
- Confirm email task unlocks only after all three MCQ assessments.
- Submit one email topic; verify it becomes locked.
- Login to Trainer/Admin and grade the email; verify final score out of 100.

NOTES
- Do not run setup against a different spreadsheet or remove the existing Script Properties.
- Existing historical records in the old Email Assessment tab are not automatically migrated into the new separate-assessment structure.
- This is email-ID based duplicate prevention, not identity verification. Anyone who can access the portal and knows an email address could attempt to use it; share the portal only with the intended executives.
