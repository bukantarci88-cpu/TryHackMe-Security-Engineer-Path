# Eng 1.3. Introduction to Cryptography

#### **Task 1 - Introduction**

The purpose of this room is to introduce users to basic cryptography concepts such as:

Symmetric encryption, such as AES
Asymmetric encryption, such as RSA
Diffie-Hellman Key Exchange
Hashing
PKI

Simple substitution and transposition ciphers are easily broken using automated frequency analysis tools without needing an encryption key, rendering them unsuitable for confidential communication.

> Q. You have received the following encrypted message: “Xjnvw lc sluxjmw jsqm wjpmcqbg jg wqcxqmnvw; xjzjmmjd lc wjpm sluxjmw jsqm bqccqm zqy.” Zlwvzjxj Zpcvcol. You can guess that it is a quote. Who said it?
> 

Miyamoto Musashi

<img width="933" height="157" alt="image" src="https://github.com/user-attachments/assets/41a89e34-0990-4ddc-954e-813d315e3578" />


#### **Task 2 - Symmetric Encryption**

**Cryptographic Algorithm or Cipher:** This algorithm defines the encryption and decryption processes.
**Key:** The cryptographic algorithm needs a key to convert the plaintext into ciphertext and vice versa.
**plaintext** is the original message that we want to encrypt.
**ciphertext** is the message in its encrypted form.

| **Encryption Algorithm** | **Notes** |
| --- | --- |
| AES, AES192, and AES256 | AES with a key size of 128, 192, and 256 bits |
| IDEA | International Data Encryption Algorithm (IDEA) |
| 3DES | Triple DES (Data Encryption Standard) and is based on DES. We should note that 3DES will be deprecated in 2023 and disallowed in 2024. |
| CAST5 | Also known as CAST-128. Some sources state that CAST stands for the names of its authors: Carlisle Adams and Stafford Tavares. |
| BLOWFISH | Designed by Bruce Schneier |
| TWOFISH | Designed by Bruce Schneier and derived from Blowfish |
| CAMELLIA128, CAMELLIA192, and CAMELLIA256 | Designed by Mitsubishi Electric and NTT in Japan. Its name is derived from the flower camellia japonica. |

Symmetric encryption uses the same shared key for both encryption and decryption, requiring communicating parties to securely establish this secret before exchanging messages.

On the other end, the recipient provides the *decrypt* process with the same key used by the sender to recover the original plaintext from the received ciphertext. Without knowledge of the key, the recipient won’t be able to recover the plaintext.

**GNU Privacy Guard: A**lso known as GnuPG or GPG, implements the OpenPGP standard. We can encrypt a file using GnuPG (GPG) using the following command:

`gpg --symmetric --cipher-algo CIPHER message.txt`, where CIPHER is the name of the encryption algorithm. 

You can decrypt using the following command:

`gpg --output original_message.txt --decrypt message.gpg`

