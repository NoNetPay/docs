
## 📡 NoNetPay: Offline Crypto Yield & Payment Network

### 🔧 Overview

**NoNetPay** enables **offline crypto access and passive yield earning** by leveraging **mesh-based message sharing**, **trusted relayers**, and **TEE-secured wallets**, all integrated with **on-chain DeFi protocols**.

🧬 Example Flow: Sending USDC Offline
User A (offline) creates a signed intent:
“Send 5 USDC to User B”
![image](https://github.com/user-attachments/assets/4c607b27-dad5-4dab-bcab-c05c9a6608f8)

- It’s shared with nearby User B, then User C (connected to a relayer)
- User C forwards the intent to a +91 Registered Relayer
- The relayer passes the message to Phala TEE
- TEE validates the signature, confirms balance, and executes transfer
- Safe Account triggers USDC transfer on-chain
- User B receives updated balance


### 🧩 System Architecture & Workflow

1. ### 🔐 TEE-Backed Wallet Custody

   * Every user has a **Safe Smart Account** on-chain.
   * The **private key of this wallet is never stored on-device**.
   * Instead, it resides **securely inside a Phala TEE**.
   * Only the TEE can sign transactions, based on verified user intents.

2. ### 📲 Local Communication (Offline Access)

   * Users can create or approve intents (e.g. send USDC, check balance).
   * These **intent messages are shared locally** over:

     * Bluetooth
     * Mesh WiFi
     * SMS
   * Messages propagate across users until they reach a **relayer-connected user**.

3. ### 🔁 Trusted Relayers

   * Relayers are **registered nodes** (e.g., country-specific SMS gateways).
   * These nodes forward the signed user intents to the **Phala TEE**, unmodified.
   * List of registered services is maintained by NoNetPay and validated on-chain.

4. ### 🧠 Secure Execution via Phala TEE

   * Phala validates the message:

     * Verifies the user identity & access rights
     * Executes logic (e.g., transfer funds, deposit/withdraw)
   * **Private keys never leave the TEE**.
   * Execution state is stored in **encrypted storage**.

5. ### 💰 Yield-Generating Smart Accounts

   * User funds are deposited to a **Safe Smart Account**
     ([Factory](https://pharosscan.xyz/address/0x3a689E0bB15655Dd71312AaD8BB734c434193F3b))
   * Deposits (e.g., USDC) are forwarded to a **lending protocol**
     ([Lending Protocol](https://pharosscan.xyz/address/0x0cdc955265276C912824750C66900FFe66cbE17f))
   * Assets are **natively supplied as liquidity** to earn yield automatically.
   * These funds can also be **composed into other protocols** to optimize yield.

6. ### 🔄 Yield Access & Withdrawal

   * Users can later request withdrawal or view balances using the same **offline message propagation model**.
   * Once the signed message is relayed to the TEE, it processes the request and updates the Safe wallet state accordingly.

