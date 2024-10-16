## AIM:
To implement the Diffie-Hellman algorithm to securely exchange keys and generate a shared secret key.
## ALGORITHM:
Step 1:
Design the Diffie-Hellman key exchange algorithm.<br>

Step 2:
Implement the algorithm using C.<br>

Step 3:
The Diffie-Hellman algorithm uses a large prime number p and a primitive root g. Both Alice and Bob select private keys and exchange public keys computed using the formula:<br>

Public Key = (g^Private Key) % p<br>

After exchanging public keys, both compute a shared secret key using:<br>

Shared Secret = (Other's Public Key^Private Key) % p
<br>
## PROGRAM:
```c
#include <stdio.h>
#include <math.h>

int modExp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1) {
            result = (result * base) % mod;
        }
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
   
    int p = 23;  
    int g = 5;   
    
    int a, b;
    printf("Enter Alice's private key: ");
    scanf("%d", &a);
    printf("Enter Bob's private key: ");
    scanf("%d", &b);
    
    int A = modExp(g, a, p);  
    int B = modExp(g, b, p);  
    
    printf("Alice's Public Key: %d\n", A);
    printf("Bob's Public Key: %d\n", B);
    
   
    int sharedKeyAlice = modExp(B, a, p);  
 
    int sharedKeyBob = modExp(A, b, p);   
    
    printf("Shared Secret Key (Alice): %d\n", sharedKeyAlice);
    printf("Shared Secret Key (Bob): %d\n", sharedKeyBob);
    
    if (sharedKeyAlice == sharedKeyBob) {
        printf("Key Exchange Successful! Shared Secret Key: %d\n", sharedKeyAlice);
    } else {
        printf("Key Exchange Failed!\n");
    }

    return 0;
}
```
## OUTPUT:
![Screenshot 2024-10-16 201358](https://github.com/user-attachments/assets/eaf76a92-a394-4674-86a5-bb7cacfbb219)


## RESULT:
The program for the Diffie-Hellman algorithm is executed successfully, and Alice and Bob have securely derived a shared secret key.
