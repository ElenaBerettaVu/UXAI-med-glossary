---
title: Contribute
nav_order: 3
---

# Contribute to the UXAI Medical Glossary

To update the glossary follow the instructions below 👇 

---

## 1. Editing the glossary (GitHub)

The glossary lives in:

👉 [`glossary.md`](https://github.com/ElenaBerettaVu/UXAI-med-glossary/blob/main/glossary.md)

To propose a change:

1. Create or log into your **GitHub account**.
2. Go to the repository:  
   **https://github.com/elenaberettavu/UXAI-med-glossary**
3. Open `glossary.md`.
4. Click the **pencil icon** (“Edit this file”).
5. Add or modify entries using the same structure:

## Term {#anchor-name}
Definition here.


The {#anchor-name} part defines the URL fragment (e.g., #accuracy, #confidence-interval).
This anchor is used to link directly to that term from other documents.
Scroll down, briefly describe your change, and Commit changes (you can commit directly to main or open a Pull Request if preferred).

If you are not comfortable editing the file directly,
👉 just ask Elena and she will add the term for you 🙂

---

## 2. Updating links in the Key Concepts (Google Docs)

The [Key Concepts](https://docs.google.com/document/d/1qO1dPGkcsYDYMiDQ2dA-dkHJNbJlv2z__QHNHcFdpp8/edit?tab=t.0) Google Doc includes clickable links from terms to this glossary.

If you add new terms here and want them to appear as links inside the Google Doc, the process is more technical:

1. the new term and its glossary URL must be added to a Google Sheet (mapping term → url),
2. a Google Apps Script must be run to automatically update all links in the document,
3. sometimes we need small adjustments for acronyms, plurals, or terms with parentheses.

👉 For this part, please contact Elena directly if you want the Google Docs version to be updated with new terms or links.

She maintains:
1. the central Google Sheet with the mappings term → glossary URL, and
2. the Apps Script code that injects links into the Doc.

---

## 3. Using the glossary in your own Google Docs

You can also use this glossary to automatically link terms inside *your own* Google Docs.
There are two ways to do this:
- **Option A — Easy:** use Elena’s [shared template](https://docs.google.com/document/d/1cgfigM550F9oYdLJc_elNjoMVW1HPecAG1F8re7FLkU/edit?usp=drive_link)
- **Option B — Advanced:** set up everything manually (Apps Script + Sheet)

---

## 3.1 Recommended: using the shared template (easy)

If you have access to:
- the [**Google Sheet**](https://docs.google.com/spreadsheets/d/1Ge7F0QLDx9DMFQEkL8HJz0upJCumXFsx4l0Hpb5FAqA/edit?usp=drive_link) with the mapping `term | url`, and  
- the [**Google Doc template**](https://docs.google.com/document/d/1cgfigM550F9oYdLJc_elNjoMVW1HPecAG1F8re7FLkU/edit?usp=drive_link) containing the Apps Script,

then you can create your own automatically-linked documents in a few steps.

### Important
Even when using the template,  
➡️ **you must open the Apps Script once and authorize it**.  
You do *not* need to edit or understand the code — just authorize it.

---

### How to use the template

1. Create a new Google Doc **inside the shared Drive folder** provided by Elena.  
   Documents created there inherit the necessary access and link to the central Sheet.

2. Open the Doc, then go to:  
   **Extensions → Apps Script**  
   (This is required only the first time.)

3. In the Apps Script window:
   - You do **not** need to change any code.  
   - Simply click **Run** ▷ (play icon) on the function that appears (usually `onOpen` or `applyGlossaryLinks`).

4. Google will ask you to **Authorize** the script:
   - choose your Google account  
   - click **Allow**

5. Close the Apps Script tab and return to the Doc.

6. Now you will see a new menu at the top:  
   **Glossary Links**

7. To apply the links, click:  
   **Glossary Links → Apply glossary links from Sheet**

After that:

- the script reads the term list from the shared Google Sheet,  
- scans your document,  
- and converts matching terms into hyperlinks pointing to the glossary on GitHub Pages.

Example:  
`calibration` →  
`https://elenaberettavu.github.io/UXAI-med-glossary/glossary.html#calibration`

---

If you only need to apply glossary links,  
👉 **this is the easiest and fastest method**.

Ask Elena for access to the template if you do not have it.

---

## 3.2 Advanced: full setup (Apps Script + Sheets)

If you prefer to configure a new Doc **from scratch**, here are the full steps.
You will need:

- a Google Sheet with two columns: `term | url`  
- a Google Doc where the links will be applied  
- permission to run Apps Script

---

### Step 1 — Prepare the Google Sheet

Your Sheet must have the following structure:

| term                | url                                                                 |
|---------------------|---------------------------------------------------------------------|
| calibration         | https://elenaberettavu.github.io/UXAI-med-glossary/glossary.html#calibration |
| confidence interval | https://elenaberettavu.github.io/UXAI-med-glossary/glossary.html#confidence-interval |
| ...                 | ...                                                                 |

To add a new term:

1. Go to the glossary page and click the term.
2. Copy the URL (example:  
   `https://elenaberettavu.github.io/UXAI-med-glossary/glossary.html#calibration`).
3. Add a new row:
   - **term:** exactly as it appears in your Google Doc  
   - **url:** the glossary URL + anchor

You may add multiple variants, for example:

- `CI` → `#confidence-interval`
- `confidence interval` → `#confidence-interval`

---

### Step 2 — Attach Apps Script to your Google Doc

1. Open the Google Doc.
2. Go to **Extensions → Apps Script**.
3. Delete any existing code.
4. Paste the following script:

```javascript
/***********************
 * CONFIGURATION
 ***********************/
const SHEET_ID = 'PASTE_YOUR_SHEET_ID_HERE';
const SHEET_NAME = 'Foglio1'; // Change if needed

function onOpen() {
  DocumentApp.getUi()
    .createMenu('Glossary Links')
    .addItem('Apply glossary links from Sheet', 'applyGlossaryLinks')
    .addToUi();
}

function applyGlossaryLinks() {
  const doc = DocumentApp.getActiveDocument();
  const body = doc.getBody();
  const sheet = SpreadsheetApp.openById(SHEET_ID).getSheetByName(SHEET_NAME);

  const values = sheet.getDataRange().getValues();
  const mappings = [];

  for (let i = 1; i < values.length; i++) {
    const term = (values[i][0] || '').toString().trim();
    const url = (values[i][1] || '').toString().trim();
    if (!term || !url) continue;

    mappings.push({
      termLower: term.toLowerCase(),
      url: url
    });
  }

  linkTermsInElement_(body, mappings);

  DocumentApp.getUi().alert(
    'Done! Applied glossary links for ' + mappings.length + ' terms.'
  );
}

function linkTermsInElement_(element, mappings) {
  if (element.editAsText) {
    linkTermsInText_(element.editAsText(), mappings);
    return;
  }
  const n = element.getNumChildren();
  for (let i = 0; i < n; i++) {
    linkTermsInElement_(element.getChild(i), mappings);
  }
}

function linkTermsInText_(textEl, mappings) {
  const text = textEl.getText();
  const lower = text.toLowerCase();
  mappings.sort((a, b) => b.termLower.length - a.termLower.length);

  mappings.forEach(mapping => {
    let start = 0;
    while (true) {
      const idx = lower.indexOf(mapping.termLower, start);
      if (idx === -1) break;
      const end = idx + mapping.termLower.length - 1;
      try {
        textEl.setLinkUrl(idx, end, mapping.url);
      } catch (e) {}
      start = end + 1;
    }
  });
}
```

5. Replace:
```javascript
const SHEET_ID = 'PASTE_YOUR_SHEET_ID_HERE';
```
with your Sheet ID (from its URL).

6. Adjust SHEET_NAME if necessary.
7. Click Save.

### Step 3 — Authorize and run the script

1. In the Apps Script editor, run applyGlossaryLinks once.
2. Follow the authorization steps (choose your account → Allow).
3. Refresh the Google Doc.
4.Use the menu:
Glossary Links → Apply glossary links from Sheet

All matching terms will become hyperlinks to the glossary.

#### 3.3 Need help?

If something doesn’t work (terms not linking, script errors, overlapping variants):

👉 Ask Elena, she can debug the Sheet, the Script, or help with tricky terms.
