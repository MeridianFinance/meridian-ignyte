# Track 4 · Agentic Economy · YieldClaw

**Talk to it like a person. It shops for you, pays in stablecoins, verifies who it is paying, and reports back.**

*Part of [Meridian × Ignyte](../README.md). For educational and testnet demo purposes only.*

**Live agent activity feed:** https://arcagent.live
**Demo:** the agent screenshots and on-chain identity below, plus the overview video. The agent page itself is in private access for now, open to the Circle and Arc team.
**Track:** 4, Best Agentic Economy Experience on Arc
**Circle products used:** USDC · EURC · Circle Wallets · Nanopayments · Gateway

---

## What it is

**YieldClaw** is a live autonomous AI agent on Arc with a real on-chain identity (ERC-8004). You give it a goal in plain language and it executes the whole transaction on your behalf:

> "Buy me a hoodie and a cap."
> "How much USDC do I have?"
> "Get me a sticker pack, cheapest option."

YieldClaw then:

1. **Understands** the request in natural language.
2. **Checks your balance** in USDC or EURC on Arc.
3. **Finds the best option**, the right item, the best merchant, the lowest price.
4. **Funds if needed** and **pays the merchant** in USDC or EURC, with zero gas and instant, deterministic settlement on Arc.
5. **Verifies the counterparty** through Firmata before releasing payment, identity and reputation checked on-chain. This is Know Your Agent, KYA.
6. **Reports back** with a clear summary of what it bought, where, and for how much.

The same agent also runs treasury operations autonomously. The shopping flow is the demonstration for this track, but the broader role is simple to state: give it a goal, the agent handles the rest.

## Why it fits Track 4

The track asks for an AI agent that autonomously discovers and executes a stablecoin-settled purchase using Arc smart contracts. That is YieldClaw, live today, not a concept: a conversational agent that discovers the best option, settles in USDC or EURC at machine speed with no gas, and does it with on-chain trust verification built in. Most entries in this track will demo an idea. This one is running, its activity is public at arcagent.live, and its identity is a real contract on Arc.

## How it works

```mermaid
flowchart LR
    U(["User · plain language"]) --> AG["YieldClaw agent<br/>intent + reasoning"]
    AG --> BAL["Balance check<br/>Circle Wallets · USDC/EURC"]
    AG --> DISC["Discovery<br/>best item · best merchant · best price"]
    DISC --> PAY["Meridian Pay<br/>settle in USDC/EURC · zero gas"]
    PAY --> ARC["Arc Testnet<br/>instant deterministic finality"]
    KYA["Firmata · KYA<br/>identity + reputation on-chain"] -. "verifies merchant before payment" .-> PAY
    PAY --> REP["Report back to user<br/>what · where · how much"]
```

## The hard part is trust, and that is our moat

Anyone can wire an agent to a payment SDK. Discovery and checkout are the easy 80 percent. The hard part, the part that decides whether an agent economy is safe enough to actually exist, is trust: when an agent pays a merchant it has never met, on behalf of a person who is not watching, who verifies the merchant is legitimate and the payment is warranted?

YieldClaw answers that with Firmata. Before it releases payment, it checks the counterparty's on-chain identity and reputation. Payments settle in USDC at machine speed; the trust layer decides who is allowed to be paid. That is the difference between an agent that moves money and an agent you can let loose. It is also why an agent needs an identity of its own, which brings us to the proof.

## How we integrate Circle, product by product

- **USDC and EURC** are the settlement rails. Every purchase is paid and settled in Circle stablecoins on Arc, so the agent transacts in regulated, dollar and euro denominated value.
- **Circle Wallets** give the agent secure key management so it can check balances and initiate payments on the user's behalf without ever exposing a seed phrase. This is what makes an autonomous agent acceptable rather than reckless.
- **Nanopayments** enable high-frequency, low-value, sub-cent payments at machine speed, which is what an agent economy actually runs on and what card rails cannot serve.
- **Gateway** provides the backend liquidity and routing behind the payment flows the agent orchestrates.
- **Gas paid in USDC on Arc** means the agent can make many small payments without the economics breaking, and the user never has to hold or think about a separate gas token.

## Proof it is live

The agent page, top and bottom:

![YieldClaw agent, top of the page](../assets/Agent-dashboard1.png)
![YieldClaw agent, bottom of the page](../assets/Agent-dashboard2.png)

The agent has a real on-chain identity. The AgentIdentity registry (ERC-8004) is live and public on Arc Testnet:

**AgentIdentity (ERC-8004):** [`0x8004A818BFB912233c491871b3d84c89A494BD9e`](https://testnet.arcscan.app/address/0x8004A818BFB912233c491871b3d84c89A494BD9e)

Live agent activity feed, public: [arcagent.live](https://arcagent.live). Overview walkthrough: https://youtu.be/b7Ww4dd5ntU.

## The numbers

- 19 contracts live on Arc Testnet (chain 5042002), verifiable on [testnet.arcscan.app](https://testnet.arcscan.app)
- 47,800+ on-chain transactions across the Meridian stack
- Firmata implements ERC-8004, ERC-8183 and x402 together, the identity, commerce and settlement standards an agent economy needs
- Building since day one of Testnet, October 28, 2025

## What is next

The shopping flow is the demo. The direction is an agent that runs a full operating budget: discover, negotiate, pay, verify, and report, across many merchants and many small payments, with the treasury layer (Track 3) funding it and the trust layer (Track 2) gating every counterparty. The four tracks are not four products, they are the surfaces an autonomous agent transacts across, which is exactly why we built them on one connected stack.

## Run it

The flows are shown in the screenshots above and the overview video. The live agent page is in private access for now, open to the Circle and Arc team. The production protocol source stays private. The demo calls Meridian's already-deployed contracts on Arc (addresses public on testnet.arcscan.app), and references Firmata at the standard level, ERC-8004 identity and reputation.

## Circle product feedback

See [`../docs/circle-feedback.md`](../docs/circle-feedback.md) for our notes on USDC, EURC, Circle Wallets, Nanopayments and Gateway in production.
