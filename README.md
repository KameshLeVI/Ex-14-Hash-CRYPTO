# Ex-14-Hash-CRYPTO

## AIM:

To generate a simple hash of a given message using a custom hash function.

## DESIGN STEPS:

### Step 1:

Input a message from the user.

### Step 2:

Use a basic custom hash function that applies simple operations like XOR and addition on the characters of the message.

### Step 3:

Convert the resulting hash into a hexadecimal format.

### Step 4:

Display the computed hash to the user.

### Step 5:

Optionally verify the hash by recomputing it and comparing it with a received hash.

## PROGRAM:

```c
#include <stdio.h>
#include <string.h>
void computeSimpleHash(const char *message, unsigned char *hash) {
    unsigned char temp = 0;

    for (int i = 0; message[i] != '\0'; i++) {
        temp = temp ^ message[i];  
        temp += message[i];
    }
    *hash = temp;
}

int main() {
    char message[256];      
    unsigned char hash;    
    char receivedHash[3];  
    printf("Enter the message: ");
    scanf("%s", message);

    computeSimpleHash(message, &hash);

    printf("Computed Hash (in hex): %02x\n", hash);

    printf("Enter the received hash (in hex): ");
    scanf("%s", receivedHash);

    unsigned int receivedHashValue;
    sscanf(receivedHash, "%02x", &receivedHashValue);

    if (hash == receivedHashValue) {
        printf("Hash verification successful. Message is unchanged.\n");
    } else {
        printf("Hash verification failed. Message has been altered.\n");
    }

    return 0;
}
```

## OUTPUT:
![image](https://github.com/user-attachments/assets/06573f57-048e-47c0-b908-68e77e37005e)



## RESULT:

The program for generating and verifying a simple hash of a given message using a custom hash function was executed successfully. The computed hash ensures basic integrity of the message.
