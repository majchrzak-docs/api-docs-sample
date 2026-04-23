# API Documentation Sample

This sample demonstrates how I structure developer documentation for clarity, usability, and machine readability.

Focus areas:
- Clean API structure
- Developer usability
- Consistent request/response patterns
- LLM-friendly formatting


# Wallet Creation & Transaction Signing

This guide demonstrates how to:
- Create a wallet
- Sign a transaction
- Broadcast a transaction


## Overview

Turnkey provides secure, programmable key management via API. Private key material is never exposed. All cryptographic operations are executed within a secure environment.


## Prerequisites

- API credentials (API Key, Organization ID)
- Node.js 18+ or Python 3.9+
- Basic familiarity with REST APIs


## 1. Create a Wallet

### Endpoint

POST /v1/wallets


### Request

```json
{
  "name": "example-wallet",
  "type": "EOA",
  "curve": "secp256k1"
}
### Response
{
  "walletId": "wlt_12345",
  "address": "0xABCDEF...",
  "createdAt": "2026-04-23T12:00:00Z"
}

Notes
	•	type specifies the wallet type (EOA = externally owned account)
	•	curve defines the cryptographic curve used for key generation

2. Sign a Transaction

Endpoint

POST /v1/transactions/sign

### Request
{
  "walletId": "wlt_12345",
  "payload": {
    "to": "0xRecipientAddress",
    "value": "0x2386F26FC10000",
    "gasLimit": "0x5208"
  }
}

### Response
{
  "signature": "0xSignedTransactionData",
  "status": "signed"
}

Notes
	•	The private key is never exposed
	•	Signing is performed within a secure execution environment

3. Broadcast Transaction

Endpoint

POST /v1/transactions/broadcast

### Request

{
  "signedTransaction": "0xSignedTransactionData"
}

### Response

{
  "txHash": "0xTransactionHash",
  "status": "pending"
}

Error Handling

All endpoints return standard HTTP status codes:
	•	200: Success
	•	400: Invalid request
	•	401: Authentication error
	•	500: Internal error

### Example Error

{
  "error": {
    "code": "INVALID_WALLET_ID",
    "message": "Wallet not found"
  }
}

Design Considerations
	•	Security-first: key material is never exposed
	•	Consistent structure improves usability and reliability
	•	Documentation is formatted for both human and machine readability

Next Steps
	•	Add multi-signature support
	•	Integrate smart contract interactions
	•	Automate workflows using agents

---

# What To Do After Pasting

1. Scroll down  
2. In the small box, write:

Add API documentation sample


