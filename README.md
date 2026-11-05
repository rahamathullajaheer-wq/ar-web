# ARH AGENCY — Futuristic Recruitment & Talent Portal

A modern, high-performance recruitment web application for **ARH AGENCY**, engineered with React, Vite, Three.js, and Google Apps Script / Google Sheets.

---

## 🚀 Live Features & Specifications

### 1. Futuristic Cyber Aesthetic & Design
- **Theme**: Premium dark cyber theme (`#05050b`) with electric cyan (`#38bdf8`) and neon purple (`#a855f7`) glow accents.
- **Typography**: Clean hierarchy with Google Fonts (*Space Grotesk*, *Outfit*, and *JetBrains Mono*).
- **Interactive 3D Core**: Custom Three.js interactive wireframe torus knot, glowing cyber core, and particle swarm with mouse parallax tracking.
- **Laptop & 8GB RAM Optimization**:
  - Device pixel ratio capped at 1.5 to prevent GPU strain.
  - Automatic `IntersectionObserver` pause: when the user scrolls away from the Hero section, the 3D animation loop pauses to save RAM, CPU, and battery.
  - Geometry and buffer disposals on unmount to eliminate memory leaks.
- **Full Responsiveness**: Optimized for high-resolution desktop monitors, tablets, and Android smartphones with an interactive mobile drawer menu.

### 2. Website Sections
1. **Navigation Bar**: Glowing brand mark, active recruitment badge, smooth scroll links, and "Apply Now" button.
2. **Hero Section**: Heading *"Build Your Career with ARH AGENCY"*, 3D Three.js particle canvas, trust metrics, and action CTAs.
3. **About Us**: Agency vision, culture manifesto, and live stats (50+ Team Members, 250+ Deliverables, 99.4% Satisfaction).
4. **Our Services**: Interactive cards for all 5 core agency domains:
   - *Graphic Designing*
   - *Video Editing*
   - *Animation & Motion Graphics*
   - *Content Writing*
   - *Web Development*
   *(Clicking any domain automatically pre-selects that skill in the application form).*
5. **Why Join Us**: Benefits, remote flexibility, tech equipment stipends, meritocracy, and student/fresher welcome banner.
6. **Career Opportunities**: Filterable job board with role requirements, stipends, and 1-click *"Apply For This Role"* routing.
7. **Job Application Form**: Glassmorphism application card connected to Google Sheets:
   - Full Name
   - Age (16-99 validation)
   - Mobile Number (7-15 digits format)
   - Email Address (RFC email validation)
   - College Course
   - College Name
   - Skills (multiple selection pills)
   - Additional Information / Portfolio link
   - Terms and privacy consent checkbox
8. **Digital Receipt Modal**: Displays verified confirmation with unique Application ID (e.g. `ARH-2026-X8K9L2`), one-click Copy ID, and celebration confetti.
9. **Frequently Asked Questions**: Expandable accordion answering common applicant questions.
10. **Contact Section**: Talent desk email, phone, hours, and quick message form.
11. **Footer**: Social links, legal terms, operational system status indicator, and Back to Top button.

---

## 🛠️ Step-by-Step Guide for Beginners

### STEP 1: How to Run the Website Locally

1. Open PowerShell or Command Prompt in this project folder:
   ```bash
   cd "C:\Users\ELCOT\Documents\New folder (3)"
   ```

2. Start the Vite development server:
   ```bash
   npm run dev
   ```
   *(If your Windows PowerShell gives an execution policy error, run: `cmd /c npm run dev`)*

3. Open your browser and navigate to:
   ```
   http://localhost:3000
   ```

---

### STEP 2: How to Connect Google Sheets (Google Apps Script)

Your current Google Apps Script URL is pre-configured in `.env`:
```env
VITE_GOOGLE_SCRIPT_URL=https://script.google.com/macros/s/AKfycby0qdEBg3uis5gNZyhUXltBzIRbTBU5qwV58dll_LlI5WgwRg78Hj2Ov2K5biVQf4jx/exec
```

> [!IMPORTANT]
> **Why your current script showed an error:**
> When tested, your deployed script returned: `Illegal spreadsheet id: PASTE_YOUR_SHEET_ID_HERE`.
> This means your Google Apps Script is running live, but it needs your real Google Sheet connected to it!

#### Follow these 2 easy minutes to connect your Google Sheet:

