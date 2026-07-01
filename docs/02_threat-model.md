# **Threat Model: Assistant Memory Harvesting (AMH)**

## **Introduction**

Assistant Memory Harvesting (AMH) describes a post-compromise technique in which an attacker interrogates a memory-enabled AI assistant to extract structured personal, operational, or organizational intelligence. Unlike prompt injection or memory poisoning, AMH assumes the attacker already controls the endpoint or an authenticated assistant session. The AI assistant responds as if interacting with the legitimate user, exposing accumulated context that would otherwise require extensive manual analysis.

---

# **Adversary Profile**

## **Required Capability Level**

AMH requires minimal technical expertise once initial compromise has occurred. The attacker only needs the ability to issue natural-language prompts to the assistant. Through normal conversation, the attacker gains access to:

- Summaries of prior interactions
    
- Prioritized insights and recurring themes
    
- Behavioral and routine information
    
- Relationship and social-graph structures
    
- Technical, logistical, or organizational context
    

The assistant effectively becomes an intelligence-processing interface for the attacker.

## **Likely Adversaries**

- Cybercriminals targeting identity information or financial gain
    
- Advanced persistent threat (APT) groups conducting human-centric reconnaissance
    
- Insider threats exploiting unlocked or shared devices
    
- Domestic abusers or individuals with opportunistic physical access
    
- Red teams evaluating AI-assistant exposure risks
    

## **Adversary Goals**

Attackers leveraging AMH may seek to:

- Reconstruct detailed personal profiles
    
- Map social networks and interpersonal dynamics
    
- Identify behavioral patterns or psychological leverage points
    
- Extract operational or project-related intelligence
    
- Learn about systems, tools, accounts, or dependencies previously discussed
    
- Generate highly targeted phishing, fraud, or extortion campaigns
    

---

# **Preconditions for Attack**

## **1. Endpoint or Session Compromise**

AMH requires the attacker to already control the victim’s device or authenticated session. Common paths include:

- Malware or remote access trojans
    
- Lost or stolen devices with active sessions
    
- Session token hijacking
    
- Screen or browser hijacking
    
- Physical access to unlocked systems
    

AMH is strictly a **post-compromise** technique.

## **2. Authenticated AI Assistant Session**

The attacker must have access to an AI assistant that:

- Maintains long-term memory, **or**
    
- Retains conversational context, **or**
    
- Integrates with personal or organizational data sources
    

## **3. Historical User Interaction**

The assistant must hold accumulated user context such as:

- Routines, habits, or preferences
    
- Personal reflections or long-term plans
    
- Professional responsibilities and workflows
    
- Tools, platforms, or services the user has discussed
    
- Relationship information or social context
    
- Notes, summaries, or guidance from past interactions
    

## **4. Freedom to Issue Prompts**

The attacker must be able to prompt the assistant without additional barriers.

- No elevated privileges required
    
- No jailbreaks necessary
    
- Natural-language interaction is sufficient
    

---

# **Assets at Risk**

## **Personal / Behavioral Intelligence**

- Routines, habits, and lifestyle patterns
    
- Long-term goals or private concerns
    
- Emotional states or stress indicators
    
- Reflections, preferences, or life plans
    

## **Social / Relational Intelligence**

- Important contacts and relational structures
    
- Family or household composition
    
- Workplace connections or team dynamics
    
- Areas of interpersonal conflict or influence
    

## **Technical / Operational Intelligence**

- Systems, tools, applications, or platforms discussed
    
- Workflows, processes, or troubleshooting history
    
- Technical responsibilities or areas of expertise
    
- Cloud services or third-party integrations referenced
    

## **Organizational Intelligence**

- Project summaries and progress updates
    
- Meeting patterns or team responsibilities
    
- Internal terminology, processes, or dependencies
    
- Operational rhythms or strategic initiatives
    

## **Identity and Security Intelligence**

- Partial identifiers, account hints, or service providers
    
- Security-question–adjacent information
    
- Financial or administrative patterns
    
- Platforms or services the user interacts with
    

---

# **Threat Scenarios**

## **Scenario 1: Identity Reconstruction**

The attacker queries the assistant to compile routines, identifiers, and personal details into a complete impersonation profile.

## **Scenario 2: Enhanced Social Engineering**

The assistant enables creation of highly tailored pretexts, phishing messages, or multi-step fraud campaigns based on user history.

## **Scenario 3: Exposure of Sensitive Personal Information**

Private reflections, emotionally charged topics, or sensitive disclosures made to the assistant become accessible to the attacker.

## **Scenario 4: Organizational Reconnaissance**

Work-related conversations provide insight into projects, dependencies, team structures, or internal processes useful for deeper compromise.

## **Scenario 5: Physical or Real-World Targeting**

Habits, routines, or travel patterns may expose opportunities for surveillance, impersonation, or physical intrusion.

---

# **Attack Constraints**

Despite its effectiveness, AMH is limited by:

- The requirement for pre-existing endpoint or session compromise
    
- The need for access to a live or unexpired assistant session
    
- The dependence on sufficiently rich historical context
    
- The requirement for human-driven prompting rather than automated extraction
    

AMH is opportunistic, not self-propagating.

## **Observed Yield Characteristics**

AMH's yield is not uniform. Early testing against a live memory-enabled assistant suggests it varies by category and by the user's disclosure habits:

- **Relational intelligence scales with disclosure.** A user who discusses projects and tasks more than people yields a sparse social graph; the assistant does not manufacture relationships that were never mentioned. Social-reconnaissance value is therefore highly user-dependent.
    
- **The inference layer is robust regardless.** Psychological and behavioral conclusions (stress, fatigue, motivation, personality) were derived even from purely operational, task-focused history. The user need not have discussed emotions for the assistant to infer them from logistics—so the novel payload does not depend on the user being self-disclosing.
    
- **Memory hygiene does not defeat inference.** A privacy-conscious, local-first user—one who avoids the cloud and never enters credentials—was still fully profiled. Withholding secrets limits the *recall* layer but not the *inference* layer.
    
- **AMH extracts the profile, not withheld secrets.** Credentials, passwords, and financial account numbers the user never entered did not appear; AMH surfaces synthesized understanding, not data the user deliberately kept out of the assistant.
    

This makes AMH's impact simultaneously **bounded** (it cannot exceed what the assistant can recall or infer) and **resilient** (the highest-value inferred intelligence survives even careful data hygiene).

---

# **Threat Model Summary**

Assistant Memory Harvesting constitutes a distinct threat class because:

- It exploits **semantic knowledge**, not raw files or model internals
    
- The assistant’s intended functionality becomes an intelligence surface
    
- Structured personal and organizational context can be extracted effortlessly
    
- It dramatically expands the informational blast radius of endpoint compromise
    
- It provides attackers with insights rarely accessible through traditional forensics
    

---

> **This threat model forms the basis for the attack-chain analysis described in `03_Attack-Chain.md`.**
