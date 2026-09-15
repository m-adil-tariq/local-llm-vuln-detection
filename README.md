# local-llm-vuln-detection

Benchmarking local, open-weight LLMs (phi3:mini, llama3.1:8b, codellama:7b) on code vulnerability detection and CWE classification across prompting strategies.

## Overview

This project evaluates whether model choice and prompting strategy affect how well locally-run LLMs can detect and correctly classify security vulnerabilities in code. Three models were tested via [Ollama](https://ollama.com) against a hand-curated, CWE-labeled dataset of 24 Python snippets spanning six vulnerability classes, under two prompt conditions (neutral vs. OWASP-guided), with two repetitions each (288 total inference calls).

## Key Findings

- All three models detect *that* a vulnerability exists more reliably than they identify *what* it is.
- `llama3.1:8b` and `codellama:7b` show high recall (0.92–1.00) but weak precision (~0.50–0.55) — strong over-flagging bias.
- `phi3:mini` is more balanced on precision/recall but scores 0% CWE-match accuracy, driven by outright fabrication of CWE identifiers.
- Prompting strategy has a small, model-dependent effect rather than a uniform improvement.

Full write-up: [`report/LLM_Vulnerability_Detection_Report.pdf`](./report.pdf)
