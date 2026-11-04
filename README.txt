# PayRupik Email Writing Assessment (Separate Application)

This is a standalone email-writing assessment. It does not replace or modify the existing PKT / MCQ assessment page.

## Included files
- `index.html` — GitHub Pages frontend.
- `Code.gs` — Google Apps Script backend for Google Sheets.
- `README.txt` — setup and deployment instructions.

## Assessment design
- Five scenario-based customer email tasks.
- 20 marks per task; 100 marks total.
- Executives enter name, official email and assessment date.
- One submission per email address.
- Responses are saved in Google Sheets.
- Trainer/admin can review each email, score each task from 0–20, add feedback and export submissions as CSV.
- Scoring is manual by the trainer. The app does not automatically judge writing quality.

## 1. Create the Google Sheet backend
1. Open https://script.google.com and create a **New project**.
2. Open `Code.gs` in this package, copy all its contents, and replace the default Apps Script code.
3. Save the project.
4. From the function dropdown, select `setup` and click **Run**.
5. Approve the Google permissions.
6. Open **Execution log** (or View > Logs) and copy the created spreadsheet URL. The script also stores its Spreadsheet ID in Script Properties.
7. In Apps Script, open **Project Settings** (gear icon) > **Script properties** > Add script property:
   - Property: `ADMIN_PASSWORD`
   - Value: choose a strong password for the trainer dashboard.
8. Save the Script Property.

## 2. Deploy Apps Script as a Web App
1. Click **Deploy** > **New deployment**.
2. Select type **Web app**.
3. Description: `PayRupik Email Assessment Backend`.
4. Execute as: **Me**.
5. Who has access: **Anyone** (required for the public GitHub Pages form to submit).
6. Click **Deploy**, authorize if prompted, then copy the Web App URL ending in `/exec`.
7. Do not share the Apps Script editor or Google Sheet with executives. Only share the assessment website.
8. If you change `Code.gs` later, use **Deploy > Manage deployments > Edit > New version > Deploy**.

## 3. Configure index.html
1. Open `index.html`.
2. Find this line near the bottom:
   `const BACKEND_URL = "PASTE_YOUR_APPS_SCRIPT_WEB_APP_URL_HERE";`
3. Replace the placeholder with your deployed `/exec` URL, keeping the quotation marks.
4. Save the file.

## 4. Upload as a separate page in GitHub
Recommended: create a separate folder in your existing repository so your current website and assessment remain untouched.

1. Open your GitHub repository: `mby0025/xploretechai`.
2. Click **Add file** > **Create new file**.
3. In the filename box, enter:
   `email-assessment/index.html`
4. Paste the complete configured `index.html` code.
5. Commit the file to the `main` branch.
6. Upload `Code.gs` only to Google Apps Script. Do **not** upload it to the public GitHub repository because it contains backend implementation details and should not be the public frontend.
7. Your separate page should be available at:
   `https://www.xploretechai.com/email-assessment/`
   If your GitHub Pages custom domain is different, use that domain instead.

You can also use **Add file > Upload files** to upload the `index.html` inside an `email-assessment` folder.

## 5. Test before sharing with executives
1. Open the website in an Incognito/private browser window.
2. Submit one test response using your own test email.
3. Check that a row appears in the Google Sheet.
4. Try starting again with the same email; it should be blocked.
5. Open Admin Login on the page and enter the `ADMIN_PASSWORD`.
6. Review the five responses, enter marks from 0–20 for every task, add feedback and save.
7. Confirm the total out of 100 is saved in the sheet.
8. Test CSV export.

## Important security and operational notes
- The frontend and Apps Script Web App are public-facing. Keep the admin password strong and do not put it in `index.html`.
- Anyone who knows the admin password can view submissions and grade them. Share it only with authorized trainers.
- The current implementation uses a shared admin password, not individual Google-account sign-in.
- The one-submission rule is based on email address; it is not proof of identity. For stronger identity verification, use an approved company login or allowlisted employee directory.
- Do not place real customer personal or financial data in practice responses. The scenarios are fictional training exercises.
