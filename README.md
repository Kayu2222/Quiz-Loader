# 📚 Quiz Loader

A lightweight, mobile-friendly quiz app hosted on GitHub Pages.  
No backend, no build tools — just HTML + JSON files.

🔗 **Live site:** https://kayu2222.github.io/Quiz-Loader/

---

## ✨ Features

- 📂 Swap question banks from a dropdown — no code changes needed
- 🔀 Shuffle questions every session
- ⚑ Flag questions for focused review
- 👆 Click-to-reveal answers with explanations
- 🗂 Filter by week / topic tab
- 📱 Fully mobile-friendly

---

## 📁 File Structure

```
cloudSecurityQuiz/
├── index.html              ← Quiz UI (edit only to add new subject options)
└── questions/
    ├── cloud_security.json ← Cloud Security W1–W7 (192 questions)
    └── your_new_subject.json  ← Add new subjects here
```

---

## ➕ How to Add a New Question Bank

### Step 1 — Create the JSON file

Create a new file under `questions/` with this format:

```json
{
  "title": "Your Subject Name",
  "subject": "your_subject",
  "weeks": ["W1", "W2", "W3"],
  "questions": [
    {
      "id": 1,
      "week": 1,
      "q": "Question text here?",
      "opts": ["A. Option one", "B. Option two", "C. Option three", "D. Option four"],
      "ans": "A",
      "exp": "Optional explanation shown after revealing the answer."
    },
    {
      "id": 2,
      "week": 1,
      "q": "Another question?",
      "opts": ["A. ...", "B. ...", "C. ...", "D. ..."],
      "ans": "C",
      "exp": ""
    }
  ]
}
```

**Field reference:**

| Field | Required | Description |
|-------|----------|-------------|
| `title` | ✅ | Displayed in the header when this bank is loaded |
| `subject` | ✅ | Short identifier (no spaces) |
| `weeks` | ✅ | Array of tab labels — use `[]` if no week grouping needed |
| `id` | ✅ | Unique integer per question |
| `week` | ✅ | Integer matching one of the week labels (use `0` if none) |
| `q` | ✅ | Question text |
| `opts` | ✅ | Exactly 4 options, each starting with `A.` / `B.` / `C.` / `D.` |
| `ans` | ✅ | Correct answer letter: `"A"`, `"B"`, `"C"`, or `"D"` |
| `exp` | ✅ | Explanation text — use `""` to leave blank |

---

### Step 2 — Register it in `index.html`

Open `index.html` and find this block (around line 110):

```html
<select id="subjectSel" onchange="loadSubject(this.value)">
  <option value="">── Select the Script ──</option>
  <option value="questions/cloud_security.json">Cloud Security（W1–W7）</option>
  <!-- new questions code ↓ -->
</select>
```

Add one line for your new file:

```html
<option value="questions/your_new_subject.json">Your Subject Name</option>
```

That's it — no other changes needed.

---

## 🗂 Question Banks

| File | Subject | Questions |
|------|---------|-----------|
| `cloud_security.json` | Cloud Security W1–W7 | 192 |

---

## 🛠 Tech Stack

| Layer | Technology |
|-------|-----------|
| Hosting | GitHub Pages (free) |
| UI | Vanilla HTML / CSS / JS |
| Data | JSON files in `questions/` |
| Fonts | Google Fonts — DM Sans, DM Serif Display |

No frameworks, no npm, no build step.
