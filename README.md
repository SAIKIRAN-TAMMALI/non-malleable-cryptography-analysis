# 🧩 Non-Malleable Cryptography — String Commitments · Zero-Knowledge Proofs of Knowledge

[![Cryptography](https://img.shields.io/badge/Cryptography-1F3A6E?style=flat-square)](https://en.wikipedia.org/wiki/Cryptography) [![Zero-Knowledge](https://img.shields.io/badge/Zero--Knowledge_Proofs-6A1B9A?style=flat-square)](https://en.wikipedia.org/wiki/Zero-knowledge_proof) [![Commitments](https://img.shields.io/badge/Commitment_Schemes-00796B?style=flat-square)](https://en.wikipedia.org/wiki/Commitment_scheme) [![SIAM](https://img.shields.io/badge/SIAM_J._Computing-003087?style=flat-square)](https://epubs.siam.org/journal/smjcat)

> **A technical analysis of Dolev, Dwork & Naor's *Non-Malleable Cryptography* — why "the attacker can't read it" is not enough, and how to stop attackers from creating related cryptographic messages.**
> Completed as a cryptography course research report at **Stevens Institute of Technology**.

---

## 📌 Scope Note

This report focuses on two primitives from the paper: **string commitment schemes** and **zero-knowledge proofs of knowledge**. The public-key encryption component of the paper was deliberately excluded.

**Paper analyzed:** D. Dolev, C. Dwork, M. Naor. *Non-Malleable Cryptography.* SIAM Journal on Computing, 30(2):391–437, 2003.

---

## 📄 Full Report

> Read the complete write-up: [`non-malleable-cryptography-report.pdf`](non-malleable-cryptography-report.pdf)

---

## 🎯 The Problem in One Line

**Semantic security** guarantees an attacker learns nothing about a secret from its ciphertext or commitment. It does **not** stop the attacker from producing a *different but related* message. **Non-malleability** closes that gap.

---

## ⚔️ Attack Scenarios Studied

| Scenario | Attack | Why it matters |
|----------|--------|----------------|
| **Sealed-bid underbidding** | Seeing Party A's commitment to bid `s`, an attacker commits to `s'` that is always slightly lower — without ever learning `s`. | Breaks fairness in auctions, voting, and contract signing. |
| **Transparent prover (man-in-the-middle)** | Professor B relays every question and answer between Researcher A and Professor E, claiming A's zero-knowledge proof as his own. | Shows that standard zero-knowledge proofs can be hijacked across concurrent sessions. |

---

## 🧠 Key Concepts Covered

| Concept | Summary |
|---------|---------|
| **Commitment scheme** | Two stages: commit (sender is bound to a value) and reveal (receiver verifies). Must be **binding** and **hiding**. |
| **Adversarially coordinated system** | A model where one attacker controls agents in two concurrent protocol sessions and the timing between them. |
| **Relation approximator** | A test that measures whether the attacker's value is related to the honest party's value. |
| **Non-malleability definition** | Seeing one instance gives the attacker no meaningful advantage in producing a related instance. |
| **BCK protocol & knowledge extraction** | Multiple BCK instances force the committer to prove consistency; "exposed triples" let an extractor recover the attacker's committed value. |
| **Non-interactive zero-knowledge (NIZK)** | Completeness, soundness, and zero-knowledge properties, used to build non-malleable proofs of knowledge. |
| **Compiler** | Converts any zero-knowledge protocol into a non-malleable one by adding commitments and consistency proofs. |

---

## 🔍 Why This Was a Breakthrough

| Prior approaches | Dolev–Dwork–Naor approach |
|------------------|---------------------------|
| Trusted center required | No trusted center assumed |
| Parties must know each other's identities | No identity knowledge required |
| Secure against passive adversaries | Secure against active, coordinated adversaries |
| Single-session security | Concurrent multi-session security |

---

## ⚠️ Limitations Identified

| Limitation | Impact | Severity |
|------------|--------|:---:|
| High computational overhead — O(n) BCK instances | Impractical for real-time applications | **High** |
| Communication complexity O(n²) vs O(n) | Bandwidth-intensive, poor scalability | **High** |
| Not guaranteed under arbitrary composition | Unsafe in complex multi-protocol environments | **High** |
| Identity verification dependency | Cannot solve the credit problem with anonymous parties | Medium |
| Restricted relation class | Some relational attacks not covered | Medium |
| Relies on a common random string for NIZK | Weak trusted-setup assumption | Medium |
| Complex compiled protocols | Hard to implement correctly | Medium |

---

## 🧠 Key Takeaways

1. **Confidentiality is not integrity of meaning.** An attacker who can't read a message may still manipulate what it means.
2. **Concurrency changes the threat model.** Protocols that are safe in one session can fail when an attacker runs two at once.
3. **Security has costs.** Strong guarantees came with large computation and bandwidth overhead, which drove decades of follow-up work.
4. **This paper shaped modern cryptography.** Universally composable security, efficient non-malleable commitments, and non-malleable codes all build on it.

---

## 📂 Repository Structure

```
non-malleable-cryptography-analysis/
├── README.md                                   ← this file
└── reports/
    └── non-malleable-cryptography-report.pdf   ← full report (definitions, constructions, limitations)
```

---

## 📚 References

1. D. Dolev, C. Dwork, M. Naor. *Non-Malleable Cryptography.* SIAM J. Computing, 30(2):391–437, 2003.
2. S. Goldwasser, S. Micali. *Probabilistic Encryption.* JCSS, 28(2):270–299, 1984.
3. M. Blum, P. Feldman, S. Micali. *Non-Interactive Zero-Knowledge and Its Applications.* STOC 1988.
4. R. Canetti. *Universally Composable Security.* FOCS 2001.
5. M. Naor. *Bit Commitment Using Pseudorandomness.* Journal of Cryptology, 4(2):151–158, 1991.

---

## 👤 Author

**Saikiran Tammali** — Cybersecurity Graduate · Cryptography · Security Engineering

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat-square&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/saikiran-tammali-cybersec32)
[![GitHub](https://img.shields.io/badge/GitHub-181717?style=flat-square&logo=github&logoColor=white)](https://github.com/SAIKIRAN-TAMMALI)

*Cryptography research report — M.S. Cybersecurity, Stevens Institute of Technology.*
