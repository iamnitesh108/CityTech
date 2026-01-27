# Complete Guide to Payment Systems & Financial Terminology

## Table of Contents
1. Foundation Concepts
2. Key Participants in Payment Systems
3. Payment Methods Deep Dive
4. Payment Lifecycle Stages
5. Nepal-Specific Payment Systems
6. Advanced Concepts

---

## 1. Foundation Concepts

### What is Money Movement?
Before diving into technical terms, understand that all payment systems exist to move money from one person/entity to another. Every terminology we'll learn relates to different stages or aspects of this money movement.

### Basic Definitions

**Payment**: The act of transferring money from a payer (buyer) to a payee (seller) in exchange for goods, services, or to settle a debt.

**Transaction**: A single instance of payment activity. When you buy coffee for Rs. 100, that's one transaction. It includes:
- Amount (Rs. 100)
- Payer (you)
- Payee (coffee shop)
- Timestamp (when it happened)
- Method (card, QR, cash)

**Digital Payment**: Any payment made electronically without physical cash changing hands.

---

## 2. Key Participants in Payment Systems

Understanding WHO is involved in payments is crucial before understanding HOW payments work.

### The Card Payment Ecosystem

**Cardholder**: The person who owns and uses the payment card (you, the customer).

**Merchant**: The business accepting the payment (shop, restaurant, online store).

**Issuer (Issuing Bank)**: 
- The bank that gave you your debit/credit card
- Holds your actual money/credit line
- Authorizes whether you have enough balance
- Example: If you have an NMB Bank debit card, NMB is your issuer
- Responsibilities:
  - Verify your identity
  - Check available balance
  - Approve or decline transactions
  - Debit money from your account

**Acquirer (Acquiring Bank/Merchant Bank)**:
- The bank that provides payment acceptance services to merchants
- Receives money on behalf of the merchant
- Example: If a coffee shop uses Nabil Bank's POS machine, Nabil is the acquirer
- Responsibilities:
  - Install POS terminals at merchant locations
  - Process merchant transactions
  - Credit money to merchant accounts
  - Handle chargebacks

**Payment Network (Card Scheme)**:
- The infrastructure connecting issuers and acquirers
- Examples: Visa, Mastercard, RuPay, NCB (Nepal Credit Bureau)
- Responsibilities:
  - Set rules and standards
  - Route transaction messages between banks
  - Manage security protocols
  - Handle dispute resolution

**Payment Gateway** (for online payments):
- Technology that captures and transmits card information securely
- Acts as the virtual equivalent of a POS terminal
- Examples: eSewa, Khalti (also work as payment gateways)

**Payment Processor**:
- Technical service that handles the actual transaction processing
- Connects merchants to payment networks
- May be the same entity as the acquirer or separate

---

## 3. Payment Methods Deep Dive

### A. Card-Based Payments

#### Card Components
A payment card contains:
- **Card Number (PAN - Primary Account Number)**: 16-digit unique identifier
- **Expiry Date**: Validity period
- **CVV (Card Verification Value)**: 3-digit security code
- **Chip (EMV)**: Embedded microprocessor for secure transactions
- **Magnetic Stripe**: Older technology for card reading

#### Types of Card Transactions

**Card Present (CP) Transaction**:
- Physical card is present at payment location
- Customer swipes/inserts/taps card on POS machine
- More secure, lower fraud risk
- Examples: Buying groceries, paying at restaurants

**Card Not Present (CNP) Transaction**:
- Card details entered manually without physical card
- Includes online payments, phone orders
- Higher fraud risk
- Examples: E-commerce, subscription payments

**Contact Transaction**:
- Card inserted into POS and chip read
- Requires PIN entry
- Most secure method

**Contactless Transaction**:
- Card tapped near POS terminal
- Uses NFC (Near Field Communication) technology
- Usually limited to smaller amounts (e.g., Rs. 5,000)
- No PIN required for small amounts

