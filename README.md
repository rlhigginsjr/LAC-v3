# MOAA Legislative Action Center

A web-based advocacy tool that makes it simple for MOAA members to contact their elected officials on priority state and federal legislation — directly from their own email client, with no backend infrastructure, no subscriptions, and no technical expertise required by members.

**Live demo:** [rlhigginsjr.github.io/LAC](https://rlhigginsjr.github.io/LAC/)

Developed by the SE Michigan Chapter, MOAA (SEMIMOAA)** and offered freely to all state MOAA Councils.

---

## What It Does

Members complete three steps:

1. **Enter their information** — name, address, city, ZIP, email, and MOAA chapter
2. **Select a bill** — from the council's current priority legislation
3. **Send their message** — a personalized email opens pre-filled in the member's own email client, one button per legislator, ready to review and send

No data is collected. No accounts are required. Nothing is stored.

---

## How It Works (Technical Overview)

- Single self-contained HTML file — no frameworks, no dependencies, no build step
- Bill data and legislator data are configured in two JavaScript arrays in the source
- Email merge fields are replaced at runtime with what the member typed
- Each legislator button generates a `mailto:` link with subject and body pre-populated
- A personalized phone call script is generated automatically at Step 3
- Hosted free on GitHub Pages; embeds on any website with one line of code
- The G-XXXXXXXXXX placeholder in <head> needs to be replaced with a real Google Analystics Measurement ID
- Add mcoc-logo.png to the repo root to display your council logo in the header

---

## Using This Code for Your State Council

The source code is free to download and use. There are two paths:

### Path 1 — Self-Service (Free)

Download `index.html`, adapt it for your state's legislation and legislators, host it on GitHub Pages, and embed it on your council's website. The technical requirements are:

- Ability to edit a text file
- A free GitHub account
- Access to your council's website to add an embed or button link

No step-by-step deployment guide is provided here beyond what is in this README. Councils with a technically capable volunteer should be able to work from the source code directly.

### Path 2 — Guided Deployment ($1,000 contribution)

SEMIMOAA will handle the complete deployment for your council — researching and populating your priority legislation, verifying legislator contact information, applying your council's branding, setting up GitHub Pages hosting, embedding the tool on your website, and conducting a training session so your team can maintain it going forward.

In lieu of a service fee, councils are asked to make a **$1,000 tax-deductible contribution** to the **Southeastern Michigan Chapter, MOAA Scholarship Fund**, which supports educational scholarships for Michigan military families.

To request a guided deployment, contact:

**LCDR Rich Higgins, USN (Ret.)**
President, Michigan Council of Chapters, MOAA
[moaamcoc.com](https://www.moaamcoc.com)

---

## Michigan Deployment — Current Legislation

| Bill | Title | Status |
|------|-------|--------|
| **HB 5280** ★ | Income Tax Act — retirement pay equity for NOAA & USPHS officers | **Primary target** |
| HB 5262 | Uniformity of Service Dates Act — veteran recognition | Active |
| HB 5278 | State Personal Identification Card Act — veteran ID designation | Active |
| HB 5279 | Michigan Vehicle Code — veteran driver's license designation | Active |

Targeting the **Michigan House Committee on Government Operations** — five members, all pre-loaded with verified email addresses and phone numbers.

---

## Maintaining Your Deployment

Once deployed, your council's legislative chair can update bills and legislators without outside help. The key structures to know:

### Bills — `const BILLS = [` in the script section

Each bill is one entry `{ ... }` inside the array. Fields:

| Field | Purpose |
|-------|---------|
| `id` | Unique number — increment for each new bill |
| `code` | Bill number, e.g. `'HB 1234'` |
| `priority` | `true` shows the gold Primary target badge; `false` does not |
| `short` | Brief title shown on the bill card |
| `desc` | One or two sentence plain-English description |
| `url` | Link to the full bill text |
| `subject` | Email subject line |
| `body` | Full email template text — use merge fields below |

**Merge fields available in email body:**

| Field | Replaced with |
|-------|--------------|
| `[FULL_NAME]` | Member's full name |
| `[LAST_NAME]` | Legislator's last name |
| `[CITY]` | Member's city |
| `[ZIP]` | Member's ZIP code |
| `[EMAIL]` | Member's email address |
| `[ADDRESS]` | Member's street address |
| `[CHAPTER]` | Member's MOAA chapter |
| `[SALUTATION]` | Representative or Senator |

**Critical:** Every entry except the last must end with `},` — the final entry ends with `}` before the closing `];`. A missing or extra comma will cause the page to go blank.

### Legislators — `const LEGISLATORS = [` in the script section

Each entry contains:

```javascript
{ 
  name: 'Full Name', 
  title: 'Role · Party · District', 
  salutation: 'Representative',
  email: 'email@house.mi.gov', 
  phone: '(517) 000-0000' 
},
```

Update, add, or remove entries as needed when committee membership or bill targets change.

---

## Resources

- [Live Demo](https://rlhigginsjr.github.io/LAC/)
- [MCOC Legislation Page](https://www.moaamcoc.com/legislation.html)
- [HB 5280 Battle Card (PDF)](https://www.moaamcoc.com/uploads/1/4/8/4/148483887/hb_5280_battle_card_r2.pdf)
- [HB 5280 One-Pager (PDF)](https://www.moaamcoc.com/uploads/1/4/8/4/148483887/michigan_house_bill_5280_-_one-pager.pdf)
- [Michigan Legislature — Bill Search](https://www.legislature.mi.gov)

---

## About

Developed and maintained by the SE Michigan Chapter, MOAA.
Contributions supporting deployment benefit the Southeastern Michigan Chapter, MOAA Scholarship Fund.

© SE Michigan Chapter, MOAA. Free to use and adapt for any MOAA Council or Chapter.
