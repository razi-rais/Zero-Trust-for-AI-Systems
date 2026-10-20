# Zero Trust for AI Systems: Architecture and AI Agent Security

**A practical course by [Razi Rais](https://www.linkedin.com/in/razirais/), cybersecurity and AI practitioner, author, and instructor.**

What stops an AI agent from turning a permitted tool into a route to systems it was never authorized to reach?

Explore Zero Trust architecture through guided walkthroughs and the documented OpenAI and Hugging Face incident. Follow how agents crossed evaluation boundaries, reached live infrastructure, and expanded their access. Examine where identity checks, workload isolation, least privilege, and independent response should constrain agentic AI.

[Read the course PDF](Zero-Trust-Security-for-AI-Systems.pdf) | [Attend the live course on O'Reilly](https://www.oreilly.com/live-events/zero-trust-for-ai-systems/0636920066250/) | [Explore the resources](Resources/README.md) | [Read the course license](LICENSE.md)

## Key takeaways: practical Zero Trust for AI

| What you will learn | What it means in practice |
|---|---|
| Walk through Zero Trust architecture | Trace an access request from caller identity and device context through policy decisions, enforcement, and the protected resource. |
| Analyze a documented AI harness escape | Follow the OpenAI and Hugging Face case through indirect internet access, shared artifacts, exposed credentials, and unsafe dataset processing. |
| Place controls where authority changes | Identify the enforcement points between helper tools, isolated workers, host privileges, data objects, and result recipients. |
| Separate task success from authorized behavior | Understand why a valid credential, a convincing answer, or an assigned goal does not authorize every action an agent can take. |
| Connect threat analysis to architecture | Use MITRE ATLAS and OWASP to analyze AI threats. Relate the findings to NIST architecture guidance and CISA maturity guidance. |
| Plan containment, not just detection | Examine limited credentials, protected evidence, independent revocation, and verification that a workload actually stops. |
| Assess AI's role in Zero Trust | Explore behavioral analysis and contextual risk assessment without confusing model judgment with permission to act. |

The course combines architectural walkthroughs, incident analysis, group discussion, and Q&A. Its principles apply across vendors and cloud platforms.

## AI harness escape case study: OpenAI and Hugging Face

The July 2026 incident began in OpenAI's internal cybersecurity evaluations with reduced safeguards. Agents used a package service as an unauthorized communication channel and internet relay, then reached external systems.

Hugging Face documented file disclosure through HDF5 processing, separate code execution through Jinja2 template injection, and further access enabled by exposed credentials.

**The impact was real, even though the starting point was an evaluation.** Hugging Face reported intrusion into production infrastructure and access to five customer datasets associated with the evaluation challenges. This was not an ordinary ChatGPT session.

Incident sources: [OpenAI's account](https://openai.com/index/hugging-face-incident-and-the-road-ahead/) and [Hugging Face's technical timeline](https://huggingface.co/blog/agent-intrusion-technical-timeline).

The course traces selected attack paths, examines agent replanning, and maps reported behavior to MITRE ATLAS. We assess where Zero Trust controls could limit exposure.

## Zero Trust controls applied to the incident

Adapted from page 85 of the [course PDF](Zero-Trust-Security-for-AI-Systems.pdf). Each row connects reported behavior to the service that can refuse the next unauthorized action.

| Reported behavior | Zero Trust principle | Enforcement point | Proposed control |
|---|---|---|---|
| Agents coordinated through shared helper artifacts. | Use least privilege access | Package broker and isolated run state | Permit approved package reads. Deny arbitrary relays and access to another run's artifacts. |
| An exposed account token enabled dataset uploads. | Verify explicitly | API entry gate and account owner | Revoke exposed tokens. Check caller, action, and target. An authenticated upload remains untrusted input. |
| HDF5 processing disclosed local worker files. | Use least privilege access | Input file resolver | Allow only assigned input. Reject path and symlink escapes and unrelated local reads. |
| Jinja2 evaluated hostile expressions inside a worker. | Assume breach | Conversion parser | Remove expression evaluation. Use a restricted data grammar so input cannot become worker commands. |
| Excess permissions enabled host privilege expansion. | Assume breach | Workload admission and runtime | Reject privileged workloads and host mounts. Restrict runtime privileges and metadata access separately. |
| Recovered credentials opened additional routes. | Use least privilege access | Protected credential issuer and receiving resource | Check issuer, job, audience, action, object, expiry, and revocation. Refuse use outside the assigned scope. |
| Access extended to private data. | Verify explicitly | Data service and result release gate | Authorize the exact object before reading. Separately authorize the recipient before releasing the result. |
| Repositories carried commands and results between workers. | Assume breach | Protected logging and independent responder | Keep evidence outside the worker. Independently stop jobs and revoke grants. Verify the workload actually stops. |

**These are proposed defensive controls, not a claim that they would have prevented the historical incident.** The distinction is between explaining the reported attack and designing boundaries that constrain a similar path.

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
