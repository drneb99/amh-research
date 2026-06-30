# **References and Related Work**

Assistant Memory Harvesting (AMH) does not currently appear in academic literature or industry taxonomies as a named or formally defined threat category. However, several adjacent research areas partially overlap with the mechanisms underlying AMH—particularly memory leakage, semantic exposure, post-compromise agent abuse, and model or adapter exfiltration. These works provide conceptual foundations but do not directly address the post-compromise semantic interrogation of memory-enabled AI assistants.

Each entry below notes its **relevance** (why it is adjacent), the **overlap** with AMH, and the **gap** it leaves open.

---

# **1. Memory Leakage and Memory Poisoning**

### **OWASP GenAI Security Project — "Agentic AI: Threats and Mitigations" / "Top 10 for Agentic Applications" (2025)**

- **Link:** https://genai.owasp.org/2025/12/09/owasp-top-10-for-agentic-applications-the-benchmark-for-agentic-security-in-the-age-of-autonomous-ai/
- **Relevance:** Names **Memory Poisoning** as a core risk for agents with persistent memory, and recommends session-scoped memory isolation as a mitigation.
- **Overlap:** Recognizes agent memory as a sensitive store whose contents can be disclosed or corrupted.
- **Gap:** Frames the risk as memory *corruption/injection* by an external input, not attacker-driven *interrogation* of intact memory after the endpoint or session is compromised.

---

# **2. Post-Compromise AI Abuse**

### **Europol, UNICRI & Trend Micro — "Malicious Uses and Abuses of Artificial Intelligence" (November 2020)**

- **Link:** https://www.europol.europa.eu/publications-events/publications/malicious-uses-and-abuses-of-artificial-intelligence
- **Relevance:** Surveys how attackers misuse AI systems and capabilities, establishing precedent for adversarial interaction with AI following access.
- **Overlap:** Treats AI as both an attack tool and an attack surface in criminal workflows.
- **Gap:** Predates memory-enabled assistants; does not consider extraction of a user-specific semantic profile held by an assistant.

---

# **3. Model and Adapter Exfiltration**

### **Palo Alto Networks Unit 42 — "ModeLeak: Privilege Escalation to LLM Model Exfiltration in Vertex AI" (2024)**

- **Link:** https://unit42.paloaltonetworks.com/privilege-escalation-llm-model-exfil-vertex-ai/
- **Relevance:** Demonstrates exfiltration of fine-tuned model adapters and the semantic knowledge embedded in them following privilege escalation.
- **Overlap:** Confirms that structured semantic data becomes a target once a system is compromised.
- **Gap:** Targets model *weights/adapters*, not the assistant's accumulated world-model of an individual user.

---

# **4. Privacy and Surveillance Research**

### **UCL & UC Davis — "Big Help or Big Brother? Browser Tracking by GenAI Assistants" (USENIX Security Symposium, 2025)**

- **Link:** https://www.ucdavis.edu/news/uc-davis-study-reveals-alarming-browser-tracking-genai-assistants
- **Relevance:** Measures how in-browser GenAI assistants accumulate personal context, and—critically—shows several assistants generate outputs reflecting **inferred** attributes such as wealth and lifestyle. This is direct evidence for AMH's central premise: assistants derive intelligence the user never explicitly states.
- **Overlap:** Confirms assistants build and retain rich, inferred user profiles.
- **Gap:** Studies vendor-side data collection and telemetry, not adversarial interrogation of that profile after compromise.

---

# **5. Prompt Injection and Assistant-Level Abuse**

### **SafeBreach Labs — "Invitation Is All You Need: Targeted Promptware Attacks Against Gemini" (Black Hat USA / DEF CON 33, 2025)**

- **Authors/Sources:** Ben Nassi, Stav Cohen, Or Yair. SafeBreach blog; coverage by Bitdefender.
- **Link:** https://www.safebreach.com/blog/invitation-is-all-you-need-hacking-gemini/
- **Relevance:** Shows how indirect prompt injection (via a calendar invite) can hijack a deeply integrated assistant and abuse its permissions.
- **Overlap:** Highlights the breadth of capability and data an integrated assistant exposes.
- **Gap:** Content-triggered injection from an *external* attacker without account access; AMH instead assumes the attacker already holds an authenticated session and uses the assistant as intended.

---

# **6. Hardware and Model-Level Side-Channel Attacks**

### **MoEcho — "Exploiting Side-Channel Attacks to Compromise User Privacy in Mixture-of-Experts LLMs" (ACM CCS, 2025)**

- **Link:** https://arxiv.org/abs/2508.15036
- **Relevance:** Recovers user prompts and responses from architectural side-channels (cache, TLB, performance counters) in MoE models.
- **Overlap:** Demonstrates that LLM usage can leak sensitive user information through indirect channels.
- **Gap:** A *true* side-channel against model internals and live inference traffic—distinct from AMH, which uses the assistant's intended interface to read high-level semantic memory. (This contrast is also why this research was renamed away from "side-channel"; see the README.)

---

# **Summary of the Literature Gap**

Across all reviewed sources:

- **No publication defines a threat where an attacker leverages a compromised device or authenticated session to interrogate a memory-enabled AI assistant for structured personal, relational, behavioral, or operational intelligence.**
- Existing literature addresses related risks—memory poisoning, prompt injection, model/adapter theft, vendor-side profiling, and architectural side-channels—but none recognize the assistant's **synthesized model of the user** as a post-compromise intelligence target.
- The UC Davis/UCL finding that assistants infer unstated attributes (wealth, lifestyle) is the closest empirical support, but it studies vendor collection, not adversarial extraction.

AMH occupies a distinct conceptual space: **the extraction of synthesized, assistant-organized, and partly inferred user context after endpoint or session compromise.** This gap supports recognizing AMH as a novel and emerging threat category within AI and cybersecurity research.
