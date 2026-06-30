# **References and Related Work**

Assistant Memory Harvesting (AMH) does not currently appear in academic literature or industry taxonomies as a named or formally defined threat category. However, several adjacent research areas partially overlap with the mechanisms underlying AMH—particularly memory leakage, semantic exposure, post-compromise agent abuse, and model or adapter exfiltration. These works provide conceptual foundations but do not directly address the post-compromise semantic interrogation of AI assistants.

---

# **1. Memory Leakage and Memory Poisoning**

### **OWASP – Agentic AI Core Security Risks (2024)**

- **Relevance:** Identifies “Memory-Based Data Leakage” and “Memory Poisoning” as risks for AI agents with contextual retention.
    
- **Overlap:** Demonstrates the potential for unintended disclosure of sensitive context stored in agent memory.
    
- **Gap:** Focuses primarily on memory corruption, injection, or unintended leakage—not attacker-driven interrogation after compromise.
    

### **AIMultiple – “15 Security Threats to LLM Agents” (2025)**

- **Relevance:** Discusses memory poisoning and semantic leakage scenarios in LLM-powered agents.
    
- **Overlap:** Acknowledges risks of exposing personal or contextual data.
    
- **Gap:** Primarily concerned with input manipulation; does not address post-compromise semantic extraction.
    

---

# **2. Post-Compromise AI Abuse**

### **Trend Micro – “Malicious Uses of AI” (2020)**

- **Relevance:** Surveys ways attackers may misuse legitimate AI systems following system compromise.
    
- **Overlap:** Establishes precedent for adversarial interaction with AI systems after initial access.
    
- **Gap:** Does not explore extraction of user-specific semantic memory or world-modeling data.
    

### **Salesforce – LLM Security White Paper (2025)**

- **Relevance:** Covers prompt injection, data poisoning, model misuse, and enterprise LLM risks.
    
- **Overlap:** Provides context for broader agentic AI threats.
    
- **Gap:** Lacks discussion of memory-enabled assistants as structured intelligence targets in post-compromise conditions.
    

---

# **3. Model and Adapter Exfiltration**

### **Palo Alto Networks Unit 42 – “ModeLeak: Privilege Escalation to LLM Model Exfiltration in Vertex AI” (2024)**

- **Relevance:** Describes attacks that exfiltrate fine-tuned model adapters and embedded semantic knowledge following privilege escalation.
    
- **Overlap:** Confirms that structured semantic data becomes a target once systems are compromised.
    
- **Gap:** Focuses on model theft and adapter extraction, not user-context world-model extraction.
    

---

# **4. Privacy and Surveillance Research**

### **UC Davis – “Browser Tracking by GenAI Assistants” (2024)**

- **Relevance:** Shows that assistant features integrated into browsers can capture extensive personal context.
    
- **Overlap:** Demonstrates that AI assistants accumulate detailed user data.
    
- **Gap:** Investigates vendor tracking and telemetry, not adversarial interrogation after compromise.
    

---

# **5. Prompt Injection, Indirect Prompting, and Assistant-Level Abuse**

### **Gemini/Calendar “Promptware” Vulnerabilities (2024–2025)**

- **Sources:** SafeBreach, Bitdefender
    
- **Relevance:** Illustrate how malicious content can influence LLM behavior, leading to leakage or unintended actions.
    
- **Overlap:** Highlights risks associated with deeply integrated assistants.
    
- **Gap:** These are content-triggered vulnerabilities; they do not consider attacker access via compromised sessions.
    

---

# **6. Hardware and Model-Level Side-Channel Attacks**

### **MoEcho and Other LLM Architectural Side-Channel Research (2023–2024)**

- **Relevance:** Demonstrate how timing, cache, or GPU-level artifacts can leak training data or model internals.
    
- **Overlap:** Shows that LLMs can leak sensitive information through indirect channels.
    
- **Gap:** Targets low-level model internals, not high-level semantic memory derived from user interaction.
    

---

# **Summary of the Literature Gap**

Across all reviewed sources:

- **No publication defines a threat where attackers leverage a compromised device or authenticated session to interrogate a memory-enabled AI assistant for structured personal, relational, behavioral, or operational intelligence.**
    
- Existing literature addresses related risks—memory leakage, prompt injection, model theft, semantic leakage—but none recognize AI assistants as **semantic intelligence repositories** vulnerable to post-compromise interrogation.
    
- AMH occupies a distinct conceptual space:  
    **the extraction of synthesized, assistant-organized user context after endpoint compromise.**
    

This gap supports recognizing AMH as a novel and emerging threat category within AI and cybersecurity research.
