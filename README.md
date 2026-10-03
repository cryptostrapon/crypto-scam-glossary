# Crypto Scam Vectors — Glossary & Field Guide

An open-source glossary of documented crypto scam patterns — wallet drainers, approval phishing, honeypot tokens, bridge exploits, AI-powered scams, OTC fraud, laundering networks, investment fraud, data breaches, and airdrop fraud. Each entry covers how the mechanism actually works, the red flags that give it away before you lose funds, and the steps to take if you've already been hit.

**Live demo:** https://cryptostrapon.github.io/crypto-scam-glossary/
**Plain-text version:** [GLOSSARY.md](GLOSSARY.md)
**Full interactive version with filters:** https://cryptostrapon.com/scams

## Why this exists

Most "scam glossaries" are a one-line definition per term. That's not enough to actually recognize a scam in progress — you need to know *how the mechanism works*, not just its name. Each entry here is structured the same way: mechanics (how it's built), red flags (what to notice before you act), and recovery steps (what to do if you didn't catch it in time).

## Project structure

```
index.html      Interactive, searchable glossary (vanilla HTML/CSS/JS, no build step, no dependencies)
vectors.json    The structured data — one object per scam vector
GLOSSARY.md     The same content as plain markdown, for easy reading/citing/forking
```

## Running it locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Contributing

New vectors, corrections, and translations are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

## License

- Code (`index.html` and any scripts): [MIT](LICENSE)
- Glossary content (`vectors.json`, `GLOSSARY.md`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — reuse freely with attribution to CryptoStrapon.

## About

Maintained by [CryptoStrapon](https://cryptostrapon.com) — a free AI scam detector and crypto-scam education hub. We document real fraud cases and build free tools so people don't have to learn these lessons the expensive way.
