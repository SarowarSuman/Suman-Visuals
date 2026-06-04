<div align="center">

# 📷 Suman Visuals
### *A Personal Photography & Videography Portfolio*

[![Live Site](https://img.shields.io/badge/🌐_Live_Site-suman--visuals.netlify.app-63b3ed?style=for-the-badge&labelColor=0b1222)](https://suman-visuals.netlify.app)
[![Netlify](https://img.shields.io/badge/Hosted_on-Netlify-00C7B7?style=for-the-badge&logo=netlify&logoColor=white)](https://netlify.com)
[![Supabase](https://img.shields.io/badge/Storage-Supabase-3ECF8E?style=for-the-badge&logo=supabase&logoColor=white)](https://supabase.com)
[![License](https://img.shields.io/badge/License-MIT-blue?style=for-the-badge)](LICENSE)

<br/>

> *"I don't wait for the perfect shot — I walk until the world shows me one."*

<br/>

**A fully dynamic, cloud-powered photography & videography portfolio.**
Built with pure HTML/CSS/JS - no frameworks, no build tools, no complexity.
Just clean code, real photos, and a backend that actually works.

</div>

---

## ✨ What Makes This Different

Most portfolio sites are static photos hardcoded, no way to update without editing code. This one is **fully live**:

- Upload a photo from my devices → it appears on the site **instantly** for everyone
- Delete a photo from admin → gone from the site in seconds
- Every visitor sees the same up-to-date gallery, always

---

## 🛠️ Tech Stack — and *Why* Each One

### 🏗️ Pure HTML / CSS / JavaScript
**What it does:** The entire site is one `index.html` file.

**Why this, not React/Vue/Next.js?**
Frameworks are powerful but they come with overhead — `node_modules`, build steps, deployment pipelines, and bundle sizes that slow things down. For a portfolio site, that complexity adds zero value.

A single HTML file means:
- ✅ Zero build time — drag and drop to deploy
- ✅ Loads instantly — no JavaScript framework overhead
- ✅ Works on any hosting — Netlify, GitHub Pages, anywhere
- ✅ Easy to maintain — open file, edit, done

**What you'd lose with a framework:** Nothing meaningful for this use case. What you'd gain: 200MB of `node_modules` you don't need.

---

### ☁️ Supabase Storage
**What it does:** Stores all photos and videos in a cloud bucket. Serves them via public CDN URLs.

**Why Supabase, not Firebase / AWS S3 / Cloudinary?**

| Feature | Supabase | Firebase Storage | AWS S3 | Cloudinary |
|---|---|---|---|---|
| Free tier storage | 1GB | 5GB | 5GB | 25GB |
| Free bandwidth | 2GB/month | 1GB/day | 15GB/month | 25GB/month |
| Setup complexity | ⭐ Simple | ⭐⭐ Medium | ⭐⭐⭐ Complex | ⭐⭐ Medium |
| Open source | ✅ Yes | ❌ No | ❌ No | ❌ No |
| Self-hostable | ✅ Yes | ❌ No | ❌ No | ❌ No |
| SQL database included | ✅ Yes | ❌ (NoSQL) | ❌ No | ❌ No |

**The real reason:** Supabase gives a clean JavaScript SDK, public bucket support, and a generous free tier — all without vendor lock-in. Firebase is Google-owned and can be shut down. AWS S3 requires IAM roles, policies, and a billing alarm just to get started.

**Benefits here:**
- Upload files with 3 lines of JS (`sb.storage.from('media').upload(...)`)
- Public CDN delivery — fast load worldwide
- Files persist forever (until you delete them)
- No server needed — the browser talks to Supabase directly

---

### 🌐 Web3Forms
**What it does:** Handles the contact form — sends submitted messages to Gmail without a backend server.

**Why Web3Forms, not EmailJS / Formspree / a custom backend?**

| | Web3Forms | EmailJS | Formspree | Custom Backend |
|---|---|---|---|---|
| Free messages/month | 250 | 200 | 50 | Unlimited |
| Setup | Copy API key | JS SDK setup | Form action URL | Full server needed |
| Spam protection | ✅ Built-in | ❌ Manual | ✅ Built-in | ❌ Manual |
| No backend needed | ✅ | ✅ | ✅ | ❌ |

**The real reason:** A contact form on a static site has no server to receive POST requests. Web3Forms acts as the middleman — it receives the form data and forwards it to your email. Free, reliable, and takes 2 minutes to set up.

Without it, the options are: `mailto:` links (opens an email client, terrible UX) or a full Node.js/Python backend (massive overkill for one form).

---

### 🎨 Playfair Display + Outfit (Google Fonts)
**What it does:** Typography - Playfair Display for headings, Outfit for body text.

**Why these two, not system fonts or other Google Fonts?**

Typography makes or breaks a portfolio. The rule: pair a **serif** (personality, emotion) with a **sans-serif** (clarity, readability).

- **Playfair Display** — A high-contrast, editorial serif. Used by magazines and creative studios. Gives the site a "this person takes their craft seriously" feel. The italic variant is particularly elegant for accent text.
- **Outfit** — A geometric sans-serif designed for screens. Highly legible at small sizes, has personality at larger sizes. Feels modern without being cold.

**Why not system fonts?** `-apple-system, BlinkMacSystemFont` looks different on every device. The design breaks.

**Why not Roboto/Inter?** Roboto is a Google product font — fine, but ubiquitous and characterless. Inter is excellent for apps but feels corporate for a creative portfolio. Playfair+Outfit hits the "artistic but professional" tone precisely.

---


## 🏛️ Architecture Overview

```
┌─────────────────────────────────────────────────────┐
│                    Browser                          │
│                                                     │
│  index.html  ──────────────────────────────────    │
│     │                                               │
│     ├── Gallery  ←──── Supabase Storage (CDN)      │
│     │                  (photos + videos)            │
│     │                                               │
│     ├── Admin Panel                                 │
│     │     └── Upload ──→ Supabase Upload            │
│     │                                               │
│     │                                               │
│     └── Contact Form ──→ Web3Forms ──→ Gmail        │
└─────────────────────────────────────────────────────┘
```

**No server. No build step. No dependencies to install.**

---

## 🚀 Features

| Feature | Details |
|---|---|
| 📸 Dynamic Gallery | Loads from Supabase Storage in real-time |
| 🎬 Video Support | Upload + play MP4/MOV directly in the gallery |
| 📱 Fully Responsive | Works on phones and desktops |
| ✉️ Contact Form | Messages delivered to Gmail via Web3Forms |
| 🌌 Animated Hero | Particle canvas + orbiting photo system |
| 🗑️ Admin Delete | Remove photos/videos from gallery instantly |
| 🔍 Lightbox | Full-screen photo view + in-page video player |

---

## 📂 Project Structure

```
suman-visuals/
│
└── index.html          # The entire site — HTML + CSS + JS in one file
    │
    ├── <style>         # All CSS — variables, components, animations
    ├── <body>          # HTML structure — nav, hero, gallery, about, contact
    └── <script>        # All JavaScript — Supabase, gallery, upload
```


## 👤 Author

**Sarowar Suman** — Photographer · Videographer · Editor · Software Engineering Student

[![Linkedin](https://img.shields.io/badge/Linkedin-linkedin.com/in/sarowarsuman-63b3ed?style=flat-square)](www.linkedin.com/in/sarowarsuman)
[![Facebook](https://img.shields.io/badge/Facebook-sms.fm.gp-1877F2?style=flat-square&logo=facebook)](https://facebook.com/sms.fm.gp)
[![Email](https://img.shields.io/badge/Email-sarowarsumancontact@gmail.com-EA4335?style=flat-square&logo=gmail)](mailto:sarowarsumancontact@gmail.com)

---

<div align="center">

Made with ♥ in Bangladesh

*"Real walks. Real light. Real feelings. Nothing staged."*

</div>
