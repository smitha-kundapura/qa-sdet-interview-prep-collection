# Data Masking Interview Guide

Data masking is critical in QA, especially for protecting sensitive data during testing. Let’s cover **key concepts, cheat sheets, and detailed explanations**.

---

## Quick Reference Cheat Sheet

| Topic               | Summary |
|---------------------|---------|
| What is Data Masking? | Hides sensitive data for testing/training. |
| Types               | Static, Dynamic, Deterministic, On-the-fly |
| Techniques          | Substitution, Shuffling, Nulling, Encryption |
| Key Challenges      | Referential integrity, performance, compliance |
| Common Questions    | Definitions, use cases, challenges, compliance |

---

## What is Data Masking?

Data masking means replacing sensitive data with **realistic but fake data** to protect privacy and compliance while preserving functionality for testing or training.

- **Example:** Replace "John Doe" with "Alex Smith" in test databases.

---

## Types of Data Masking

| Type                 | Description |
|----------------------|-------------|
| **Static Masking**   | Data is masked once in a non-production copy. |
| **Dynamic Masking**  | Data is masked in real-time during query execution. |
| **Deterministic Masking** | Same input = same output, maintaining joins. |
| **On-the-fly Masking** | Data is masked as it's moved from prod to test. |

---

## Techniques

| Technique              | Example |
|------------------------|---------|
| **Substitution**       | Replace names or emails. |
| **Shuffling**          | Randomize existing data to break links. |
| **Nulling Out**        | Replace with blanks or nulls. |
| **Encryption**         | Secure with AES or SSL. |
| **Masking Algorithms** | Hashing or custom logic. |

---

## Key Challenges

- Maintaining **referential integrity** (e.g., foreign keys).
- Performance impact on large datasets.
- Regulatory compliance (GDPR, CCPA).
- Consistent masking for test data that requires joins.

---

## Common Interview Questions and Answers

**Q1. What is data masking and why is it important?**  
A1. Data masking hides sensitive data for safe testing and training, ensuring compliance with regulations like GDPR while maintaining functional accuracy.

**Q2. Explain static vs dynamic masking.**  
A2. Static masking replaces data in a snapshot; dynamic masking applies on-the-fly during runtime without modifying stored data.

**Q3. How would you mask PII data in QA?**  
A3. Use a tool or script to substitute PII with realistic values while maintaining referential integrity.

**Q4. What are challenges in masking relational data?**  
A4. Ensuring consistent masking across related tables to preserve joins.

**Q5. How do you ensure referential integrity when masking?**  
A5. Use deterministic or algorithmic masking to maintain consistent key relationships.
