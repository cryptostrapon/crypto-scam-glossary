# Crypto Scam Vectors — Glossary & Field Guide

[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.23326056.svg)](https://doi.org/10.5281/zenodo.23326056)
[![Code: MIT](https://img.shields.io/badge/code-MIT-green)](LICENSE) [![Content: CC BY 4.0](https://img.shields.io/badge/content-CC%20BY%204.0-blue)](LICENSE-CONTENT.md) ![Scam vectors: 11](https://img.shields.io/badge/scam%20vectors-11-orange) [![Live demo](https://img.shields.io/badge/live-demo-brightgreen)](https://cryptostrapon.github.io/crypto-scam-glossary/)

An open-source glossary of crypto scam patterns observed in our investigations — wallet drainers, approval phishing, honeypot tokens, bridge exploits, AI-powered scams, OTC fraud, laundering networks, investment fraud, data breaches, and airdrop fraud. Each entry covers how the mechanism actually works, the red flags that give it away before you lose funds, and the steps to take if you've already been hit.

**Live demo:** https://cryptostrapon.github.io/crypto-scam-glossary/
**Plain-text version:** [GLOSSARY.md](GLOSSARY.md)
**Full interactive version with filters:** https://cryptostrapon.com/scams
**Investigations on the main site:** https://cryptostrapon.com/stories
**Free scam checker:** https://cryptostrapon.com/scam-detector
**Lost funds? What to do next:** https://cryptostrapon.com/report-crypto-theft

## Use it

Embed the glossary in a blog, classroom page or community wiki:

```html
<iframe src="https://cryptostrapon.github.io/crypto-scam-glossary/" width="100%" height="720" style="border:0" title="Crypto scam vectors glossary" loading="lazy"></iframe>
```

Or reuse the text directly from [GLOSSARY.md](GLOSSARY.md). Content is CC BY 4.0: copy, translate and adapt it with attribution to CryptoStrapon.

**Pairs well with:** the open [Crypto Scam Detection Quiz](https://github.com/cryptostrapon/crypto-scam-quiz) (50 scenarios, same licence).

## Why this exists

Most "scam glossaries" are a one-line definition per term. That's not enough to actually recognize a scam in progress — you need to know *how the mechanism works*, not just its name. Each entry here is structured the same way: mechanics (how it's built), red flags (what to notice before you act), and recovery steps (what to do if you didn't catch it in time).

## Project structure

```
index.html      Interactive, searchable glossary (vanilla HTML/CSS/JS, no build step, no dependencies)
vectors.json    The structured data — one object per scam vector
GLOSSARY.md     The same content as plain markdown, for easy reading/citing/forking
```

## Use the data in your bot, wallet or app

`vectors.json` is a plain JSON file you can load directly: no API key, no dependencies.

```
https://raw.githubusercontent.com/cryptostrapon/crypto-scam-glossary/main/vectors.json
https://cdn.jsdelivr.net/gh/cryptostrapon/crypto-scam-glossary@main/vectors.json
```

Use it for scam warnings in wallets, browser extensions, Telegram bots or training material. It is CC BY 4.0: please credit "CryptoStrapon" and link to https://cryptostrapon.com/scams.

## Running it locally

```bash
python3 -m http.server 8000
# open http://localhost:8000
```

## Contributing

New vectors, corrections, and translations are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

## Disclaimer and corrections

This glossary is for education only. It is not financial, legal or investment advice. Company, wallet and product names appear only to show how scammers impersonate them. They do not imply wrongdoing by those companies.

Found an error? Open a "Report an inaccuracy" issue or write to cryptostrapon@proton.me. Verified corrections are fixed as soon as we can.

## License

- Code (`index.html` and any scripts): [MIT](LICENSE)
- Glossary content (`vectors.json`, `GLOSSARY.md`): [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/) — reuse freely with attribution to CryptoStrapon. Full notice: [LICENSE-CONTENT.md](LICENSE-CONTENT.md).
- Citing: see [CITATION.cff](CITATION.cff). Security reports: see [SECURITY.md](SECURITY.md).

## About

Maintained by [CryptoStrapon](https://cryptostrapon.com) — a free AI scam detector and crypto-scam education hub. We investigate crypto scams and build free tools so people don't have to learn these lessons the expensive way.
