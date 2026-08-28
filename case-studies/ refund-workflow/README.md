# Refund Workflow — QA Test Design Case Study

## Overview

This case study demonstrates a risk-based test design approach for a refund workflow based on a simplified business rule.

The objective is to demonstrate:

* Test case design from business requirements
* Identification of specification gaps and risks
* Boundary value analysis
* Data integrity considerations
* API/UI/database/email validation
* Critical thinking when requirements are ambiguous

## Business Rule

> A customer can request a refund for a payment within 90 days from the payment date. The refund is returned to the original payment method. If the original payment method is no longer available, the amount is credited as account balance. Every refund generates a confirmation email.

## Approach

The test scenarios prioritize financial integrity, eligibility boundaries, refund destination, duplicate processing, and consistency between the user interface, database, account balance, and email notification.

Ambiguous requirements are explicitly identified rather than assumed.

