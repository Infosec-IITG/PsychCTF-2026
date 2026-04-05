# Exposed

## Summary

- Analyzing meta-data and picking out important info
- Extracting data from LSB layers of image
- Decrypting the flag using Vigenere cipher

## Solve

Performed basic file analysis, metadata reveals:

- Artist: Morphine

Using zsteg to reveal hidden data in LSB:

```
aHR0cDovLzQwLjgxLjI5LjI1NDo4MDcwL3dhcmQ0
```

Decoding Base64 to URL:

```
http://40.81.29.254:8070/ward4
```

Visiting URL shows:

```
bgpro{beltx3_z4p3g3k_u4qr3eg}
```

Decrypting with Vigenere key `morphine`:

```
psych{tr1pl3_l4y3r3d_m4dn3ss}
```

## Commands Used

```
file exposed.png
exiftool exposed.png
strings exposed.png
zsteg exposed.png
echo "aHR0cDovLzQwLjgxLjI5LjI1NDo4MDcwL3dhcmQ0" | base64 -d
```

---
