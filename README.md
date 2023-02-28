# Data-Encryption-using-RSA-and-Elgamal-Algorithms

With the growth in the amount of transmitted data day by day, security has come to be
considered one of the backbones of message transmission across various communication
mediums, particularly when the secrecy of the information exchanged is paramount. Ensuring
the security, authenticity, and integrity of data is becoming an increasingly complex task. As a
result, cryptographic techniques are used to secure data transmissions over these
communication mediums, ensuring data confidentiality while in transit. In this research paper,
a system of multi-layered security through the implementation of public-key cryptographic
techniques, namely the RSA and ElGamal algorithms, one atop the other, has been highlighted.
Our project proposes a way to use both the RSA algorithm and ElGamal to ensure maximum
safety and avoid the risks of online data transfer theft and malicious observation of personal
data like online credentials. It proposes a system to challenge people with malicious intent who
are trying to get access/steal important data. We do this in order to not only encrypt a user's
data but also to make it harder for people with malicious intent to get access to them by
embedding them onto an image so that it will be harder for the hackers to get to know where
the credentials are stored as they would be searching for text-based files.

Encryption Algorithms Used:

I. RSA Algorithm:

The RSA algorithm utilizes both a public key and a private key because it is an asymmetric
cryptography algorithm (i.e., two different, mathematically linked keys). A private key is secret
and should never be disclosed, contrary to what their names imply. A public key is shared
publicly.
How the RSA algorithm functions are demonstrated in the subsequent steps:
1. First, create the keys
- Choose the big prime numbers x and y. It is necessary for the prime numbers to be huge
in order for someone to have trouble deciphering them.
- Calculate n= x*y
- Determine the value of the totient function ϕ(n)=(x−1)(y−1)
- Choose an integer e that is both coprime to ϕ(n) and 1<e<ϕ(n).
- The public key is made up of a pair of numbers (n,e).
- Determine d so that e.d = 1 mod ϕ(n).
2. Encryption
- The ciphertext C is computed as follows given a plaintext P, which is expressed as a
number: C= P^e mod n
3. Decryption
- You can find the plaintext by using the private key (n,d), P= C^d mod n.

II. RSA Digital Signature Scheme

The RSA digital signature scheme refers to the application of the RSA concept to the
signing and validation of messages.
The function of the private and public keys is altered by a digital signature scheme.
- Only the sender's private and public keys are used, not the recipient's
- The document is signed using the sender's private key, and the recipient verifies it using
the sender's public key.
- The same function is used by the signing and verifying sets, but with different inputs.
The verifier checks for congruence by comparing the message with the function's
output. The message is accepted if the outcome is two true.
- Key generation for the RSA cryptosystem and the RSA digital signature technique are
identical.
Working:
- The digital signature S calculated over the message M is what Sender A intends to
convey to the receiver B together with the message M.
- Step 1: The sender A calculates the message digest MD1 over the original message M
using the message digest algorithm.
- Step 2: Using her private key, sender A now encrypts the message digest. The digital
signature is the result of this operation.
- Step 3: The sender A now transmits the recipient B the original message M and digital
signature DS.
- Step 4: After receiving the initial message M and the sender A's digital signature,
receiver B calculates its own message digest MD2 using the same message digest
technique as sender A.
- Step 5: The receiver B now decrypts the digital signature using sender A's public key.
It should be noted that A created the digital signature by using his private key to decrypt
the message digest MD1. Therefore, it can only be unlocked with A's public key. The
original message digest, which A (MD1) calculated in step 1, is the procedure's output.
- Step 6: The next step is for B to compare the next two message digests.
o 1)It had calculated MD2 in step 4
o 2)Step 5 involves retrieving MD1 from A's digital signature.
o The following facts are established if MD1 = MD2.
- a. B acknowledges that the initial message (M) from A is the true,
unaltered message.
- b. B is also confident that A sent the message and not someone else 
associated who was impersonating A.
- As a result, the digital signature idea is very solid, safe, and trustworthy.

III. Elgamal Algorithm

The encryption technique used by ElGamal's cryptosystem to secure communication between
two systems uses the ideas of public and private keys. With the use of both public and private
keys, encryption and decryption are accomplished using what is known as an asymmetric
algorithm. The client uses the public key to encrypt the communication, and the server can use
the private key to decrypt the message. This algorithm is thought to be effective for both
encryption and decryption since the keys are very difficult to guess.
The steps involved in the protocol are as follows:
Suppose person A wants to communicate with person B; the first requirement would be to pick
the following two fixed, public parameters:
p - 2048-bit prime number
g - generator in the range 1 < g < p-1
The recipient of the message, B, will pick a random number x in the range 0 <= b <= p-2 and
compute X = gxmod p. Here, X is B’s public key, which B broadcasts to everyone, and x is B’s
private key which B will keep a secret.
1. Now that B’s public key is known to A and A wants to send a message m to B, A will
pick a random number r in the range 0 < r < p-2. To encrypt the message m, A will
compute the ciphertext by calculating its public key as R = gr mod p.
2. A will then calculate the shared key K = Xrmod p.
3. A will encrypt the message m by computing S = m * K. The ciphertext format is (R, S),
where R and S numbers lie in the range 0 to p-1.
4. A will send the ciphertext (R, S) to B.
5. B will decrypt the ciphertext by first computing R-x
* S mod p. Upon calculation, this
results in the message m sent by A.
The next time A wants to send a message to B, A will choose a new random number r, and
calculates a new public key each time. However, B will use its long-term public key calculated
previously.

IV. Elgamal Digital Signature Scheme

One of the first digital signature systems based on an arithmetic modulo a prime is the ElGamal
signature technique. It can be seen as a forerunner of the Schnorr signature system and the
Digital Signature Standard. In comparison to DSS and Schnorr signatures, ElGamal signatures
are substantially lengthier. Because of this, this signature system is rarely utilised and is mostly
interesting for historical purposes. We offer a slight change to the initial strategy that
incorporates the hash function required for the security evaluation.
The global ingredients of an Elgamal digital signature are the prime number q and a, which is
a primitive root of q, much like with Elgamal encryption.
User A generates a private/public key pair as follows.
- Generate a random integer XA, such that 1 < XA < q - 1.
- Compute YA = aXA mod q.
- A’s private key is XA; A’s public key is {q, a, YA}.
User A’s Work:
To sign a message M, user A first computes the hash m = H(M), such that m is an integer in
the range 0 ≤m ≤ q - 1. A then forms a digital signature as follows.
- Choose a random integer K such that 1 ≤ K ≤ q - 1 and gcd (K, q - 1) = 1. That is, K is
relatively
prime to q - 1.
- Compute S1 = aK mod q. Note that this is the same as the computation of C1
for Elgamal encryption.
- Compute K-1 mod (q - 1). That is, compute the inverse of K modulo q - 1.
- Compute S2 = K-1(m - XAS1) mod (q - 1).
- The signature consists of the pair (S1, S2).
User B’s Work:
Any user B can verify the signature as follows.
- Compute V1 = α m mod q.
- Compute V2 = (YA)S1(S1)S2 mod q.
The signature is valid if V1 = V2. Let us demonstrate that this is so.
