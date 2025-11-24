## Fundamentals of Encryption
The encryption process utilizes a mathematical algorithm, known as a **cipher**, along with a secret value, the **key (K)**.
The original unencrypted message is the **plaintext (P)**, and the output is the **ciphertext (C)**. 
This chapter primarily addresses **symmetric encryption**, where the same key is used for both encryption and decryption.
A cipher is composed of two functions: encryption, C=E(K,P), and decryption, P=D(K,C). 
Ciphertexts can never be shorter than plaintexts

---
## Classical Ciphers
Early ciphers, designed before computers, worked on letters rather than bits:

• **The Caesar Cipher:** Encrypts a message by applying a fixed numerical shift (e.g., three positions) to each letter in the alphabet
*This cipher is easily broken by trying all possible shifts*

• **The Vigenère Cipher:** An improvement over the Caesar cipher, using a secret keyword to determine varying shifts for the plaintext letters
*Despite its greater complexity, it can be broken using **frequency analysis**.*

---
## Cipher Mechanics
Secure ciphers rely on two fundamental elements:

• **The Permutation (Substitution):** A transformation of letters or bits such that every element has a **unique inverse**.
*For security, the permutation must appear random.*

• **The Mode of Operation:** An algorithm that uses the underlying permutation to process messages of varying sizes.
The mode should mitigate the risk of revealing patterns by applying different permutations to repeated elements in the plaintext.

---
## Perfect Security: The One-Time Pad (OTP)
The OTP is theoretically the **most secure cipher**, guaranteeing **perfect secrecy** (or informational security).
It uses the **exclusive OR (XOR) operation** (C=P⊕K) between the plaintext (P) and a truly random key (K) of equal length. 
However, the OTP is fundamentally **impractical** and is susceptible to **malleability** (meaning an attacker can modify the ciphertext C1​ to C2​ such that the resulting plaintext P2​ is predictably related to P1​).

---
## Modern Encryption Security Concepts
Since perfect security (informational security) is unrealistic for practical applications, modern cryptography relies on **computational security**, meaning a cipher is considered secure if the cost and time required to break it are unreasonably high.

Security is defined by combining **Attack Models** and **Security Goals** into **Security Notions**:

• **Attack Models (Attacker Capabilities)**:

    ◦ Ciphertext-Only Attackers (COA): Observe ciphertexts passively.

    ◦ Known-Plaintext Attackers (KPA): Observe known plaintext/ciphertext pairs.

    ◦ Chosen-Plaintext Attackers (CPA): Active attackers who can query the encryption function with chosen plaintexts.

    ◦ Chosen-Ciphertext Attackers (CCA): The strongest model, allowing both encryption and decryption queries.

• **Security Goals (Successful Attack Definition)**:

    ◦ Indistinguishability (IND): Ciphertexts must be indistinguishable from random strings.

    ◦ Non-Malleability (NM): Preventing the attacker from creating a new valid ciphertext related to the original message.

• **Key Notion:** **IND-CPA** (or Semantic Security) is vital and necessitates **randomized encryption** to ensure that encrypting the same plaintext twice yields different ciphertexts.

---
## Asymmetric and Advanced Ciphers
• **Asymmetric Encryption:** Also known as public-key encryption, it uses a **public key** for encryption and a different **private key** for decryption.
The default security model is CPA, as the encryption key is public.

• **Authenticated Encryption (AE):** A type of symmetric encryption that returns both a ciphertext (C) and an **authentication tag (T)**, ensuring both confidentiality and authenticity.

    ◦ Authenticated Encryption with Associated Data (AEAD): An extension that authenticates additional unencrypted data (A) alongside the ciphertext (C).

• **Format-Preserving Encryption (FPE):** Produces a ciphertext that retains the format of the original plaintext (e.g., encrypting IP addresses to IP addresses).

• **Fully Homomorphic Encryption (FHE):** The goal of allowing arbitrary computations on encrypted data without prior decryption.

• **Tweakable Encryption (TE):** Uses an additional public parameter, the "tweak," to provide an extra layer of context or variation to the encryption process.

---
## Common Vulnerabilities
Encryption schemes can fail due to using **weak ciphers** (e.g., A5/1 in 2G communications)

or selecting the **wrong attack model**. 
For example, certain vulnerabilities, like **Padding Oracle Attacks**, demonstrate that security can be compromised if an application leaks information based merely on whether a ciphertext is valid, even without fulfilling the strict requirements of a CCA attack model.

---
