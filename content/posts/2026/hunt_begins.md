---
showTableOfContents: true
title: "The Hunt Begins in 2026: Building Numinon and the Future of Threat Hunting"
type: "page"
---

![begins](/images/hunt_begins/001.png)

<br>

## And So It Begins...

What if your defensive posture never slept?

Not shifts, not on-call rotations—but truly continuous hunting. Agents reasoning over telemetry 24/7, building threat narratives in real-time, escalating high-fidelity leads while your team focuses on what humans do best: strategy, creativity, high-stakes decisions.

This isn't theory. We're building it. And we're teaching you to build it with us.

---

## The Problem: Threat Hunting as a Luxury Commodity

Threat hunting today is expensive.

Not because the tooling is expensive (Sysmon, Zeek, Wazuh, Velociraptor, Suricata are all free). Not because the data is expensive (storage is cheap). 

But because **human expertise doesn't scale**.

Elite threat hunting requires:
- Dedicated practitioners who understand adversary TTPs
- 24/7 coverage (attackers don't work business hours)
- Deep telemetry analysis (not just alert triage)
- The creativity to hunt for unknown threats (not just detect known patterns)

For Fortune 500s with seven-figure+ security budgets, this is achievable. Build a team. Run shifts. Hunt continuously.

For everyone else? Threat hunting is episodic at best. A luxury reserved for post-incident forensics or quarterly "hunting sprints."

**Meanwhile, the adversary operates on unbounded time.**

They persist across sessions, days, weeks. They adapt. They wait. 
And our defenses—built around point-in-time detection and human-dependent analysis—are always one step behind.

---

## The Inflection Point: Why Now Is Different

In late 2025, I took some time off. 
Like many of us, I had a backlog of articles, research papers, and videos I'd been meaning to consume but never found the time for.

**What I discovered changed everything.**

The convergence of three things made agentic threat hunting not just possible — but **inevitable**:

### 1. LLMs Can Reason Over Unstructured Data
GPT-4 class models (and beyond) don't just pattern-match. They reason. They build narratives. 
They connect disparate evidence into coherent hypotheses.

Feed Claude Code a sequence of Sysmon process creation events, network connections, and file modifications — and it can diagnose "credential dumping → lateral movement → data exfiltration" without hardcoded correlation rules.


### 2. Orchestration Frameworks Enable Agent Coordination
Frameworks like Google's ADK let us build teams of specialized agents that coordinate, delegate, and reason together.

One agent monitors endpoint telemetry. Another analyzes network metadata. A third queries historical archives. A fourth validates findings against MITRE ATT&CK. They work as a nervous system — not isolated neurons.

### 3. The Economics Finally Work
Local LLMs (Llama, Mistral) handle routine tasks at near-zero marginal cost. Premium models (Gemini, Claude) are reserved for complex reasoning. Self-hosted infrastructure is affordable.

**For the first time, continuous agentic hunting costs less than hiring one additional analyst.**

This isn't incremental improvement. It's a capability unlock. And the window is open — early movers will define the category.

*Ready to build this? [Join the course waitlist](../../course.md)*

---

![quote](/images/hunt_begins/002.png)

---

## What We're Building

**Numinon** is AionSec's open-source, sovereign agentic threat hunting platform.

The name comes from Kant's concept of the *noumenon*—that which is knowable through intuition rather than empirical observation alone. It represents the fusion we're building: human intuition guiding autonomous intelligence.

### The Core Philosophy

Numinon is built on three pillars:

**1. Human-Centric, Agent-Driven**
We reject the false choice between "human expertise" and "AI automation." The future is symbiosis. Hunters don't become obsolete—they become orchestrators. One practitioner managing a team of autonomous agents achieves coverage previously requiring dedicated teams.

**2. Continuous, Not Point-in-Time**
Traditional detection operates in snapshots. Alerts fire. Tickets close. The adversary persists. Numinon maintains stateful awareness—agents hunt continuously, building narratives in real-time, not reconstructing timelines post-incident.

**3. Sovereign and Open-Source**
Your telemetry. Your logic. Your deployment. No vendor SaaS. No black boxes. Modular, adaptable, community-driven. The platform adapts to your environment like quicksilver—no "one size fits all" configurations.

### The Technical Stack (Level 1 MVP)

Numinon's architecture is designed for practitioners to build themselves:

**Telemetry Sources:**
- **Sysmon** (endpoint): Process execution, network connections, credential access, injection detection
- **Zeek** (network): Protocol-level metadata (DNS, HTTP, SMB, SSL/TLS, custom scripts)

**The Receptor (Stateful Memory Core):**
- Go-based analysis engine maintaining a 10-minute sliding window of telemetry
- Not a database—a living memory agents query for context
- Events older than 10 minutes archive to DuckDB (cold storage, queryable via MCP)

**Agent Orchestration:**
- Multi-model LLM strategy: Local models (Llama) for routine tasks, premium models (Gemini, Claude) for complex reasoning
- Specialized agents: Reconnaissance, analysis, validation, action
- Coordination via Google ADK and Model Context Protocol (MCP)

**Knowledge Resources:**
- MITRE ATT&CK framework integration
- Sigma rules library
- OSINT agent capabilities
- Optional threat intel feeds

**Database & Normalization:**
- DuckDB for historical telemetry (fast analytical queries, embeddable, Parquet support)
- ECS (Elastic Common Schema) for normalization
- Languages: Golang (primary), Python (secondary)

This is the **minimal viable stack**. Levels 2 and 3 (launching 2027-2028) add Windows Event Logs, PowerShell Script Block logs, Suricata, Wazuh, and Velociraptor.

But 80% of modern threats? Detectable with Sysmon + Zeek + agentic reasoning.

**[CTA 2: INLINE LEARN MORE - Place here]**
*Want to build Numinon yourself? The course launches Q2 2026. Join the waitlist: [MAILERLITE_LINK]*

---

![quote](/images/hunt_begins/003.png)

---

## How We're Building It: The Course + Platform Strategy

We're not just shipping a platform. We're teaching practitioners to build it themselves.

### Q2 2026: "Building Numinon" Course (Level 1 of 3)

**What You'll Build:**
A fully functional agentic threat hunting system from scratch. Deploy the Receptor. Integrate Sysmon and Zeek. Orchestrate multi-model agents. Implement clinical reasoning over telemetry. Build autonomous action loops with safety rails.

**Who It's For:**
Threat hunters, detection engineers, security practitioners who want to own this capability—not rent it from a vendor.

**What Makes It Different:**
- Hands-on deployment (not theory)
- Open-source stack (no vendor lock-in)
- Sovereign architecture (you control everything)
- Cost-optimized design (local + premium LLM strategy)
- Real-world hunting scenarios (credential dumping, C2 detection, lateral movement, exfiltration)

**Who's Teaching It:**
I've been teaching security practitioners for the past year as an instructor at AntiSyphon—delivering workshops and multi-day courses on threat hunting and detection engineering. This course is the culmination of what I've been building and teaching in parallel.

**Timeline:**
Course launches Q2 2026. Join the waitlist: [MAILERLITE_LINK]

### Q3-Q4 2026: Open-Source Platform Launch

The platform is **100% free and open-source**.

Why? Because democratization isn't marketing—it's our mission. Elite defensive capabilities shouldn't be locked behind vendor paywalls.

**Modular Architecture:**
Start with the MVP (Sysmon + Zeek). Add telemetry sources as needed (WEL, PowerShell, Suricata, Wazuh, Velociraptor). Choose your LLM models (local, premium, or hybrid). Deploy on-prem, cloud, or hybrid.

Like quicksilver, Numinon adapts to your environment.

**Community-Driven:**
GitHub repo. Contributor ecosystem. Shared detection libraries. Open development roadmap. The community improves the platform together.

### 2027-2028: Levels 2 & 3 Courses + Certification

- **Level 2 (Intermediate):** Extended telemetry integration, advanced agent orchestration, campaign-level threat narratives
- **Level 3 (Advanced):** Full-stack deployment, custom integrations, autonomous action loops at scale
- **Three-tier certification:** CAATH-Foundational, CAATH-Practitioner, CAATH-Architect

---

![quote](/images/hunt_begins/004.png)
---

## Why This Matters: The Mission Beyond the Code

This isn't just about building better tooling. It's about fundamentally shifting how we think about defense.

### Symbiosis Over Replacement

The "AI will replace security analysts" narrative is a false dichotomy.

Hunters aren't being replaced—they're being promoted. From manual log analysis to orchestrating autonomous agent teams. From tactician to strategist. From hunting one hypothesis at a time to managing distributed hunts across your entire environment.

The craft remains. Intuition, creativity, adversarial thinking—these are irreplaceable. But now they're amplified by agents that operate at machine speed and never tire.

### Democratization of Elite Defense

If you don't have a dedicated threat hunting team with 24/7 coverage, you're not defenseless—you're just operating with one hand tied behind your back.

Numinon changes the economics. One practitioner + agentic system = continuous hunting that rivals (and in some cases exceeds) what dedicated teams achieve manually.

This levels the playing field. Small security teams. Solo practitioners. Startups. Regional organizations. Everyone gets access to elite capabilities.

### Sovereignty and Transparency

Vendor SaaS means trusting someone else with your telemetry, your detection logic, and your response actions.

Sovereign hunting means:
- **Your data stays yours** (compliance, data residency, trust)
- **Your logic is auditable** (no black-box algorithms)
- **Your deployment is flexible** (on-prem, cloud, air-gapped)
- **Your costs are predictable** (no per-seat licensing, no surprise bills)

This isn't anti-cloud. It's pro-sovereignty.

### The Eternal Hunt

The adversary operates on unbounded time—Aion, not Chronos. They persist. They adapt. They wait.

Our defenses have operated on Chronos: business hours, shift rotations, episodic hunting sprints.

**With Numinon, we match their persistence with our own.**

Continuous hunting becomes the default posture. Not a luxury. Not a quarterly exercise. The baseline.

---

![quote](/images/hunt_begins/005.png)
---

## What Happens Next

I'm building Numinon in public. Sharing what I learn as I build it. Teaching the system as it takes shape.

**The course launches Q2 2026.** Join the waitlist: [MAILERLITE_LINK]

**The platform launches Q3-Q4 2026.** Open-source, on GitHub, free for everyone.

This is collaborative, not transactional. The community builds this together.

---

## The Invitation: Build This With Us

I'm not building Numinon in a vacuum and unveiling it as a finished product. I'm building it in public. Sharing what I learn. Teaching the system as I build it.

This is collaborative, not transactional.

**If you're a threat hunter,** this is your opportunity to evolve from analyst to orchestrator.

**If you're a detection engineer,** this is the next frontier—teaching agents when and how to apply your rules.

**If you're a security leader,** this is how you achieve continuous hunting without hiring a dedicated team.

**If you're a solo practitioner,** this is how you punch above your weight class.

The technology exists. The architecture is proven. The economics finally work.

**The only question is: who builds it first?**

---

## The Hunt Begins in 2026

The adversary operates on unbounded time.

With Numinon, so do you.

**Join the course waitlist:** [MAILERLITE_LINK]

**Follow the build:** aionsec.ai

**Connect on LinkedIn:** [Faan Rossouw](https://linkedin.com/in/faanrossouw) | [AionSec](https://linkedin.com/company/aionsec)

**The hunt is eternal. Let's make it ours.**



---

[|TOC|]({{< ref "../_index.md" >}})

[//]: # ([|NEXT|]&#40;{{< ref "./02_history.md" >}}&#41;)

