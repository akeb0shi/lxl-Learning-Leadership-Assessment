# Lead By Learning Leadership Assessment | Editing Guide

_This guide explains how to update the survey even for non-technical users with no coding experience._
This guide shows how to:

- Edit Leadership questions  
- Edit Adult Learning Culture questions  
- Add new questions  
- Change which result type (Partner, Learner, Visionary, etc.) a question belongs to  
- Change the PDF images shown at the end  
- Add new partnership sites in the About You section  

---

## CRUCIAL NOTE:

In order to not break the code, be **extremely** careful to only edit text within quotation marks ("). **Never** delete quotation marks or type outside of them

---

## 1. Finding the Editable Question Section

Open **survey_v2.html** and scroll until you see:

```
CONFIGURE SURVEY QUESTIONS HERE
```
_Quick tip: use Command+F (or Ctrl+F on windows) and type "CONFIGURE" to jump straight there_

This section contains everything you will edit.

---

## 2. Editing Leadership Questions

Leadership questions are stored here:

```javascript
const leadershipQuestions = [
    { text: "I seek input from staff before making important decisions.", type: "Partner" },
    { text: "I listen and acknowledge perspectives when concerns are shared.", type: "Partner" },
];
```


### To edit a question  
Change the text inside quotes after `text:`.

### To add a question  
Copy one line and paste underneath:

```javascript
{ text: "Your new leadership question here", type: "Learner" },
```

### Valid Leadership Types  
Use one of these exactly as written:

- `"Partner"`
- `"Learner"`
- `"Visionary"`

The type determines which PDF result the user receives.

---

## 3. Editing Culture Questions

Culture questions appear below leadership:

```javascript
const cultureQuestions = [
    { text: "Adults seek real-time local data...", type: "Equity" },
    { text: "Adults help build a culture of trust...", type: "Equity" },
];
```

### Valid Culture Types  
Use one of these:

- `"Equity"`
- `"PublicLearning"`
- `"SharedGoals"`

### Adding or editing works the same as leadership

```javascript
{ text: "Your new culture question", type: "SharedGoals" },
```

---

## 4. Changing Which Image Appears at the End

_Please note that the code refers to the files as PDFs, but the code is optimized to take image files such as .png, .jpeg, etc. When in doubt, use the link to an image_

Scroll to the `finishSurvey()` function.

_Quick tip: use Command+F (or Ctrl+F on windows) and type "REPLACE" to jump straight there_

You will see this structure for leadership:

```javascript
if (winningType === "Partner")
    pdfURL = "LINK_TO_PARTNER_PDF_OR_IMAGE";
if (winningType === "Learner")
    pdfURL = "LINK_TO_LEARNER_PDF_OR_IMAGE";
if (winningType === "Visionary")
    pdfURL = "LINK_TO_VISIONARY_PDF_OR_IMAGE";
```

And for culture:

```javascript
if (cultureType === "Equity")
    pdfURL = "LINK_TO_EQUITY_PDF_OR_IMAGE";
```

### To update images  
Replace ONLY the link:

```javascript
pdfURL = "https://your-new-link-here.pdf";
```

### Requirements for links  
- Must be publicly accessible  
- GitHub Pages, Google Drive (with public access), or any direct URL works  

---

## 5. Adding New Partnership Options (About You section)

Scroll to Line 151 where it says ✅✅✅ ADD NEW PARTNERSHIPS HERE ✅✅✅ 
_Quick tip: use Command+F (or Ctrl+F on windows) and type "ADD NEW" to jump straight there_


You will see:

```html
<option value="21CSLA Teacher Leader Community of Practice">
    21CSLA Teacher Leader Community of Practice
</option>
```

### To add a new partnership  
Paste THIS new line:

```html
<option value="New Partnership Name">New Partnership Name</option>
```

---

## 6. How Scoring Works

Each answer gives a numerical value:

| Response | Score |
|---------|-------|
| Not at all like me | 1 |
| Somewhat like me | 2 |
| A lot like me | 3 |
| Exactly like me | 4 |
| Don’t know / Unsure | 0 |

The code totals scores separately for each **type**.

Example:

- Partner total score  
- Learner total score  
- Visionary total score  

Whichever type is highest becomes the "winning" category.

A similar process happens for culture:

- Equity  
- PublicLearning  
- SharedGoals  


---

## 7. Editing the Downloaded Word Document Output

Search for this function:

```javascript
downloadResponseDoc()
```

Inside, you can edit:

- Header title text  
- The layout of answers  
- The About You section  

You do **not** need to touch anything else.

---

## 8. Rules to Avoid Breaking the Code

- Always keep `{}`, `[]`, commas, and quotation marks.  
- Every question MUST follow this pattern:

```javascript
{ text: "Question goes here", type: "TypeName" },
```

- Do NOT remove the comma at the end of each line (except the last one).
- The last question **never** has a comma at the end of the line
- Type names must match exactly and are case sensitive. 

---

## 9. If You Need Help

For help adding new result types, changing scoring rules, or redesigning the page, contact me (Dylan Kao) on teams or via email at kao.d@northeastern.edu.  
This file is designed such that meaningful updates can be made without any coding background.

---

## End of README
