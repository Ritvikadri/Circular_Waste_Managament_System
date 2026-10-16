# Circular_Waste_Managament_System
♻️ Circular Smart Recycling is an AI-powered waste management app built with Python and Streamlit. It classifies waste into Wet, Dry, and E-waste, monitors bin capacity, tracks disposal history, schedules maintenance, and uses Google Gemini AI to guide users toward responsible recycling.

# ♻️ Circular Smart Recycling

🚀 LIVE DEPLOYMENT
**THIS PROJECT IS DEPLOYED ON STREAMLIT: https://circularai.streamlit.app/**
Open the live app here: https://circularai.streamlit.app/


## A simple guide for everyday users

Circular Smart Recycling is a web app for managing waste bins in a campus, college, office, or other building. It helps people record waste disposals, check bin capacity, review disposal history, schedule pickups or maintenance, and use AI tools for waste-sorting guidance and reports.

You do not need to be a programmer to use the app. The first part of this guide explains how to start it; the next part explains what each screen does.

---

## 1. What you need

- A computer with Python installed.
- The project’s `app.py` file and any other files supplied with it.
- An internet connection to install software packages and use AI features.
- A Google Gemini API key for AI features.
- A webcam if you want to use live camera sorting.

The app may store records in an Excel workbook. Keep any workbook supplied with your project in the same folder as `app.py`, and back it up regularly. Do not rename or edit its sheets or columns unless you know how the app expects them to be arranged.

## 2. Start the app

### Windows

1. Put `app.py` and the other project files in one folder.
2. Open that folder in File Explorer.
3. Click the address bar, type `cmd`, and press **Enter**.
4. Create a separate Python environment (recommended):

   ```bash
   python -m venv .venv
   ```

5. Activate it:

   ```bash
   .venv\Scripts\activate
   ```

6. Install the packages used by the app:

   ```bash
   python -m pip install --upgrade pip
   pip install streamlit pandas altair streamlit-webrtc google-genai openpyxl
   ```

7. Start the app:

   ```bash
   streamlit run app.py
   ```

8. Look for the local web address printed in the terminal. It is usually `http://localhost:8501`. Open that address in your browser.

Keep the terminal window open while using the app. Closing it stops the app.

### macOS or Linux

Open a terminal in the project folder and run:

```bash
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
pip install streamlit pandas altair streamlit-webrtc google-genai openpyxl
streamlit run app.py
```

If the project includes a `requirements.txt` file, you can install its listed packages instead:

```bash
pip install -r requirements.txt
```

## 3. Set up AI features (Gemini)

AI features—such as identifying an item through the camera, asking the AI advisor questions, analysing disposal trends, or generating a weekly report—may require a Google Gemini API key.

1. Open Google AI Studio: <https://aistudio.google.com/apikey>
2. Create or copy your API key.
3. In the project folder, create a folder named `.streamlit` if it does not already exist.
4. Inside it, create a file named `secrets.toml`.
5. Add this line:

   ```toml
   GEMINI_API_KEY = "paste-your-key-here"
   ```

6. Replace `paste-your-key-here` with your actual key.
7. Stop and restart Streamlit so it loads the setting again.

**Keep your API key private.** Do not post it in screenshots, source-code repositories, or support messages. If your project already has a different documented way to configure the key, follow that project configuration.

Some non-AI parts of the app may still work if AI is not configured.

---

## 4. Using the app

Use the navigation menu on the left side of the screen to open the different sections. The exact controls may vary slightly by version.

### Overview

A quick summary of the bin network and recorded activity. Use it to check the overall status before managing individual bins.

### Live sorting

Use this section to identify and record an item.

**Using the camera**
1. Select the appropriate camera/device if prompted.
2. Allow camera access in your browser.
3. Start the camera.
4. If available, enable automatic identification to let the app analyse items periodically.
5. Review the suggested item name, category, and guidance before saving.

**Using manual entry**
1. Enter the item's name.
2. Choose its waste category.
3. Enter the estimated volume in litres.
4. Select the bin you intend to use.
5. Click **Save disposal + update digital twin**.

The common categories are:

- **Wet:** food scraps and other suitable organic/compostable waste.
- **Dry:** dry recyclables and other waste accepted by your local dry-waste rules.
- **E-waste:** electronic items that need a dedicated electronic-waste collection stream.

