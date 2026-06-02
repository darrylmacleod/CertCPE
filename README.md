# CertCPE - CPE & Certification Tracker

A self-contained, single-file HTML app for tracking Continuing Professional Education (CPE) activities and cybersecurity certification renewals. No installation, no server, no account required — open in any browser and start tracking.

## Features

- **CPE Activity log** with file evidence attachments stored in-browser
- **Certification registry** with renewal cycle and fee tracking
- **Activity → Certification mapping** with submission and evidence status
- **Dashboard** with per-certification progress, pace gap analysis, and deadline alerts
- Data persists in browser `localStorage` — no data leaves your machine

## Getting Started

1. Download `certcpe.html`
2. Open it in any modern browser (Chrome, Firefox, Edge, Safari)
3. Update the pre-loaded certifications with your actual renewal dates and IDs
4. Add CPE activities as you complete them
5. Map activities to certifications to track your progress

No internet connection required after the file is downloaded.

## The Four Sections

### Dashboard
An at-a-glance view for every certification you hold:
- Earned and submitted hours progress bars
- **Pace gap** — how many hours behind (or ahead) you are given time elapsed in the cycle
- Remaining hours to complete the cycle
- Alerts for renewal fees and certification expiry within 60–90 days
- Missing evidence warnings

### CPE Activities
Log every CPE event with:

| Field | Description |
|---|---|
| Date | When the activity occurred |
| Title | Name of the course, webinar, conference, etc. |
| Provider | Issuing organisation (SANS, ISACA, Coursera, etc.) |
| Category | Training, Webinar, Conference, Self-Study, Research, Volunteer, Exam, Work Experience |
| Hours | CPE hours earned |
| Description | Brief summary of content |
| Evidence File | Attach a PDF, image, or document directly in the app |
| URL | Link to the activity or certificate of completion |
| Notes | Any additional context |

Activities are searchable and filterable by category.

### Certifications
Track renewal requirements for each certification:

| Field | Description |
|---|---|
| Certification | Name (e.g. CISSP) |
| Issuing Body | (e.g. ISC², ISACA, CompTIA, EC-Council) |
| Cycle Start / End | Your personal renewal cycle dates |
| Annual Minimum | Minimum hours required each calendar year |
| Cycle Total | Total hours required over the full cycle |
| Fee Due Date | When your maintenance fee is next due |
| Member / Cert ID | Your certification or member ID for reference |

Pre-loaded with: **CISSP, CISM, CISA, CRISC**

### Mapping
Links individual activities to certifications and tracks submission:

| Field | Description |
|---|---|
| Activity | The CPE activity being applied |
| Certification | The certification it applies toward |
| Eligible Hours | Hours applicable to this certification (may differ from total activity hours) |
| Submitted | Whether hours have been submitted to the certifying body |
| Submission Date | Date submitted |
| Evidence Status | Not Required / Pending / Attached / Submitted / Missing |

Filterable by certification and submission status.

## Evidence Files

Evidence files (certificates of completion, screenshots, receipts) are attached at the activity level and stored as base64 in browser `localStorage`.

- Supported types: PDF, PNG, JPG, GIF, DOCX, TXT, ZIP
- PDF and image files can be previewed directly in the app
- All file types can be downloaded via the evidence viewer
- **Storage limit:** browsers typically allow 5–10 MB of localStorage per origin. For large files, use the URL field to link to a cloud-stored copy (Google Drive, OneDrive, SharePoint, etc.) instead

## Data Storage

All data is stored in your browser's `localStorage` under the key `cpe_tracker_v2`. This means:

- Data is private and stays on your device
- Data persists between browser sessions
- Clearing browser site data will erase your records — **export or back up regularly**
- Data is tied to the browser and device you use; it does not sync across devices

### Backing Up Your Data

To back up or transfer data, open the browser developer console (`F12` → Console) and run:

```js
copy(localStorage.getItem('cpe_tracker_v2'))
```

Paste the output into a `.json` file. To restore, run:

```js
localStorage.setItem('cpe_tracker_v2', '<paste JSON here>')
```

Then refresh the page.

## Pre-loaded Certifications Reference

| Cert | Body | Cycle (yrs) | Total CPE | Annual Min |
|---|---|---|---|---|
| CISSP | ISC² | 3 | 120 | 40 |
| CISM | ISACA | 3 | 120 | 20 |
| CISA | ISACA | 3 | 120 | 20 |
| CRISC | ISACA | 3 | 120 | 20 |

Update cycle start/end dates to match your actual certification dates before use.

## Browser Compatibility

Tested in Chrome, Firefox, Edge, and Safari. Requires a browser released after 2018. JavaScript must be enabled.
