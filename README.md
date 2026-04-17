# TrustCTF 2025 Write-Ups — IIT Bombay

This repository contains concise summaries of three challenges solved during **TrustCTF 2025 (IIT Bombay)**: API Security, Data Privacy, and Cryptanalysis.

---

## Challenges Solved

### 1) API Security
A parameter-parsing mismatch in `/api/balance` led to HTTP Parameter Pollution and an IDOR-style access control bypass.  
**Flag:** `trustctf{1n53cur3_0bj3c7_r3f3r3nc3_f7w}`

### 2) Data Privacy
A leaked `ADMIN_API_KEY` allowed access to the runtime database, which was used to derive the final HMAC-based flag.  
**Flag:** `trustctf{aefefb18de55}`

### 3) Cryptanalysis
A weak XOR stream cipher backed by an LCG was broken using known plaintext and parameter recovery.  
**Flag:** `trustktf{y0u_d0nt_3v3n_n33d_2_b_sm4rt_4_th15}`

---

## Full Write-Up

Full detailed analysis, screenshots, and proofs of concept are available here:  
[**Write-Up_TrustCTF.pdf**](./Write-Up_TrustCTF.pdf)

---

## Authors

Kamal Akhter  
Syed Misbah Uddin
