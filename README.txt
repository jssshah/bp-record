VITALITY BP RECORD - how to put it on patients' phones
======================================================

WHAT IS IN THIS FOLDER
  index.html     the app (everything in one file)
  manifest.json  lets Android "install" it with the clinic logo
  sw.js          lets it open with no internet after the first visit
  icon-192.png, icon-512.png   app icons

ONE-TIME SETUP (about 20 minutes, free)
  1. Create a free GitHub account (github.com). Make a new PUBLIC repository
     named, for example, "bp-record".
  2. Upload all files in this folder to the repository (Add file > Upload files).
  3. Settings > Pages > Source: "Deploy from a branch", branch "main", folder "/ (root)". Save.
  4. After 1-2 minutes the app is live at:  https://<your-account>.github.io/bp-record/
     (Make a short link or QR code of this address for the clinic wall.)
  No patient data is ever stored on GitHub. The page is only the empty app.

ON EACH PATIENT'S PHONE (Android + Chrome)
  1. Open the link in Chrome.
  2. Chrome menu (three dots) > "Add to Home screen" / "Install app".
  3. Open BP Record from the home screen. Tap "Add real patient", then remove the example.
  4. After every visit: Backup tab > "Save backup to Google Drive" > choose Drive >
     folder "Vitality BP backups" > Save.
  If the phone is lost: install the app on the new phone, Backup tab > Restore,
  pick the latest file from Google Drive.

CLINIC TABLET
  Use the same link. The tablet can hold every patient (switch with the name button
  at the top). "Export visits (CSV)" on the Backup tab gives a spreadsheet for the
  monthly indicators in Protocol C5 (open it in Google Sheets).

IMPORTANT
  - Records are stored inside Chrome on that phone. Clearing Chrome's site data or
    "Clear storage" deletes them. That is why the Drive backup matters.
  - Always use Chrome (not a different browser) to open the app on the same phone.
  - Basic phones without a browser: use the paper BP card instead.
  - Backups contain health information. Keep the Drive folder private, shared only
    with the patient and the clinic account.
