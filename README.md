# EX-NO-12-ELGAMAL-ALGORITHM

## AIM:
To Implement ELGAMAL ALGORITHM

## ALGORITHM:

1. ElGamal Algorithm is a public-key cryptosystem based on the Diffie-Hellman key exchange and relies on the difficulty of solving the discrete logarithm problem.

2. Initialization:
   - Select a large prime \( p \) and a primitive root \( g \) modulo \( p \) (these are public values).
   - The receiver chooses a private key \( x \) (a random integer), and computes the corresponding public key \( y = g^x \mod p \).

3. Key Generation:
   - The public key is \( (p, g, y) \), and the private key is \( x \).

4. Encryption:
   - The sender picks a random integer \( k \), computes \( c_1 = g^k \mod p \), and \( c_2 = m \times y^k \mod p \), where \( m \) is the message.
   - The ciphertext is the pair \( (c_1, c_2) \).

5. Decryption:
   - The receiver computes \( s = c_1^x \mod p \), and then calculates the plaintext message \( m = c_2 \times s^{-1} \mod p \), where \( s^{-1} \) is the modular inverse of \( s \).

6. Security: The security of the ElGamal algorithm relies on the difficulty of solving the discrete logarithm problem in a large prime field, making it secure for encryption.

## Program:
```
#include <stdio.h>
#include <math.h>

long long int modExp(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        base = (base * base) % mod;
        exp = exp / 2;
    }
    return result;
}

int main() {
    long long int p, g, privateKeyRoshan, publicKeyRoshan;
    long long int k, message, c1, c2, decryptedMessage;

    printf("Enter a large prime number (p): ");
    scanf("%lld", &p);

    printf("Enter a generator (g): ");
    scanf("%lld", &g);

    printf("Enter Roshan's private key: ");
    scanf("%lld", &privateKeyRoshan);

    publicKeyRoshan = modExp(g, privateKeyRoshan, p);
    printf("Roshan's public key: %lld\n", publicKeyRoshan);

    printf("Enter the message to encrypt (as a number): ");
    scanf("%lld", &message);

    printf("Enter a random number k: ");
    scanf("%lld", &k);

    c1 = modExp(g, k, p);
    c2 = (message * modExp(publicKeyRoshan, k, p)) % p;

    printf("Encrypted message (c1, c2): (%lld, %lld)\n", c1, c2);

    decryptedMessage = (c2 * modExp(c1, p - 1 - privateKeyRoshan, p)) % p;

    printf("Decrypted message: %lld\n", decryptedMessage);

    return 0;
}
```

## Output:
<img width="437" height="331" alt="image" src="https://github.com/user-attachments/assets/16b94fe3-5861-4b16-8026-4b3875b8c95d" />


## Result:
The program is executed successfully.
