# Error Codes for Travel Rule Verification

**Background**

The Travel Rule is a critical compliance requirement for Virtual Asset Service Providers (VASPs) to ensure transparency
and accountability in virtual asset transactions. The rule mandates the collection, verification, and transmission of
certain Personally Identifiable Information (PII) during transactions to prevent illicit activities. The process
typically involves multiple verification stages, including address validation, identity verification, and sanction
screening.

Throughout the Travel Rule process, different types of failures can occur, leading to various error codes. These errors
are categorized into verification status, business failures, request submission issues, and networking failures.
This document outlines the error codes used in Travel Rule verification processes, categorized by different types of
failures. These error codes help identify issues and ensure smooth troubleshooting in VASP transactions.

---

## 1. Verification Status Codes

These codes indicate whether the verification process has passed or is still pending.

| Category                     | Name    | Code Number | Description                                          |
|------------------------------|---------|-------------|------------------------------------------------------|
| **Verification Pass or Not** | SUCCESS | 100000      | Verification successful.                             |
|                              | PENDING | 100002      | Verification is incomplete or awaiting confirmation. |

---

## 2. Common Business Failures

These errors indicate failures in processing transactions due to common business logic issues.

| Category                     | Name                               | Code Number | Description                                                             |
|------------------------------|------------------------------------|-------------|-------------------------------------------------------------------------|
| **Common Business Failures** | FAIL                               | 100001      | Verification failed.                                                    |
|                              | CANCEL                             | 100028      | Travel Rule verification was canceled by VASP.                          |
|                              | FAIL_ON_COMMON_ADDRESS_NOT_EXISTS  | 200001      | The address could not be found.                                         |
|                              | FAIL_ON_STANDARD_PII_DECRYPT       | 200002      | Failed to decrypt PII.                                                  |
|                              | FAIL_ON_STANDARD_PII_VERIFY        | 200003      | PII verification failed.                                                |
|                              | FAIL_ON_STANDARD_PII_ENCRYPT       | 200006      | Unable to encrypt PII.                                                  |
|                              | FAIL_ON_CHALLENGE_HASH_NOT_MATCH   | 200004      | Hash verification failed.                                               |
|                              | FAIL_ON_COMMON_ADDRESS_VERIFY_FAIL | 200005      | Address verification failed due to incorrect or incomplete information. |
|                              | FAIL_ON_COMMON_TX_ID_NOT_FOUND     | 200007      | Transaction ID not found.                                               |

---

## 3. Detailed Business Failures

These errors provide more specific reasons for verification failures related to user KYC, wallet ownership, and VASP
interactions.

| Category                       | Name                                      | Code Number | Description                                                                                 |
|--------------------------------|-------------------------------------------|-------------|---------------------------------------------------------------------------------------------|
| **Detailed Business Failures** | FAIL_ON_NO_KYC                            | 200008      | User lacks KYC data; must complete KYC before proceeding.                                   |
|                                | FAIL_ON_IVMS_NAME_MISMATCH                | 200009      | Name mismatch in IVMS data.                                                                 |
|                                | FAIL_ON_SANCTION_LIST                     | 200010      | User is listed in the VASP's sanction list.                                                 |
|                                | FAIL_ON_PII_ORIGINATOR_INFO_INSUFFICIENT  | 200011      | Insufficient PII information for the originator.                                            |
|                                | FAIL_ON_PII_BENEFICIARY_INFO_INSUFFICIENT | 200012      | Insufficient PII information for the beneficiary.                                           |
|                                | FAIL_ON_UNHOSTED_WALLET_WRONG_OWNER       | 200013      | The provided wallet address does not match the declared owner (user ID).                    |
|                                | FAIL_ON_UNHOSTED_WALLET_CANNOT_LOCATE     | 200014      | Wallet found, but user cannot be identified—user ID is required.                            |
|                                | FAIL_ON_BENEFICIARY_REJECT_TRANSFER       | 200015      | The beneficiary has rejected the transfer—user confirmation required.                       |
|                                | FAIL_ON_VASP_REJECT_REQUEST               | 200016      | Target VASP has rejected the request (e.g., not whitelisted or no due diligence agreement). |
|                                | EXISTS_BUT_WRONG_VASP                     | 200017      | Address or transaction exists but is linked to the wrong VASP—redirect required.            |

---

## 4. Failures for Submit Requests

Errors related to incorrect or duplicate request submissions.

| Category                         | Name                              | Code Number | Description                         |
|----------------------------------|-----------------------------------|-------------|-------------------------------------|
| **Failures for Submit Requests** | FAIL_ON_CLIENT_BAD_PARAMETERS     | 100004      | Incorrect request parameters.       |
|                                  | FAIL_ON_CLIENT_INVALID_PARAMETERS | 100023      | Invalid parameters in the request.  |
|                                  | FAIL_ON_REQUEST_ID_DUPLICATED     | 100005      | Duplicate request ID detected.      |
|                                  | FAIL_ON_TX_DUPLICATED             | 100029      | Transaction ID has been duplicated. |

---

## 5. Networking Failures

Errors caused by system connectivity issues or incorrect process execution.

| Category                | Name                      | Code Number | Description                                      |
|-------------------------|---------------------------|-------------|--------------------------------------------------|
| **Networking Failures** | ORIGINATOR_SERVER_FAIL    | 100007      | Originating VASP internal server error.          |
|                         | BENEFICIARY_SERVER_FAIL   | 100008      | Beneficiary VASP internal server error.          |
|                         | VASP_NOT_FOUND            | 100015      | Target VASP could not be found.                  |
|                         | VASP_PUBLIC_KEY_NOT_FOUND | 100016      | Target VASP public key could not be found.       |
|                         | FAIL_ON_WRONG_FLOW        | 100027      | Incorrect invocation order—flow execution error. |

---

## Conclusion

This structured list of error codes ensures clarity in diagnosing issues during Travel Rule verification. By
categorizing errors, VASPs can efficiently identify and address problems related to compliance, transaction
verification, and system connectivity.

---