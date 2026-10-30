# EX-9_RSA-Algorithm-Implementation-in-C
Implementation of the RSA (Rivest-Shamir-Adleman) encryption and decryption algorithm using C programming for Cryptography laboratory experiments.

## NAME: JOSHNA.M
## REFERENCE NUMBER: 212225230118

# AIM:
To Implement RSA Encryption Algorithm in Cryptography

# ALGORITHM:
Step 1: Design of RSA Algorithm
The RSA algorithm is based on the mathematical difficulty of factoring the product of two large prime numbers. It involves generating a public and private key pair, where the public key is used for encryption, and the private key is used for decryption.

Step 2: Implementation in Python or C This algorithm can be implemented in languages like Python or C by performing large integer calculations for key generation, encryption, and decryption, utilizing libraries for modular arithmetic if necessary.

Step 3: Algorithm Description

    Key Generation:
        Select two large prime numbers ( p ) and ( q ).
        Calculate ( n = p \times q ), which will be used as the modulus.
        Compute the totient ( \phi(n) = (p - 1)(q - 1) ).
        Choose a public exponent ( e ) such that ( e ) is coprime with ( \phi(n) ).
        Compute the private key ( d ), which is the modular inverse of ( e ) mod ( \phi(n) ).

    Encryption:
        Convert the plaintext message ( M ) into a numerical form ( m ) (such that ( 0 \le m < n )).
        Compute the ciphertext ( c ) using the formula: ( c = m^e \mod n ).

    Decryption:
        Use the private key ( d ) to recover ( m ) from ( c ) using: ( m = c^d \mod n ).
        Convert ( m ) back into the original message ( M ).

Step 4: Mathematical Representation

    Encryption: ( E(m) = m^e \mod n )
    Decryption: ( D(c) = c^d \mod n )

Step 5: **Security Foundation
The security of RSA relies on the difficulty of factoring large numbers; thus, choosing sufficiently large prime numbers for ( p ) and ( q ) is crucial for security.

# PROGRAM:
```

#include <stdio.h>

int gcd(int a, int b) {
    while (b != 0) {
        int t = b;
        b = a % b;
        a = t;
    }
    return a;
}

int power(int a, int b, int n) {
    int result = 1;
    while (b > 0) {
        result = (result * a) % n;
        b--;
    }
    return result;
}

int main() {
    int p = 3, q = 11;
    int n = p * q;
    int phi = (p - 1) * (q - 1);
    int e = 3, d = 7;
    int msg, cipher, decrypted;

    printf("Enter a number (0-32): ");
    scanf("%d", &msg);

    if (msg < 0 || msg >= n) {
        printf("Invalid message!");
        return 0;
    }

    cipher = power(msg, e, n);
    decrypted = power(cipher, d, n);

    printf("\nPublic Key: (%d, %d)", e, n);
    printf("\nPrivate Key: (%d, %d)", d, n);
    printf("\nOriginal Message: %d", msg);
    printf("\nEncrypted Message: %d", cipher);
    printf("\nDecrypted Message: %d\n", decrypted);

    return 0;
}
```

# OUTPUT:

<img width="1369" height="254" alt="Screenshot 2026-10-30 134222" src="https://github.com/user-attachments/assets/8e5904bf-35bc-4057-b0c1-a3a5648b24bb" />

# RESULT:
The RSA encryption and decryption algorithm was successfully implemented using C programming. The original message was encrypted using the public key and successfully decrypted using the private key.