#### How a Card Payment Works (Detailed Flow)

**Step 1: Initiation**
- Customer presents card at POS terminal
- Merchant enters amount
- Customer inserts/taps card

**Step 2: Card Reading**
- POS reads card details from chip/stripe
- Encrypts the information

**Step 3: Authorization Request**
- POS sends request to acquirer's system
- Request contains: card number, amount, merchant ID, timestamp
- Acquirer forwards to card network (Visa/Mastercard)
- Network routes to issuing bank

**Step 4: Authorization Decision**
- Issuer checks:
  - Is card valid and not blocked?
  - Is there sufficient balance/credit?
  - Does transaction pattern seem normal (fraud check)?
- Issuer responds: Approved or Declined

**Step 5: Authorization Response**
- Response travels back: Issuer → Network → Acquirer → POS
- POS displays result to customer
- If approved, transaction is "authorized" but money hasn't moved yet

**Step 6: Completion**
- Customer receives receipt
- Transaction is recorded but in "pending" status
- Issuer places a "hold" on the funds

All this happens in 2-3 seconds!

---

### B. QR Code Payments

QR (Quick Response) codes are 2D barcodes that contain payment information. They've become popular because they don't require expensive POS machines.

#### Types of QR Codes

**Static QR Code**:
- Fixed QR code that doesn't change
- Merchant displays it at their shop
- Customer scans and enters amount manually
- Used for: Small shops, street vendors, donation boxes
- Example: A tea shop prints one QR code and sticks it on the wall

**Dynamic QR Code**:
- Generated fresh for each transaction
- Contains pre-filled amount
- Customer just scans and confirms
- Used for: Restaurants, larger merchants, e-commerce
- Example: Restaurant bill includes QR code with exact amount

#### QR Payment Standards in Nepal

**NPQR (Nepal QR - National Payment QR)**:
- Unified QR standard created by Nepal Rastra Bank (NRB)
- One QR code works with multiple payment apps
- Interoperable across banks and payment service providers
- Merchant needs only ONE QR code instead of separate codes for each bank/wallet
- Promotes financial inclusion

**Smart QR**:
- Enhanced QR payment system
- May include additional features like loyalty programs
- Can contain merchant information, tax details
- Sometimes used interchangeably with NPQR but may have proprietary features

**How NPQR Works**:
1. Merchant registers with any bank/PSP for NPQR
2. Merchant receives unique NPQR code
3. Code contains merchant ID, account details
4. Customer scans with ANY compatible app (eSewa, Khalti, bank apps)
5. Payment routes through NCHL (see below)
6. Money reaches merchant account

#### QR Payment Flow (Detailed)

**Step 1: QR Generation**
- Merchant account information encoded in QR
- For dynamic QR, amount also included
- QR displayed via print, phone screen, or digital display

**Step 2: Customer Scanning**
- Customer opens payment app (eSewa, Khalti, bank app)
- Uses camera to scan QR code
- App decodes merchant information and amount

**Step 3: Payment Initiation**
- Customer reviews merchant name and amount
- Enters PIN/biometric authentication
- Confirms payment

**Step 4: Processing**
- App sends request to customer's bank/wallet provider
- Request routed through payment switch (like NCHL)
- Customer account debited

**Step 5: Notification**
- Both parties receive instant confirmation
- Digital receipt generated
- Merchant can verify payment on their app/system

**Advantages of QR over Cards**:
- No expensive POS terminal needed
- Works on basic smartphones
- Lower transaction fees
- Faster adoption for small merchants
- Contactless and hygienic

---

## 4. Payment Lifecycle Stages

Every payment goes through distinct stages. Understanding these is crucial for reconciliation and troubleshooting.

### Authorization

**What it is**: The approval or denial of a transaction request.

**What happens**:
- Issuer verifies if transaction can proceed
- Funds are "reserved" or "held" but not transferred
- Creates an authorization code (approval reference)

