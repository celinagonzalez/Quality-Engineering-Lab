# Questions Before Testing

The following questions would be clarified with Product/Engineering before execution to avoid making assumptions that could affect financial correctness, customer experience, or test results.

## Business Rules

1. Is the 90-day window based on calendar days or exactly 90 × 24 hours?

2. Is a refund requested exactly 90 days after the payment date considered eligible?

3. Which timezone should be used when calculating the 90-day eligibility window?

4. Are partial refunds supported, or must the full payment amount be refunded?

5. Are there any additional eligibility rules based on payment status, previous refunds, chargebacks, or account status?

## Payment Method

6. What exactly qualifies as an "unavailable" original payment method? For example, does an expired, replaced, or deleted payment method qualify?

7. What should happen if the payment provider rejects or fails the refund to the original payment method?

## Data Integrity

8. Can a customer submit multiple refund requests for the same payment? If so, how should duplicate or concurrent requests be handled?

9. What should be considered the source of truth in the database when verifying the refund amount, status, destination, and account balance?

## Notifications

10. Should the confirmation email be sent only after the refund or account credit has been successfully completed?

11. What should happen if the refund succeeds but the confirmation email cannot be delivered?

12. Should rejected or failed refund requests generate an email notification?

## Key Risks Identified

* **Financial integrity:** Incorrect refund amounts or duplicate processing could result in financial loss.
* **Eligibility boundary:** Ambiguity around the 90-day limit could lead to inconsistent refund decisions.
* **Refund destination:** Incorrect classification of an unavailable payment method could result in funds being sent to the wrong destination.
* **Data consistency:** The payment, refund, account balance, and notification should remain consistent after processing.

