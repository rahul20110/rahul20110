<div align="center">
  <img src="assets/banner.svg" width="880" alt="Rahul Kumar — AI engineer. I build AI agents and debug them down to the packets." />
</div>

<p align="center">
  <a href="https://linkedin.com/in/jhajharia110"><img src="https://img.shields.io/badge/LinkedIn-jhajharia110-0F1720?style=flat-square&logo=linkedin&logoColor=C97E4A" alt="LinkedIn" /></a>
  <a href="mailto:rahul20110@iiitd.ac.in"><img src="https://img.shields.io/badge/Email-rahul20110%40iiitd.ac.in-0F1720?style=flat-square&logo=gmail&logoColor=C97E4A" alt="Email" /></a>
  <a href="https://pypi.org/project/fika-langwatch/"><img src="https://img.shields.io/badge/PyPI-fika--langwatch-0F1720?style=flat-square&logo=pypi&logoColor=C97E4A" alt="PyPI" /></a>
</p>

Most engineers stop at the API. I keep going — from the agent's prompt down to the bytes on the wire. Here's the stack, top to bottom.

### `L5 · AGENTS` — what people talk to

At [FIKA (powersmy.biz)](https://powersmy.biz) I build AI agents that hold real conversations, on whatever channel the customer is on:

- An outbound voice agent (LiveKit + Gemini) scaled to **1M+ calls a month** in **10 Indian languages**, with AI post-call analysis synced to client CRMs
- **15+ chat agents** across WhatsApp, Instagram, email, and web — fintech, healthcare, real estate, e-commerce — wired into live CRMs, payments, and booking APIs, so answers stay true when the data changes
- An email support agent architected for **60K tickets/month** on AWS (Bedrock, Kafka, ECS Fargate)

### `L3 · GATEWAY` — what keeps them honest

Agents are only as reliable as the layer under them. I run a self-hosted multi-provider LLM gateway (routing, fallback, per-customer cost tracking) that powers everything above, and I benchmark obsessively — one measured pass over sample rates, VAD, and STT/TTS/LLM providers cut voice cost **26% per minute**.

### `L1 · PACKETS` — where the real bugs live

When ~90% of calls started failing in bursts, the answer wasn't in the logs — it was in the pcap. A carrier was emitting SIP-over-TCP responses with broken framing, and a keep-alive heuristic was corrupting the stream for every later call on the connection. Found it in raw packet captures, fixed it in the parser, shipped it.

| Project | What it does |
|---|---|
| [`rahul20110/sip`](https://github.com/rahul20110/sip) | Fork of LiveKit's SIP bridge carrying that TCP framing fix — plus recording rebuilt as an **in-process service**: taps already-decoded PCM into stereo WAV (caller left, agent right) and uploads to S3, replacing a separate egress server at negligible CPU cost |
| [`fika-langwatch`](https://pypi.org/project/fika-langwatch/) | Automatic LLM fallback chains for LangChain — per-key health tracking, recovery detection, Slack/email alerts when a provider dies mid-traffic |
| [`fika-logger`](https://pypi.org/project/fika-logger/) | Structured logging for agent fleets — error deduplication, distributed trace IDs, opens GitHub issues on new failures by itself |

### `THE STACK` — tools I reach for

<p>
  <img src="https://img.shields.io/badge/Python-0F1720?style=flat-square&logo=python&logoColor=C97E4A" alt="Python" />
  <img src="https://img.shields.io/badge/FastAPI-0F1720?style=flat-square&logo=fastapi&logoColor=C97E4A" alt="FastAPI" />
  <img src="https://img.shields.io/badge/LangGraph-0F1720?style=flat-square&logo=langchain&logoColor=C97E4A" alt="LangGraph" />
  <img src="https://img.shields.io/badge/LiveKit-0F1720?style=flat-square" alt="LiveKit" />
  <img src="https://img.shields.io/badge/SIP%2FWebRTC-0F1720?style=flat-square" alt="SIP / WebRTC" />
  <img src="https://img.shields.io/badge/MongoDB-0F1720?style=flat-square&logo=mongodb&logoColor=C97E4A" alt="MongoDB" />
  <img src="https://img.shields.io/badge/PostgreSQL-0F1720?style=flat-square&logo=postgresql&logoColor=C97E4A" alt="PostgreSQL" />
  <img src="https://img.shields.io/badge/Redis-0F1720?style=flat-square&logo=redis&logoColor=C97E4A" alt="Redis" />
  <img src="https://img.shields.io/badge/Kafka-0F1720?style=flat-square&logo=apachekafka&logoColor=C97E4A" alt="Kafka" />
  <img src="https://img.shields.io/badge/Docker-0F1720?style=flat-square&logo=docker&logoColor=C97E4A" alt="Docker" />
  <img src="https://img.shields.io/badge/Kubernetes-0F1720?style=flat-square&logo=kubernetes&logoColor=C97E4A" alt="Kubernetes" />
  <img src="https://img.shields.io/badge/GCP-0F1720?style=flat-square&logo=googlecloud&logoColor=C97E4A" alt="Google Cloud" />
  <img src="https://img.shields.io/badge/AWS-0F1720?style=flat-square" alt="AWS" />
  <img src="https://img.shields.io/badge/Wireshark-0F1720?style=flat-square&logo=wireshark&logoColor=C97E4A" alt="Wireshark" />
</p>

<p>
  <img src="https://github-readme-stats.vercel.app/api?username=rahul20110&show_icons=true&hide_border=true&bg_color=00000000&title_color=C97E4A&icon_color=C97E4A&text_color=8FA3B0&ring_color=E5B567" alt="GitHub stats" height="165" />
  <img src="https://github-readme-stats.vercel.app/api/top-langs?username=rahul20110&layout=compact&hide_border=true&bg_color=00000000&title_color=C97E4A&text_color=8FA3B0" alt="Top languages" height="165" />
</p>

### `PING` — reach me

Fastest route is [LinkedIn](https://linkedin.com/in/jhajharia110) or [rahul20110@iiitd.ac.in](mailto:rahul20110@iiitd.ac.in). If it involves agents, hard latency budgets, or a bug nobody can find — I want to hear about it.

<div align="center">
  <sub><code>64 bytes from rahul: icmp_seq=1 ttl=64 — reply guaranteed</code></sub>
</div>
