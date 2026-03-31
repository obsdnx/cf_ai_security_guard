# cf_ai_security_guard

A cybersecurity AI assistant built on Cloudflare's Agents platform. Ask it anything about vulnerabilities, network attacks, CTF challenges, secure coding, or breaking into cybersecurity — it explains everything from first principles.

## Live Demo

https://security-guard.systemsobsidian.workers.dev

## What it does

- Explains vulnerability classes (SQLi, XSS, buffer overflows, RCE, privilege escalation)
- Walks through how network attacks work at a low level (SYN floods, ARP poisoning, MITM)
- Gives CTF hints and methodology
- Explains security tools (nmap, Burp Suite, Wireshark, Metasploit) from the ground up
- Remembers your entire conversation across sessions via Durable Objects

## Architecture

- **LLM**: Kimi K2.5 via Cloudflare Workers AI
- **State & Memory**: Durable Objects with built-in SQL — conversation history persists across sessions automatically
- **Coordination**: Cloudflare Agents SDK (AIChatAgent) handles message routing, streaming, and tool orchestration
- **Frontend**: React chat UI served via Cloudflare Pages
- **Tools**: Weather, timezone, calculator, task scheduler

## Running locally
```bash
npm install
npm run dev
```

Open http://localhost:5173

## Deploying
```bash
npm run deploy
```
