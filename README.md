# Pariox — IT Helpdesk AI Demo

A custom fine-tuned AI model for IT helpdesk automation. Built by [Pariox](https://pariox.co) — private AI for business.

## What this is

A TinyLlama 1.1B model fine-tuned on IT helpdesk data using LoRA/QLoRA. It answers common IT support questions with structured, step-by-step responses — trained to match the format, tone, and procedures of a specific company.

This repo contains the demo version trained on generic IT data. Client versions are trained on the client's own ticket history, documentation, and internal procedures.

## Live demo

Try it here: [pariox.co/demo](https://pariox.co)

## What it does

- Handles Tier 1 IT support questions automatically
- Answers in a structured format with numbered steps
- Runs privately — no data sent to external servers
- Improves over time as more ticket data is added

## Example

**Input:**
```
My VPN won't connect.
```

**Output:**
```
VPN Troubleshooting Steps:
1. Confirm your internet connection is working
2. Open the VPN client and check you're using server: vpn.company.com
3. Verify your MFA app is generating codes correctly
4. Try disconnecting and reconnecting
5. Restart the VPN client completely
6. Alternative server: vpn2.company.com

If none of these work, call helpdesk at ext. 100.
```

## Tech stack

- Model: TinyLlama 1.1B Chat
- Fine-tuning: LoRA via PEFT + TRL
- Hardware: NVIDIA RTX 4060 (local training)
- Interface: Gradio
- Deployment: Local or RunPod

## For businesses

This demo is trained on generic IT data. A production version is trained on your company's:
- Internal documentation
- Past support tickets
- Escalation procedures
- System names and configurations

**Contact:** victor@pariox.co
