# cf_ai_security_guard

A stateful cybersecurity intelligence assistant built on Cloudflare's newest primitives.

## Why this is useful 

Most AI assistants suffer from a knowledge cutoff, making them unreliable for discussing vulnerabilities discovered last week. I wanted to build an assistant that doesn't just guess from its weights: our agent fetches live data, caches it globally, and remembers everything.

## Live Demo

https://security-guard.systemsobsidian.workers.dev

## The Stack

- **Orchestration:** Cloudflare Agents SDK (`AIChatAgent`) handles message routing, streaming, and tool orchestration
- **Inference:** Kimi K2.5 via Workers AI
- **Persistent Memory:** Durable Objects with built-in SQL. This maintains a high-consistency record of every conversation across sessions
- **Global Intelligence Cache:** Workers KV — CVE lookups are cached at the edge globally, *reducing redundant outbound API calls* and improving response times
- **Zero-Infra Deployment:** The React frontend and entire agentic backend are bundled into a single Worker — no external databases, no containers, just V8 isolates

## Key Features

- **Live CVE Intel:** When asked about a specific vulnerability, the agent triggers a real-time tool call to fetch live data from the National Vulnerability Database via `cve.circl.lu`
- **First-Principles Explanations:** Explains complex topics — buffer overflows, SYN floods, ARP poisoning — by breaking down what is actually happening at the packet and memory level
- **Persistent Investigation History:** Conversation state survives restarts and deploys via Durable Objects
- **Edge Performance:** Runs across Cloudflare's global network with near-zero cold starts and localised execution


## Running Locally
```bash
npm install
npm run dev
```

Open http://localhost:5174

## Deploying
```bash
npm run deploy
```
