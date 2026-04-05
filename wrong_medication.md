# 2. Wrong Medication

**Category:** Crypto

## Approach

The given file _pharmacy.py_ contains the following:

```python
# ===== Pharmacy private key (SECRET) ====================================
d     = 597561114
Q     = (119507153144501, 37069259253313)   # d * G

# ===== Encrypted flag ====================================================
# Decrypt with: AES-ECB( SHA256(d.to_bytes(16,'big'))[:16] , enc )
ENCRYPTED_FLAG_HEX = (
    "cdae39f8460cceafc1b2a14af55b831f"
    "7ffa1badaec839ee8f3f616f22125cab"
    "2b8272079e459db6c9bd1825218eeea9"
    "da840108443416de5a883251ad349dfb"
)
```

Thus, the encrypted flag along with the decryption technique have been provided.

## Breakdown of provided decryption code

```python
d.to_bytes(16, 'big')
```

The integer d is converted to 16-byte binary representation

```python
SHA256(...)[:16]
```

Produces 32-byte hash of which the first 16 bytes are kept. This gives us the AES key.

```python
AES-ECB(key, enc)
```

Here, the enc must be in bytes which can be obtained from the given ENCRYPTED_FLAG_HEX.

## Final Flag

psych{wr0ng_m3d5_wr0ng_curv3_n0_v4l1d4t10n_1s_f4t4l_e7c3a9}
