
#  CodeGenie System Architecture

This document explains the internal design and component flow of **CodeGenie**.  
The goal of the architecture is to provide fast, secure, and scalable AI-based code explanation and review while keeping the system modular and easy to extend.

---

##  High-Level Architecture
User ↓ Web Interface (React + Tailwind CSS) ↓ Firebase Backend (Auth, Firestore, Hosting) ↓ Gemini AI Service Layer

The system is built as a **three-layer architecture**:
1. **Presentation Layer (Frontend)**
2. **Backend & Data Layer (Firebase)**
3. **AI Processing Layer (Gemini API)**

---

##  Presentation Layer (Frontend)

The frontend is a single-page React application responsible for:
- Accepting Python code input  
- Allowing users to choose between **Explain** and **Review** modes  
- Providing tone selection for review  
- Displaying AI responses and code comparisons  
- Managing authentication state  
- Rendering history and community pages  

### Main UI Components

| Component        | Purpose                          |
|------------------|----------------------------------|
| **CodeEditor**   | Handles code input               |
| **ModeSelector** | Explain / Review toggle          |
| **ToneSelector** | Review tone selection            |
| **OutputViewer** | Displays AI output               |
| **HistoryPanel** | Shows saved sessions             |
| **CommunityFeed**| Discussion board                 |
| **Navbar/Footer**| Layout and navigation            |

---

##  Backend & Data Layer (Firebase)

Firebase is used as a serverless backend for:
- Google authentication  
- Firestore database for history and community data  
- Hosting the frontend application  

### Firestore Collections

| Collection         | Description                          |
|--------------------|--------------------------------------|
| **users**          | User profile and auth metadata       |
| **history**        | Saved explanation/review sessions    |
| **community_posts**| Community questions and replies      |

---

##  AI Processing Layer (Gemini API)

CodeGenie uses the **Gemini API** to generate:
- Natural language code explanations  
- Comparative AI-optimized code reviews  
- Tone-specific feedback responses  

The prompt sent to the AI is dynamically constructed using:
- Selected mode (**Explain / Review**)  
- Selected tone (**Gentle, Zen, Brutal**)  
- User code length and complexity  

> ⚠️ Live AI prompt-engineering logic is intentionally kept private in public builds.

---

##  Request Flow

1. User enters Python code  
2. User selects mode and tone  
3. Frontend builds the AI request  
4. Request is sent to Gemini API  
5. Response is parsed  
6. Output is rendered  
7. If signed in, session is stored in Firestore  

---

##  Scalability Design

- Firebase allows horizontal scaling without server management  
- Frontend is fully static and CDN-served  
- AI layer is decoupled and can be replaced or extended for other models  

---

##  Security Design

- No backend code execution  
- No sensitive API keys in frontend  
- Authentication handled through Firebase  
- IP-sensitive prompt logic kept private  

---

##  Extensibility

The modular structure allows future upgrades such as:
- Multi-language code support  
- Secure sandboxed code execution  
- Learning paths and gamification  
- Community moderation using AI  
