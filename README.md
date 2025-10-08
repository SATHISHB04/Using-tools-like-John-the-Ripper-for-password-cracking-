# Using-tools-like-John-the-Ripper-for-password-cracking
## AIM:
To crack password hashes using John the Ripper in Kali Linux.
## REQUIREMENTS:
- **Operating System:** Kali Linux / Ubuntu / Windows (with JtR binaries)
- **Tools:**
    - John the Ripper (Community/Pro version)
    - Hash generating tools (e.g., openssl, unshadow)
- **Test Data:**
    - /etc/shadow file (Linux hashed passwords)
    - Custom password-protected file (ZIP, RAR, etc.)
## ARCHITECTURE DIAGRAM:
```mermaid
flowchart TD
    A[Password Protected File / Hash] --> B[John the Ripper]
    B --> C[Select Attack Mode: Dictionary or Brute Force]
    C --> D[Load Wordlist / Charset Rules]
    D --> E[Password Cracking Process]
    E --> F[Recovered Passwords]
```
## DESIGN STEPS:
### Step 1: Install John the Ripper
```bash
sudo apt update
sudo apt install john -y
```

### Step 2: Prepare Hash File
- Extract hashes (Linux example):
```
unshadow /etc/passwd /etc/shadow > myhashes.txt
```
- For a ZIP file:
```
zip2john secret.zip > ziphash.txt
```
### Step 3: Run John the Ripper
- Dictionary Attack:
```
john --wordlist=/usr/share/wordlists/rockyou.txt myhashes.txt
```
- Brute Force (Incremental Mode):
```
john --incremental myhashes.txt
```
### Step 4: Show Cracked Passwords
```
john --show myhashes.txt
```
## PROGRAM:
1. **Hash Extraction** – Obtain password hashes from system files or encrypted archives.
2. **Attack Mode Selection** – Choose between dictionary, brute force, or hybrid.
3. **Cracking Phase** – John the Ripper runs through candidate passwords.
4. **Password Recovery** – Successfully cracked passwords are displayed.

## OUTPUT:
Cracked Passwords from Hash File
![WhatsApp Image 2025-10-08 at 13 26 37_ebb5a896](https://github.com/user-attachments/assets/a9515428-7063-4db8-bb93-3c174602e3ec)

![WhatsApp Image 2025-10-08 at 13 26 37_d47dee3f](https://github.com/user-attachments/assets/1c8e3091-7981-431f-8d0e-7457f2d69fb2)
![WhatsApp Image 2025-10-08 at 13 26 39_e8a6fcbc](https://github.com/user-attachments/assets/1249e1ff-5ea5-4302-a8e5-4702ac3771dc)
![WhatsApp Image 2025-10-08 at 13 26 39_5768e031](https://github.com/user-attachments/assets/48e06126-800a-47c9-ba1e-fecb48224600)

![WhatsApp Image 2025-10-08 at 13 26 40_8a2f5cc7](https://github.com/user-attachments/assets/92cb5930-93de-49b4-a81e-28b0cec18d0c)




## RESULT:
The password hashes were successfully cracked using John the Ripper.

