# AcademiaVault

## Decentralized Academic Credential Management System on Stacks

---

## 📚 Overview

**AcademiaVault** is a decentralized academic credential issuance, management, and verification platform built on the **Stacks blockchain**, leveraging the **Bitcoin network's security** via Proof-of-Transfer (PoX). It empowers educational institutions to mint and manage cryptographically verifiable credentials, such as diplomas and certificates, as digital assets.

AcademiaVault brings paper-based verification into the modern era, ensuring lifelong verifiability, ownership, and transparency—without relying on centralized intermediaries.

---

## 🚀 Features

* **Institutional Onboarding with Stake**
  Universities and colleges register on-chain by staking tokens, ensuring accountability and reputation tracking.

* **Immutable Digital Credentials**
  Institutions issue credentials tied to Bitcoin via Stacks smart contracts—secure, traceable, and fraud-proof.

* **Batch Credential Issuance**
  High-throughput issuance of up to 50 credentials per transaction with full on-chain metadata and validation.

* **Decentralized Endorsements**
  Institutions can endorse credentials issued by others, providing validation layers with weight and comments.

* **Secure Ownership Transfer**
  Enables peer-to-peer transfer of credentials with built-in expiration and dual-party confirmation.

* **Delegation and Role-Based Permissions**
  Institutions can assign delegates with scoped permissions and expirations for internal governance.

---

## 🏗 System Overview

```
+---------------------------+
|    Educational Institution|
+-------------+-------------+
              |
              | Register + Stake
              v
+-------------+-------------+
|       AcademiaVault       |
|     (Clarity Smart Contract)|
+-------------+-------------+
              |
              | Issue Credentials (Single or Batch)
              v
+-------------+-------------+
|  Credentials Ledger (Map) |
|     + Metadata, Expiry    |
|     + Verification        |
+-------------+-------------+
              |
              | Endorsements + Transfer Requests
              v
+-------------+-------------+
| Users (Students/Employers)|
+---------------------------+
```

---

## 📜 Contract Architecture

AcademiaVault is built with Clarity, the smart contract language for Stacks. It uses a modular, secure, and extensible architecture with strict input validation and error management.

### 📌 Key Components

| Component               | Description                                                            |
| ----------------------- | ---------------------------------------------------------------------- |
| `institutions`          | Stores registered institutions and their stake, reputation, and state. |
| `credentials`           | Maps credential IDs and students to credential metadata.               |
| `endorsements`          | Tracks third-party institutional endorsements.                         |
| `institution-delegates` | Manages scoped delegate permissions for institutional accounts.        |
| `transfer-requests`     | Handles secure credential ownership transfers.                         |

### 🧩 Contract Constants

* `MINIMUM-STAKE`: Minimum STX required to register an institution.
* `MAX-BATCH-SIZE`: Controls maximum credentials issued per batch.
* `contract-owner`: Creator of the contract.

### ❗ Error Codes

Standardized error handling is provided using constants such as:

* `ERR-NOT-AUTHORIZED`
* `ERR-INVALID-INPUT`
* `ERR-CREDENTIAL-NOT-FOUND`
* `ERR-ALREADY-ENDORSED`, etc.

---

## 🔄 Data Flow: Credential Issuance & Verification

1. **Institution Registers**: Stakes required amount and registers name.
2. **Credential Issuance**: Institution issues credentials to students (single or batch).
3. **Endorsement**: Other institutions can endorse issued credentials.
4. **Transfer Request**: Credential owners can request a transfer to another user.
5. **Verification**: Employers or verifiers can query credentials via read-only functions.

---

## 📘 Key Functions

### Institution Management

* `register-institution(name)`
* `add-delegate(delegate, permissions, expiry)`

### Credential Management

* `issue-credential(id, student, degree, year, metadata-url, expiry, category)`
* `batch-issue-credentials(...)`

### Endorsements

* `endorse-credential-extended(id, student, weight, comment, type)`

### Transfer System

* `request-credential-transfer(id, new-owner, type, expiry)`

### Read-Only Utilities

* `get-institution-info(...)`
* `get-credential-info(...)`
* `is-credential-valid(...)`
* `get-validation-level(...)`

---

## 🔐 Security Considerations

* **Immutable Data**: Once issued, credentials cannot be edited—only revoked or expired.
* **Strict Validation**: Extensive use of `asserts!` and internal validators.
* **Delegated Authority**: Institutions can delegate specific roles, with expiry and permission control.
* **Ownership Checks**: Prevents self-delegation, duplicate endorsements, and unauthorized actions.

---

## 🧪 Testing & Deployment

Use the Clarity testing environment (`clarinet`) to run tests and simulate deployment scenarios. Ensure you test:

* Credential issuance & validation
* Expiry & revocation edge cases
* Delegation permission flows
* Batch issuance limits

---

## 🧠 Future Enhancements

* **Credential Revocation Lists (CRLs)**
* **ZK-Based Privacy Layer**
* **Integration with Decentralized Identity (DID) protocols**
* **Institutional Reputation Weighting in Endorsements**
* **Cross-chain Portability via sBTC or Bitcoin Ordinals**

---

## 🤝 Contributors

Built by a senior Stacks developer community committed to decentralized education reform and lifelong verifiability of learning achievements.

---

## 📄 License

MIT License. See `LICENSE` for more details.

---

## 🔗 Useful Links

* [Stacks Documentation](https://docs.stacks.co/)
* [Clarity Language Reference](https://docs.stacks.co/references/language-clarity)
* [Bitcoin Proof-of-Transfer (PoX)](https://docs.stacks.co/understand-stacks/proof-of-transfer)
