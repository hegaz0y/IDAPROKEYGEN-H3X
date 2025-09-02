 IDA Pro Fake License Generator

## 📌 Case Context
This repository contains **forensic analysis evidence** of a Python script discovered during an investigation.  
The script is designed to **generate fake licenses** for *IDA Pro 9.2* and **patch program binaries** to bypass license verification.  

⚠️ **Disclaimer:** This repository is **for investigative and educational purposes only**.  
It must **not** be used to circumvent license protection or for illegal purposes.  

---

## 🧾 Script Overview
The Python script performs the following steps:

1. **Builds a JSON license object**  
   - Contains fake metadata: product name, version (9.2), owner (`HexRays`), validity until 2033.  
   - Adds multiple add-ons (x86, ARM, MIPS, PPC, RISC-V, ARC).  

2. **Creates a deterministic JSON serialization**  
   - Ensures a stable representation before hashing & signing.  

3. **Generates a digital signature (fake RSA-like)**  
   - Computes SHA-256 hash of the payload.  
   - Encrypts it with a fake private key.  
   - Produces a hexadecimal signature.  

4. **Writes license file**  
   - Saves output as `idapro.hexlic`.  

5. **Binary patching**  
   - Searches IDA libraries (`ida.dll`, `libida.so`, `libida.dylib`) for the public modulus.  
   - Modifies a single byte (`5C → CB`) to accept the forged license.  

---

## 🔍 Forensic Indicators (IOCs)
- Presence of **`idapro.hexlic`** → forged license file.  
- Modified binaries (`ida.dll`, `libida.so`, etc.) containing altered modulus.  
- Script artifacts with RSA modulus values in hexadecimal.  
- SHA-256 hashing & fake RSA signature generation logic.  

---

## ⚖️ Evidential Value
- **The script itself**: proof of intent to bypass software licensing.  
- **Forged license file**: counterfeit license not issued by Hex-Rays.  
- **Patched binaries**: tampered executables with altered cryptographic constants.  

Together, these demonstrate **unauthorized use and distribution of software piracy tools**.  

---

## 📂 Files in Repository
- `forensic_report.md` → This report file.  
- `evidence_script.py` → Original suspicious Python script (for evidence, read-only).  
- `samples/idapro.hexlic` → Example of generated forged license.  
- `binaries_diff/` → Before/after comparison of patched binaries (hex diff).  

---

## 👥 Investigation Team Notes
- Ensure chain of custody is documented for all files.  
- Compare patched binaries with official vendor binaries for byte-level differences.  
- Retain SHA-256 hashes of evidence files for integrity verification.  




