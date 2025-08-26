---
{"topic":"SoftwareEngineering","dg-publish":true,"permalink":"/Notes/Unit Tests/","dgPassFrontmatter":true,"noteIcon":""}
---

### What is unit testing
= testing the smallest pieces of code (usually functions or methods) in isolation to verify they behave correctly

### Basic things unit tests should cover
- positive tests/normal cases
- negative tests/edge cases
- error handling: check that the function raises appropriate errors for bad input
- code coverage: test all logic branches (if/else, loops, early returns) are actually executed during the tests
- consistency & idempotence
	- run the function multiple times to ensure it gives the same result if expected

### Key Principles
- test one thing at a time
- keep tests fast
- tests should be deterministic
- run often
