# nvidiascape Vulnerability Lab (Memory-Based Container Escape) 

This lab simulates a container breakout using *CVE-2025-23266 (Nvidiascape)* and Pytorch.  It demonstrates how attaackers might interact with the host system **without immediately accessing sensitive data**, and how **proper hardening, runtime security tools, andhuman investigation** reduce the damage and improve defense.   

## Lab Summary 

**Platform:** Ubuntu (host), Docker, Pytorch container 
**Type:** Home Lab | Container Security | Runtime Analysis | Blue Team 
**Author:** Me 
**Focus:** Memory-Based container escape, runtime defense, SIEM response 

## Objectives

Simulate a container escape vulnerability using Pytorch and Docker 
Understand how memory-based inspection can lead to host interaction 
Observe how hardening and runtime tools affect attacker capability 
Reflect on Blue Team responsibiities: detection, investigation, and hardening 

## Tools Used 
| Tool           | Purpose                                |
|----------------|----------------------------------------|
| **Docker**     | Containerization of PyTorch environment |
| **PyTorch**    | Used to simulate memory access          |
| **/proc**, `gdb` | Container memory/proc exploration     |
| **AppArmor**   | Runtime policy enforcement              |
| **Falco**      | Runtime detection and alerting          |
| **SIEMs (Splunk, ELK, Graylog)** | Manual log review and incident correlation |

## Procedure (Simplified) 

A. Deploy a Pytorch container inside Docker 
B. Simulate memory inspection and internal privilege escalation 
C. Attempt to escape the container and touch host system interfaces 
D. Confirm which actions are allowed or blocked 
E. Capture activity using Falco (Detector) and Apparmor (enforcer) 
F. Forward alerts to SIEM for investigation 
G. Respond and harden system based on investigation results 

## Key Findings

Containers can be breached, especially if exposed on an internal network.

Not running as root **limits** what an attacker can do - but **does not stop** them from trying.

Tools like **AppArmor** and **Seccomp** can **block the attack**, but **do not explain it**.

You still need a **SIEM and human investigation** to understand the root cause.

Proper hardening is a **continuous loop**: detect → respond → investigate → prevent.

## Personal Reflection 

This lab helped me unlearn a misconception: I originally thought that not running as root meant the container couldn't hold sensitive data.  That's false.  What really matters is **how much power the attacker has once they get in.**

I learned that runtime tools like **AppArmor** enforce policy, while tools like **Falco* detect and alert on activity. But it's still the job of the Blue team analyst to investigate, understand, and harden the system. 
in short: **you might get into my house - but you still come up short, and I'll make sure that door doesn't open again.**

 [Full Word Lap report](Nvidiascape_Lab_Report.docx)

 ## Security Concepts Reinforced 

 Never run containers as root unless necessary 

 Use **AppArmor/Seccomp** to enforce runtime restrictions 

 Use **Falco** to detect unexpected behavior 

 Investigate all alerts manually using a **SIEM**

 Apply hardening based on findings - close the loop 

 ## Part of a Larger Series 

 This is one of several home labs that I am creating to build Blue Team mastery from the ground up 
 
Connect on [Linkeding](https://www.linkedin.com/in/robert-b-6221182a1/) or follow this repsository for more container and cloud defense projects.  
