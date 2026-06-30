# **Assistant Memory Harvesting (AMH)**

### _An Emerging Post-Compromise Semantic-Intelligence Threat in AI-Assisted Environments_

> **Note:** This work was formerly explored under the name **Cognitive Side-Channel Extraction (CSCE)**. It has been renamed to **Assistant Memory Harvesting (AMH)** for technical accuracy — the technique is post-compromise abuse of a legitimate assistant feature, not a true side-channel.

## **Overview**

Assistant Memory Harvesting (AMH) is a proposed threat category describing how an attacker—after compromising a victim’s endpoint or authenticated session—can interrogate a memory-enabled AI assistant to extract structured, high-value semantic intelligence.

Modern AI assistants often retain summaries of user behavior, preferences, relationships, routines, and operational details. Once a device or session is compromised, this synthesized contextual knowledge becomes an intelligence-rich surface available to adversaries.

AMH is **not** prompt injection, memory poisoning, or model exfiltration.  
It is a **post-compromise semantic reconnaissance technique** that leverages the assistant’s accumulated understanding of the user.

This repository defines the concept, its threat model, attack sequence, potential impact, and associated defensive strategies.

**Author:** Ben Phelps

> This repository supersedes the original `caleb-branton/csce-research` repo, which is no longer accessible. All content here is the same original research, re-hosted under the author's primary account.

---

## **What Makes AMH Distinct**

Traditional data exfiltration focuses on raw assets:

- credentials
    
- documents
    
- emails
    
- configuration files
    
- logs
    
- source code
    

AMH instead targets the assistant’s **internal semantic model of the user**—a distilled and searchable representation generated through normal interaction.

This model may contain:

- behavioral patterns and routines
    
- relationship mappings and social context
    
- personal goals, concerns, and long-term plans
    
- organizational responsibilities and workflows
    
- technology usage patterns
    
- psychological or emotional cues
    

AI assistants convert fragmented information into coherent summaries—and go further, **inferring** attributes the user never explicitly stated: emotional state, relationship friction, financial pressure, risk tolerance, daily rhythm.

This is what makes AMH categorically different from data theft, not merely more convenient than it. Raw exfiltration is bounded by what the user wrote down; AMH also yields the assistant's *derived* conclusions about the user—intelligence that exists in no file, email, or document on the device. An attacker reading stolen files must still infer the person behind them. An attacker querying the assistant is handed those inferences directly.

---

## **Why AMH Matters**

As AI assistants gain:

- long-term memory,
    
- deeper context retention,
    
- cross-platform integration, and
    
- access to personal or workplace data,
    

they increasingly function as **compressed personal knowledge bases**.

During a breach, they act as high-bandwidth intelligence surfaces, enabling attackers to extract meaningfully structured insights far more efficiently than traditional forensic or manual search methods.

AMH reframes the impact of post-compromise access:

- **Old question:** “What files were accessed?”
    
- **New question:** “What does the assistant _know_ about the user?”
    

This shift has implications for personal security, enterprise risk, insider-threat modeling, and breach-response workflows.

---

## **Repository Structure**

- **`01_overview.md` — Overview**  
    Conceptual introduction and high-level framing of AMH.
    
- **`02_threat-model.md` — Threat Model**  
    Adversary profiles, preconditions, and assets at risk.
    
- **`03_attack-chain.md` — Attack Sequence**  
    Generalized kill-chain describing AMH exploitation.
    
- **`04_examples.md` — Example Scenarios**  
    Hypothetical cases illustrating AMH across environments.
    
- **`05_defensive-controls.md` — Mitigation Strategies**  
    Controls for individuals, enterprises, SOC teams, and AI platform designers.
    
- **`06_references.md` — Related Work**  
    Sources describing partially overlapping AI security risks.
    
- **`diagram.mmd` — Visual Model**  
    Mermaid diagram depicting the AMH process.
    
- **`license` — MIT License**  
    Open-use licensing for research and derivative work.
    

---

## **License**

This project is provided under the terms of the **MIT License**.  
See `license` for details.
