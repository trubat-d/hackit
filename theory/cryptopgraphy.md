# Cryptopgraphy

### Keywords

* Plaintext - Human readable text
* Ciphertext - Illegible sequence of characters to humans, it requires decryption
* Encryption - Obfuscation of plaintext’s content using algorithms
* Decryption - Reversing Encryptions process turning ciphertex to plaintext

### Goals

* Confidentiality
* Integrity
* Authentication
* Non-repudiation

### Symmetric

* One key for Encryption and decryption
* More efficient than asymmetric but less secure
* Used in day-to-day scenarios where big chunks of data need to be encrypted
* Examples: AES-128/192/256 (Advanced Encryption Standard), Blowfish, Twofish, cast5

<figure><img src="../.gitbook/assets/image (4).png" alt=""><figcaption></figcaption></figure>

### Asymmetric

* One key for encryption (public key) and another one for decryption (private or secret key)
* Public for encryption
* Private for decryption
* Slower due to the complexity of the key-pair
* Examples: RSA (Rivest-Shamir-Adleman), ECC, DSA

## Hashing

> _“What if i take some file, take its content out, and use every single byte inside it to create a unique value that represents this pattern of bytes”_

#### Hashing is primordial in cyber for

* Data integrity and verification - generating a fixed-length value allows quick verification of data authenticity
* Password security - Storing password in hashed form adds an extra layer of protection in case of breach
* File verification - Permit to identify alterations, corruption of tampering in files
* Digital Signature - Encryption the hash of a message permit having a digital signature ensuring message authenticity
* Blockchain Technology - Each black contains a hash of the previous block securing the blockchain’s immutability of data
* Protection against collision attacks - A secure hash makes it computationally infeasible to find two inputs giving the same hash

Examples of Algorithms: MD5 (Message digest 5), SHA-256 (Secure Hash Algorithm 256-bit)

### Salt

Password can be Salted adding a random generated Salt value that will then be hashed in conjunction with the password so that two hashes of the same base password aren’t the same in the database as they where added each a randomly generated salt