**Status after**: Transaction is "authorized" but money still in customer account (just held/blocked)

**Example**: You pay Rs. 5,000 at a restaurant. Your bank approves and blocks Rs. 5,000 from your available balance, but the restaurant hasn't received money yet.

---

### Capture

**What it is**: The process of requesting the actual fund transfer after authorization.

**What happens**:
- Merchant confirms they want to collect the payment
- Usually happens automatically for most transactions
- For some businesses (hotels, car rentals), capture happens later

**Example**: Hotel authorizes Rs. 10,000 when you check in, but captures actual amount (Rs. 8,000) at checkout after calculating your bill.

**Timeframe**: Usually within 24-48 hours of authorization

---

### Clearing

**What it is**: The exchange of transaction information between financial institutions.

**What happens**:
- Banks share details of all day's transactions
- Each bank calculates what they owe to/receive from other banks
- Transaction details verified and matched
- Happens in batches, not individually

**Example**: At end of day, NMB Bank says "We owe Nabil Bank Rs. 500,000 from today's transactions" and vice versa.

**Timeframe**: Usually happens end of business day (EOD)

---

### Settlement

**What it is**: The actual transfer of funds between financial institutions.

**What happens**:
- Money moves from issuing bank to acquiring bank
- Usually netted (only difference paid, not gross amounts)
- Happens through central bank or clearinghouse

**Example**: If NMB owes Nabil Rs. 500,000 and Nabil owes NMB Rs. 300,000, NMB only transfers Rs. 200,000 net amount.

**Timeframe**: T+0 to T+2 days (T = Transaction day)
- T+0: Same day settlement (instant)
- T+1: Next day settlement
- T+2: Two days later

**Settlement Types**:
- **Gross Settlement**: Each transaction settled individually
- **Net Settlement**: All transactions batched and only difference paid
- **Real-time Settlement**: Instant settlement (used in UPI, some QR systems)

---

### Reconciliation

**What it is**: The process of matching and verifying transaction records across different systems.

**Why it's needed**: Different parties (merchant, acquirer, issuer) keep their own records. These must match.

**What happens**:
- Merchant compares POS records with bank deposits
- Banks match their records with payment network records
- Discrepancies identified and investigated

**Common Discrepancies**:
- Transaction authorized but not settled (reversal needed)
- Amount mismatch
- Transaction settled to wrong account
- Duplicate transactions
- Chargebacks (customer disputes)

**Example**: Restaurant POS shows 100 transactions totaling Rs. 50,000, but bank deposit is Rs. 49,500. Reconciliation finds one Rs. 500 transaction was reversed due to customer cancellation.

**Frequency**: Daily, weekly, monthly

**Reconciliation File**: A report containing:
- Transaction ID
- Date and time
- Amount
- Status (approved, declined, reversed)
- Settlement batch reference

---

### Disbursement

**What it is**: The payout of funds to the final recipient.

**What happens**:
- Acquiring bank transfers settled funds to merchant account
- May deduct fees (MDR - Merchant Discount Rate)
- Merchant receives net amount

**Example**: 
- Gross transactions: Rs. 100,000
- MDR (2%): Rs. 2,000
- Disbursement to merchant: Rs. 98,000

**Timeframe**: Varies by agreement
- Next day disbursement
- Weekly disbursement
- Monthly disbursement

**Disbursement Methods**:
- Direct bank account credit
- Wallet credit (for PSPs)
- Check (rare nowadays)

---

### Fund Transfer

**What it is**: Generic term for moving money from one account to another.

**Types**:

**RTGS (Real Time Gross Settlement)**:
- Individual, high-value transactions
- Settled immediately and individually (gross)
- Usually for amounts above Rs. 100,000
- Irrevocable once processed
- Example: Transferring Rs. 5,000,000 for property purchase

**NEFT (National Electronic Funds Transfer)**:
- Batch processing system
- Settled in hourly batches
- Used for smaller amounts
- Example: Paying monthly rent of Rs. 20,000

