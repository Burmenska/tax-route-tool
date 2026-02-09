# tax-route-tool
Decision‑support tool comparing net salary by country.

Tax Route is an AI‑assisted decision‑support tool that helps tax residents from EU compare their net salary across different countries and understand where they could keep more of their income, without replacing professional tax advice.

**What is Tax Route?**

Choosing where to live and work has a huge impact on how much of your salary you actually keep after taxes and social contributions. Today, figuring this out means searching many websites, reading complex rules, and manually running numbers in different calculators.

Tax Route turns this into a guided, structured experience.

You describe your situation in simple terms (salary, country and region, family status, target countries), and the tool will:

Estimate your net salary in your country.

Estimate your net salary in selected destination countries using simplified public tax rules.

Show a side‑by‑side comparison of gross vs net, effective tax rate, and key caveats.

Explain the main assumptions and limitations in plain language, so you know what to discuss with a human advisor.

This repository contains the public shell of the project: documentation, high‑level architecture, and integration points. The core tax engine and country data live in a separate private module.


**Features**

Salary‑based comparison for Spanish residents
Start with Spanish tax residency and compare your net salary against a curated list of other countries.

Simple, guided questionnaire
A short flow collects only the inputs that materially affect the estimate: salary, Spanish region, employment type, and basic family situation.

Transparent assumptions
The tool uses simplified, conservative rules derived from public information. It clearly states what is included (e.g. basic allowances) and what is not (e.g. complex deductions, special regimes).

Decision support, not advice
Outputs are designed to support conversations with tax professionals, not to serve as formal tax or legal advice.

Extensible design
The architecture is built so new countries, more detailed regimes, or business‑owner scenarios can be added over time.



**Architecture**

Tax Route is split into two logical parts:

Public Shell (this repository)

Project documentation and roadmap.

High‑level domain models (what inputs the questionnaire collects, what outputs are produced).

Integration points and contracts for the tax engine.

Private Core Module (linked as a submodule)

Versioned country sheets (e.g. spain.json) with tax brackets, basic allowances, and social contributions.

A deterministic tax calculation engine that converts “gross salary + profile” into “net salary + effective rate”.

Tests to validate calculations against known scenarios.

The public repository never contains proprietary calculation logic or sensitive data; it focuses on design, interfaces, and collaboration.

Tech Stack (planned)
Backend / Engine: Python (salary and tax calculations, scoring logic)

API Layer: Python (FastAPI or similar) serving a simple HTTP API

Frontend (later): Web UI for the questionnaire and comparison table

Data: Structured country sheets in JSON/YAML, versioned alongside the engine

CI/CD: GitHub Actions to run tests on each change to the core logic

**⚠️ Important Disclaimer**

Tax Route is a decision‑support tool for educational and planning purposes only. It does not provide tax, legal, or financial advice. Actual tax outcomes depend on full personal and factual circumstances and on up‑to‑date laws and regulations. Always consult a qualified professional before making decisions about residence, employment, or company structure.
