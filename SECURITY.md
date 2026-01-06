#  Security and Data Protection

CodeGenie is designed with a **security-first architecture** to ensure user safety, data integrity, and protection of internal AI orchestration logic.

---

##  No Code Execution Policy
CodeGenie does not execute user-submitted code on backend servers.  

This prevents:
- Remote code execution attacks  
- Malicious payload execution  
- Server-side compromise  

All analysis is performed through **AI-generated reasoning only**.

---

##  API Key Protection
- All Gemini API keys are securely stored  
- Keys are never exposed to the frontend  
- API usage is rate-limited and monitored  
- In public builds, live AI execution is intentionally disabled  

---

##  Authentication Security
User authentication is handled through **Firebase Authentication**:
- Secure OAuth-based Google Sign-In  
- Encrypted session handling  
- No password storage by the application  

---

##  Firestore Data Protection
- User history and community data are stored in Firestore  
- Read/write rules are restricted by authentication status  
- All sensitive data is protected by Firebase security rules  

---

##  Prompt and IP Protection
- Core prompt engineering logic, optimization strategies, and AI orchestration workflows are kept private  
- Protects intellectual property and system integrity  

---

##  Abuse Prevention
- Community posts are moderated  
- Repeated abusive behavior can be restricted  
- Invalid or malicious content is filtered  

---

##  Public Repository Policy
This public repository is a **showcase build** and intentionally excludes:
- Production secrets  
- API keys  
- Internal orchestration logic  
