# Circle Product Feedback

*Part of [Meridian × Ignyte](../README.md). Notes from running Circle products in production on Arc, not from a weekend of testing.*

Meridian has integrated 20 Circle products across the stack, live since day one of Arc Testnet (October 28, 2025), with 47,800+ on-chain transactions. The feedback below is grouped by product and reflects real usage in payments, treasury, streaming and agent flows.

---

## USDC and EURC

**Why we use them.** They are the settlement rails for the whole stack. A merchant accepts them, the treasury earns on them, payroll streams out of them, and an agent transacts against them. Having a regulated dollar and a regulated euro from the same issuer means a European merchant can price in EUR and settle in USD without leaving the same trust model.

**What worked.** Native issuance on Arc with gas paid in USDC removes the usual friction of holding a separate gas token. For a euro-first user base, EURC is the piece that makes the product make sense.

**What could improve.** Clearer, in-one-place guidance on EURC availability per chain would save integration time, since it is not everywhere USDC is.

## Arc

**Why we use them.** Sub-second finality and USDC-denominated gas are what make machine-speed and micro-value flows viable. Card rails cannot match the cost or the settlement guarantee.

**What worked.** Deterministic finality changes how you design a payment flow: you can confirm and report to a user in one step instead of waiting on probabilistic confirmations.

**What could improve.** Testnet explorer and tooling maturity is the main gap while the network is young. It is getting better quickly.

## CCTP

**Why we use them.** Cross-chain USDC without a third-party bridge. Burn on the source chain, mint on the destination by Circle, which removes the bridge risk that has repeatedly hurt the industry.

**What worked.** For cross-border and multi-chain treasury it simplifies the logistics and cuts a whole category of security surface.

**What could improve.** Faster attestation on some routes would help time-sensitive settlement.

## Circle Wallets

**Why we use them.** Safe key management so a user, a merchant, or an agent can transact without exposing a seed phrase. This is what makes an autonomous agent paying on a user's behalf acceptable.

**What worked.** The programmatic control fits an agent context well, where a wallet has to act on a goal rather than a manual click.

**What could improve.** Agent-specific primitives, for example tighter spend-policy hooks at the wallet layer, would let us push more of the trust logic down the stack.

## Gateway

**Why we use them.** Backend liquidity and routing behind the payment flows, especially when a payment crosses chains or currencies.

**What worked.** It keeps the user-facing flow simple while the routing happens underneath.

## USYC

**Why we use them.** Tokenized short-term US Treasuries are the real-world asset behind our YieldVault. The yield is real and auditable, not a reward token invented for the occasion.

**What worked.** Holding the Teller whitelist, we integrate the actual product, so our RWA and treasury flows are the real thing rather than a concept most teams are limited to.

**What could improve.** Broader documentation for builders who are new to the redemption and settlement mechanics would widen adoption.

## StableFX

**Why we use them.** On-chain euro to dollar settlement for cross-border, with escrow so both legs settle together or not at all, which removes counterparty risk from the FX step.

**What worked.** The all-to-all model means we do not have to negotiate bilateral FX relationships to get access to liquidity.

**What could improve.** As it moves from testnet toward mainnet, clear timelines help teams plan production corridors around it.

## Gas Station and Paymaster

**Why we use them.** So the user, or the agent, never has to hold or think about a gas token. Cost stays dollar-denominated and predictable.

**What worked.** This is a large part of why an agent can make many small payments without the economics breaking.

## Nanopayments

**Why we use them.** High-frequency, low-value, sub-cent payments at machine speed, which is what an agent economy actually needs and what card rails cannot serve.

**Recommendation.** Batching ergonomics for very high-frequency agent flows would be a strong addition.

---

**Overall.** The combination that stands out is USDC and EURC settlement plus USDC-denominated gas on Arc plus programmable wallets. Together they make agent-frequency and cross-border stablecoin commerce economically real, not a demo. The gaps are mostly maturity and documentation, expected for a network this young, and they are closing fast.
