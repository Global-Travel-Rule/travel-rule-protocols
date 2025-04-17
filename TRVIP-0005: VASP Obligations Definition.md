[# **VASP Obligations Definition**

### Introduction

The Financial Action Task Force (FATF) Travel Rule establishes regulatory requirements for Virtual Asset Service
Providers (VASPs) to enhance transparency and mitigate financial crime risks associated with virtual asset transactions.
This paper defines the obligations of VASPs under the FATF Travel Rule, focusing on compliance measures, data-sharing
responsibilities, and risk mitigation strategies. Key obligations include customer due diligence (CDD), collection and
transmission of originator and beneficiary information, secure data handling, and collaboration with other VASPs and
regulators. Additionally, this paper outlines the technical and operational challenges in implementing the Travel Rule,
addressing issues such as interoperability, regulatory variations across jurisdictions, and privacy concerns. By
adhering to these obligations, VASPs can strengthen anti-money laundering (AML) and counter-terrorism financing (CFT)
efforts, ensuring regulatory compliance while fostering trust within the virtual asset ecosystem.

## Travel Rule (GTR) Obligations

The **Financial Action Task Force (FATF) Travel Rule** requires **Virtual Asset Service Providers (VASPs)** to collect,
verify, and transmit key identity information for originators and beneficiaries of virtual asset transactions. This
document outlines the obligations of different categories of VASPs and wallet providers, explaining their
responsibilities in ensuring compliance with the Travel Rule.

## 1. VASP (Regulated)

Regulated VASPs must ensure compliance with jurisdictional AML/CFT regulations, collecting and verifying user
information before processing transactions.

### 1.1 VASP(O) - Originating VASP

The originating VASP (VASP(O)) initiates a transaction and is responsible for collecting and verifying the sender's and
recipient's details.

| Obligation                       | Description                                                                                                  |
|----------------------------------|--------------------------------------------------------------------------------------------------------------|
| Collect Beneficiary PII          | Obtain personally identifiable information (PII) from the user before initiating a blockchain transaction.   |
| Send Beneficiary PII             | Transmit the collected beneficiary PII securely to the receiving VASP (VASP(B)).                             |
| Decision on Transaction          | Determine whether to proceed with the blockchain transaction based on verification results from VASP(B).     |
| Sync Blockchain Transaction      | Ensure that the blockchain transaction is synchronized with the Travel Rule information and sent to VASP(B). |
| Transaction Verification         | Validate transaction integrity and ensure compliance.                                                        |
| Receive Originator PII           | Receive the originator PII from VASP(B).                                                                     |
| Decrypt & Verify PII             | Decrypt and verify the received PII against compliance rules.                                                |
| Respond with Verification Result | Send the verification outcome to VASP(B).                                                                    |

### 1.2 VASP(B) - Beneficiary VASP

The beneficiary VASP (VASP(B)) is responsible for verifying the recipient's details and responding to the originating
VASP.

| Obligation                       | Description                                                                                    |
|----------------------------------|------------------------------------------------------------------------------------------------|
| Address Verification             | Validate the beneficiary address before processing the transaction.                            |
| Receive Beneficiary PII          | Accept and process beneficiary PII sent by VASP(O).                                            |
| Decrypt & Verify PII             | Ensure the received PII is valid and complies with regulations.                                |
| Respond with Verification Result | Provide verification feedback to VASP(O).                                                      |
| Collect Originator PII           | Obtain originator PII from the user after the blockchain transaction.                          |
| Data Sources for Originator PII  | Gather PII from either GTR or from VASP(B) users (offshore or non-integrated users).           |
| Send Originator PII to VASP(O)   | Transmit the collected PII back to the originating VASP.                                       |
| Decision to Complete Deposit     | Make a final decision on completing the deposit based on the verification result from VASP(O). |

---

## 2. VASP (Offshore)

Offshore VASPs operate outside regulated jurisdictions but may still interact with regulated VASPs under the Travel
Rule.

### 2.1 VASP(O) - Offshore Originating VASP

| Obligation                       | Description                                                        |
|----------------------------------|--------------------------------------------------------------------|
| Verify Transaction Existence     | Confirm that the transaction exists and is valid.                  |
| Receive Beneficiary PII          | Accept and process beneficiary PII from VASP(B).                   |
| Decrypt & Verify PII             | Ensure the received PII complies with internal verification rules. |
| Respond with Verification Result | Provide verification feedback to VASP(B).                          |

### 2.2 VASP(B) - Offshore Beneficiary VASP

| Obligation                       | Description                                                                     |
|----------------------------------|---------------------------------------------------------------------------------|
| Verify Address Existence         | Ensure that the provided address is valid and associated with the correct user. |
| Receive Beneficiary PII          | Accept and process beneficiary PII from VASP(O).                                |
| Decrypt & Verify PII             | Confirm the legitimacy of the received PII.                                     |
| Respond with Verification Result | Send verification results back to VASP(O).                                      |

---

## 3. Custodial Wallets

Custodial wallets are provided by VASPs, meaning they control users' private keys and must comply with Travel Rule
obligations.

### 3.1 VASP(O) - Custodial Originating VASP

| Obligation                  | Description                                                        |
|-----------------------------|--------------------------------------------------------------------|
| Collect Beneficiary PII     | Obtain beneficiary details before initiating the transaction.      |
| Send Beneficiary PII        | Transmit beneficiary PII securely to VASP(B).                      |
| Decision on Transaction     | Approve or reject the transaction based on VASP(B)’s verification. |
| Sync Blockchain Transaction | Ensure blockchain transaction details match Travel Rule records.   |

### 3.2 VASP(B) - Custodial Beneficiary VASP

| Obligation                       | Description                                                                          |
|----------------------------------|--------------------------------------------------------------------------------------|
| Collect Originator PII           | Obtain PII from the originator after the transaction is completed.                   |
| Data Sources for Originator PII  | Gather PII from either GTR or from VASP(B) users (offshore or non-integrated users). |
| Verify Address Existence         | Ensure the validity of the receiving wallet address.                                 |
| Receive Beneficiary PII          | Accept and process beneficiary PII from VASP(O).                                     |
| Decrypt & Verify PII             | Validate the received PII against regulatory standards.                              |
| Respond with Verification Result | Send verification results to VASP(O).                                                |

---

## 4. Unhosted Wallets

Unhosted wallets (self-custodial wallets) allow users to retain control over their private keys. While they are not
VASPs, VASPs interacting with them must still verify compliance.

### 4.1 Self-Hosted Wallets

| Role        | Obligation                            |
|-------------|---------------------------------------|
| **VASP(B)** | Verify Beneficiary address ownership. |
| **VASP(O)** | Verify Originator address ownership.  |

### 4.2 Third-Party Hosted Wallets

| Role        | Obligation                                            |
|-------------|-------------------------------------------------------|
| **VASP(B)** | Establish 3rd-party identity verification mechanisms. |
|             | Establish the identity of the Beneficiary.            |
|             | Verify Beneficiary address ownership.                 |
| **VASP(O)** | Establish 3rd-party identity verification mechanisms. |
|             | Establish the identity of the Originator.             |
|             | Verify Beneficiary address ownership.                 |

---

## Conclusion

The FATF Travel Rule imposes strict compliance obligations on VASPs, custodial wallet providers, and other virtual asset
entities to prevent financial crimes such as money laundering and terrorist financing. **Regulated VASPs** have the most
stringent responsibilities, including the collection, verification, and transmission of originator and beneficiary PII.
**Offshore VASPs** and **custodial wallets** must also ensure compliance based on their jurisdictional regulations.
Meanwhile, **unhosted wallets** present additional challenges, requiring VASPs to implement identity verification
measures when interacting with them.

By adhering to these obligations, VASPs contribute to a more secure and transparent virtual asset ecosystem, ensuring
regulatory compliance and fostering trust among users and regulators.](https://git.toolsfdg.net/bigdata/protocols.git)