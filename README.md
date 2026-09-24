VITALITY BP RECORD v2: SETUP GUIDE
==================================

What you get
  - A phone app (index.html) that works on any Android phone or iPhone, even with no internet.
  - A clinic database: one Google Sheet owned by the clinic. Every phone sends its records there
    automatically whenever it has internet. The Sheet has 4 tabs:
      Summary    live numbers: patients enrolled, BP control rate, missed-visit rate, overdue patients
      Patients   one row per patient (last BP, step, next visit, full record)
      Visits     one row per visit (all 3 readings, average, step, missed pills, action, next visit)
      Medicines  one row per medicine (dose, dates, Adjusting / Working / Stopped, and why stopped)

Files in this folder
  index.html, manifest.json, sw.js, icon-192.png, icon-512.png   the phone app
  Code.gs                                                          the clinic server script (goes in the Google Sheet)

-------------------------------------------------------------------
PART 1: CLINIC DATABASE (about 15 minutes, free, one time)
-------------------------------------------------------------------
Use a Google account that belongs to the CLINIC (not a staff member's personal account).

 1. Go to sheets.google.com and create a blank sheet. Name it "Vitality BP Database".
 2. In the sheet: Extensions > Apps Script.
 3. Delete everything in the editor. Open Code.gs from this folder, copy ALL of it, paste it in. Click Save.
 4. At the top, choose the function "setup" and click Run.
    Google asks for permission: click Review permissions, choose the clinic account,
    click Advanced > "Go to ... (unsafe)" > Allow. (This warning appears for every private script.)
 5. Click "Execution log". You will see two codes:
       WRITE_CODE  (starts with W-)  for patients' phones. It can only SEND records.
       STAFF_CODE  (starts with S-)  for clinic phones. It can also DOWNLOAD any patient's record.
    Write them down and keep the STAFF_CODE private.
 6. Click Deploy > New deployment > the gear icon > "Web app".
       Description: BP Record
       Execute as: Me
       Who has access: Anyone
    Click Deploy and copy the "Web app URL" (it starts with https://script.google.com/macros/s/ and ends with /exec).
    This is the "clinic sync link".

Check: go back to the Sheet. You should see the tabs Summary, Patients, Visits, Medicines.

To change a code later: Apps Script > Project Settings > Script properties, edit WRITE_CODE or STAFF_CODE.
If you ever edit Code.gs: Deploy > Manage deployments > edit (pencil) > Version: New version > Deploy.
The link stays the same.

-------------------------------------------------------------------
PART 2: PUT THE APP ONLINE (about 15 minutes, free, one time)
-------------------------------------------------------------------
 1. Create a free GitHub account at github.com. Make a new PUBLIC repository named "bp-record".
 2. Add file > Upload files: upload index.html, manifest.json, sw.js, icon-192.png, icon-512.png.
    Do NOT upload Code.gs or this README. Click "Commit changes".
 3. Settings > Pages > Source: "Deploy from a branch", branch "main", folder "/ (root)". Save.
 4. After 1-2 minutes the app is live at:  https://<your-github-name>.github.io/bp-record/
    Print that link as a QR code for the clinic wall.
 No patient data is ever stored on GitHub. It only holds the empty app.

-------------------------------------------------------------------
PART 3: EACH PHONE
-------------------------------------------------------------------
 1. Open the app link in Chrome (Android) or Safari (iPhone).
 2. Add it to the home screen:
      Android: Chrome menu (three dots) > "Add to Home screen" or "Install app".
      iPhone:  Share button > "Add to Home Screen".
 3. Open "BP Record" from the home screen. Tap the Sync tab.
 4. Paste the clinic sync link and type the access code:
      Clinic phones and tablets:  STAFF_CODE (S-...)
      Patients' own phones:       WRITE_CODE (W-...)
    Tap Connect. The pill at the top right turns green ("Synced").
 5. Remove the example patients (Patients tab or Sync tab). Examples are never sent to the database.

Everyday use
  - Patients tab: search by name, clinic ID or phone. The "+ New patient" button registers someone.
  - Open a patient > "Record a visit": enter the 3 readings (the app moves to the next box by itself),
    answer 1-2 quick questions, and the app shows what the protocol says. Tap Save visit.
  - Medicines tab on a patient: "Stop, or mark as not working" records why a drug was stopped.
  - Follow-up tab: everyone overdue or due this week, with Call and WhatsApp buttons.
  - No internet? Keep working. The pill shows "2 to send" and the records go automatically later.
  - Clinic phones: Sync tab > "Get updates from the clinic" downloads records entered on other phones.
    "Find a patient on the server" downloads one patient (for example, a patient seen on another phone).

Good to know
  - Records live inside the browser on each phone AND in the Google Sheet. If a phone is lost,
    the data is safe in the Sheet: on a new clinic phone, use "Get updates from the clinic".
  - Always open the app from the same browser on a phone. Clearing that browser's site data
    removes the phone's copy (the Sheet copy stays).
  - If two phones change the same patient, the most recent change wins.
  - The Google Sheet holds health information. Share it only with the people who need it,
    and turn on 2-step verification for the clinic Google account.
