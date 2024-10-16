# EX.-NO-2-A-IMPLEMENTATION-OF-DES

## AIM:
  To write a program to implement Data Encryption Standard (DES).

## ALGORITHM:

  STEP-1: Read the 64-bit plain text.
  
  STEP-2: Split it into two 32-bit blocks and store it in two different arrays.
  
  STEP-3: Perform XOR operation between these two arrays.
  
  STEP-4: The output obtained is stored as the second 32-bit sequence and the original second 32-bit sequence forms the first part.
  
  STEP-5: Thus the encrypted 64-bit cipher text is obtained in this way. Repeat the same process for the remaining plain text characters.
  
## PROGRAM:
```
#include <stdio.h>
    #include <string.h>
    #include <stdint.h>

    uint64_t stringToBinary(const char *str) {
    uint64_t binary = 0;
    for (int i = 0; i < 8 && str[i] != '\0'; ++i) {
        binary <<= 8;
        binary |= (uint64_t)str[i];
    }
    return binary;
    }

    uint32_t XOR(uint32_t a, uint32_t b) {
    return a ^ b;
    }

    uint64_t encryptDES(uint64_t plainText) {
    uint32_t left = (plainText >> 32) & 0xFFFFFFFF;
    uint32_t right = plainText & 0xFFFFFFFF;
    uint32_t xorResult = XOR(left, right);
    uint64_t cipherText = 0;
    cipherText = ((uint64_t)right << 32) | xorResult;

    return cipherText;
    }

    int main() {
    char plainText[9];  
    printf("Enter an 8-character plaintext: ");
    fgets(plainText, sizeof(plainText), stdin);
    plainText[strcspn(plainText, "\n")] = 0;  
    uint64_t binaryPlainText = stringToBinary(plainText);

    uint64_t cipherText = encryptDES(binaryPlainText);

  
    printf("Encrypted Cipher Text (in hex): %016llX\n", cipherText);

    return 0;
    }

```

## OUTPUT:
![image](https://github.com/user-attachments/assets/acbbdf72-7500-493b-8b40-496ca114e889)


## RESULT:

  Thus the data encryption standard algorithm had been implemented successfully.
