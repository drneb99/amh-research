# Assistant Memory Harvesting (AMH) Research  
*Author: Ben Phelps*  
*License: MIT*

---

## Overview

Assistant Memory Harvesting (AMH) is a proposed **post-compromise** technique in which an attacker—having already gained control of a victim's device or authenticated session—interrogates a memory-enabled AI assistant to harvest the structured profile it has accumulated about the user.  
Unlike traditional data theft, which targets raw files, AMH targets the assistant's **synthesized model of the user**: the behavioral, relational, and contextual understanding it has built—and the inferences it volunteers—through normal interaction. This is most pronounced in memory-enabled systems, multi-turn agents, and embedded assistants.

This repository contains the formal structure, research notes, threat modeling, defensive considerations, and supporting examples for the AMH methodology.

---

## Repository Structure

### **1. Abstract & Overview**  
`01_overview.md`  
High-level explanation of AMH, its origin, conceptual framing, and background.

### **2. Threat Model**  
`02_threat-model.md`  
Defines attacker goals, preconditions, capabilities, and boundaries of the AMH model.

### **3. Attack Chain**  
`03_attack-chain.md`  
Detailed breakdown of how AMH exploitation occurs, from initial low-risk probing through targeted semantic extraction, structured consolidation, and weaponization.

### **4. Examples & Prompt Evidence**  
`04_examples.md`  
Hypothetical prompt sequences illustrating memory probing, profile extraction, and identity inference across personal, organizational, and technical settings.

### **5. Defensive Controls**  
`05_defensive-controls.md`  
Mitigation strategies for AI vendors, agent developers, and system integrators:  
memory isolation, semantic throttling, inference-limiting policies, and model-level safeguards.

### **6. References & Notes**  
`06_references.md`  
Supporting readings, related works, adjacent fields (e.g., memory poisoning, semantic leakage), and citations.

### **Diagram**  
`diagram.md`  
Visual representation of the AMH flow, conceptual model, and architecture implications.

---

## Abstract

AI systems with memory, persistent persona layers, or long-context retention accumulate internalized user data, learned behavioral patterns, and latent psychological or contextual insights. Once an attacker controls the user's device or session, this accumulated understanding becomes directly queryable.  
AMH explores how an attacker probes this surface and weaponizes the assistant's own summarization to obtain:

- Stress levels  
- Relationship dynamics  
- Habits and routines  
- Personal vulnerabilities  
- Intentions  
- Emotional states  
- Patterns of reasoning  
- Private contextual information held in memory  

AMH is **strictly a post-compromise technique**: it presupposes that the attacker has already obtained access by other means (malware, a stolen session, or physical access to an unlocked device). AMH itself introduces no exploit—it abuses the assistant's *legitimate* memory and summarization features to convert accumulated context into actionable intelligence.

---

## Purpose of This Work

The goal of this research is to:

1. Propose formal terminology for this post-compromise semantic-reconnaissance technique.  
2. Document reproducible examples.  
3. Establish a structured threat model for AMH.  
4. Provide a standard attack chain for academic study.  
5. Offer vendor-neutral defensive recommendations.  

This repo is intended for:

- AI safety researchers  
- Cybersecurity professionals  
- SOC analysts and threat modelers  
- AI developers integrating memory-enabled systems  
- Organizations deploying multi-agent architectures  

---

## Ethical Disclaimer

All research within this repository is designed for **defensive**, **academic**, and **safe** evaluation of semantic leakage risks in AI systems.  
No techniques described here bypass system security, execute code, or compromise devices.

This work focuses solely on understanding model behavior to enhance future safety.

---

## License

This project is licensed under the MIT License.  
See the `LICENSE` file for details.
