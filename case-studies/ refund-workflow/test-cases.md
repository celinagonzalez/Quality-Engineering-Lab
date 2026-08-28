# Test Cases — Refund Workflow

## TC-01 — Refund within the 90-day eligibility window

**Risk / Rationale**

A valid refund could be incorrectly rejected or processed incorrectly, resulting in customer impact or financial discrepancies.

### Preconditions

* A customer has a successful payment.
* The payment was made less than 90 days ago.
* The original payment method is available.
* The payment has not been refunded previously.

### Steps

1. Log in as the customer.
2. Navigate to the payment history.
3. Select an eligible payment.
4. Request a refund.
5. Confirm the refund request.

### Expected Result

* The refund request is accepted.
* The refund is processed to the original payment method.
* The refund amount matches the original payment amount.
* The refund status is updated correctly.
* A confirmation email is generated.

### Verification

**UI**

* Verify refund status.
* Verify refund amount.
* Verify the refund destination.

**Database**

* Verify the original payment record.
* Verify that a refund record exists.
* Verify the refund amount, status, and reference to the original payment.
* Verify that the original payment method is associated with the refund.

**Email**

* Verify that a confirmation email was generated and sent to the correct customer.
* Verify the payment/refund reference and amount.

---

## TC-02 — Refund requested exactly at the 90-day boundary

**Risk / Rationale**

An incorrect interpretation of the 90-day boundary could cause valid refund requests to be rejected or invalid requests to be accepted, creating financial and customer-impacting issues.

### Preconditions

* A successful payment exists.
* The payment date is exactly 90 days before the refund request.

### Steps

1. Log in as the customer.
2. Navigate to the payment history.
3. Select the payment at the 90-day boundary.
4. Request a refund.

### Expected Result

**To be confirmed with Product.**

The current specification does not explicitly define whether a refund requested exactly 90 days after the payment date is considered eligible or how the boundary is calculated.

### Verification

Once the expected business behavior is confirmed:

**UI**

* Verify the eligibility decision and refund status.

**Database**

* Verify that the refund record and payment status reflect the expected business rule.

**Email**

* Verify the expected notification behavior based on the confirmed outcome.

---

## TC-03 — Refund requested after the 90-day eligibility window

**Risk / Rationale**

Allowing a refund after the eligibility period could result in unauthorized financial loss.

### Preconditions

* A successful payment exists.
* The payment was made more than 90 days ago.

### Steps

1. Log in as the customer.
2. Navigate to the payment history.
3. Select the payment.
4. Attempt to request a refund.

### Expected Result

* The refund request is rejected.
* No refund is processed.
* The customer's account balance is not modified.
* The original payment remains unchanged.
* Notification behavior follows the confirmed business rule.

### Verification

**UI**

* Verify that the refund request is rejected.
* Verify that no successful refund is shown.

**Database**

* Verify that no successful refund record was created.
* Verify that the payment and account balance were not incorrectly modified.

**Email**

* Verify the expected behavior for rejected refund requests once confirmed with Product.

---

## TC-04 — Refund when the original payment method is unavailable

**Risk / Rationale**

Incorrect classification of the payment method or incorrect handling of the fallback could result in funds being sent to the wrong destination or the customer receiving an incorrect account balance.

### Preconditions

* A successful payment exists.
* The payment is within the eligible 90-day period.
* The original payment method is considered unavailable according to the business definition.
* The payment has not been refunded previously.

### Steps

1. Log in as the customer.
2. Navigate to the payment history.
3. Select the eligible payment.
4. Request a refund.
5. Confirm the refund request.

### Expected Result

* The refund is not returned to the unavailable payment method.
* The refund amount is credited to the customer's account balance.
* The account balance increases by exactly the refund amount.
* The refund is processed only once.
* A confirmation email is generated.

### Verification

**UI**

* Verify the updated account balance.
* Verify the refund status and amount.
* Verify that the refund destination is account balance.

**Database**

* Verify the refund record.
* Verify the refund amount and destination.
* Compare the account balance before and after the refund.
* Verify that the balance increased exactly once.

**Email**

* Verify that the confirmation email contains the correct refund amount and reference.

---

## TC-05 — Duplicate refund request for the same payment

**Risk / Rationale**

Duplicate processing could result in a double refund, duplicate account credit, and financial loss.

### Preconditions

* A successful payment exists.
* The payment is eligible for a refund.
* The payment has already been successfully refunded.

### Steps

1. Submit a valid refund request for the payment.
2. Confirm that the refund has been successfully processed.
3. Attempt to submit another refund request for the same payment.

### Expected Result

* The second request is rejected or identified as already processed.
* No second refund is processed.
* The customer is not credited twice.
* The original payment is not refunded more than once.
* Notification behavior follows the confirmed business rule.

### Verification

**UI**

* Verify that the second request cannot result in another successful refund.

**Database**

* Verify that only one successful refund exists for the payment.
* Verify that the refund amount has not been duplicated.
* Verify that the account balance has not been incorrectly increased twice.

**Email**

* Verify that no confirmation email is generated for a refund that was not actually processed.

