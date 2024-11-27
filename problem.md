# Reversing Python

- Namespace: picoctf/examples
- ID: ECDSA
- Type: custom
- Category: Cryptography
- Points: 1
- Templatable: yes
- MaxUsers: 1

## Description

There is a service accepting input using elliptic curve based digital signature. If you can sing a specif message with a valid signature the prize is yours ! 

* This is based off of an actual security vulnerability SONYECDSA vulnerability in 2013

## Details

Connect to the program with netcat:



The program's source code can be downloaded {{url_for("picker-I.py", "here")}}.

1. Connect to the server at `$ nc {{server}} {{port}}`
2. Receive a public key and instructions to sign the message 'CTF_CHALLENGE'
3. Generate a valid ECDSA signature 
4. Submit the signature to  `$ nc {{server}} {{port}}`
5. If the signature is valid, receive the flag




## Hints

* In ECDSA, a signature (r, s) for a message m is generated using the following equation:

s = k^(-1)(z + xr) mod n

Where:
- k is the nonce
- z is the hash of the message
- x is the private key
- n is the order of the curve

* Try looking at the difference in the two signatures and hashes 
* Look at this mathematically before you try to brute force something!


## Solution Overview

Enter 'win' as the input to the program

## Challenge Options

```yaml
cpus: 0.5
memory: 128m
pidslimit: 20
ulimits:
  - nofile=128:128
#diskquota: 64m
init: true
```

## Learning Objective

Examining source code to identify functionality

## Tags

- python

## Attributes

- author: LT 'syreal' Jones
- organization: picoCTF
- event: picoCTF Problem Developer Training