**SWIFT (Society for Worldwide Interbank Financial Telecommunication)**:
- International money transfers
- Messaging network between banks globally
- Example: Sending money from Nepal to USA

**Interbank Transfer vs. Intrabank Transfer**:
- **Intrabank**: Within same bank (instant, usually free)
- **Interbank**: Between different banks (requires clearing)

---

## 5. Nepal-Specific Payment Systems

### NCHL (National Clearing and Settlement House Limited)

**What it is**: Central payment switch and clearinghouse operator in Nepal, operated under Nepal Rastra Bank.

**Functions**:
1. **Switching**: Routes transactions between different banks and PSPs
2. **Clearing**: Processes and calculates inter-bank obligations
3. **Settlement**: Facilitates final fund transfer between banks

**Services Provided**:
- **NCHL-IPS (Inter-bank Payment System)**: Real-time interbank fund transfers
- **NCHL-ECC (Electronic Cheque Clearing)**: Electronic cheque processing
- **ConnectIPS**: Consumer-facing instant payment service
- **NPQR Switch**: Routes QR code payments

**How NCHL Enables Interoperability**:
- Customer at NMB Bank can pay via QR to merchant with Nabil Bank account
- NCHL acts as middleman, routing the transaction
- Both banks settle through NCHL

**Example Flow with NCHL**:
1. You (NMB customer) scan NPQR at merchant (Nabil account)
2. Request goes from NMB → NCHL → Nabil
3. Nabil confirms merchant account valid
4. NCHL debits NMB's account, credits Nabil's account (settlement)
5. Nabil credits merchant
6. All happens in near real-time

---

### ConnectIPS

**What it is**: Real-time interbank payment system for retail customers.

**Features**:
- Mobile-based fund transfers
- QR payments
- Works across all member banks
- Instant settlement

**Example**: You use your NMB mobile banking app to send money to your friend's Sanima Bank account instantly via ConnectIPS.

---

## 6. Advanced Concepts

### Acquiral vs. Accrual

**Acquiral** (in payments context):
- The act of acquiring/accepting a payment
- From acquirer's perspective: taking in merchant transactions
- Example: "Daily acquiral volume was Rs. 10 million" means that much was accepted from merchants

**Accrual** (in accounting):
- Recording revenue/expense when earned/incurred, not when cash received
- Example: Merchant made Rs. 100,000 sales today but won't get paid for 3 days. Still recorded as today's revenue (accrued).

---

### Chargeback

**What it is**: Reversal of a card payment initiated by the cardholder's bank.

**Common Reasons**:
- Fraudulent transaction
- Service not delivered
- Product defective
- Duplicate charge

**Process**:
1. Customer disputes transaction with issuer
2. Issuer reverses payment (debits acquirer)
3. Acquirer debits merchant account
4. Merchant can provide evidence to fight chargeback
5. If merchant wins, funds returned

**Impact**: Costly for merchants (chargeback fees, lost goods)

---

### Refund vs. Reversal

**Refund**:
- Merchant-initiated return of funds
- Transaction has already settled
- New transaction created (in opposite direction)
- Takes several days

**Reversal**:
- System-initiated cancellation
- Happens before settlement
- Original transaction voided
- Usually immediate
- Example: Transaction declined after authorization

---

### Authorization Hold

**What it is**: Temporary freeze on funds during authorization.

**Duration**: Usually 24-72 hours, can be up to 30 days for some merchants.

**Example**: You pay for gas with card, station authorizes Rs. 5,000 (hold), but you only fill Rs. 3,000. Hold releases after few days, only Rs. 3,000 charged.

---

### MDR (Merchant Discount Rate)

**What it is**: Fee charged to merchant for accepting card/digital payments.

