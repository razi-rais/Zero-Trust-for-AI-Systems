# Zero Trust for AI Systems

**Course resources by [Razi Rais](https://www.linkedin.com/in/razirais/), cybersecurity and AI practitioner, author, and instructor.**

How should an enterprise control an AI system that can choose tools, access data, and act on results? This course examines that question through Zero Trust architecture, technical walkthroughs, and incident analysis.

[Read the course PDF](Zero-Trust-Security-for-AI-Systems.pdf) | [Attend the live course on O'Reilly](https://www.oreilly.com/live-events/zero-trust-for-ai-systems/0636920066250/) | [Explore the resources](Resources/README.md) | [Read the course license](LICENSE.md)

## The core thesis

**An AI system's authority must be defined and enforced independently of the model's judgment.**

A legitimate task does not authorize every method of completing it. An authenticated caller does not make supplied data safe. Permission to read an object does not automatically authorize releasing its contents to another recipient.

Zero Trust makes those distinctions explicit. Each resource evaluates the caller, requested action, exact target, and relevant context. Credentials have limited scope and lifetime. Workloads operate within enforced boundaries. Evidence and response authority remain outside a potentially compromised job.

AI can also support Zero Trust through device profiling, behavioral analysis, and anomaly detection. Those capabilities inform security decisions. They do not replace authorization, isolation, or accountable response.

The practical test is straightforward: the assigned job should succeed, while requests outside its authority should fail.

## About the author

**Razi Rais** brings more than 20 years of experience across cybersecurity, systems architecture, engineering, and product leadership, including work at Microsoft. He coauthored *Zero Trust Networks, Second Edition* and *Azure Confidential Computing and Zero Trust*. He is a Microsoft Certified Trainer and serves on the GIAC advisory board.

His teaching connects architectural principles to the decisions practitioners face when designing, operating, and defending real systems.

[Author website](https://www.razibinrais.com/) | [Website contact page](https://www.razibinrais.com/contact/) | [Contact Razi on LinkedIn](https://www.linkedin.com/in/razirais/)

## What the course covers

| Area | What we examine |
|---|---|
| Zero Trust foundations | The limits of perimeter trust, explicit verification, least privilege, and the assumption of compromise. |
| Architecture and maturity | Policy decisions, enforcement, contextual access, organizational adoption, and the distinct roles of NIST architecture guidance and CISA maturity guidance. |
| AI risk and assurance | How model output, action selection, and system authority differ. Why a convincing answer or a valid credential is insufficient evidence of a safe action. |
| Threat frameworks | Using OWASP and MITRE ATLAS to describe AI risks, analyze observed behavior, and connect threats to enforcement points. |
| Incident analysis | The OpenAI and Hugging Face research incident, including agent replanning, shared state, input processing flaws, credential exposure, and changes in authority. |
| Control placement and response | Constraints on helpers and workers, authorization for objects and recipients, protected evidence, revocation, isolation, and verification that a job actually stops. |
| AI supporting Zero Trust | Opportunities for contextual risk assessment and detection, considered alongside the controls that must remain independently enforceable. |

Incident walkthroughs distinguish reported evidence from proposed defensive designs. A suggested control is not presented as proof that it would have prevented the historical incident.

The course combines conceptual explanations, scenario walkthroughs, group discussion, and Q&A. Its principles apply across vendors and cloud platforms.

## Who this is for

Security and systems architects, engineers, security practitioners, and technical leaders who need to evaluate AI workflows and their access to enterprise resources.

Bring a basic understanding of authentication, authorization, networking, and cloud systems. Familiarity with AI workflows is helpful. Prior specialization in Zero Trust is not required.

## Course PDF

[Read or download Zero Trust Security for AI Systems](Zero-Trust-Security-for-AI-Systems.pdf).

See the [course material license](LICENSE.md) for personal study permissions and uses requiring written permission.

## Resources

The reference readings below complement the course PDF. This repository does not include a deployable reference implementation.

| Reading | Purpose |
|---|---|
| [NIST SP 800 207](Resources/NIST-SP-800-207-Zero-Trust-Architecture-2020.pdf) | The foundational Zero Trust architecture reference. |
| [NIST SP 1800 35](Resources/NIST-SP-1800-35-Implementing-Zero-Trust-Architecture-2025.pdf) | The final high level document on implementing Zero Trust architecture. |
| [CISA Zero Trust Maturity Model](Resources/CISA-Zero-Trust-Maturity-Model-2023-v2.0.pdf) | A framework for discussing adoption and maturity. |
| [OWASP LLM Top 10](Resources/OWASP-Top-10-LLM-Applications-2026.pdf) and [Agentic Applications Top 10](Resources/OWASP-Top-10-Agentic-Applications-2026.pdf) | Complementary risk references for LLM applications and agentic systems. |
| [NSA MCP security guidance](Resources/NSA-MCP-Security-Design-Considerations-2026-v1.0.pdf) | Security design considerations for workflows using the Model Context Protocol. |
| [CSA Secure Agentic System Design](https://cloudsecurityalliance.org/artifacts/secure-agentic-system-design) | An architecture reading organized around agentic system traits. Provided as an official publisher link. |

See the [resource index](Resources/README.md) for publisher sources, edition details, and document notes.

## Live course

[Join Zero Trust for AI Systems on O'Reilly](https://www.oreilly.com/live-events/zero-trust-for-ai-systems/0636920066250/).

Use the official course page for the current description, prerequisites, session availability, and registration.

## Usage and permissions

The [course material license](LICENSE.md) sets out personal study permissions, attribution requirements, and uses requiring prior written permission for original course material owned by Razi Rais.

Third party resources retain their respective copyright and license terms. The course license does not replace those terms. To request permission for the original course material, contact Razi Rais through either the [website contact page](https://www.razibinrais.com/contact/) or [LinkedIn](https://www.linkedin.com/in/razirais/).
