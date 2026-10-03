# Crypto Scam Vectors — Glossary & Field Guide

An open-source glossary of documented crypto scam patterns: how each one works, the red flags that give it away, and what to do if you're hit. Maintained by [CryptoStrapon](https://cryptostrapon.com), a free AI scam detector and education hub.

Full interactive version with filters: https://cryptostrapon.com/scams

---

## Contents

- [Wallet drainers](#wallet-drainers)
- [Approval phishing](#approval-phishing)
- [Fake tokens & honeypots](#fake-tokens-honeypots)
- [Bridge exploits](#bridge-exploits)
- [OTC & cash fraud](#otc-cash-fraud)
- [AI-powered scams](#ai-scams)
- [Protocol exploits](#protocol-exploits)
- [Laundering networks](#money-laundering)
- [Investment fraud](#investment-fraud)
- [Data breaches](#data-breaches)
- [Airdrop fraud](#airdrop-fraud)

---

## Wallet drainers

<a id="wallet-drainers"></a>
*One signature, empty wallet. The mechanics of drainers, poisoned addresses and tampered devices.*

**Categories:** Wallet Security, Developer Scam  
**Tags:** signature, keys, impersonation, jobs

A wallet drainer does not break cryptography. It gets you to sign something — a transfer to an address that looks like yours, a firmware seed that was never random, an npm script that reads your keystore while you review a 'test task'. The maths stays intact; the human gets rerouted.

Every case below ends the same way: funds leave in one transaction and never come back. What differs is the setup, and the setup is where the tell is. Read the mechanics, then check your own habits against the red flags.

### How it works

- **The lookalike** — The attacker generates an address sharing your recipient's first and last characters, then dusts your history with it. Next time you copy from history, you copy theirs.
- **The compromised source of randomness** — If a device or library generates keys from a weak seed, the wallet is public from birth. No phishing needed — the attacker simply derives the same key.
- **The trusted context** — A recruiter, a repo, a support agent, a firmware update. The payload arrives inside something you already had a reason to run.

### Red flags

- You are copying a recipient address from transaction history instead of the original source.
- A wallet, device or firmware arrived from a marketplace reseller rather than the manufacturer.
- A 'test task' asks you to run a project locally on a machine that holds keys.
- The address matches at the ends but you never compared the middle characters.
- Anyone at all asks for a seed phrase — support never does.

### If it already happened

- Move whatever is left to a wallet generated on a clean device — the old one is burned.
- Revoke every outstanding token approval from the compromised address.
- Save the transaction hashes: they are the only evidence that survives.
- Report to the chain analytics firms and the exchange that received the funds; freezes do happen, but only fast.

---

## Approval phishing

<a id="approval-phishing"></a>
*They don't want your keys. They want your permission — granted once, used forever.*

**Categories:** Approval Phishing, Phishing, Fake Security Alerts  
**Tags:** signature, impersonation, token, keys

Approval phishing is the polite robbery. Nothing is broken into. You are asked, in language that sounds procedural, to grant a contract permission over a token balance — and then the contract exercises that permission at a time of its choosing.

It works because approvals are invisible after the fact. The wallet shows a successful transaction, the balance stays put, and the drain arrives days later when nobody is watching the screen.

### How it works

- **The pretext** — A security alert, a migration notice, an airdrop claim, a support call. Anything that makes signing feel like the safe option.
- **The signature** — An unlimited allowance, a Permit2 blob, or setApprovalForAll on an NFT collection. Human-readable only if the wallet decodes it — many do not.
- **The delay** — The drainer waits. Time between signature and theft breaks the victim's mental link between the two events.

### Red flags

- A signature request that grants an allowance instead of moving a fixed amount.
- The wallet cannot decode what you are signing and shows raw hex.
- Urgency framed as safety: 'migrate now', 'verify to protect your funds'.
- Inbound contact — a call, DM or email you did not initiate.
- The claim page needs an approval before it will show you anything.

### If it already happened

- Revoke the approval immediately; revoking after the drain still stops the next one.
- Check every other approval on the same address — drainer kits request several.
- Move remaining balances to a fresh address rather than trusting the cleaned one.
- Keep the signature hash: it identifies the drainer kit, and kits get attributed.

---

## Fake tokens & honeypots

<a id="fake-tokens-honeypots"></a>
*The balance is real on screen and fictional on-chain. Honeypots, flash USDT and exit rugs.*

**Categories:** Token Scam  
**Tags:** token, profit, signature, protocol

A fake token is a user-interface attack. Wallets render whatever a contract claims, so a scammer only needs to make the number look right for long enough to close a deal — the sell function is where the truth lives.

The variants below span cloned stablecoins, contracts that permit buys and block sells, supply that vanishes on a timer, and liquidity that leaves in one block. All of them are checkable before you pay, and each investigation shows exactly where to look.

### How it works

- **The display trick** — Name, ticker and decimals are free text. USDT-Z, HKDAP, a mirrored logo — the wallet has no opinion on authenticity.
- **The asymmetric contract** — Buys succeed, sells revert for anyone outside a whitelist. Blacklists, transfer taxes and pausable transfers do the same job.
- **The exit** — Liquidity is pulled, ownership is renounced after a hidden mint, or the deployer bridges out. The chart goes vertical, then to zero.

### Red flags

- The contract address does not match the issuer's official one, character for character.
- Nobody except a handful of addresses has ever successfully sold.
- The deployer holds a mint, pause, blacklist or fee-setting function.
- Liquidity is unlocked, or the lock expires within weeks.
- The deal happens in a private chat with a countdown attached.

### If it already happened

- Stop trying to sell — a honeypot's sell attempts only pay gas to the attacker's design.
- Record the contract address and the deployer; both feed public scam databases.
- If a counterparty pushed the token during an OTC deal, treat every other asset in that deal as suspect.
- Report the contract to the explorer — labelled contracts stop the next buyer.

---

## Bridge exploits

<a id="bridge-exploits"></a>
*Real collateral on one side, a claim on the other. When verification breaks, the claim wins.*

**Categories:** Bridge Exploit  
**Tags:** protocol, token, bridge, laundering

Every bridge is the same promise in different code: lock value here, mint a claim there, and let a verifier swear the two match. The verifier is the entire security model, and it is usually the least reviewed component in the stack.

The exploits collected here are failures of proof, not of cryptography — a message accepted without validation, a DVN that signed what it should have refused, a router that trusted its caller. Each case shows the exact line where the promise stopped being enforced.

### How it works

- **Lock and mint** — Collateral sits on chain A. Chain B mints a representation of it. Solvency depends entirely on the two staying in sync.
- **The verification gap** — A forged message, a quorum that can be reached alone, or a missing check lets chain B mint without chain A ever locking.
- **The cash-out** — The phantom asset is swapped against real liquidity within minutes, then bridged onward before governance can pause anything.

### Red flags

- The bridge's verifier set is small, permissioned, or run by the same team as the bridge.
- Upgrade keys are a single multisig with a low threshold and no timelock.
- Total value locked greatly exceeds the size of the last audit's scope.
- Wrapped supply on the destination chain has drifted from locked collateral.
- Incident communications arrive hours after on-chain sleuths already published.

### If it already happened

- Exit wrapped positions before the peg follows the news — depegs are fast.
- Withdraw approvals to the bridge router; exploited routers are re-used.
- Track the official post-mortem for a reimbursement snapshot block, and keep proof of your position at that block.
- Do not trust 'recovery portals' announced in replies — they are the second wave of the same attack.

---

## OTC & cash fraud

<a id="otc-cash-fraud"></a>
*Big-ticket deals, private rooms, no referee. Where OTC settlement goes wrong.*

**Categories:** OTC Fraud, Advance-Fee Fraud, Social Engineering  
**Tags:** offchain, impersonation, profit, laundering

OTC fraud is the oldest trick with a new settlement layer. The size of the number does the persuading, the privacy of the channel removes the referee, and the irreversibility of the chain does the rest.

These cases cover impersonated desks, cash meetings that were always a robbery, 'discounted' coins with a criminal history attached, and fees paid up front for volumes nobody ever had. The pattern repeats so precisely that it reads like a script — because it is one.

### How it works

- **Manufactured credibility** — A cloned desk profile, a borrowed company name, a proof-of-funds screenshot, a lawyer in the loop. All cheap to fake, all reassuring.
- **Sequencing the settlement** — Whoever moves first loses. The script always finds a reason why you must — a fee, a deposit, a 'good faith' tranche, a customs charge.
- **The private room** — Cash meetings, hotel suites, escrow agents chosen by the counterparty. No venue, no recourse, sometimes no exit.

### Red flags

- A price meaningfully below market, explained by urgency or the seller's legal trouble.
- Any payment before settlement: escrow fee, compliance fee, unlock fee, insurance.
- The counterparty insists on a physical meeting to hand over cash.
- The 'desk' only exists on Telegram and the profile was created this quarter.
- Proof of funds is a screenshot or a video, never a signed message from the address.

### If it already happened

- Stop paying. The next fee is always presented as the last one — it never is.
- Preserve the chat export, wallet addresses and any documents; this is what the police can use.
- File a report where the money left, not where the counterparty claims to be.
- If a physical meeting is already scheduled, cancel it. This is the point where OTC fraud turns violent.

---

## AI-powered scams

<a id="ai-scams"></a>
*Deepfaked founders, hallucinated audits, agents that sign for you. Fraud at machine speed.*

**Categories:** AI Scam  
**Tags:** ai, impersonation, signature, jobs

AI did not invent a new crime. It removed the two bottlenecks that used to limit the old ones: the cost of being convincing, and the cost of doing it at scale. A face, a voice, a term sheet and a plausible audit report are now commodities.

The investigations here cover both directions of the problem — attackers using models to impersonate, and users trusting models that confidently produce nonsense. The second is the quieter loss, and the one that ships to production.

### How it works

- **Synthetic identity** — A recorded founder becomes a live video call. Voice cloning needs seconds of audio; the call needs no more than plausibility.
- **Agentic access** — An AI agent with wallet permissions reads untrusted text. Prompt injection turns that text into an instruction it will happily sign.
- **Confident fabrication** — A model returns findings with no basis, or a clean bill of health it never verified. The output looks like a report because reports are what it was trained on.

### Red flags

- A video call where the face never occludes, turns fully sideways, or reacts to an unexpected request.
- Investment or partnership contact that starts with a familiar name and ends at a fresh domain.
- An 'AI-audited' badge with no auditor, no scope and no reproducible findings.
- An agent that can both read arbitrary web content and sign transactions.
- A security tool whose report has zero false positives and zero cited evidence.

### If it already happened

- Verify identity on a channel the impersonator does not control, then invalidate the compromised one.
- Revoke any permissions granted to an agent, and rotate its API keys.
- Have a human re-check every finding an AI tool cleared before you shipped.
- Report the deepfake to the platform: takedowns are slow, but attribution accumulates.

---

## Protocol exploits

<a id="protocol-exploits"></a>
*The contract worked perfectly. That was the problem.*

**Categories:** Smart Contract Exploit, Security Incident  
**Tags:** protocol, token, bridge, laundering

A protocol exploit is rarely a bug in the romantic sense. It is a contract executing its stated rules against an input nobody modelled — a price that can be moved, a sponsor that pays for anything, a delegation that outlives its purpose.

The cases below share a structure: an assumption written into code, an attacker who reads code better than the reviewers did, and a window measured in blocks. Two of them are repeat incidents, which is its own lesson about remediation.

### How it works

- **The assumption** — A price feed is trusted, a caller is trusted, a gas sponsor is unlimited. The assumption is invisible because it was never written down as one.
- **The manipulation** — Flash-borrowed capital, a crafted call sequence, or a delegated account turns the assumption false for exactly one block.
- **The repeat** — The patch addresses the symptom. The class of bug stays, and the same protocol is hit again weeks later.

### Red flags

- A single price source, or an oracle with thin liquidity behind it.
- Gas sponsorship or fee abstraction without per-user limits.
- Audit scope that excludes the module handling the money.
- A previous incident whose post-mortem promised process changes rather than code changes.
- Admin functions reachable without a timelock.

### If it already happened

- Withdraw from the affected pools before secondary liquidations cascade.
- Revoke approvals to the exploited contract, including any router in front of it.
- Record your position at the incident block; reimbursements are settled from a snapshot.
- Read the post-mortem for the bug class, not the patch — the class predicts the next incident.

---

## Laundering networks

<a id="money-laundering"></a>
*The theft is the easy part. This is the industry that turns stolen coins into spendable money.*

**Categories:** Money Laundering  
**Tags:** offchain, token, laundering, bridge

Stealing crypto is a technical problem solved in one transaction. Spending it is a logistics problem that employs thousands of people — mules, brokers, shell companies, compliant-looking exchanges and a great deal of patience.

These investigations follow the money after the headline: how proceeds are layered, who moves them, which jurisdictions absorb them, and why victim funds so often surface in accounts belonging to other victims.

### How it works

- **Placement** — Proceeds are split across fresh addresses and mule accounts, often recruited with fake job offers.
- **Layering** — Mixers, cross-chain swaps, privacy coins and thousands of hops designed to exhaust an analyst's budget rather than defeat the maths.
- **Integration** — Cash-out through complicit OTC brokers, cash pickup networks or businesses that need volume more than they need answers.

### Red flags

- A remote 'payment processing' or 'financial agent' job that uses your personal bank account or wallet.
- Someone offers a fee to receive and forward funds you have no business receiving.
- A relationship built over weeks that arrives at an investment platform you had never heard of.
- Withdrawals from that platform require a tax, a fee or a topped-up balance.
- The counterparty is fine paying above market to move funds quickly and quietly.

### If it already happened

- Stop all transfers immediately — continuing makes you a participant, not just a victim.
- Preserve every transaction record before deleting an app or account.
- Report to your bank and to the receiving exchange; both can freeze faster than law enforcement.
- Get legal advice if your account was used to forward funds; that exposure is real and time-sensitive.

---

## Investment fraud

<a id="investment-fraud"></a>
*Guaranteed returns are a maths problem, and the maths always resolves the same way.*

**Categories:** Investment Fraud, Ponzi Scheme  
**Tags:** profit, impersonation, offchain, jobs

Investment fraud in crypto rarely needs a technical exploit. It needs a number that compounds faster than reality and an audience that has seen enough genuine upside to believe it.

The cases here run from classic pay-the-old-with-the-new schemes to funded projects that raised, delivered nothing and left quietly, and to payment mandates signed during what felt like routine onboarding. Different wrappers, one arithmetic.

### How it works

- **The promise** — A fixed daily or weekly return, described as arbitrage, market making or an AI trading engine. Volatility is never mentioned.
- **The circulation** — Early withdrawals are paid from later deposits. Real yield never exists; the dashboard is a spreadsheet with a chart on it.
- **The wall** — Withdrawals slow, then require a fee, a tax, an upgrade. Deposits are still instant. That asymmetry is the whole story.

### Red flags

- Any return described as guaranteed, fixed or risk-free.
- Referral commissions that pay more than the underlying strategy plausibly could.
- Withdrawals gated behind a payment you must fund from outside.
- No verifiable counterparty, licence or on-chain proof of the strategy.
- A mandate, direct debit or recurring authorisation signed during onboarding.

### If it already happened

- Cancel any recurring mandate at the bank, not just in the platform's settings.
- Do not pay the withdrawal fee — it is the scheme's last revenue line, not a route out.
- Export the account history and all communications before access disappears.
- Warn whoever referred you; in most schemes they are the next victim, not the operator.

---

## Data breaches

<a id="data-breaches"></a>
*The keys stay safe. The customer list does not — and that list is the next phishing campaign.*

**Categories:** Data Breach  
**Tags:** data, impersonation, offchain, ai

A crypto data breach is not usually a theft of funds. It is a theft of context: who you are, which platform you use, how much you hold, what your last ticket was about. Everything a convincing impersonator needs.

The investigations here trace breaches back to the boring places they actually happen — a third-party analytics vendor, a support tool, a phone call to a help desk — and forward to the phishing waves that follow within days.

### How it works

- **The soft edge** — The exchange is hardened; the analytics vendor, CRM or outsourced support desk is not. Access there is access to customers.
- **The enrichment** — Leaked records are merged with older dumps to build a profile: balance range, platform, language, timezone.
- **The follow-up** — A support call or email that knows your last ticket. The credibility is borrowed from the breach, not manufactured.

### Red flags

- Inbound contact that already knows your account details or recent activity.
- A breach notification arriving from anywhere other than the platform's official domain.
- Pressure to 'secure' your account by moving funds to a new address.
- A password reset you did not request, especially alongside a SIM issue.
- Support asking to verify by reading back a code, a phrase or a key.

### If it already happened

- Assume the leaked data is permanent: change what you can, and treat the rest as public.
- Move to app-based or hardware 2FA and remove SMS as a recovery path.
- Set a withdrawal allowlist on every exchange account that supports one.
- Expect targeted phishing for months, and verify support contact by calling the platform yourself.

---

## Airdrop fraud

<a id="airdrop-fraud"></a>
*Free money is the bait. The signature on the claim page is the trap.*

**Categories:** Airdrop Fraud  
**Tags:** profit, signature, token, impersonation

Airdrop fraud runs on a legitimate expectation: protocols really do give tokens away, and being early really does pay. The scam only has to imitate the paperwork of a real claim.

Every variant funnels to the same screen — connect, verify eligibility, sign to claim. The signature is never a claim. It is an allowance, and the wallet empties once the page is closed and forgotten.

### How it works

- **The eligibility hook** — A checker tells you that you qualify for an amount worth acting on. The number is personalised to your balance.
- **The gate** — A survey, a Discord role, a small 'gas fee' — friction that makes the process feel administrative and legitimate.
- **The claim signature** — The final button requests an approval or a Permit signature. Nothing is claimed; permission is granted.

### Red flags

- The claim link came from a DM, reply, or an ad rather than the protocol's own channel.
- Claiming requires paying gas to a contract you cannot read.
- The page asks for a signature before showing your allocation.
- The token is tradeable before the official distribution date.
- Eligibility is universal — everyone who connects qualifies.

### If it already happened

- Revoke the approval granted on the claim page immediately.
- Check for a second, quieter approval — claim kits often request two.
- Move funds to a fresh address if an unlimited allowance was signed.
- Report the domain; claim pages are cloned across dozens of lookalike hosts.

---
