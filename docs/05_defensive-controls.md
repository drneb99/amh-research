# **Defensive Controls for Assistant Memory Harvesting (AMH)**

## **Overview**

Assistant Memory Harvesting (AMH) is a post-compromise reconnaissance technique in which an attacker interrogates a memory-enabled AI assistant to extract structured personal, technical, or organizational intelligence. Because AMH requires authenticated access rather than direct model exploitation, effective defense centers on endpoint hardening, access control, memory governance, and detection engineering.

The following control strategies apply to individuals, enterprises, SOC teams, and AI system architects.

---

# **A Guiding Principle: Defend the Access, Not the Wording**

AMH cannot be stopped by filtering what the attacker *says*. As shown in the attack chain (`03_attack-chain.md`), the most effective extraction prompts are framed as legitimate self-reflection or a personal “security self-audit”—indistinguishable from a privacy-conscious user protecting themselves. There is no malicious phrasing to block, and the assistant's own safety training guards only overt payload generation (e.g., “write the scam message”), not the far more valuable benign-framed target prioritization.

Consequently, **content moderation and keyword filtering are structurally inadequate against AMH.** Effective defense must instead constrain *who* can reach the memory and *under what conditions*—an access and architecture problem, not a content problem. The controls below are ordered accordingly: endpoint and session boundaries first, memory governance and behavioral detection second, and platform architecture as the backstop.

---

# **1. Endpoint Security as the Primary Line of Defense**

AMH cannot occur without device or session compromise. Strengthening endpoint resilience is therefore the most impactful mitigation.

### **Recommended Controls**

- Full-disk encryption (FDE)
    
- Strong OS-level authentication (PIN, passphrase, biometrics)
    
- Hardware-backed MFA for critical accounts
    
- OS, browser, and application patch hygiene
    
- Restriction of untrusted extensions, apps, and plugins
    
- Anti-malware and endpoint detection and response (EDR) solutions
    
- Disable browser session restoration where feasible
    
- Enforce automatic logout or inactivity timeouts
    

If an adversary cannot access the session, AMH is impossible.

---

# **2. AI Assistant Access Controls**

AI assistant sessions should not remain continuously authenticated.

### **Controls**

- Enforce session timeouts
    
- Require reauthentication after extended inactivity
    
- Apply MFA to memory or history retrieval features
    
- Disable automatic assistant launch at system startup
    
- Restrict assistant usage on shared or unmanaged devices
    

Tightening authentication reduces the attack window.

---

# **3. Memory and Data Hygiene**

Limiting sensitive information in long-term assistant memory reduces the potential impact of AMH.

### **Mitigations**

- Avoid entering highly sensitive personal identifiers (e.g., SSNs, card numbers, passwords)
    
- Limit discussion of sensitive emotional or psychological content
    
- Avoid embedding unpublished internal organizational information
    
- Periodically review and purge retained assistant memory (where supported)
    
- Use separate accounts or profiles for personal, professional, and administrative use
    

Effective memory hygiene constrains the scope of extractable intelligence.

---

# **4. Organizational Policy and Governance**

Enterprises should formalize expectations and restrictions around AI assistant usage.

### **Recommended Policies**

- Clear rules defining acceptable and prohibited AI assistant disclosures
    
- Restrictions on entering sensitive corporate data into conversational systems
    
- Governance for AI integrations with email, calendars, document stores, and workflows
    
- Regular audits of assistant usage patterns for risk identification
    
- Documentation of sanctioned vs. unsanctioned assistant use-cases
    

### **Governance Considerations**

- Maintain an AI risk register
    
- Apply organizational data-classification standards to AI interactions
    
- Require justification for enabling or extending memory features
    

Strong governance reduces inadvertent exposure.

---

# **5. Monitoring and Detection Engineering**

SOC teams should treat AI assistant activity as a visibility surface and potential indicator of compromise.

### **Signals to Monitor**

- Bursts of summarization or “show me everything” style queries
    
- Assistant use during unusual hours
    
- Access from atypical geolocations or devices
    
- Uncharacteristic query topics (financial, relational, administrative, or highly personal)
    
- Reconnaissance-style sequences (profiles, lists, summaries)
    
- Behavioral deviations from the user’s typical prompting patterns
    

### **Logging Recommendations**

- Session creation, termination, and authentication events
    
- Records of memory retrieval or access
    
- Correlation of assistant activity with EDR alerts or suspicious device behavior
    

Assistant usage should be monitored similarly to other privileged productivity tools.

---

# **6. Incident Response Procedures for AMH**

If AMH is suspected or confirmed, responders should:

1. Immediately revoke all AI assistant sessions
    
2. Invalidate browser tokens and cloud sessions
    
3. Quarantine the endpoint and initiate forensic acquisition
    
4. Review available assistant history or memory logs
    
5. Assess what categories of information may have been extracted
    
6. Update breach impact assessments to include semantic/contextual exposure
    
7. Notify stakeholders if recovered intelligence could be weaponized
    

AMH expands the potential blast radius of a compromise; IR processes must account for this added dimension.

---

# **7. Architectural Mitigations for AI Developers**

AI platform providers and system architects can reduce AMH risk through first-party design decisions.

### **Hard Controls**

- Memory encryption tied to session or device context
    
- Separation of memory stores from conversational interfaces
    
- Access controls governing memory retrieval
    
- Minimization of long-term user context stored by default
    
- **Step-up re-authentication before privileged memory operations**—treat whole-memory retrieval and full-profile synthesis (e.g., “summarize everything you know about me,” “build a profile of me”) as sensitive actions requiring fresh authentication, not ordinary chat turns
    
- **Friction and rate-limiting on bulk recall**—throttle or challenge rapid, broad “show me everything” sequences regardless of how each prompt is phrased
    
- **Gate on the operation, not the wording**—since benign-framed prompts cannot be distinguished by content, scope controls to the *sensitivity of what is being retrieved or synthesized*, not to keywords in the request
    

### **Soft Controls**

- User warnings when sensitive identifiers are entered
    
- User-configurable “protected data categories”
    
- Memory access logs or audit trails
    
- Optional privacy modes that disable retention
    

Architectural design should prevent trivial access to high-context semantic memory.

---

# **Conclusion**

AMH is an emergent security risk arising from the way AI assistants store, recall, and structure long-term contextual information. Defenses must emphasize endpoint protection, authenticated access boundaries, memory governance, and detection engineering. By adopting layered controls across individuals, organizations, and AI platforms, the potential impact of AMH can be significantly mitigated.
