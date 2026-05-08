<p align="center">
  <img src="https://img.shields.io/badge/CVEs-3-red?style=for-the-badge" alt="CVEs"/>
  <img src="https://img.shields.io/badge/Focus-MCP%20Security-blue?style=for-the-badge" alt="Focus"/>
  <img src="https://img.shields.io/badge/Tool-mcpsec-green?style=for-the-badge" alt="Tool"/>
</p>

# 🔐 Security Research & CVE Writeups

Technical writeups for vulnerabilities I've discovered, primarily in **MCP (Model Context Protocol)** server implementations. Each writeup includes root cause analysis, proof-of-concept code, and remediation guidance.

---

## 📋 CVE Index

| CVE ID | Product | Severity | Type | Status |
|--------|---------|----------|------|--------|
| [CVE-2026-6942](./CVE-2026-6942/) | radare2-mcp | ![Critical](https://img.shields.io/badge/9.8-Critical-red) | RCE via Shell Escape | ✅ Fixed |
| [CVE-2026-42449](./CVE-2026-42449/) | n8n-mcp | ![High](https://img.shields.io/badge/8.5-High-orange) | SSRF via IPv6 Bypass | ✅ Fixed |
| [CVE-2026-35394](https://medium.com/@manthan27ghasadiya/cve-2026-35394-pwning-androids-via-ai-prompt-injection-bae9b7ff9654) | mobile-mcp | ![High](https://img.shields.io/badge/8.3-High-orange) | Prompt Injection → Android Intent | ✅ Fixed |

---

## 🎯 Research Focus: MCP Security

MCP (Model Context Protocol) is Anthropic's open standard for connecting AI agents to external tools and data sources. As AI assistants gain access to filesystems, databases, and APIs through MCP servers, the attack surface expands dramatically.

**Key findings from my research:**

- 🔴 **Trust boundary violations** - MCP servers often trust client input without validation
- 🔴 **Prompt injection via tools** - Malicious content in files/data can manipulate AI behavior  
- 🔴 **Missing input sanitization** - Shell escapes, path traversals, and SSRF are common
- 🔴 **SDK-level vulnerabilities** - Bugs in official SDKs affect all downstream servers

---

## 🛠️ Discovery Tool

All vulnerabilities in this repo were discovered using **[mcpsec](https://github.com/manthanghasadiya/mcpsec)**, an open-source security scanner I built for MCP server implementations.

```bash
# Install
pip install mcpsec

# Scan an MCP server
mcpsec scan --stdio "npx @modelcontextprotocol/server-filesystem /tmp"

# Fuzz for crashes
mcpsec fuzz --stdio "python my_server.py" --intensity high

# Static analysis
mcpsec audit --github https://github.com/org/mcp-server
```

---

## 📁 Repository Structure

```
writeups/
├── README.md                    # This file
├── CVE-2026-6942/              # radare2-mcp RCE
│   ├── README.md               # Full writeup
│   ├── poc.py                  # Proof of concept
│   └── images/                 # Screenshots
├── CVE-2026-42449/             # n8n-mcp SSRF
│   ├── README.md               # Full writeup
│   ├── poc/                    # PoC scripts
│   └── images/                 # Screenshots
└── ...
```

---

## 📬 Responsible Disclosure

I follow coordinated disclosure practices:

1. **Report** - Contact maintainer via security advisory or private channel
2. **Collaborate** - Work with maintainer on fix and timeline
3. **Publish** - Release writeup after patch is available

All vulnerabilities listed here have been patched. Please update to the latest versions.

---

## 🔗 Links

- **mcpsec:** [github.com/manthanghasadiya/mcpsec](https://github.com/manthanghasadiya/mcpsec)
- **LinkedIn:** [man-ghasadiya](https://linkedin.com/in/man-ghasadiya)
- **Twitter/X:** [@g_m_j_2703](https://twitter.com/g_m_j_2703)
- **Medium:** [@manthan27ghasadiya](https://medium.com/@manthan27ghasadiya)

---

## 📄 License

All writeups are provided for educational and defensive purposes. Use responsibly.

---

<p align="center">
  <i>Found a bug in an MCP server? <a href="https://github.com/manthanghasadiya/mcpsec">Try mcpsec</a></i>
</p>
