# **Google Sheets Attendee Review Script**

This Google Apps Script adds a custom menu to your spreadsheet, allowing you to quickly "Accept" or "Reject" one or more selected rows. It is designed to update status columns, add a reviewer email, and timestamp the decision.

This script supports selecting:

* A single row  
* Multiple adjacent rows  
* Multiple non-adjacent rows (e.g., by holding Ctrl or Cmd while clicking)

## **1\. Setup Instructions**

### **Step 1: Prepare Your Google Sheet**

1. Create a new Google Sheet (or open an existing one).  
2. Create a sheet tab (or rename an existing one) to **Recommended Executives**. This exact name is required for the script to work.  
3. In the first row (row 1\) of this sheet, create the following headers. The spelling and capitalization must match:  
   * Status  
   * DecisionNotes  
   * ReviewerEmail  
   * UpdatedAt

### **Step 2: Open the Apps Script Editor**

In your Google Sheet, go to the menu Extensions \> Apps Script. A new browser tab will open with the script editor.

### **Step 3: Add the Script File (AttendeeReview.gs)**

1. In the script editor, you will see a default file named Code.gs. Click the three dots next to it and rename it to **AttendeeReview.gs**.  
2. Delete any placeholder code inside it.  
3. Copy all the code from the AttendeeReview.gs file and paste it into this file.  
4. Click the "Save project" icon (💾).

### **Step 4: Add the Manifest File (appsscript.json)**

1. In the script editor, click the **Project Settings** icon (⚙️) on the left sidebar.  
2. Check the box that says **"Show 'appsscript.json' manifest file in editor"**.  
3. Click the **Editor** icon (\<\>) on the left sidebar to return.  
4. You will now see a new file: appsscript.json. Click it.  
5. Delete any default content inside it.  
6. Copy all the JSON data from the appsscript.json file and paste it into this file.  
7. Click the "Save project" icon (💾).

## **2\. Authorization (Critical Step)**

You must manually run the script once from the editor to grant it the necessary permissions.

1. While still in the Apps Script editor, look at the toolbar at the top.  
2. From the function dropdown menu, select **acceptRow**.  
3. Click the **"Run"** button.  
4. An "Authorization required" window will pop up. Click **"Review permissions"**.  
5. Choose your Google account.  
6. You will see a "This app isn't verified" screen. This is normal for your own scripts. Click **"Advanced"**.  
7. Click **"Go to \[Your Project Name\] (unsafe)"**.  
8. A new screen will show what the script needs. It will ask for permission to **"See, edit, create, and delete all your Google Sheets spreadsheets"**. This broad permission is necessary to fix a known bug with getActiveRangeList().  
9. Click **"Allow"**.

The script will try to run and may show a red error box ("You must select a row," etc.). This is fine. You have successfully authorized the script.

## **3\. How to Use the Script**

1. Go back to your Google Sheet browser tab.  
2. **Reload the page.**  
3. A new custom menu named **"Attendee Review"** should now be visible at the top (it may take a few seconds to load).  
4. On the "Recommended Executives" sheet, select any data row(s) you want to review. You can hold Ctrl (Windows) or Cmd (Mac) to select multiple non-adjacent rows.  
5. Click the Attendee Review menu and choose Accept Selected Row(s) or Reject Selected Row(s).  
6. Follow the prompts for confirmation or to add rejection notes.

## **4\. Troubleshooting**

* **Error: "Please run this script on the 'Recommended Executives' sheet."**  
  * This script is hard-coded to *only* run on the sheet named Recommended Executives. Make sure you are on that sheet when you use the menu.  
* **Error: "Column '...' not found in sheet\!"**  
  * Make sure you have all four required headers (Status, DecisionNotes, ReviewerEmail, UpdatedAt) in row 1, with the exact spelling and capitalization.  
* **Menu doesn't show up.**  
  * Reload the page. It can sometimes take 5-10 seconds for the menu to appear. If it's still missing, double-check that your onOpen() function is in the script and that the project is saved.