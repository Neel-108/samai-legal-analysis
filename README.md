## SAMAI — Legal Document Analysis Assistant

SAMAI is an AI-powered legal document analysis tool built for a legal professional in India. It performs structured risk analysis on contracts, legal notices, and regulatory filings for flagging issues by severity, explaining legal reasoning, and never crossing into legal advice.
It was deliberately built as a pure prompt-based system.


## Why no bot, no SaaS, no server:

Legal documents are confidential by definition. A SaaS product or Telegram bot would mean client documents passing through servers, API logs, third party infrastructure, and databases outside the lawyer's control. That is not acceptable in legal work regardless of how good the privacy policy is.

A self-contained prompt running inside the lawyer's own AI interface means no data stored anywhere outside their session, no logs, no third party exposure. The lawyer pastes the document and gets the analysis and closes the window. Nothing persists especially if "improve the model for everyone" and data sharing for training the AI is disbaled.

The architecture was chosen to match the confidentiality requirements of the domain. Simplicity here is not a technical limitation it is the correct security model.


## Where RITA comes in:

SAMAI was not built through trial and error prompting. It was designed using RITA, a personal orchestration framework I developed for building reliable, structured AI workflows.

RITA operates at the level above the model. It controls how prompts are structured, how outputs are bounded, how iteration is managed, and how drift is prevented across versions. Without something like RITA, prompt-based systems tend to degrade unpredictably across versions where you fix one thing and break another.

SAMAI v1 through v1.7 were built and tested inside this framework. Every version had a defined scope, a defined failure mode to address, and a measurable outcome. 


## The testing methodology:

I ran 6 levels of adversarial testing across versions each designed to break the previous version in a different way. This was not borrowed from AI literature. It came directly from how I was trained to think about system validation as an electronics engineer.

In hardware, you do not ship a circuit because it worked once. You stress test it, find the failure modes, fix them, and test again. You document what broke and why and I applied the same logic here.

Each version of SAMAI was tested against a defined set of failure scenarios like giving advice when it should only flag, hallucinating legal principles, missing high-risk clauses, drifting outside the document. By v1.7, every identified failure mode had been addressed.


## What it handled in real testing:

The test session in this repository covers three completely different legal domains in a single session:

An Indian criminal-cum-civil legal notice under the Bharatiya Nyaya Sanhita 2023 -> weak mens rea pleading, conspiracy allegations without factual grounding, defamation risk from third party circulation.

A Delaware series LLC operating agreement -> governance structure, investor rights, liability exposure across the full document.

A US securities fraud scenario -> SEC enforcement risk, Rule 10b-5 omission liability, criminal exposure under DOJ prosecution standards.

3 jurisdictions. 3 document types. One session. No hallucinated law. No advice given. Confidence levels stated honestly throughout.


## Current status:
Delivered to the client in late December 2025. Not commercially available. Built for a specific professional use case and delivered as a complete package including usage guidelines and client documentation.

## What is in this repository:

The full system prompt at v1.7, the QA report covering adversarial testing across all versions, and client delivery documentation.

The real lawyer transcript session document is also included here with the consent of the practicing lawyer and after removing any confidential information which is consistent with why SAMAI was built the way it was.
