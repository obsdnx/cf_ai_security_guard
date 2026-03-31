# cf_ai_security_guard

A cybersecurity AI assistant built on Cloudflare's Agents platform. Ask it anything about vulnerabilities, network attacks, CTF challenges, secure coding, or breaking into cybersecurity — it explains everything from first principles.

## Why this is different

Most AI assistants answer security questions from training data alone — which has a cutoff date and can't know about vulnerabilities discovered last week. CyberGuard is different: when you ask about a specific CVE or vulnerable library, it fetches live data from the National Vulnerability Database in real time, then uses Cloudflare's edge network to cache that result globally so the next person who asks gets an instant response. It's not just a chatbot — it's a stateful security intelligence tool that gets smarter the more it's used, remembers your entire conversation history across sessions, and runs at the edge in hundreds of locations worldwide with no cold starts.

Built using Cloudflare's newest primitives: the Agents SDK (open beta), Workers AI, Durable Objects for persistent memory, and Workers KV for edge caching — all deployed in a single Worker with no external infrastructure.

## Live Demo

https://security-guard.systemsobsidian.workers.dev

## What it does

- Explains vulnerability classes (SQLi, XSS, buffer overflows, RCE, privilege escalation)
- Walks through how network attacks work at a low level (SYN floods, ARP poisoning, MITM)
- Gives CTF hints and methodology
- Explains security tools (nmap, Burp Suite, Wireshark, Metasploit) from the ground up
- Looks up real-time CVE vulnerability data and caches results at the edge via Workers KV
- Remembers your entire conversation across sessions via Durable Objects

## Architecture

- **LLM:** Kimi K2.5 via Cloudflare Workers AI
- **State & Memory:** Durable Objects with built-in SQL — conversation history persists across sessions automatically
- **Coordination:** Cloudflare Agents SDK (AIChatAgent) handles message routing, streaming, and tool orchestration
- **Frontend:** React chat UI served directly from the Cloudflare Worker
- **Edge Caching:** Workers KV caches CVE lookups globally, reducing latency and external API calls
- **Tools:** CVE lookup with real-time data via cve.circl.lu, edge caching via Workers KV, weather, timezone, calculator, task scheduler

## Running locally
```bash
npm install
npm run dev
```

Open http://localhost:5174

## Deploying
```bash
npm run deploy
```
