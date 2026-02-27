# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

long long int mod_exp(long long int base, long long int exp, long long int mod) {
    long long int result = 1;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;

        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    long long int P, G, a, b, x, y, ka, kb;
    char name1[50], name2[50];

    printf("Enter name of first user: ");
    scanf("%s", name1);

    printf("Enter name of second user: ");
    scanf("%s", name2);

    printf("\nEnter a prime number P: ");
    scanf("%lld", &P);
    printf("The value of P: %lld\n", P);

    printf("Enter a primitive root G for P: ");
    scanf("%lld", &G);
    printf("The value of G: %lld\n\n", G);

    printf("Enter the private key for %s: ", name1);
    scanf("%lld", &a);
    x = mod_exp(G, a, P);
    printf("The public key for %s (x = G^a mod P): %lld\n", name1, x);

    printf("\nEnter the private key for %s: ", name2);
    scanf("%lld", &b);
    y = mod_exp(G, b, P);
    printf("The public key for %s (y = G^b mod P): %lld\n\n", name2, y);

    ka = mod_exp(y, a, P);
    kb = mod_exp(x, b, P);

    printf("Shared secret key for %s: %lld\n", name1, ka);
    printf("Shared secret key for %s: %lld\n", name2, kb);

    if (ka == kb) {
        printf("\nDiffie-Hellman Key Exchange successful. Both parties share the same key.\n");
    } else {
        printf("\nError: The keys do not match.\n");
    }

    return 0;
}
```


## Output:

<img width="1723" height="908" alt="image" src="https://github.com/user-attachments/assets/96fab723-7bc8-4ef5-b491-d12548d07827" />


## Result:
  The program is executed successfully

