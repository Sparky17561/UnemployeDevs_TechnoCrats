<div align="center">

# 🌐 **JobSphere**

### *Your Agentic AI Co-Pilot for Getting the Job You Deserve*

<img width="1024" height="329" alt="JobSphere Banner" src="https://capsule-render.vercel.app/api?type=waving&color=gradient&height=300&section=header&text=JobSphere&fontSize=90&animation=fadeIn&fontAlignY=38&desc=Technocrats%20Hackathon%20%7C%20Team%20UnemployeDevs&descAlignY=55&descAlign=50" />

> **Automate every step of the hiring journey — from tailoring resumes to filling forms, preparing interviews, tracking applications, and finding referrals.**  
> **AI-Powered • ATS-Optimized • Personalized • Integrated**

[![GitHub stars](https://img.shields.io/github/stars/Sparky17561/UnemployeDevs_TechnoCrats?style=social)](https://github.com/Sparky17561/UnemployeDevs_TechnoCrats/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
![Render](https://img.shields.io/badge/Backend-Render-46E3B7?logo=render&logoColor=white)
![Vercel](https://img.shields.io/badge/Frontend-Vercel-000000?logo=vercel&logoColor=white)
![MongoDB](https://img.shields.io/badge/Database-MongoDB_Atlas-13aa52?logo=mongodb&logoColor=white)
![Gemini API](https://img.shields.io/badge/AI-Gemini_API-4285F4?logo=google&logoColor=white)

</div>

---

## 🌟 **The Future of Job Hunting**

**JobSphere** is an **agentic AI co-pilot** powered by **Google Gemini** that automates your entire job search. Upload a resume, paste a job description, and instantly get an ATS-optimized resume, tailored cover letter, form-ready answers, interview roadmap, and smart outreach.

No tedious manual work. No generic applications. Just intelligent automation that gets you **hired faster**.

---

## 🚀 **Core Superpowers**

| Feature | Magic Behind It |
|---------|-----------------|
| 🤖 **AI Form Filler** | Parse JD + resume with Gemini → auto-fill job forms + generate long-form answers instantly |
| 📄 **Resume & Cover Letter** | Gemini generates ATS-optimized LaTeX resume + tailored cover letter in one click |
| 🎯 **Interview Prep Hub** | Gemini creates company/role-specific roadmaps, behavioral Q&As, system design, coding problems |
| 📊 **Application Tracker** | Track versions, statuses, deadlines, callbacks, and performance metrics |
| 📧 **Outreach Generator** | Gemini generates personalized cold emails, DMs, and LinkedIn messages with tone adaptation |
| 🏆 **Gamified Referral Pool** | Two-way referrals — referrers set assessments, top performers get priority |

---

## 🏗️ **Architecture: Scalable. Intelligent. Secure.**

```mermaid
graph TB
    A[Browser] -->|HTTPS| B[Frontend: Vercel<br/>React + Vite<br/>Session Cookie Auth]
    B -->|API Calls| C[Backend: Render<br/>Django + DRF<br/>Session-based Auth]
    C -->|Query/Update| D[(MongoDB Atlas<br/>User Data, Resumes,<br/>Applications)]
    C -->|Generate| E[LaTeX → PDF<br/>via pdflatex]
    C -->|Gemini API Calls| F[Google Gemini<br/>Resume, Questions,<br/>Answers Generation]
    E -->|Store| D
    F -->|Results| C
```

> **Render backend + Vercel frontend + MongoDB Atlas database + Google Gemini API. Session-based auth, fully deployed and production-ready.**

---

## 🔬 **Technical Highlights**

### **1. ATS-Optimized Resume Generation (LaTeX + Gemini)**

```python
# Example: backend/resume/views.py
import google.generativeai as genai

genai.configure(api_key=GEMINI_API_KEY)
model = genai.GenerativeModel("gemini-pro")

system_prompt = (
    "You are a senior resume writer and LaTeX expert. "
    "Generate a ONE-PAGE ATS-optimized LaTeX resume using the provided template. "
    "Output ONLY valid LaTeX code. Do not modify the template structure."
)

response = model.generate_content(
    f"{system_prompt}\n\nJob Description: {jd_text}\nUser Profile: {user_profile}\nTemplate: {latex_template}"
)

# Flow: Gemini generates LaTeX → pdflatex compiles → PDF stored in MongoDB → User download
```

### **2. Conversational Form Answers (Gemini JSON Contract)**

```json
{
  "formData": {
    "full_name": "Alice Johnson",
    "role": "Senior Software Engineer",
    "why_us": "I'm passionate about building scalable systems..."
  },
  "followUpQuestion": "I filled your name and role. For 'Why our company?', would you like me to emphasize:\n• Technical growth\n• Company culture\n\nJust say the word! 😊"
}
```

---

## ⚙️ **Setup in 3 Minutes**

### **Prerequisites**

```bash
# You need:
- Python 3.10+
- Node.js + npm
- MongoDB Atlas connection string (or local Mongo)
- Google Gemini API key (get from https://ai.google.dev)
- TeX Live / MiKTeX (optional for local dev, required for production)
```

---

### **Step 1: Backend (Django on Render)**

```bash
cd backend
python -m venv venv
source venv/bin/activate  # or venv\Scripts\activate on Windows
pip install -r requirements.txt
python manage.py migrate
python manage.py createsuperuser  # optional
python manage.py runserver
# API: http://localhost:8000
```

Create `.env`:
```
DJANGO_SECRET_KEY=your-secret-key
DEBUG=True
MONGODB_URI=mongodb+srv://user:pass@cluster.mongodb.net/jobsphere
ALLOWED_HOSTS=localhost,127.0.0.1
CORS_ALLOWED_ORIGINS=http://localhost:5173
GEMINI_API_KEY=your-gemini-api-key
```

---

### **Step 2: Frontend (React on Vercel)**

```bash
cd frontend
npm install
npm run dev
# UI: http://localhost:5173
```

Create `.env.local`:
```
VITE_API_URL=http://localhost:8000
```

---

### **Step 3: Deploy**

**Backend → Render:**
- Push to GitHub → Create Web Service on Render → Connect repo
- Build: `pip install -r requirements.txt && python manage.py migrate`
- Start: `gunicorn backend.wsgi:application`
- Add env vars in Render dashboard (including `GEMINI_API_KEY`)

**Frontend → Vercel:**
- Push to GitHub → Import into Vercel
- Root: `frontend`
- Add `VITE_API_URL` pointing to your Render backend
- Auto-deploys on push

---

## 📸 **See It in Action**

<div align="center">

### **System Flow**
<img width="1024" height="559" alt="image" src="https://github.com/user-attachments/assets/63f2c083-2832-4ef6-9bae-2028543da17f" />


### **Key Features**
<table>
<tr>
<td><img width="400" height="300" alt="Resume Builder" src="https://placehold.co/400x300/1a1a1a/ffffff?text=Resume+Builder+Preview" /></td>
<td><img width="400" height="300" alt="Interview Prep" src="https://placehold.co/400x300/1a1a1a/ffffff?text=Interview+Prep+Hub" /></td>
</tr>
</table>

</div>

---

## 🔥 **Why JobSphere Stands Out**

| Old Way | **JobSphere** |
|---------|---------------|
| Manual form-filling | **Gemini AI auto-fills + generates answers** |
| Generic resumes | **Gemini-tailored, ATS-optimized LaTeX PDFs** |
| No interview prep | **Gemini creates company/role-specific roadmaps** |
| Random outreach | **Gemini generates personalized, tone-aware emails** |
| Disorganized tracking | **Unified dashboard with analytics** |
| Favor-based referrals | **Gamified, merit-driven pool** |

---

## 🎯 **Quick Demo Flow**

1. **Sign up** with email/password
2. **Upload master resume** (PDF or text)
3. **Paste a job description**
4. **Generate**: Gemini tailors resume + cover letter in 30 seconds
5. **Use form filler**: Gemini auto-fills any job application
6. **Prep for interviews**: Gemini generates company-specific roadmap + questions
7. **Track applications**: Monitor status and performance
8. **Send outreach**: Gemini-generated cold emails and DMs

---

## 🛠️ **Project Structure**

```
UnemployeDevs_TechnoCrats/
├── README.md
├── backend/
│   ├── manage.py
│   ├── requirements.txt
│   ├── backend/              # Django project config
│   ├── resume/               # Resume generation + LaTeX + Gemini integration
│   ├── coldconnect/          # Referral + outreach (Gemini-powered)
│   └── users/                # Auth + profiles
└── frontend/
    ├── package.json
    ├── vite.config.js
    └── src/
        ├── pages/            # Home, Dashboard, ResumeBuilder, etc.
        ├── components/       # UI components
        ├── contexts/         # Auth context
        └── lib/              # Utilities
```

---

## 🌱 **Contributing**

Contributions welcome! Workflow:

```bash
git clone https://github.com/Sparky17561/UnemployeDevs_TechnoCrats.git
git checkout -b feature/your-feature-name
# Make changes, test, commit
git push origin feature/your-feature-name
# Open PR with clear description
```

Open issues for bugs or feature requests.

---

## 📄 **License**

[MIT License](LICENSE) — Free to use, modify, and ship.

---

<div align="center">

### **JobSphere doesn't just apply to jobs.**
### **It gets you hired.**

**Powered by Google Gemini • Built with ❤️ and ☕ during Technocrats Hackathon • Open Track**

</div>
