# Hikma Assist

A mobile-first **AI clinical assistant app for doctors**. It lets a physician manage
patients, view their medical records/reports, and run an AI-powered consultation chat
(symptom analysis, differentials, drug interactions, dosing, etc.).

> **Status:** High-fidelity front-end prototype / UI mock. There is **no backend** —
> all data is hardcoded dummy data in JavaScript, and actions like "saving", "uploading",
> and AI replies are simulated client-side.

---

## Tech & structure

- **Single self-contained file:** `index.html` (~4,000 lines). All HTML, CSS, and
  JavaScript live inline in this one file. No build step, no frameworks, no
  dependencies (only the Google Fonts "Inter").
- **Assets:** `logo.png` and `dummy_report.jpeg` (placeholder image used for report attachments).
- **Architecture pattern:** a fake "phone frame" containing multiple `.screen` divs;
  only one has the `.active` class at a time. Navigation is JS-driven via a
  `showScreen('id')` function that toggles which screen is visible. Bottom-tab
  navigation switches between the three main tabs.
- **Theming:** CSS custom properties (variables) in `:root` with a `body.dark` override.
  The app uses a **muted/dark emerald-green clinical theme** (dark green is the brand
  color; an earlier gold/yellow accent was deliberately removed in favor of green).

---

## Main screens / flows

1. **Splash → Login / Signup** — auth mock
2. **Patients tab** — searchable list of patient cards (name + age + MRN); long-press to
   edit, tap to open
3. **AI chat tab** — a ChatGPT-style general clinical assistant ("Ask anything clinical")
4. **Profile tab** — doctor profile (Dr. Sarah Mitchell), settings, dark-mode toggle
5. **Patient detail** — hero with avatar, badges, stats (Last Visit, Visits), Clinical
   Notes (including current medications), a **Reports section** (7 folders), and a
   Recommendation / consultation-history timeline
6. **Report gallery + lightbox** — tapping a report folder opens a grid of attachment
   images (uses `dummy_report.jpeg`); attachments can be uploaded or deleted
7. **Patient AI chat** — per-patient consultation chat with structured AI responses
8. **Add patient** — form with DOB→age auto-fill, gender, blood type, previous
   conditions, and medical history inside a collapsible "Complete Patient Details" tile

### Report folders (7)

`Lab Recommendation`, `ECG and Echo Recommendation`, `Radiology Recommendation`,
`Culture Recommendation`, `Biopsy Recommendation`, `Medications Recommendation`, and
`Notes` (full-width tile). Each tile shows a report count and an **Upload** text button.

---

## Key data

- **`patients`** array — Ahmed Al-Rashid, Fatima Hassan, Raj Patel, Maria Santos — with
  fields like `name, age, gender, mrn, diagnosis, notes, meds, badge1/badge2, visits`.
- **`reportFolders`** array — defines the 7 report categories and their dummy reports
  (each report has `title, meta, date`).

---

## Conventions

- Pure vanilla JS with `onclick` handlers in markup.
- Render functions (e.g. `renderPatients()`, `renderDetailFolders()`) rebuild HTML via
  template strings.
- Mobile UI patterns: safe-area insets, bottom nav, action sheets, modals, lightbox.

> **For anyone making changes:** everything is in `index.html` — edit the inline
> `<style>` for design and the inline `<script>` for behavior.
