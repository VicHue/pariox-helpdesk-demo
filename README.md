# 🔒 Pariox Helpdesk AI

> **Private, fine-tuned language models for IT helpdesks.**
> Trained on your data. Runs on your hardware. Owned by you.

[![Live Demo](https://img.shields.io/badge/Live_Demo-Try_it_now-10b981?style=for-the-badge)](https://huggingface.co/spaces/VicHue/pariox-helpdesk-demo)
[![Built with](https://img.shields.io/badge/Built_with-PyTorch_+_PEFT-blue?style=flat-square)](https://github.com/huggingface/peft)
[![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)](LICENSE)

---

## What this is

A custom fine-tuned language model purpose-built for IT helpdesk workflows. Unlike generic AI tools (ChatGPT, Copilot) that send your data to third-party servers and return generic answers, this model:

- **Learns your business** — trained on your actual ticket history, documentation, and procedures
- **Stays on your hardware** — zero data exposure, zero cloud dependency, works offline
- **Belongs to you** — not a subscription; you own the model weights permanently

This repo contains the public demo version. Production deployments are built to client specifications.

## 👉 [Try the live demo](https://huggingface.co/spaces/VicHue/pariox-helpdesk-demo)

Ask it realistic helpdesk questions — password resets, VPN issues, phishing concerns, printer problems. Notice how the responses are structured like a real tech would write a ticket: numbered steps, specific URLs, escalation paths, and security notes.

## How it works

```
┌────────────────────┐     ┌──────────────────┐     ┌──────────────────┐
│  Client data       │ ──> │  LoRA/QLoRA      │ ──> │  Deployed on     │
│  (tickets, docs)   │     │  fine-tuning     │     │  client hardware │
└────────────────────┘     └──────────────────┘     └──────────────────┘
    Never uploaded           Training on RTX 4060      Private inference
    to third parties         (local, no cloud)         behind firewall
```

**Technical stack:**

- **Base model:** TinyLlama-1.1B-Chat (production deployments use 3B–7B models like Phi-3, Mistral, or Llama 3)
- **Fine-tuning:** LoRA rank 8, targeting `q_proj` and `v_proj`, alpha 16
- **Training framework:** Hugging Face `transformers`, `peft`, `trl`
- **Hardware:** RTX 4060 (8GB VRAM), 48GB DDR5 RAM
- **Inference:** Local PyTorch, CPU or GPU depending on deployment
- **Training data:** 150 curated IT helpdesk scenarios for this demo; production models use 500–2,000+ examples

## Why fine-tuning (not RAG or ChatGPT wrappers)

Most "AI for business" tools upload your documents to OpenAI's servers and search them at runtime. This has three problems for regulated or privacy-conscious businesses:

1. **Data leaves your network** — every query sends client data to a third party
2. **Generic answers** — the model wasn't trained on your procedures, it's just searching your docs
3. **Subscription lock-in** — no ownership, no offline use, dependent on vendor terms

Fine-tuning solves all three. The model learns your workflows during training, runs anywhere you deploy it, and answers in the format your team actually uses.

## Sample interaction

**Prompt:**
> "My VPN won't connect."

**Response:**
> VPN Connection Troubleshooting:
>
> 1. Verify your credentials — confirm username and password match your domain login
> 2. Check that you're using the correct VPN profile for your location
> 3. Restart the VPN client application
> 4. If on Wi-Fi, try a wired connection to rule out network issues
> 5. Clear any saved VPN configurations that may be corrupted
>
> If steps 1–5 don't resolve the issue, submit a ticket via the helpdesk or call ext. 100. Include error messages and screenshots.

Notice the structure: numbered steps, specific references (ext. 100), and a clear escalation path. A production model would use your actual extension, your actual ticketing system URL, and your internal shorthand.

## Use cases

**MSPs** — Tier 1 ticket deflection, technician knowledge base, onboarding tool for new hires
**Law firms** — Private document Q&A, case file lookups, clause references
**Accounting firms** — Client intake guidance, tax code references, procedure lookups
**Property management** — Lease clause lookups, maintenance triage, tenant FAQ
**Any business** — with internal knowledge that staff need to reference frequently

## Get a custom version for your business

I build these for businesses that need AI without the compliance risk:

- **Build fee:** $1,500 (50% upfront)
- **Monthly retainer:** $300/month for retraining and support
- **Timeline:** 2–3 weeks from kickoff to deployment
- **Deliverables:** Fine-tuned model, inference scripts, deployment docs, ongoing updates

No long-term contracts. You own the model outright.

## Contact

**Victor Huerta** · Bellingham, WA
🌐 [pariox.co](https://pariox.co)
✉️ [victor@pariox.co](mailto:victor@pariox.co)
💼 [LinkedIn](https://www.linkedin.com/in/victor-huerta-6058b1403/)

---

*This repository is a public demonstration. Client implementations are confidential and not published.*
