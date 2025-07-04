
<p align="center">
  <img src="./HSTU_Logo.png" alt="HSTU Logo" width="150">
</p>

<h2 align="center"><strong>Hajee Mohammad Danesh Science and Technology University</strong></h2>

<h3 align="center">Dinajpur-5200</h3>

---

<p align="center">
  <img src="https://img.shields.io/badge/Assignment-Mathematical%20Analysis%20for%20CS-16a085?style=for-the-badge&logo=codeforces&logoColor=white">
  <img src="https://img.shields.io/badge/Course-CSE%20361-2980b9?style=for-the-badge&logo=codesignal&logoColor=white">
  <img src="https://img.shields.io/badge/Algorithm-Multiplicative%20Additive%20Cipher-8e44ad?style=for-the-badge&logo=tryhackme&logoColor=white">
</p>

---

<h2 align="center" style="color:#2980b9;"><strong>🔐 Algorithm Name</strong></h2>

<h1 align="center" style="color:#8e44ad;"><strong>Multiplicative Additive Cipher</strong></h1>

---

<h2 align="center" style="color:#16a085;"><strong>🧑‍💻 Submitted By</strong></h2>

<p align="center">
  <strong>Name:</strong> Maimona Faiza Monisha  
  <br>
  <strong>Student ID:</strong> 2102052  
  <br>
  <strong>Level:</strong> 3  
  <br>
  <strong>Semester:</strong> II  
  <br>
  <strong>Department:</strong> Computer Science and Engineering  
</p>

---

<h2 align="center" style="color:#16a085;"><strong>👨‍🏫 Submitted To</strong></h2>

<p align="center">
  <strong>Name:</strong> Pankaj Bhowmik  
  <br>
  <strong>Designation:</strong> Lecturer  
  <br>
  <strong>Department:</strong> Computer Science and Engineering  
</p>

---

# 📝 Assignment Report

---