1. **Create your Google Sheet**:
   - Go to [https://sheets.new](https://sheets.new) in your web browser.
   - Name the spreadsheet: **`ARH AGENCY - Applications`**.
   - Copy the Sheet ID from the browser address bar:
     - URL looks like: `https://docs.google.com/spreadsheets/d/`**`1xYzAbc...12345`**`/edit`
     - The bold part between `/d/` and `/edit` is your **Sheet ID**.

2. **Open Apps Script from the Sheet**:
   - In your Google Sheet top menu, click **Extensions** > **Apps Script**.
   - Delete any placeholder code.
   - Open the file [`google-apps-script/Code.gs`](./google-apps-script/Code.gs) from this project, copy everything, and paste it into the Apps Script editor.
   - Line 24: Paste your Sheet ID between the quotes (or leave as `''` if bound directly to the sheet).
   - Click the **Save** (💾) icon.

3. **Deploy as a Web App**:
   - Click the blue **Deploy** button (top right) -> **New deployment**.
   - Click the gear icon next to "Select type" -> choose **Web app**.
   - Set:
     - **Execute as**: `Me`
     - **Who has access**: `Anyone` *(Crucial: must be Anyone so applicants can submit)*
   - Click **Deploy**.
   - Click **Authorize access**, choose your Google account, click **Advanced** -> **Go to (unsafe)** -> **Allow**.
   - Copy the **Web App URL** Google gives you.

4. **Update `.env`**:
   - Open `.env` in this project folder and replace the URL:
     ```env
     VITE_GOOGLE_SCRIPT_URL=https://script.google.com/macros/s/YOUR_NEW_DEPLOYMENT_ID/exec
     ```
   - Restart `npm run dev` so Vite loads the new URL.

---

### STEP 3: How to Test the Application Form

1. In the website on `localhost:3000`, scroll to the **Job Application Portal** section (or click "Apply Now").
2. Fill out sample test data:
   - Full Name: `Jane Doe`
   - Age: `22`
   - Mobile: `9876543210`
   - Email: `jane.doe@example.com`
   - College Course: `B.Tech Computer Science`
   - College Name: `MIT`
   - Skills: Click `Graphic Designing` and `Web Development`
   - Consent: Check the agreement box
3. Click **Submit Official Application**.
4. You will see:
   - A loading indicator while the data is transmitted.
   - A glowing **Official Confirmation Modal** with a unique Application ID (e.g., `ARH-2026-XXXXX`).
   - Confetti celebrating the submission.
5. Open your Google Sheet — you will see a newly appended row with all candidate details!

---

### STEP 4: How to Publish the Website Online for Free

You can deploy the site for free using either **Vercel** or **Netlify**. Both are 100% free and provide a public `.vercel.app` or `.netlify.app` URL, with support for custom domains (e.g. `arh.agency`).

#### Option A: Deploy via Netlify (Drag & Drop — Easiest, 60 seconds)
1. In your terminal, build the production files:
   ```bash
   cmd /c npm run build
   ```
   This generates a folder named `dist`.
2. Go to [https://app.netlify.com/drop](https://app.netlify.com/drop).
3. Drag and drop the `dist` folder into the Netlify drop zone.
4. Netlify will immediately give you a live public URL (e.g. `https://arh-agency.netlify.app`).

#### Option B: Deploy via Vercel (CLI)
1. Run in PowerShell:
   ```bash
   cmd /c npx vercel
   ```
2. Follow the 3 prompts (login with GitHub/Email, accept default project settings).
3. Vercel will deploy and output your live production URL!

---

## 📁 Project Structure

```
├── .env                         # Google Apps Script Endpoint URL
├── .env.example                 # Environment template
├── netlify.toml                 # Netlify routing configuration
├── vercel.json                  # Vercel single-page app configuration
├── package.json                 # Project dependencies & scripts
├── vite.config.js               # Vite config with Three.js manual chunking
├── index.html                   # HTML entry point with Space Grotesk fonts
├── public/
│   └── favicon.svg              # Futuristic ARH Agency logo favicon
├── google-apps-script/
│   ├── Code.gs                  # Production Google Apps Script backend
│   └── README.md                # Dedicated Google Apps Script setup guide
└── src/
    ├── main.jsx                 # React root renderer
    ├── App.jsx                  # Main application orchestrator
    ├── index.css                # CSS import root
    ├── components/
    │   ├── Navbar.jsx           # Fixed responsive navigation bar
    │   ├── Hero3D.jsx           # Three.js 60fps interactive 3D canvas
    │   ├── HeroSection.jsx      # Hero section with headline and CTAs
    │   ├── AboutSection.jsx     # Agency vision and culture manifesto
    │   ├── ServicesSection.jsx  # 5 agency services cards
    │   ├── WhyJoinSection.jsx   # Perks and student welcome banner
    │   ├── CareersSection.jsx   # Filterable career openings
    │   ├── ApplicationForm.jsx  # Google Sheets connected application form
    │   ├── SuccessModal.jsx     # Digital receipt with Application ID & confetti
    │   ├── FaqSection.jsx       # Interactive accordion FAQ
    │   ├── ContactSection.jsx   # Contact coordinates & quick messaging
    │   └── Footer.jsx           # Footer branding & social links
    ├── data/
    │   ├── servicesData.js      # The 5 services metadata
    │   ├── careersData.js       # Job listings & requirements
    │   ├── perksData.js         # Agency perks & stats
    │   └── faqData.js           # FAQ items
    ├── services/
    │   └── submissionService.js # Validation, ID generator, & API client
    └── styles/
        ├── variables.css        # Design tokens & color variables
        ├── global.css           # Typography, buttons, & keyframes
        └── components.css       # Component-specific styles
```

---

## 🛡️ Quality & Security
- **Anti-Duplicate Submission**: Local duplicate detection and Google Apps Script concurrency locking (`LockService.getScriptLock()`) prevent duplicate rows.
- **Client & Server Validation**: Both React frontend and Google Apps Script validate input constraints.
- **Optimized for 8GB RAM Laptops**: Three.js rendering pauses when scrolled out of view and caps pixel ratio to 1.5.
