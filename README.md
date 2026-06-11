# AbotPera 🚀

## 🧩 Problem
Many people in rural areas, remote barangays, island communities, and provincial towns have limited, unreliable, or zero access to 4G/WiFi. Because of this, they are often excluded from using e-wallets and digital transactions that require a constant broadband internet connection. This heavily affects small merchants, sari-sari stores, wet market vendors, tricycle drivers, and everyday users who want to participate in digital payments but cannot rely on online systems.

Our challenge: **How can people continue to access secure, real-time digital payments in zero-data areas without requiring merchants to buy expensive hardware or assume the risk of delayed settlement?**

## 🌟 Vision
Digital money within reach, even without mobile data. Our vision is to bridge the gap between cutting-edge Web3 blockchain cryptography and ubiquitous 20-year-old GSM cellular infrastructure. We aim to make decentralized finance accessible to 100% of Filipinos, regardless of their geographical location or telco data connectivity.

## 🎯 Purpose
We built AbotPera to onboard the unbanked and disconnected into the decentralized financial system. By eliminating the reliance on active broadband internet for settlement, we empower grassroots micro-economies to transact with the speed, security, and finality of the Stellar network, using the simple feature phones and basic smartphones they already own.

## 👥 Target Users
Our primary users are Filipinos operating in the informal or provincial economy:
- **Sari-Sari Store Owners & Market Vendors:** Micro-merchants who need to receive real-time digital payments but lack the funds for expensive POS systems or consistent WiFi.
- **Provincial Customers & Commuters:** Everyday users who want the security of cashless transactions without the anxiety of losing their 4G signal at the point of sale.

## ✨ Features
- **Zero-Data Offline Payments:** Customers sign payments entirely offline via a cryptographically secure QR code. Merchants process the payment via a standard Unli-Text SMS.
- **Trusted Oracle Gateway:** A custom Web2.5 SMS-to-Web3 bridge that intercepts 116-character compressed SMS payloads, locally verifies Ed25519 mathematical signatures, and acts as a relayer to pay Stellar network XLM gas fees on behalf of offline users.
- **Idempotency & Telco Lag Protection (Nonces):** On-chain Soroban temporary storage (`DataKey::Nonce`) prevents double-spending. If the cellular network lags and a merchant resends the SMS, the blockchain instantly recognizes the duplicate and protects the vault.
- **Merchant Safety Timelock:** Funds are locked into a smart contract escrow vault prior to spending, guaranteeing merchants that the customer's funds are mathematically reserved and secured before goods are handed over.

## 🛠️ Tech Stack
- **Frontend:** React Native (Mobile App for Offline QR Generation & Compression)
- **Backend:** Next.js API Routes, Prisma ORM (SQLite)
- **Blockchain:** Stellar (Soroban SDK, Rust Smart Contracts, `@stellar/stellar-sdk`)
- **Other tools:** Textbee (Zero-API SMS Gateway), Tailscale, Node.js Crypto (Ed25519 Verification)

## 🚀 How to Run Locally

**1. Clone the repository**
~~~bash
git clone https://github.com/your-repo/abotpera.git
cd abotpera
~~~

**2. Setup the Next.js Backend & Webhook**
~~~bash
cd apps/backend
npm install
npx prisma generate
npx prisma db push
~~~

**3. Setup the Smart Contract Workspace (Optional)**
~~~bash
cd contracts/abotpera-contract
cargo test -- --nocapture
stellar contract build
~~~

**4. Configure Environment Variables (.env)**
~~~env
RELAYER_PUBLIC_KEY="GARFLBHJRTLJUFCXMMOTAND22OVWSFBTS2KJ73JPC754RF3WAJFPFKXY"
RELAYER_SECRET_KEY="<YOUR_SECRET_KEY>"
DATABASE_URL="file:./dev.db"
CONTRACT_ID="CDSVMX6TH3PUSGJEIZE7RCDPSUJOAX7WXXLTHKATSDI3SAVUTTFPTEJ2"
TOKEN_ID="CDLZFC3SYJYDZT7K67VZ75HPJVIEUVNIXF47ZG2FB2RMQQVU2HHGCYSC"
~~~

**5. Start the Development Server**
~~~bash
npm run dev
~~~

## 🌐 Deployment

### Testnet
- **Smart Contract Address:** `CDSVMX6TH3PUSGJEIZE7RCDPSUJOAX7WXXLTHKATSDI3SAVUTTFPTEJ2`
- **Native PHP Token Address:** `CDLZFC3SYJYDZT7K67VZ75HPJVIEUVNIXF47ZG2FB2RMQQVU2HHGCYSC`
- **Trusted Gateway / Relayer:** `GARFLBHJRTLJUFCXMMOTAND22OVWSFBTS2KJ73JPC754RF3WAJFPFKXY`
- 📸 **Screenshot — Stellar Expert (Testnet)**
  <img width="1636" height="924" alt="testnet" src="https://github.com/user-attachments/assets/09b64eca-6e43-4a6b-b8f3-c58212de8551" />


### Mainnet
- **Smart Contract Address:** `CCJUISYGMTZUMFGOBZI5BTXWR37I6FGE37BCZFVDXNXAK4BFOPAXKI6W`
- **Soroban RPC:** `https://rpc.lightsail.network`
- **Native XLM Token Address:** `CAS3J7GYLGXMF6TDJBBYYSE3HQ6BBSMLNUQ34T6TZMYMW2EVH34XOWMA`
- **Trusted Gateway / Relayer:** `GCKXZ4Y5RVLDCIRX5ULK252HBDCW52TRTYJYVHVEBVKXELVYS6M5B5MH`
- 📸 **Screenshot — Stellar Expert (Mainnet)**
  <img width="1636" height="924" alt="mainnet" src="https://github.com/user-attachments/assets/e0b46999-2540-4085-84b2-14ccfb0f2dfe" />


## 👨‍💻 Team
| Name | Role | GitHub |
|---|---|---|
|Mark Kengie Aldabon| Frontend Developer / DevOps | [@Mark](https://github.com/tambayNgOrtigasAvenue ) |
| Carl Arbolado | Backend Developer / Frontend Developer / Team Lead | [@Carl](https://github.com/Kaido147) |
| Erickson Guhilde | Backend Developer / Quality Assurance | [@Erickson](https://github.com/riXoon) |
| Cedric Paul Mendoza | System Architect / System Analyst | [@Cedric](https://github.com/daeroSys) |
| Janrell Quiaroro | Backend Developer / Quality Assurance | [@Janrell](https://github.com/0xreru) |

## 📜 License
MIT
