Google Sheets Attendee Review Script
	This Google Apps Script adds a custom menu to your spreadsheet, allowing you to quickly "Accept" or "Reject" one or more selected rows. It is designed to update status columns, add a reviewer email, and timestamp the decision.
This script supports selecting:
	A single row
	Multiple adjacent rows
	Multiple non-adjacent rows (e.g., by holding Ctrl or Cmd while clicking)
1. Setup Instructions
	Step 1: Prepare Your Google Sheet
	Create a new Google Sheet (or open an existing one).
	Create a sheet tab (or rename an existing one) to Recommended Executives. This exact name is required for the script to work.
	In the first row (row 1) of this sheet, create the following headers. The spelling and capitalization must match:
		Status
		DecisionNotes
		ReviewerEmail
		UpdatedAt
Step 2: Open the Apps Script Editor
	In your Google Sheet, go to the menu Extensions > Apps Script. A new browser tab will open with the script editor.
Step 3: Add the Script File (AttendeeReview.gs)
	In the script editor, you will see a default file named Code.gs. Click the three dots next to it and rename it to AttendeeReview.gs.
	Delete any placeholder code inside it.
	Copy all the code from the AttendeeReview.gs file and paste it into this file.
	Click the "Save project" icon (💾).
Step 4: Add the Manifest File (appsscript.json)
	In the script editor, click the Project Settings icon (⚙️) on the left sidebar.
	Check the box that says "Show 'appsscript.json' manifest file in editor".
	Click the Editor icon (<>) on the left sidebar to return.
	You will now see a new file: appsscript.json. Click it.
	Delete any default content inside it.
	Copy all the JSON data from the appsscript.json file and paste it into this file.
	Click the "Save project" icon (💾).
2. Authorization (Critical Step)
	You must manually run the script once from the editor to grant it the necessary permissions.
	While still in the Apps Script editor, look at the toolbar at the top.
	From the function dropdown menu, select acceptRow.
	Click the "Run" button.
	An "Authorization required" window will pop up. Click "Review permissions".
	Choose your Google account.
	You will see a "This app isn't verified" screen. This is normal for your own scripts. Click "Advanced".
	Click "Go to [Your Project Name] (unsafe)".
	A new screen will show what the script needs. It will ask for permission to "See, edit, create, and delete all your Google Sheets spreadsheets". This broad permission is necessary to fix a known bug with getActiveRangeList().
	Click "Allow".
	The script will try to run and may show a red error box ("You must select a row," etc.). This is fine. You have successfully authorized the script.
3. How to Use the Script
	Go back to your Google Sheet browser tab.
	Reload the page.
	A new custom menu named "Attendee Review" should now be visible at the top (it may take a few seconds to load).
	On the "Recommended Executives" sheet, select any data row(s) you want to review. You can hold Ctrl (Windows) or Cmd (Mac) to select multiple non-adjacent rows.
	Click the Attendee Review menu and choose Accept Selected Row(s) or Reject Selected Row(s).
	Follow the prompts for confirmation or to add rejection notes.
4. Troubleshooting
	Error: "Please run this script on the 'Recommended Executives' sheet."
	This script is hard-coded to only run on the sheet named Recommended Executives. Make sure you are on that sheet when you use the menu.
	Error: "Column '...' not found in sheet!"
	Make sure you have all four required headers (Status, DecisionNotes, ReviewerEmail, UpdatedAt) in row 1, with the exact spelling and capitalization.
	Menu doesn't show up.
	Reload the page. It can sometimes take 5-10 seconds for the menu to appear. If it's still missing, double-check that your onOpen() function is in the script and that the project is saved.
