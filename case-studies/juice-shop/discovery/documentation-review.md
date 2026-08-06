# Documentation Review — OWASP Juice Shop

**Task:** TASK-001 - Review documentation
**Story:** US-001 - Understand the Business Domain
**Author:** [Your Name] (Quality Engineer)
**Reviewed with:** Claude (simulated Business Analyst / Technical Writer)
**Date:** 2026-08-06

---

## Purpose

This document records the review of OWASP Juice Shop's official
documentation as the first step of the Business Discovery process.
It captures which sources were consulted, what information was
confirmed directly from official sources, and what remains a
hypothesis to be validated through hands-on exploration or with
the (simulated) Product Owner.

---

## Official Documentation Consulted

| Source | Type | URL |
|---|---|---|
| Official project page | Marketing / feature overview | https://owasp-juice.shop |
| GitHub repository (README) | Technical setup & source of truth | https://github.com/juice-shop/juice-shop |
| Pwning OWASP Juice Shop | Official companion guide (eBook) | https://pwning.owasp-juice.shop |
| OWASP Juice Shop organization page | Project governance | https://github.com/juice-shop |

---

## Observations

- The official page frames Juice Shop as an intentionally insecure
  web application, not as a real business — this confirms the
  earlier assumption made during the business discovery kickoff.
- Documentation is oriented toward **security training and CTF use
  cases**, not toward functional/business requirements. No business
  requirements document, user story backlog, or product
  specification exists — which is expected for this kind of project.
- The companion guide ("Pwning OWASP Juice Shop") is the closest
  thing to a structured reference, but its content is organized
  around vulnerability categories, not business processes.
- Architecture is documented at a technical level (JavaScript/
  TypeScript, REST API) but not at a business/domain level.

---

## Confirmed Information

- Juice Shop is officially described as an insecure web application used for security training, awareness demos, CTFs, and as a test target for security tools.
- The application covers vulnerabilities from the OWASP Top Ten and other real-world security flaws.
- The technology stack is JavaScript/TypeScript end-to-end (UI to REST API).
- The project is open source, licensed under MIT, and led by Björn Kimminich and Jannik Hollenbach as project leaders.
- The application supports customization/re-branding via a YAML configuration file, including overriding the product catalog.
- No white-box testing is intended for the security-challenge use case (the official FAQ explicitly discourages reading the source code to avoid spoiling challenges) — noted here for context, though it does not restrict black-box functional/business testing, which is this lab's approach.

---

## Information That Remains a Hypothesis

The following points could **not** be confirmed from official
documentation and require direct exploration of the application
(black-box) or a decision from the (simulated) Product Owner:

- Whether business rules such as coupon usage limits, stock control,
  or order cancellation policies exist as designed behavior or are
  incidental/undefined.
- Whether product reviews are moderated or published immediately.
- Whether all user roles observed in the UI (e.g., customer, admin)
  are the only roles that exist, or if others are hidden/unconfirmed.
- Whether checkout without authentication is possible — not
  addressed in any official document; must be validated by
  exploring the app directly.
- The exact validation rules for registration/login forms (format,
  length, required fields).

These items will be tracked as open questions and validated in
later discovery tasks and/or raised directly with the Product Owner
before writing test scenarios.

---

## Limitations

This review is intentionally limited to publicly available
official documentation.

No source code analysis was performed, as this laboratory
follows a business-first, black-box discovery approach.

---

## Decision

Business discovery will continue using a black-box exploration
approach.

Business rules not explicitly documented will be treated as
assumptions until validated through application exploration or
Product Owner clarification.

---

## Next Steps

Proceed to TASK-002 - Explore the Application, using the actors
referenced in the official documentation (customer/"Average Joe",
administrator) as a starting point, to be validated through direct
exploration of the app.