**OpenSSL Project:** The [](https://www.openssl.org/)OpenSSL project maintains the OpenSSL software.

We can encrypt a file using OpenSSL using the following command:

`openssl aes-256-cbc -e -in message.txt -out encrypted_message`

We can decrypt the resulting file using the following command:

`openssl aes-256-cbc -d -in encrypted_message -out original_message.txt`

> Q.1. Decrypt the file quote01 encrypted (using AES256) with the key s!kR3T55 using gpg. What is the third word in the file?
> 

waste

<img width="797" height="734" alt="image 1" src="https://github.com/user-attachments/assets/2c3fd515-7333-4914-8473-d2999d6ddf9e" />


> Q.2. Decrypt the file quote02 encrypted (using AES256-CBC) with the key s!kR3T55 using openssl. What is the third word in the file?
> 

science

<img width="805" height="294" alt="image 2" src="https://github.com/user-attachments/assets/1f2e61aa-cd51-4db4-91a6-3700631ab913" />


> Q.3. Decrypt the file quote03 encrypted (using CAMELLIA256) with the key s!kR3T55 using gpg. What is the third word in the file?
> 

understand

<img width="801" height="218" alt="image 3" src="https://github.com/user-attachments/assets/3a705ca5-fbdc-4dd3-84f6-2df55d2facea" />


#### **Task 3 - Asymmetric Encryption**

Asymmetric encryption uses a public-private key pair—allowing messages to be securely exchanged over an insecure (but reliable/integrity-assured) channel without sharing a secret key—where the public key is shared freely, the private key is kept secret, and deriving the private key from the public key is computationally infeasible.

Three RSA commands:

- `openssl genrsa -out private-key.pem 2048`: With `openssl`, we used `genrsa` to generate an RSA private key. Using `out`, we specified that the resulting private key is saved as `private-key.pem`. We added `2048` to specify a key size of 2048 bits.
- `openssl rsa -in private-key.pem -pubout -out public-key.pem`: Using `openssl`, we specified that we are using the RSA algorithm with the `rsa` option. We specified that we wanted to get the public key using `pubout`. Finally, we set the private key as input using `in private-key.pem` and saved the output using `out public-key.pem`.
- `openssl rsa -in private-key.pem -text -noout`: We are curious to see real RSA variables, so we used `text -noout`. The values of *p*, *q*, *N*, *e*, and *d* are `prime1`, `prime2`, `modulus`, `publicExponent`, and `privateExponent`, respectively.

If we already have the recipient’s public key, we can encrypt it with the command `openssl pkeyutl -encrypt -in plaintext.txt -out ciphertext -inkey public-key.pem -pubin`

The recipient can decrypt it using the command `openssl pkeyutl -decrypt -in ciphertext -inkey private-key.pem -out decrypted.txt`

<img width="794" height="209" alt="image 4" src="https://github.com/user-attachments/assets/7bc6afb5-0485-4579-83a9-30c1ad0e4d50" />


> Q1. Take a look at Bob’s private RSA key. What is the last byte of *p*?
> 

p=prime1:e7

<img width="813" height="466" alt="image 5" src="https://github.com/user-attachments/assets/dfa26870-72ec-4715-bcdf-3aeaffff7abc" />

<img width="510" height="212" alt="image 6" src="https://github.com/user-attachments/assets/55ee76be-228f-4892-a059-1896ccfbf2a5" />


> Q.2. Take a look at Bob’s private RSA key. What is the last byte of *q*?
> 

q=prime2=27

<img width="496" height="211" alt="image 7" src="https://github.com/user-attachments/assets/bf19855b-b4ec-49f2-a385-02637b597149" />


#### **Task 4 - Diffie-Hellman Key Exchange**

We can use `openssl` to generate them; we need to specify the option `dhparam` to indicate that we want to generate Diffie-Hellman parameters along with the specified size in bits, such as `2048` or `4096`. In the console output below, we can view the prime number `P` and the generator `G` using the command `openssl dhparam -in dhparams.pem -text -noout`. (This is similar to what we did with the RSA private key.) 

> Q.1. On the AttackBox, you can find the directory for this task located at /root/Rooms/cryptographyintro/task04; alternatively, you can use the task file from Task 2 to work on your own machine. A set of Diffie-Hellman parameters can be found in the file dhparam.pem. What is the size of the prime number in bits?
> 

4096

<img width="802" height="220" alt="image 8" src="https://github.com/user-attachments/assets/5dcc89bc-283f-4ca5-b706-82d937b6bae1" />


> Q.2. What is the prime number’s last byte (least significant byte)?
> 

4f 

<img width="533" height="157" alt="image 9" src="https://github.com/user-attachments/assets/01942dbd-3494-47c4-a6ae-6eedcd2ef415" />


#### **Task 5 - Hashing**

A cryptographic hash function is an algorithm that takes data of arbitrary size as its input and returns a fixed size value, called *message digest* or *checksum*, as its output. For example, `sha256sum` calculates the SHA256 (Secure Hash Algorithm 256) message digest. 

**HMAC:** Hash-based message authentication code (HMAC) is a message authentication code (MAC) that uses a cryptographic key in addition to a hash function.To calculate the HMAC on a Linux system, you can use any of the available tools such as `hmac256` (or `sha224hmac`, `sha256hmac`, `sha384hmac`, and `sha512hmac`, where the secret key is added after the option `--key`). Below we show an example of calculating the HMAC using `hmac256` and `sha256hmac` with two different key

> Q.1. On the AttackBox, you can find the directory for this task located at /root/Rooms/cryptographyintro/task05; alternatively, you can use the task file from Task 2 to work on your own machine.What is the SHA256 checksum of the file order.json?
> 

2c34b68669427d15f76a1c06ab941e3e6038dacdfb9209455c87519a3ef2c660

> Q.2.Open the file order.json and change the amount from 1000 to 9000. What is the new SHA256 checksum?
> 

11faeec5edc2a2bad82ab116bbe4df0f4bc6edd96adac7150bb4e6364a238466

<img width="356" height="287" alt="image 10" src="https://github.com/user-attachments/assets/8bc9b55c-0814-41eb-91eb-fd5db5cb2fe3" />


> Q.3. Using SHA256 and the key 3RfDFz82, what is the HMAC of order.txt?
> 

c7e4de386a09ef970300243a70a444ee2a4ca62413aeaeb7097d43d2c5fac89f

hmac256 3RfDFz82 order.txt

#### **Task 6 - PKI and SSL/TLS**

PKI is the infrastructure that manages digital certificates and public/private keys, while SSL/TLS is the protocol that uses those certificates to create secure encrypted communication between systems. PKI establishes trust, and TLS uses that trust to secure data in transit. For a certificate to get signed by a certificate authority, we need to:

1. Generate Certificate Signing Request (CSR): You create a certificate and send your public key to be signed by a third party.
2. Send your CSR to a Certificate Authority (CA): The purpose is for the CA to sign your certificate. The alternative and usually insecure solution would be to self-sign your certificate.

**Core Components of PKI**
Public Key → Shared openly and used for encryption or signature verification.
Private Key → Kept secret and used for decryption or digital signing.
Digital Certificate → Binds a public key to an identity (like a website or organization).
Certificate Authority (CA) → Trusted organization that issues and signs certificates.
Registration Authority (RA) → Verifies identity before certificate issuance.
Certificate Revocation List (CRL) / OCSP → Used to check if a certificate is revoked.

**How PKI Works**
A server generates a public/private key pair.
The public key is sent to a CA in a Certificate Signing Request (CSR).
The CA verifies identity and issues a digital certificate.
Clients trust the CA, so they trust the server certificate.
Secure encrypted communication can now happen.

**Uses of PKI**
HTTPS websites
VPN authentication
Email encryption/signing
Digital signatures
Secure APIs

**SSL/TLS:** SSL (Secure Sockets Layer) and TLS (Transport Layer Security) are protocols used to secure communication over a network. TLS is the modern, secure replacement for SSL.

**Main Goals**
Confidentiality → Data is encrypted.
Integrity → Data is not modified in transit.
Authentication → Confirms the server identity.

**TLS Handshake Process**
Client connects to server.
Server sends its digital certificate.
Client verifies the certificate using trusted CA certificates.
Client and server agree on encryption algorithms and exchange session keys.
A secure encrypted session is established.

**Relationship Between PKI and TLS**
TLS uses PKI for authentication.
PKI provides certificates and trust validation.
TLS uses those certificates to establish secure encrypted communication.

> Q.1. On the AttackBox, you can find the directory for this task located at `/root/Rooms/cryptographyintro/task06`; alternatively, you can use the task file from Task 2 to work on your own machine. What is the size of the public key in bits?
> 

> Q.2. Till which year is this certificate valid?
> 

openssl x509 -in cert.pem -text | less

<img width="848" height="287" alt="image 11" src="https://github.com/user-attachments/assets/a87fc5f0-0aaf-4fe1-8186-9dc7a56522d4" />


#### **Task 7 - Authenticating with Passwords**

With PKI and SSL/TLS, we can communicate with any server and provide our login credentials while ensuring that no one can read our passwords as they move across the network. This is an example of protecting data in transit. Let’s explore how we can safeguard passwords as they are saved in a database, i.e., data at rest.

You were auditing a system when you discovered that the MD5 hash of the admin password is 3fc0a7acf087f549ac2b266baf94b8b1. What is the original password? qwerty123

Use an online MD5 crack tool such as [https://www.md5online.org/md5-decrypt.html](https://www.md5online.org/md5-decrypt.html) or [https://md5decrypt.net/en/](https://md5decrypt.net/en/) 

#### **Task 8 - Cryptography and Data - Example**

Cryptography’s role starts with checking the certificate. For a certificate to be considered valid, it means it is signed. Signing means that a hash of the certificate is encrypted with the private key of a trusted third party; the encrypted hash is appended to the certificate.

If the third party is trusted, the client will use the third party’s public key to decrypt the encrypted hash and compare it with the certificate’s hash. However, if the third party is not recognized, the connection will not proceed automatically.

Once the client confirms that the certificate is valid, an SSL/TLS handshake is started. This handshake allows the client and the server to agree on the secret key and the symmetric encryption algorithm, among other things. From this point onward, all the related session communication will be encrypted using symmetric encryption.

The final step would be to provide login credentials. The client uses the encrypted SSL/TLS session to send them to the server. The server receives the username and password and needs to confirm that they match.