#### Important bin rules

- **Use the right category.** If the item is Wet, Dry, or E-waste, the selected bin must match that category. If it does not match, the app should display a red warning telling you to add the item to the right bin. The item should not be recorded in the wrong bin.
- **Check capacity.** The item must fit in the bin's remaining capacity. If it will exceed capacity, do not force the disposal; choose an appropriate bin with enough space.
- **Read the result message.** A success message means the app accepted the record. A red warning means you need to correct the category or capacity problem.
- **Hazardous items need care.** Follow your organisation's safety procedure and local regulations. Do not rely on an AI label alone to decide how to handle a hazardous item.

The volume is an estimate. AI identification and material guidance can be wrong, so check the result before acting.

### Bin network

View the bins registered in the system, including their categories, locations, and fill levels. If the app provides controls to add or edit bins, enter the bin name, floor/zone, type, and capacity carefully. Consistent floor and zone naming makes it easier to identify a bin's location.

### Monitor & trends

Use this page to review waste patterns, bin status, and planned operations. **AI trend analysis** uses the available disposal records and requires AI to be configured and working. If it fails, check the terminal error and AI setup; generating a report with no usable data may not be possible.

### Pickup calendar

View or schedule collection, cleaning, or maintenance tasks. Check the date, time, location, and task details before saving.

### Disposal log

Review previously recorded disposals. Search and export options may be available for reporting. Be careful with **Clear History** or other delete/clear actions: they can remove records you may need later. Back up your data before clearing history.

### AI advisor and weekly AI report

Use the advisor to ask questions about waste sorting, reuse, and waste reduction. Use **Generate Weekly AI Report** to request a summary of the available records, if that control is present in your version.

AI-generated advice and reports are suggestions, not official audits. Check them before using them for important decisions.

---

## 5. Protect your data

- Back up the app's Excel workbook or other data file regularly.
- Keep a copy before clearing history, editing data, or updating the code.
- Do not manually change workbook sheet names or column headings unless you know the app supports it.
- Keep `app.py`, its supporting files, and the data workbook together as required by your project.
- An exported CSV is useful for analysis, but it is not a substitute for a full data backup.

## 6. Common problems

### The app does not open

- Confirm the terminal is in the folder containing `app.py`.
- Check that the Python environment is activated.
- Install the required packages.
- Read the terminal output for the first error message.

If the `streamlit` command is not found, try:

```bash
python -m streamlit run app.py
```

### AI features fail

1. Check the internet connection.
2. Confirm the Gemini API key is configured correctly.
3. Confirm the `google-genai` package is installed:

   ```bash
   pip install google-genai
   ```

4. Restart Streamlit.
5. If the error remains, copy the full terminal traceback for troubleshooting, but remove API keys and other secrets first.

### The camera is blank

- Allow camera permission in the browser.
- Select the correct camera if more than one is available.
- Close other apps that might be using the webcam.
- Try refreshing the page and restarting Streamlit.

### The app says the item belongs in another bin

Choose a bin whose category matches the waste item. Do not try to save the item into a bin with the wrong category.

### The app says there is not enough capacity

The estimated volume is larger than the bin's remaining space. Choose a suitable bin with enough capacity, or have the bin emptied according to your organisation's procedure.

### The data looks old or unexpected

Check that you started the intended copy of the project and that it is using the correct data workbook. Back up the workbook before attempting repairs.

---

## 7. Stop the app

Return to the terminal window running Streamlit and press **Ctrl+C**.

## 8. Typical project folder

Your project may look something like this:

```text
circular-smart-recycling/
├── app.py
├── requirements.txt        # if supplied
├── circular.xlsx           # if supplied/used by your version
└── .streamlit/
    └── secrets.toml        # private; contains your API key
```

The exact files can differ by version. Do not delete supporting files just because they are not shown in this example.

## 9. Safety and privacy

- Never publish your Gemini API key or `secrets.toml`.
- Avoid entering personal or confidential information into disposal records or AI prompts.
- Verify AI sorting and hazard suggestions.
- Follow local recycling rules and your organisation's procedures for batteries, electronics, chemicals, sharp objects, and other potentially hazardous waste.
- Keep backups of records that need to be retained.

---

**Need help?** Share the error text and relevant terminal traceback, but remove API keys, passwords, tokens, and private data first.