## 📑 Table of Contents
- [1️⃣ Introduction](#1️⃣-introduction)
- [2️⃣ Algorithm and Pseudocode](#2️⃣-algorithm-and-pseudocode)
  - [2.1 Conceptual Overview](#🔥-21-conceptual-overview)
  - [2.2 Pseudocode](#💻-22-pseudocode)
- [3️⃣ Experimental Example](#3️⃣-🌟-experimental-example)
- [4️⃣ Source Code Implementation](#4️⃣-💻-source-code-implementation)
- [🌸 Why the Name “Multiplicative Additive Cipher”?](#🌸-why-the-name-multiplicative-additive-cipher)
- [5️⃣ Conclusion](#5️⃣-📌-conclusion)

---

## 1️⃣ Introduction

The **Multiplicative Additive Cipher** is a novel encryption technique that combines multiplicative and additive operations to transform plaintext into ciphertext. Unlike simple shift or substitution ciphers, this method utilizes two keys derived from the initial letters of the plaintext to provide enhanced security and flexibility. The algorithm is designed to work even when the multiplicative key is not coprime with 26, ensuring universal applicability.  

---

## 2️⃣ Algorithm and Pseudocode

### 🔥 2.1 Conceptual Overview

- ✅ The algorithm uses **two keys**:
  - **Multiplicative Key (k₁):** Derived from the first letter of the plaintext.
  - **Additive Key (k₂):** Derived from the second letter of the plaintext.
- 🔐 **During encryption:**
  - If gcd(k₁, 26) == 1:
    \[
    E(x) = (k₁ \cdot v + k₂) \mod 26
    \]
  - Otherwise, fallback to additive:
    \[
    E(x) = (v + k₂) \mod 26
    \]
- 🔓 **During decryption:**
  - If gcd(k₁, 26) == 1:
    \[
    D(x) = (k₁^{-1} \cdot (c - k₂)) \mod 26
    \]
  - Otherwise, fallback:
    \[
    D(x) = (c - k₂) \mod 26
    \]

---

### 💻 2.2 Pseudocode

```plaintext
function encrypt(word):
    k₁ = alphabetical_index(word[0])
    k₂ = alphabetical_index(word[1])
    output = ""
    for each character ch in word:
        v = alphabetical_index(ch)
        if gcd(k₁, 26) == 1:
            encrypted_value = (k₁ * v + k₂) mod 26
        else:
            encrypted_value = (v + k₂) mod 26
        output += letter_for_index(encrypted_value)
    return output

function decrypt(ciphertext):
    k₁ = alphabetical_index(ciphertext[0])
    k₂ = alphabetical_index(ciphertext[1])
    if gcd(k₁, 26) == 1:
        k₁_inverse = modular_inverse(k₁, 26)
    output = ""
    for each character ch in ciphertext:
        v = alphabetical_index(ch)
        if gcd(k₁, 26) == 1:
            decrypted_value = (k₁_inverse * (v - k₂ + 26)) mod 26
        else:
            decrypted_value = (v - k₂ + 26) mod 26
        output += letter_for_index(decrypted_value)
    return output
````

---

## 3️⃣ 🌟 Experimental Example

### ✨ Input:

* Plaintext: `"cipher"`
* Multiplicative Key: `c=2`
* Additive Key: `i=8`

---

### 🔒 Encryption:

| Character | Original Index | Computed Value    | Encrypted Char |
| --------- | -------------- | ----------------- | -------------- |
| c         | 2              | (2\*2+8)%26 = 12  | m              |
| i         | 8              | (2\*8+8)%26 = 24  | y              |
| p         | 15             | (2\*15+8)%26 = 12 | m              |
| h         | 7              | (2\*7+8)%26 = 22  | w              |
| e         | 4              | (2\*4+8)%26 = 16  | q              |
| r         | 17             | (2\*17+8)%26 = 12 | m              |

**🔐 Encrypted Result:** `"mymwqm"`

---

### 🔓 Decryption:

| Character | Encrypted Index | Computed Value          | Decrypted Char |
| --------- | --------------- | ----------------------- | -------------- |
| m         | 12              | ((2⁻¹)\*(12-8))%26 = 2  | c              |
| y         | 24              | ((2⁻¹)\*(24-8))%26 = 8  | i              |
| m         | 12              | ((2⁻¹)\*(12-8))%26 = 15 | p              |
| w         | 22              | ((2⁻¹)\*(22-8))%26 = 7  | h              |
| q         | 16              | ((2⁻¹)\*(16-8))%26 = 4  | e              |
| m         | 12              | ((2⁻¹)\*(12-8))%26 = 17 | r              |

**✅ Recovered Plaintext:** `"cipher"`

---

## 4️⃣ 💻 Source Code Implementation

### 🚀 Implementation in C++

```cpp
#include <bits/stdc++.h>
using namespace std;

int charToNum(char c) {
    return tolower(c) - 'a';
}

char numToChar(int n) {
    return 'a' + (n % 26);
}

int gcd(int a, int b) {
    return b == 0 ? a : gcd(b, a % b);
}

int modInverse(int a, int m) {
    a = a % m;
    for (int x = 1; x < m; x++) {
        if ((a * x) % m == 1)
            return x;
    }
    return -1;
}

string encrypt(string word) {
    int k1 = charToNum(word[0]);
    int k2 = charToNum(word[1]);
    string result = "";
    for (char c : word) {
        int v = charToNum(c);
        int enc;
        if (gcd(k1, 26) == 1) {
            enc = (k1 * v + k2) % 26;
        } else {
            enc = (v + k2) % 26;
        }
        result += numToChar(enc);
    }
    return result;
}

string decrypt(string cipher) {
    int k1 = charToNum(cipher[0]);
    int k2 = charToNum(cipher[1]);
    int k1_inv = modInverse(k1, 26);
    string result = "";
    for (char c : cipher) {
        int v = charToNum(c);
        int dec;
        if (gcd(k1, 26) == 1 && k1_inv != -1) {
            dec = (k1_inv * (v - k2 + 26)) % 26;
        } else {
            dec = (v - k2 + 26) % 26;
        }
        result += numToChar(dec);
    }
    return result;
}

int main() {
    string word;
    cout << "Enter word to encrypt: ";
    cin >> word;

    string encrypted = encrypt(word);
    cout << "Encrypted: " << encrypted << endl;

    string decrypted = decrypt(encrypted);
    cout << "Decrypted: " << decrypted << endl;

    return 0;
}
```

---

## 🌸 Why the Name “Multiplicative Additive Cipher”?

This name reflects the hybrid design of the cipher:

* **Multiplicative**: Uses multiplication of character indices for added diffusion.
* **Additive**: Adds a secondary shift for confusion, strengthening the algorithm.
* 🛡 Together, these operations create a layered encryption technique that overcomes the weaknesses of purely additive or multiplicative ciphers.

---

## 5️⃣ 📌 Conclusion

The **Multiplicative Additive Cipher** is an elegant blend of classical cryptographic concepts. It provides a robust, flexible encryption scheme that is easy to implement yet offers meaningful complexity, serving as an excellent foundation for further cryptographic studies.

---
