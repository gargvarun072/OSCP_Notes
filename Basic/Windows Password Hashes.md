Windows Password Hashes

# Windows Password Hashes

## LM

### The algorithm

1.  Convert all lower case to upper case
2.  Pad password to 14 characters with NULL characters
3.  Split the password to two 7 character chunks
4.  Create two DES keys from each 7 character chunk
5.  DES encrypt the string "KGS!@#$%" with these two chunks
6.  Concatenate the two DES encrypted strings. This is the LM hash.

### Cracking Methodology

```
john --format=lm hash.txt
hashcat -m 3000 -a 3 hash.txt
```

### Characteristics

- password length is limited to maximum of 14 characters
- a 14-character password is broken into 7+7 characters and the hash is calculated for the two halves separately
- if the password is 7 characters or less, then the second half of hash will always produce same constant value (AAD3B435B51404EE)
- the hash value is sent to network servers without salting
- uses DES
- 128 bits hash size

**Example** - 299BD128C1101FD6

* * *
## NTHash (A.K.A. NTLM)

### The algorithm
MD4(UTF-16-LE(password))
UTF-16-LE is the little endian UTF-16. Windows used this instead of the standard big endian, because Microsoft.

### Cracking Methodology

```
john --format=nt hash.txt
hashcat -m 1000 -a 3 hash.txt
```

### Characteristics
- uses MD4
- 128 bits hash size

**Example** - B4B9B02E6F09A9BD760F388B67351E2B

* * *
## NTLMv1 (A.K.A. Net-NTLMv1)

The NTLM protocol uses the NTHash in a challenge/response between a server and a client. The v1 of the protocol uses both the NT and LM hash, depending on configuration and what is available. The Wikipedia page on NT Lan Manager has a good explanation.

A way of obtaining a response to crack from a client, Responder is a great tool. The value to crack would be the K1 | K2 | K3 from the algorithm below. Version 1 is deprecated, but might still be used in some old systems on the network.


### The algorithm
- C = 8-byte server challenge, random
- K1 | K2 | K3 = LM/NT-hash | 5-bytes-0
- response = DES(K1,C) | DES(K2,C) | DES(K3,C)

### Cracking Methodology
```
john --format=netntlm hash.txt
hashcat -m 5500 -a 3 hash.txt
```

### Characteristics
- uses DES
- 128 bits hash size

**Example** 
u4-netntlm::kNS:338d08f8e26de93300000000000000000000000000000000:9526fb8c23a90751cdd619b6cea564742e1e4bf33006ba41:cb8086049ec4736c
* * *
## NTLMv2 (A.K.A. Net-NTLMv2)

This is the new and improved version of the NTLM protocol, which makes it a bit harder to crack. The concept is the same as NTLMv1, only different algorithm and responses sent to the server. Also captured through Responder or similar. Default in Windows since Windows 2000.

### The algorithm
1. SC = 8-byte server challenge, random
2. CC = 8-byte client challenge, random
3. CC* = (X, time, CC2, domain name)
4. v2-Hash = HMAC-MD5(NT-Hash, user name, domain name)
5. LMv2 = HMAC-MD5(v2-Hash, SC, CC)
6. NTv2 = HMAC-MD5(v2-Hash, SC, CC*)
7. response = LMv2 | CC | NTv2 | CC*

### Cracking Methodology
```
john --format=netntlmv2 hash.txt
hashcat -m 5600 -a 3 hash.txt
```

### Characteristics
- uses HMAC-MD5
- 128 bits hash size

**Example** 
admin::N46iSNekpT:08ca45b7d7ea58ee:88dcbe4446168966a153a0064958dac6:5c7830315c7830310000000000000b45c67103d07d7b95acd12ffa11230e0000000052920b85f78d013c31cdb3b92f5d765c783030