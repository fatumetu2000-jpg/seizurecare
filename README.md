# SeizureCare — Open Edition (v5)

A browser-based clinical dashboard for tracking seizures in epilepsy patients. It combines a live-monitor view, seizure and medication logging, trigger analysis, emergency alerting, and PDF/CSV reports in a single `index.html` file.

> **Status: working prototype / demo.** All patients, seizures, medications and contacts shown are **fictional sample data**. This is not a medical device and must not be used for real clinical decisions or real patient data.

## Why I built it

Epilepsy care depends on good records: when seizures happen, how severe they are, what may have triggered them, and whether medication is taken on time. SeizureCare explores how a simple web tool could help clinicians and caregivers keep that information in one place, and how security needs to be considered from the start when handling health data.

## Features

- **Live monitor (simulated):** an OpenSeizureDetector-inspired panel showing heart rate, SpO₂, power and spectrum metrics, seizure probability, and Accept / Mute / Raise alarm controls. Values are simulated in demo mode.
- **Smartwatch / sensor panel (simulated):** shows device connection states.
- **Waveform simulator:** live EEG / accelerometer / heart-rate / SpO₂ style waveform.
- **Dashboard and patients:** patient list with status (stable, warning, critical), search and filters.
- **Seizure log:** log events with type, severity, duration, triggers and notes; filter by severity.
- **Medications:** track dose, frequency, reminder time and adherence.
- **Triggers and analytics:** trigger frequency, time-of-day patterns and per-patient charts.
- **Emergency page:** SOS button, emergency contacts and an SMS alert log.
- **Reports:** export a PDF report (jsPDF) and CSV files.
- **Cloud sync option:** connect your own Supabase project from the Settings page.
- **Mobile packaging guide:** steps to wrap the app for Android and iOS with Capacitor.

## Tech stack

- HTML, CSS and vanilla JavaScript (single file)
- [jsPDF](https://github.com/parallax/jsPDF) for PDF reports
- [Chart.js](https://www.chartjs.org/) and custom bar charts
- [Supabase JS](https://supabase.com/) for optional cloud storage
- Twilio for SMS alerts (requires a backend relay, see below)
- Capacitor for optional mobile packaging

## Run it

1. Download or clone this repository.
2. Open `index.html` in a browser (or serve the folder with any static file server).
3. Choose a role on the login screen and enter the dashboard.

No build step is needed. Data is kept in your browser's `localStorage`.

## Optional: Supabase cloud sync

1. Create a free project at [supabase.com](https://supabase.com).
2. Copy the **Project URL** and **anon public key** from *Settings → API*.
3. Open *Settings & Cloud* in the app, paste both values and click **Connect**.

Credentials are entered at runtime and are **not** stored in this repository.

## Security notes and limitations

I am studying cybersecurity, so I want to be upfront about what this prototype does **not** yet do:

- **No real authentication.** The login screen is a demo role picker with quick-login buttons. There are no passwords, sessions or server-side access control, so roles do not actually restrict access.
- **Unencrypted local storage.** Data is saved in plain `localStorage` in the browser. Real patient data would need encryption and proper storage.
- **SMS needs a backend.** Twilio credentials must never live in client-side code. A production version should send SMS through a server-side function (for example a Supabase Edge Function) that keeps the secrets.
- **Cloud security not hardened.** A production Supabase setup would need user authentication and row-level security policies.
- **Simulated detection.** The live monitor and device connections are simulated; the app does not perform real seizure detection.
- **Privacy and compliance.** Handling real health data would require compliance work (for example consent, audit logging and applicable data-protection law such as NDPR or GDPR).

### Planned improvements

- Real authentication with role-based access control
- Encrypted storage and Supabase row-level security
- Server-side SMS relay
- Input validation and an audit log
- Tests for the core logging and reporting features

## How this was built

I conceived and directed the project: I defined the requirements (multi-user roles, data visualisations, a waveform simulator, cloud storage, SMS alerting and mobile packaging) and reviewed the result. The code was generated with the help of an AI assistant (Claude) from my direction.

## Inspiration and credits

The live-monitor layout is inspired by [OpenSeizureDetector](https://www.openseizuredetector.org.uk/), an open-source seizure detection project. This project is not affiliated with it.

## Author

**Fatumetu Joy Benjamin** — Computer Science graduate (Federal University Lokoja), cybersecurity focus.
GitHub: [fatumetu2000-jpg](https://github.com/fatumetu2000-jpg)
