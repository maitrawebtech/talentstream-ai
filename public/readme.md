# ⚡ TalentStream AI | AI Recruiter Portfolio

> An obsidian-gold dark portfolio and grounded AI Recruiter Representative built with Express.js, Server-Sent Events (SSE) streaming, and Google AI Studio (`gemini-2.5-flash`).

![Version](https://img.shields.io/badge/version-1.0.0-gold?style=flat-square)
![Stack](https://img.shields.io/badge/Stack-Express%20%7C%20Node.js%20%7C%20SSE%20%7C%20Vanilla%20JS-black?style=flat-square)
![License](https://img.shields.io/badge/license-MIT-blue?style=flat-square)

---

## 🌟 Overview

**TalentStream AI** is a full-stack interactive candidate portfolio and real-time AI recruiter console.

It combines a premium candidate portfolio with an AI-powered recruiter representative capable of answering questions about the candidate's background, technical skills, projects, achievements, strengths, and experience.

The application is powered by a secure **Express.js backend** and uses **Server-Sent Events (SSE)** to stream AI responses in real time.

The AI is explicitly grounded in verified candidate information to minimize hallucinations and prevent unsupported claims.

### Key Highlights

* **Zero-Hallucination Architecture** — System instructions strictly ground responses in verified achievements, technical skills, projects, and repositories.
* **Real-Time SSE Streaming** — AI responses stream chunk-by-chunk for a responsive recruiter experience.
* **Embedded Resume Server** — Direct PDF viewing and one-click downloading through the portfolio navigation.
* **Obsidian & Gold UI** — Premium dark dashboard with grid lines, micro-interactions, and crisp typography.
* **Modern Typography** — Uses `Plus Jakarta Sans` and `JetBrains Mono`.
* **White-Labeled Console** — Public-facing interface is designed without third-party AI branding.
* **Full-Stack Architecture** — Lightweight Express backend combined with a vanilla JavaScript frontend.
* **Recruiter-Oriented AI** — Designed to answer candidate-related questions naturally and consistently.

---

## 🛠️ Tech Stack

### Backend

* Node.js
* Express.js
* CORS
* Dotenv

### AI Engine

* Google Generative AI SDK
* `@google/generative-ai`
* `gemini-2.5-flash`
* Google AI Studio

### Real-Time Communication

* Server-Sent Events (SSE)
* `POST /api/chat`
* Native Fetch API
* ReadableStream

### Frontend

* HTML5
* CSS3
* Vanilla JavaScript
* ES6+
* Fetch API
* ReadableStream

### Static Assets

* Express static middleware
* PDF resume serving
* `public/resume.pdf`

---

## 📁 Project Structure

```text
ishan-ai-portfolio/
├── public/
│   ├── index.html        # Main interactive dashboard UI
│   └── resume.pdf        # Candidate Resume
│
├── .env                  # Environment variables
├── server.js             # Express backend + Gemini streaming
├── package.json          # Node.js dependencies and scripts
└── README.md             # Project documentation
```

---

# 🚀 Quick Start Guide

## Prerequisites

Before running the project, make sure you have:

* **Node.js v18.x or higher**
* A **Google AI Studio Gemini API key**
* Git
* A modern web browser

---

## 1. Clone the Repository

```bash
git clone https://github.com/maitrawebtech/ishan-ai-portfolio.git
cd ishan-ai-portfolio
```

---

## 2. Install Dependencies

```bash
npm install
```

---

## 3. Configure Environment Variables

Create a `.env` file in the root directory:

```env
PORT=3000
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

> **Security:** Never commit your real API key to GitHub. Keep `.env` in `.gitignore` and use your hosting provider's environment-variable settings in production.

---

## 4. Add Your Resume

Place your PDF resume inside the `public` directory and name it:

```text
ishan-ai-portfolio/public/resume.pdf
```

The Express server will make the file available through the application.

---

## 5. Start the Application

```bash
npm start
```

Or, if your `package.json` does not define a start script:

```bash
node server.js
```

Once the server starts, open:

```text
http://localhost:3000
```

---

# 🤖 AI Grounding & Anti-Hallucination Architecture

The AI Recruiter is designed around a strict grounding strategy.

The backend system instructions define what the AI is allowed to claim about the candidate.

The model should rely only on information explicitly supplied to the system prompt or verified project data.

### Grounding Principles

1. **Verified Facts Only**

   * Candidate background
   * Technical skills
   * Projects
   * Achievements
   * Education
   * Professional roles
   * Verified repositories

2. **No Unsupported Claims**

   * The AI should not invent companies, projects, awards, technologies, employment history, or achievements.
   * If information is unavailable, the AI should clearly state that it does not have verified information.

3. **Consistent Candidate Representation**

   * Responses should remain aligned with the candidate's actual portfolio and resume.
   * The AI should avoid exaggerating experience or inventing credentials.

4. **Recruiter-Focused Responses**

   * Technical questions should focus on actual engineering experience.
   * Behavioral questions should use configured strengths and development areas.
   * Project questions should reference verified implementations.

---

# 🧠 Candidate Intelligence Configuration

The recruiter system can be configured with verified candidate information such as:

### Education

* B.Tech in AI & ML
* BBIT

### Technical Profile

* Full-stack development
* Artificial intelligence
* Machine learning
* Cloud development
* Web development
* Node.js
* Express.js
* JavaScript
* React
* Python
* Google Cloud
* Gemini APIs

### Leadership & Entrepreneurship

* Founder of **Maitra Web Tech**
* Founder of **WebX**

### Core Strengths

* Full-stack execution
* Rapid prototyping
* AI integration
* Cloud-based development
* Product engineering
* Building complete applications from concept to deployment

### Growth Areas

The AI recruiter can provide candid, professionally framed answers around areas such as:

* Architectural perfectionism
* Spending significant time on implementation details
* Strong preference for hands-on engineering
* Balancing deep technical work with broader product considerations

These should be presented as genuine development areas rather than fabricated weaknesses.

---

# 🔗 Verified Project References

The AI recruiter can provide verified references to relevant repositories and projects, including:

* **MNCS**
* **MaitraGPT**
* **High-Integrity Alignment Engine**

Repository links should only be returned when they are explicitly configured and verified in the backend.

---

# ⚡ Server-Sent Events Architecture

The application uses **Server-Sent Events-style streaming** to deliver Gemini responses incrementally.

### Request Flow

```text
Recruiter
   │
   ▼
Portfolio UI
   │
   │ POST /api/chat
   ▼
Express.js Backend
   │
   ▼
Grounded System Instructions
   │
   ▼
Gemini 2.5 Flash
   │
   │ Streaming response
   ▼
Express.js
   │
   │ SSE chunks
   ▼
Browser ReadableStream
   │
   ▼
Live AI Recruiter Response
```

### Benefits

* Faster perceived response time
* No need to wait for the complete model response
* Natural conversational experience
* Efficient one-way server-to-client streaming
* Simple implementation using native browser APIs

---

# 📡 API

## `POST /api/chat`

Used by the frontend to send recruiter questions to the AI engine.

### Example Request

```json
{
  "message": "Tell me about Ishan's strongest technical skills."
}
```

### Response

The backend streams the generated response incrementally to the client.

The frontend consumes the response using the browser's native `ReadableStream` API.

---

# 📄 Resume Integration

The portfolio includes a built-in resume server.

Place the resume at:

```text
public/resume.pdf
```

The Express static middleware makes the PDF accessible through the application.

This allows recruiters to:

* View the resume
* Open it directly in the browser
* Download the PDF
* Access it without leaving the portfolio

---

# 🎨 UI & Design System

The interface follows an **Obsidian + Gold** visual direction.

### Design Characteristics

* Dark obsidian background
* Gold accent system
* Thin grid lines
* High-contrast typography
* Minimal dashboard layout
* Smooth micro-interactions
* Technical monospace elements
* Recruiter-console aesthetic

### Typography

**Primary UI Font**

```text
Plus Jakarta Sans
```

**Technical / Monospace Font**

```text
JetBrains Mono
```

The design intentionally avoids a generic chatbot appearance and instead presents the AI as an integrated component of the candidate's professional portfolio.

---

# 🔐 Security

Never expose your Gemini API key in frontend JavaScript.

### Recommended Architecture

```text
Browser
   │
   │ User message
   ▼
Express Backend
   │
   │ API key stored server-side
   ▼
Google Gemini API
```

The browser should never receive:

```text
GEMINI_API_KEY
```

### Environment Variables

Use:

```env
PORT=3000
GEMINI_API_KEY=YOUR_GEMINI_API_KEY
```

And ensure `.env` is included in `.gitignore`:

```gitignore
.env
node_modules/
```

---

# 🌐 Deployment

The application can be deployed to Node.js-compatible hosting platforms such as **Render** or **Railway**.

## Deployment Steps

### 1. Push the Repository

```bash
git add .
git commit -m "Initial release"
git push origin main
```

### 2. Create a Web Service

Create a new Node.js web service on your preferred hosting provider.

### 3. Build Command

```bash
npm install
```

### 4. Start Command

```bash
node server.js
```

Or:

```bash
npm start
```

if the `start` script is configured in `package.json`.

### 5. Configure Environment Variables

Add:

```text
GEMINI_API_KEY
```

through the hosting provider's environment-variable configuration.

Do **not** upload `.env` to the repository.

---

# 🧪 Local Development

Run:

```bash
npm install
npm start
```

Then visit:

```text
http://localhost:3060
```

For development, you can also use a process manager or development runner such as:

```bash
node server.js
```

---

# 🗺️ Future Roadmap

Potential future improvements include:

* [ ] Recruiter session history
* [ ] Persistent conversation storage
* [ ] Admin dashboard
* [ ] Resume version management
* [ ] Project knowledge-base ingestion
* [ ] GitHub repository synchronization
* [ ] Structured candidate knowledge graph
* [ ] Recruiter analytics
* [ ] Conversation export
* [ ] Multi-language recruiter support
* [ ] Voice-based recruiter interaction
* [ ] Authentication and protected admin routes
* [ ] Rate limiting
* [ ] Request logging and monitoring

---

# 📜 License

This project is distributed under the **MIT License**.

See the `LICENSE` file for complete license information.

---

# 📬 Contact & Links

### Developer

**Ishan Maitra**

### GitHub

**@maitrawebtech**

https://github.com/maitrawebtech

### LinkedIn

https://linkedin.com/in/ishan-maitra

### Email

**[ishanmaitra2012@gmail.com](mailto:ishanmaitra2012@gmail.com)**

---

# ⭐ Project Philosophy

> **Build the portfolio. Let the intelligence explain it.**

TalentStream AI is designed to turn a conventional developer portfolio into an interactive technical representative.

Instead of forcing recruiters to navigate through static pages, repositories, and documents, the AI recruiter provides a conversational interface for discovering the candidate's verified technical background.

The goal is simple:

**Make the candidate's work discoverable, explainable, and interactive — without compromising factual accuracy.**

---

## ⚡ TalentStream AI

**AI-powered candidate portfolio · Real-time recruiter console · Grounded candidate intelligence**

Built with **Node.js · Express.js · Gemini · SSE · Vanilla JavaScript**
