<h1 align="center">🛡️ WAF Whisper</h1>

<h4 align="center">Adaptive WAF Detection & Evasion Engine</h4>

<p align="center">
  <img src="https://img.shields.io/badge/Language-Python%203-blue?style=for-the-badge&logo=python">
  <img src="https://img.shields.io/badge/Platform-Linux%20%7C%20Windows-lightgrey?style=for-the-badge">
  <img src="https://img.shields.io/badge/License-MIT-green?style=for-the-badge">
  <img src="https://img.shields.io/badge/Focus-Red%20Teaming-red?style=for-the-badge">
</p>

<p align="center">
  <a href="#-overview">Overview</a> •
  <a href="#-architecture">Architecture</a> •
  <a href="#-installation">Installation</a> •
  <a href="#-usage">Usage</a> •
  <a href="#-disclaimer">Disclaimer</a>
</p>

---

## 📖 Overview

**WAF Whisper** is an intelligent evasion framework for **authorized** web
application testing. Modern WAFs (Cloudflare, AWS, Akamai, Imperva, F5) use
heuristic analysis and behavior profiling; naive fuzzers get IP-banned on the
first burst.

WAF Whisper is built to measure a target's defenses first and adapt to them —
profiling the WAF's tolerance, discovering its inspection limits, and mutating
payloads to stay under them — so you learn *which classes of payload a WAF lets
through* rather than tripping it immediately.

---

## 🧠 Architecture — the "Guardrail-Ghost" loop

The engine prioritizes stealth over speed:

1. **Target identification** — confirm the host is live.
2. **Passive fingerprinting** — identify the WAF vendor from response headers, without attacking.
3. **Ghost mode** — rotate realistic, TLS-consistent browser headers / User-Agents.
4. **Rate-limit profiling** — binary-search the WAF's tolerance to find a safe request cadence.
5. **Payload length discovery (MPL)** — binary-search the maximum inspected body size.
6. **Fragmentation** — split payloads below the MPL to slip past complexity filters.
7. **Semantic polyglots** — keyword-filter evasion via shell expansion / `$IFS` tricks.
8. **Reporting** — emit a Markdown report (and a PoC skeleton) for confirmed bypasses.

---

## 📜 Version history

| Version | Codename | Highlights |
| :--- | :--- | :--- |
| **5.1** | **Guardrail-Ghost** | Markdown report + PoC generation, blind time-based verification. |
| **5.0** | **Guardrail-Ghost** | MPL fragmentation, binary-search rate limiting. |
| **4.2** | **Low-and-Slow** | `--delay` algorithm to defeat heuristic rate monitoring. |
| **3.0** | **Ghost Mode** | Random UA rotation + passive WAF fingerprinting. |
| **2.1** | **Proxy Link** | `-p` flag for Burp / ZAP integration. |
| **1.0** | **Whisper** | Initial release: payload mutation (URL / double-URL encoding). |

---

## ⚙️ Installation

```bash
git clone https://github.com/R00t3dbyFa17h/WAF-Whisper.git
cd WAF-Whisper
pip3 install -r requirements.txt
```

Optionally install it as a command (`waf-whisper`):

```bash
pip3 install .
```

---

## 🚀 Usage

**1. Ghost-mode scan (recommended)**
```bash
python3 waf_whisper.py -u https://target.com --ghost
```

**2. Low-and-slow evasion (manual delay)**
```bash
python3 waf_whisper.py -u https://target.com --delay 5
```

**3. Proxied scan (Burp / ZAP)**
```bash
python3 waf_whisper.py -u https://target.com -p http://127.0.0.1:8080 -v
```

```
usage: waf_whisper.py [-h] -u URL [-v] [-p PROXY] [--delay DELAY] [--ghost]

options:
  -h, --help         show this help message and exit
  -u, --url          Target URL (e.g. https://example.com)
  -v, --verbose      Enable verbose output
  -p, --proxy        Proxy URL (e.g. http://127.0.0.1:8080)
  --delay DELAY      Manual override for Low-and-Slow delay (seconds)
  --ghost            Enable Guardrail-Ghost mode (randomized UA rotation)
```

Reports are written to `WAF_Whisper_Reports/`.

---

## ⚠️ Disclaimer

**FOR AUTHORIZED TESTING AND EDUCATIONAL PURPOSES ONLY.** Using WAF Whisper
against targets without prior mutual consent is illegal. It is the end user's
responsibility to obey all applicable local, state, and federal laws. The
author assumes no liability and is not responsible for any misuse or damage
caused by this program. Because this tool sends attack-shaped traffic, run it
only against assets that are explicitly in scope for your engagement.

---

<p align="center"><b>Created by R00t3dbyFa17h / Kr0n0s510</b><br><i>Rooted by Authority. Faith by Design.</i></p>
