# Static Challenge Writeup

## Summary

The challenge involved analyzing network traffic from a `.pcap` file and extracting hidden data from packets.

---

## Step-by-Step Solution

### 1. Inspect Protocols

Open the `.pcap` file and identify available protocols:

- DNS
- HTTP
- UDP
- ICMP

Use:

```bash
tshark -r file.pcap
```

---

### 2. Check DNS Traffic

Extract DNS queries:

```bash
tshark -r file.pcap -T fields -e dns.qry.name
```

Observation:

- Queries appeared normal
- No hidden data found

---

### 3. Check HTTP Traffic

Extract HTTP URIs:

```bash
tshark -r file.pcap -T fields -e http.request.uri
```

Observation:

- No useful or encoded data found

---

### 4. Inspect ICMP Packets

Extract ICMP payloads:

```bash
tshark -r file.pcap -Y icmp -T fields -e data
```

Convert hex to raw:

```bash
xxd -r -p data.txt > raw.bin
```

Try decoding:

```python
decoded = bytes([b ^ 0x55 for b in data])
decoded[3]
decoded[3::4]
```

Observation:

- Data looked structured but did not produce meaningful output

---

### 5. Focus on UDP Traffic

Filter UDP packets on port 7331:

```bash
tshark -r file.pcap -Y "udp.port == 7331" -T fields -e data
```

---

### 6. Decode the Payload

- Convert hex to bytes
- XOR each byte with `0x55` (decimal 85)

### 7. Extract Relevant Bytes

- Each packet contains one useful byte of the flag
- After XOR decoding, the **5th byte (index 4)** is extracted
- These bytes are combined across packets to reconstruct the full flag

```python
flag_bytes = []

for packet in packets:
    if UDP in packet and Raw in packet and packet[UDP].dport == 7331:
        decoded = bytes(b ^ 0x55 for b in bytes(packet[Raw]))
        flag_bytes.append(decoded[4])

print(bytes(flag_bytes).decode())
```

## Final Answer

psych{packet_sniffinnngggg}

---

## Misunderstanding

Focused too much on ICMP traffic instead of identifying the correct UDP port carrying the actual data.