**Components**:
- Interchange fee (goes to issuing bank)
- Assessment fee (goes to card network)
- Acquirer margin (acquirer's profit)

**Example**: 2% MDR on Rs. 1,000 transaction = Merchant receives Rs. 980, Rs. 20 goes to various parties in payment chain.

---

### Two-Factor Authentication (2FA)

**What it is**: Security measure requiring two forms of verification.

**Factors**:
1. Something you know (PIN, password)
2. Something you have (card, phone, OTP)
3. Something you are (fingerprint, face)

**Example**: Card payment requiring both card (have) and PIN (know).

---

### Tokenization

**What it is**: Replacing sensitive card data with a unique token.

**Why needed**: Protects card information from breaches.

**Example**: Your actual card number is 1234-5678-9012-3456, but stored as token "TKN-789XYZ" in merchant system. Even if hacked, real number is safe.

---

### PCI-DSS (Payment Card Industry Data Security Standard)

**What it is**: Security standards for handling card information.

**Requirements**:
- Encrypted storage
- Secure networks
- Regular security testing
- Access controls

**Who must comply**: Anyone storing, processing, or transmitting card data.

---

### API (Application Programming Interface) in Payments

**What it is**: Allows different software systems to communicate.

**Example**: E-commerce site uses payment gateway's API to process payments without building entire payment system themselves.

---

### Wallet Payments

**What it is**: Prepaid payment instrument storing funds digitally.

**Types in Nepal**:
- **Open Wallet**: Can send to bank, can withdraw (eSewa, Khalti after KYC)
- **Semi-closed Wallet**: Can only pay to merchants in network
- **Closed Wallet**: Can only use within issuer's ecosystem

**How it works**:
1. Load money from bank to wallet (top-up)
2. Wallet provider holds funds
3. Pay merchants from wallet balance
4. Settlement happens between wallet provider and merchant

---

### KYC (Know Your Customer)

**What it is**: Process of verifying customer identity.

**Required for**:
- Opening bank accounts
- Higher limits on wallets
- Large transactions

**Documents**: Citizenship, passport, utility bills, photo

---

### AML/CFT (Anti-Money Laundering / Combating Financing of Terrorism)

**What it is**: Regulations to prevent illegal money movement.

**Requirements**:
- Transaction monitoring
- Suspicious activity reporting
- Customer due diligence
- Transaction limits

---

### Merchant Category Code (MCC)

**What it is**: 4-digit code classifying merchant business type.

**Examples**:
- 5812: Restaurants
- 5411: Grocery stores
- 5541: Gas stations

**Why important**: Used for rewards, analytics, restrictions (e.g., can't use food card at gas station).

---

## 7. Putting It All Together: Complete Transaction Journey

Let's walk through a real-world example combining everything:

**Scenario**: You buy a Rs. 1,500 meal at a restaurant in Kathmandu using your Mega Bank debit card. The restaurant uses Nabil Bank's POS terminal.

**The Journey**:

**1. Initiation (0-2 seconds)**
- Waiter brings bill for Rs. 1,500
- You insert your Mega Bank card into POS
- POS reads chip, encrypts data

**2. Authorization (2-5 seconds)**
- POS sends to Nabil Bank (acquirer): "Mega Bank card requesting Rs. 1,500"
- Nabil forwards to Visa network: "Need approval"
- Visa routes to Mega Bank (issuer): "Customer wants to spend Rs. 1,500"
- Mega Bank checks:
  - Card valid? ✓
  - Balance available? (You have Rs. 25,000) ✓
  - Suspicious? (Normal spending pattern) ✓
- Mega Bank: "APPROVED - Authorization code 123456"
- Response travels back through Visa → Nabil → POS
- You enter PIN, POS prints receipt
- Your available balance now Rs. 23,500 (Rs. 1,500 held)

**3. End of Day - Clearing (11:59 PM)**
- Restaurant sends "capture" request for all day's transactions
- Nabil Bank prepares settlement file:
  - 250 transactions today
  - Total Rs. 450,000
  - Including your Rs. 1,500
- Nabil sends to NCHL: "We need Rs. 450,000 from various issuers"
- Mega Bank receives notification: "You owe Rs. 1,500 to Nabil for customer ABC's transaction"

**4. Settlement (Next Day, 10 AM - T+1)**
- NCHL calculates: Mega Bank owes Nabil Rs. 1,500 (among others)
- After netting all transactions, Mega Bank transfers net amount to Nabil through Nepal Rastra Bank
- Your Rs. 1,500 officially moves from Mega Bank to Nabil Bank

**5. Disbursement (Next Day, 5 PM)**
- Nabil Bank credits restaurant's account
- Gross amount: Rs. 1,500
- MDR (2%): Rs. 30
- Restaurant receives: Rs. 1,470

**6. Reconciliation (Next Day)**
- Restaurant's POS report shows 250 transactions, Rs. 450,000
- Bank statement shows deposit of Rs. 441,000 (after Rs. 9,000 MDR)
- Accountant matches each transaction
- Your Rs. 1,500 transaction marked as "settled"

**Final Result**:
- You: Paid Rs. 1,500 (reflected in bank statement)
- Restaurant: Received Rs. 1,470 (Rs. 30 fee paid)
- Mega Bank: Earned Rs. 5 (interchange fee)
- Visa: Earned Rs. 3 (network fee)
- Nabil Bank: Earned Rs. 22 (acquirer margin)

**Total fees: Rs. 30 (2% of Rs. 1,500)**

---

## 8. Common Questions

**Q: Why does payment take days to show in merchant account?**
A: Authorization is instant, but settlement (actual money movement) happens in batches for efficiency. Imagine if banks had to transfer money individually for millions of transactions - too slow and expensive!

**Q: Why is QR payment faster than card?**
A: Many QR systems (like NPQR through ConnectIPS) use real-time settlement, while card payments use batch settlement. Plus, QR has fewer intermediaries.

**Q: What happens if I pay but merchant says payment failed?**
A: Money is on "authorization hold" but will be automatically reversed in 3-7 days if transaction didn't complete. Always keep receipts!

**Q: Why do refunds take longer than original payment?**
A: Original payment was just authorization (instant). Refund requires creating new transaction, clearing, settlement - full cycle again.

**Q: Is NPQR safer than regular QR?**
A: NPQR follows Nepal Rastra Bank standards with mandatory security features. Regular proprietary QR codes may vary in security.

---

## 9. Key Terminology Quick Reference

| Term | Simple Definition |
|------|------------------|
| Authorization | Permission to proceed with payment |
| Capture | Requesting actual fund collection |
| Clearing | Banks sharing transaction details |
| Settlement | Actual money transfer between banks |
| Reconciliation | Matching records across systems |
| Disbursement | Paying out to final recipient |
| Issuer | Bank that gave you the card |
| Acquirer | Bank that serves the merchant |
| MDR | Fee charged to merchant |
| Chargeback | Payment reversal due to dispute |
| NCHL | Central payment switch in Nepal |
| NPQR | Unified QR standard in Nepal |
| Tokenization | Replacing card data with secure token |
| 2FA | Two-step verification |
| Interoperability | Different systems working together |

---

## Conclusion

Payment systems are complex ecosystems involving multiple parties, technologies, and processes. The key is understanding that every payment goes through distinct stages (authorization → capture → clearing → settlement → disbursement), and different parties play specific roles (issuer, acquirer, network, switch).

In Nepal, NCHL and NPQR have revolutionized payments by creating interoperability, allowing seamless transactions across banks and payment service providers.

As digital payments evolve, new technologies like blockchain, instant settlement, and AI-based fraud detection are making payments faster, cheaper, and more secure. But the fundamental concepts - moving money safely from payer to payee - remain the same.

Understanding these terminologies helps you better navigate digital payments, whether as a consumer, merchant, or someone working in the fintech industry.