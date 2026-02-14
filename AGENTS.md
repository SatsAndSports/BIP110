# AGENTS.md: The "Mass-Debater" Black Box Recorder

This document tracks the design decisions, architectural evolutions, and technical derangements that birthed the **Which Bitcoin Should You Run?** flowchart. It is a record of our struggle to balance local node policy with global protocol consensus while maintaining a healthy level of sarcasm.

---

## 1. Project Manifesto

**The North Star:** Bitcoin is sound money. Sound money requires censorship resistance. Censorship resistance is incompatible with subjective "spam" filters.

If a transaction is valid according to the consensus rules and pays a competitive fee, it belongs in a block. Whether that transaction is a payment for a coffee, a SatoshiDice bet, or a 4GB image of a cat is irrelevant to the protocol. To think otherwise is to invite the "Censorship Committee" into your living room.

> "A transaction is a transaction. Your 'spam' is my data. Your 'virtue signaling' is my centralisation risk." — Anonymous Node Operator

---

## 2. Architectural Design Decisions

### The "Snake" (S-Curve) Grid
*   **The Problem:** The initial design was a vertical "infinite scroll" spine. While logically sound, it was visually exhausting and impossible to screenshot for the 'Gram.
*   **The Fix:** We implemented a 3x4 grid using a "Snake" (S-curve) pattern. 
    *   Row 1: Left to Right
    *   Row 2: Right to Left
    *   Row 3: Left to Right
    *   Row 4: Right to Left
*   **The Result:** A wider, roughly square layout (~1400px wide) that fits on a single desktop screen. Perfect for sharing with your favorite fork-enthusiast.

### The Horizontal "Path of Enlightenment"
*   **Logic:** Questions are paired horizontally with their "Sane" answers. This creates a continuous, bold **Bitcoin Orange (#F7931A)** line snaking through the project.
*   **Dumb Exits:** All satirical or "insane" branches shoot vertically downward from the question boxes in **Warning Red (#FF4D4D)**. This makes the "Path of Enlightenment" unambiguous.

### Label-on-Wire UX
*   **Decision:** We moved YES/NO/RELAY labels out of the boxes and onto the connectors using CSS `::before` pseudo-elements.
*   **Why?** It stripped away conversational clutter. We don't need to say "Yes, I agree that..." inside a box when a green "YES" label is already pointing at it.

---

## 3. Technical Logic & Historical "Derangements"

### SatoshiDice Derangement Syndrome (SDDS)
*   **The Incident:** In October 2014, Luke Dashjr hardcoded a blacklist of SatoshiDice and Counterparty addresses into the `bitcoind` patches distributed via the Gentoo Linux package manager.
*   **The Sneak:** It was enabled by default. Users only noticed when their transactions started failing silently. 
*   **The Defense:** Luke famously replied "PEBCAK" (Problem Exists Between Chair And Keyboard) to users reporting the "bug."
*   **The Evidence:** [Gentoo Bug #524512](https://bugs.gentoo.org/524512) remains a monument to why we don't blindly accept "auto-updates" from statist devs.
*   **The Lesson:** Once you start blacklisting gambling, the path to blacklisting *you* is just one "sneaky update" away.

### The OOB (Out-of-Band) Failure Mode
*   **The Logic:** If your node filters a transaction but that transaction still gets mined via a direct pipeline (like Mara's SlipStream), your filter has **FAILED**.
*   **The Harm:** Ineffective mempool filters don't stop transactions; they only stop *you* from seeing the fees. This pushes revenue to large, well-connected miners, centralising the network.
*   **Conclusion:** A filter that doesn't stop a transaction is just "Decentralization Theatre."

### The "30 vs. 1 Million" Rule (LibreRelay Asymmetry)
*   **The Principle:** It only takes a few dozen relaxed nodes (running LibreRelay or Core v30) to defend the network's decentralization. 
*   **The Irony:** A million filtering nodes (like Knots) can coordinate an attack on a transaction, but if just 30 nodes relay it to a single miner, the filter is undone.
*   **Free-Riding:** We explicitly mock Knots users for free-riding on the security and decentralization provided by the very LibreRelay nodes they disapprove of.

### The Sub-1sat-per-vB Summer (2025)
*   **Context:** An era where high demand for "junk" transactions met a wall of ineffective mempool filters.
*   **The Outcome:** OOB mining thrived, and the filters achieved nothing but making mining less competitive. It was the empirical proof that the "Dust Limit fallacy" (thinking all filters work because dust works) was total bunk.

---

## 4. The Soft Fork Wars

### BIP-54 (Consensus Cleanup)
*   **The Sane Path:** Fixing actual bugs (like timelock issues and O(n^2) hashing) through broad technical consensus. No drama, just engineering.

### BIP 110 (The "Chain Split Speedrun")
*   **The Ridicule List:**
    *   **Surrendering `OP_SUCCESS`:** Giving up future soft fork hooks for a "temporary" fix.
    *   **Breaking `OP_IF`:** A proposal to "protect money" that might actually freeze/lose your money in pre-signed Taproot txs.
    *   **The 55% Threshold:** Because 95% consensus is too hard when your idea is this bad.
    *   **The Self-Own:** The BIP text literally admits that "spam is best fought with policy, not consensus." Then why is it a soft fork? 

---

## 5. Visual Language & Branding

*   **Core 30:** Transitioned from "Run Taproot" to "Run Core 30" to keep up with the latest protocol standards.
*   **The Victory Arrow:** An L-shaped orange wire that drops from the final sane answer and turns 90 degrees to enter the side of the glowing victory box. It represents the final "turn" towards sovereign node operation.
*   **Glow Effect:** The `victory-box` uses a CSS animation to pulse with a Bitcoin-orange aura, signifying the enlightened state of running a full node without subjective filters.

---

## 6. Quotes from the Trenches

> "I banned OP_RETURN and all I got was this lousy UTXO set bloat." — A BIP 110 Enjoyer

> "Nothing says private like asking your merchant 'Do you accept Monero?' while wearing a neon 'I AM TRANSACTING PRIVATELY' sign." — Fedimint Guardian

---

**Last Updated:** Sat Feb 14 2026  
**Status:** Polished & Sarcastic.
