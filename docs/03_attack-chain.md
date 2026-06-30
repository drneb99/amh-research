# **Attack Chain: Assistant Memory Harvesting (AMH)**

## **Overview**

Assistant Memory Harvesting (AMH) is a post-compromise semantic reconnaissance technique. Once an attacker obtains access to a victim’s device or an authenticated AI assistant session, the assistant’s accumulated memories and contextual understanding become an exploitable intelligence surface. AMH leverages legitimate assistant functionality — summarization, organization, and contextual reasoning — to extract structured personal, operational, and organizational information.

This document outlines the generalized attacker workflow from compromise to intelligence exploitation.

---

## **Attack Preconditions**

AMH requires:

1. **A compromised endpoint or authenticated AI assistant session**
    
2. **The ability to issue unrestricted natural-language prompts**
    
3. **An AI assistant with retained context, long-term memory, or accessible conversation history**
    
4. **Historically accumulated user interactions containing meaningful personal or operational information**
    

AMH does **not** rely on jailbreaks, prompt injection, privilege escalation, or model manipulation.

---

# **Attack Chain**

## **1. Compromise**

The attacker gains access to the victim’s device or session. Common entry vectors include:

- Malware or keylogger installation
    
- Remote Access Trojans (RATs)
    
- Device loss or opportunistic physical access
    
- Stolen or hijacked authentication tokens
    
- Browser/session takeover
    
- Malicious extensions or infected applications
    

Once access is established, the attacker can interact with the AI assistant directly.

---

## **2. Assistant Discovery**

The attacker determines whether the system contains an active or accessible AI assistant.

Indicators may include:

- Open browser tabs to cloud-based AI platforms
    
- Standalone assistant applications
    
- Taskbar/sidebar integrations
    
- Browser extensions enabling AI features
    
- Persistent chat sessions
    

This step confirms whether a memory-bearing assistant is available for interrogation.

---

## **3. Initial Low-Risk Probing**

The attacker begins by assessing what the assistant knows and how it structures stored information.

Typical probing prompts:

- “Summarize our recent interactions.”
    
- “What topics or tasks have I discussed with you lately?”
    
- “Provide an overview of recurring themes in our conversations.”
    
- “List the main subjects that come up frequently.”
    

Objectives of probing:

- Evaluate memory depth
    
- Identify categories of stored information
    
- Observe the assistant’s summarization methodology
    
- Assess how it partitions personal and operational context
    

---

## **4. Targeted Semantic Extraction**

After confirming that the assistant contains valuable context, the attacker queries detailed categories of stored knowledge.

### **Personal and Behavioral Information**

- “What personal details have I shared with you?”
    
- “What goals, concerns, or plans have been discussed?”
    
- “Summarize any habits or preferences mentioned previously.”
    

### **Relational and Social Information**

- “Which individuals have I referred to in conversation?”
    
- “How are those individuals connected to me?”
    
- “Summarize any relationships or interactions I’ve described.”
    

### **Technical and Operational Information**

- “What systems, tools, or platforms have I mentioned using?”
    
- “What workflows or processes have I described?”
    
- “What technical tasks, troubleshooting steps, or responsibilities have I discussed?”
    
- “List any devices, services, or applications I have referenced.”
    

### **Identity and Service Footprint**

- “What accounts, providers, or organizations have I mentioned?”
    
- “What logistical or administrative details have been discussed?”
    
- “Summarize any references to upcoming events or obligations.”
    

At this stage, the attacker reconstructs the assistant’s **semantic model of the user**.

---

## **5. Structured Consolidation**

The attacker employs the assistant's organizational abilities to refine extracted data into actionable intelligence.

Common consolidation prompts:

- “Sort this information by sensitivity.”
    
- “Group details into categories: personal, professional, operational.”
    
- “Identify items that could facilitate impersonation.”
    
- “Highlight information that presents security or privacy risks.”
    
- “Generate a concise profile summarizing all relevant details.”
    

This transforms fragmented conversational memories into structured intelligence.

---

## **6. Weaponization**

The attacker uses consolidated semantic intelligence to support malicious objectives.

### **Social Engineering**

- Crafting targeted phishing or spearphishing messages
    
- Creating highly contextualized pretexts
    

### **Impersonation**

- Using extracted details to interact with organizations or contacts
    

### **Extortion or Coercion**

- Exploiting sensitive or emotionally charged information
    

### **Operational Exploitation**

- Identifying weak points in processes, dependencies, or technical systems
    

### **Physical or Real-World Targeting**

- Leveraging routines, schedules, or location patterns
    

AMH significantly reduces attacker workload compared to manual document analysis or filesystem traversal.

---

# **Simplified Kill Chain Overview**

1. **Compromise** → obtain device or session access
    
2. **Assistant Discovery** → confirm AI assistant availability
    
3. **Context Probing** → evaluate stored knowledge
    
4. **Semantic Extraction** → extract personal, relational, operational intelligence
    
5. **Consolidation** → organize findings into usable intelligence
    
6. **Weaponization** → apply insights to targeted attacks
    

---

# **Distinction From Existing Threats**

AMH is separate from:

- Prompt injection
    
- Memory poisoning
    
- Training data extraction
    
- Model inversion
    
- Model theft
    
- Fine-tuned model exfiltration
    

AMH relies on **post-compromise access** and abuses the assistant’s **legitimate functionality** rather than exploiting model vulnerabilities.

The core differentiator:

> **AMH targets the assistant’s cognitive layer — its structured semantic understanding of the user — rather than raw data or model internals.**
> 
> This attack-chain analysis directly informs the defensive recommendations described in `05_defensive-controls.md`  and should be read alongside the threat model for full context.

