# IDGP × Sorbonne — International Certificate Landing Page

Executive landing page for the **International Certificate in Project Management and Organizational Performance**, a partnership between **IDGP Academy** and **Sorbonne Business School (IAE Paris)**.

---

## 📁 Project Structure

```
idgp-sorbonne/
├── index.html        ← Landing page (program overview)
├── admission.html    ← Enrollment form (9-section multi-step)
└── README.md         ← This file
```

---

## 🚀 Deploy on GitHub Pages (step-by-step)

### 1. Create a GitHub repository

1. Go to [github.com](https://github.com) and sign in
2. Click **New repository**
3. Name it: `idgp-sorbonne` (or any name you prefer)
4. Set visibility to **Public** (required for free GitHub Pages)
5. Click **Create repository**

### 2. Upload the files

**Option A — via GitHub web interface (simplest):**
1. In the new repository, click **Add file → Upload files**
2. Drag and drop `index.html`, `admission.html`, and `README.md`
3. Scroll down and click **Commit changes**

**Option B — via Git (terminal):**
```bash
git clone https://github.com/YOUR_USERNAME/idgp-sorbonne.git
cd idgp-sorbonne
# Copy your files here, then:
git add .
git commit -m "Initial deploy: IDGP Sorbonne landing page"
git push origin main
```

### 3. Enable GitHub Pages

1. In the repository, go to **Settings** (top menu)
2. Scroll down to **Pages** (left sidebar)
3. Under **Source**, select **Deploy from a branch**
4. Branch: **main** / Folder: **/ (root)**
5. Click **Save**

### 4. Access your live site

After 1–2 minutes, your site will be live at:
```
https://YOUR_USERNAME.github.io/idgp-sorbonne/
```

- **Landing page:** `https://YOUR_USERNAME.github.io/idgp-sorbonne/index.html`
- **Enrollment form:** `https://YOUR_USERNAME.github.io/idgp-sorbonne/admission.html`

---

## 📧 Enabling Automatic Email (EmailJS)

The form currently opens the user's email client as a fallback. To enable **fully automatic** email sending to `albergarias@idgp.global`:

### Setup EmailJS (free tier supports 200 emails/month)

1. Create a free account at [emailjs.com](https://www.emailjs.com)
2. Go to **Email Services** → Add New Service (connect your Gmail or SMTP)
3. Note your **Service ID** (e.g., `service_abc123`)
4. Go to **Email Templates** → Create New Template
   - **To:** `albergarias@idgp.global`
   - **Subject:** `Nova Inscrição - Programa Sorbonne`
   - **Body:** Use template variables like `{{applicant_name}}`, `{{applicant_email}}`, etc.
5. Note your **Template ID** (e.g., `template_xyz789`)
6. Go to **Account → API Keys** and note your **Public Key**

### Configure in admission.html

In `admission.html`, find the `<head>` section and add:
```html
<script src="https://cdn.jsdelivr.net/npm/@emailjs/browser@4/dist/email.min.js"></script>
```

Then find the `sendEmail` function and replace the commented block:
```javascript
// Replace these three values:
emailjs.init("YOUR_PUBLIC_KEY");        // ← your Public Key
emailjs.send(
  "YOUR_SERVICE_ID",                    // ← your Service ID
  "YOUR_TEMPLATE_ID",                   // ← your Template ID
  { ... }
);
```

---

## 🔐 Admin Panel

The admin dashboard is accessible from **both pages** via a discreet button in the bottom-right corner labeled `admin`.

| Credential | Value |
|---|---|
| Password | `idgp123` |

**Features:**
- Total applications counter
- Breakdown by payment option (Full / Installments)
- Full data table with all applicant fields
- **Export to CSV** button (UTF-8 with BOM, compatible with Excel)
- **Clear all data** button (with confirmation)

> ⚠️ **Important:** Application data is stored in the visitor's browser `localStorage`. This means data is stored per-browser and per-device. For production with persistent server-side storage, integrate with a backend service (see below).

---

## 💾 Data Storage Notes

| Feature | Current implementation | Production upgrade |
|---|---|---|
| Storage | Browser `localStorage` | Firebase / Supabase / Airtable API |
| Email | mailto fallback + EmailJS | EmailJS (configured) |
| PDF | Client-side jsPDF | Same (no change needed) |
| Admin auth | Password in JS | Backend session / Auth0 |

### Upgrade to Firebase (optional)

If you need persistent cloud storage:
1. Create a project at [firebase.google.com](https://firebase.google.com)
2. Enable **Firestore Database**
3. Add the Firebase SDK to `admission.html`
4. Replace the `saveApplication()` function with a Firestore `addDoc()` call

---

## 🎨 Design System

| Token | Value | Usage |
|---|---|---|
| `--navy` | `#0B1B3F` | Primary background |
| `--dark` | `#07122B` | Section backgrounds |
| `--darkest` | `#050D1E` | Form page background |
| `--gold` | `#C9A84C` | Accents, CTAs, headings |
| `--gold-light` | `#E8C96A` | Hover states, italic highlights |
| `--white` | `#FFFFFF` | Body text on dark |
| `--off-white` | `#F8F6F0` | Light section background |

**Fonts:**
- `Playfair Display` — headings and numbers
- `Cormorant Garamond` — body text, form fields
- `Montserrat` — labels, tags, navigation, buttons

---

## 📋 Form Sections

| # | Section | Fields |
|---|---|---|
| 1 | Personal Information | Name, nationality, DOB, ID, CPF, address, email, phone, LinkedIn |
| 2 | Professional Profile | Company, position, industry, experience, leadership scope |
| 3 | Education Background | Degree, university, certifications |
| 4 | Application Questions | Motivation, challenge, Paris expectations |
| 5 | Format Acknowledgment | 4 pre-checked acknowledgment items |
| 6 | Tuition Option | Full payment / Installments |
| 7 | Required Documents | Checklist of documents to send |
| 8 | Terms & Conditions | 6 required acceptance checkboxes |
| 9 | Signature | Name, date, digital signature |

---

## 🗓️ Program Calendar 2026

| Module | Format | Dates |
|---|---|---|
| Module 1 — Leadership & People Management | Presential (Rio de Janeiro) | Jun 18–21, 2026 |
| Module 2 — Foundations & Strategy | Online Synchronous | Jul 25, Aug 1, 15, 29, 2026 |
| Module 3 — Methods & Operational Efficiency | Online Synchronous | Sep 5, 19, Oct 3, 17, 2026 |
| Module 4 — Innovation & Practical Integration | Paris Immersion (Sorbonne) | Nov 2–6, 2026 |

---

## 📬 Contact

**Program coordination:** albergarias@idgp.global

---

*© 2026 IDGP Academy · International Certificate in Project Management and Organizational Performance*
