# Row Column Transformation
# Date: 15-11-2025
# Register No: 212223040171

# Aim:  
To write a C program to implement the Row Column transformation.


# Algorithm: 
STEP1: Read the plaintext P.
STEP2: Determine the number of rows:
STEP3: L = length(P)
STEP4: R = ceil(L / N) → Number of rows needed
STEP5: Create an R × N matrix M and fill it:
STEP6: Fill the matrix row-wise with characters from P.
STEP7: If the matrix is not completely filled, pad remaining cells with a filler character (e.g., 'X').
STEP8: Read the matrix column-wise using the column key:
STEP9: For each column index K[i] in the key array:
STEP10: Read the column K[i] from top to bottom and append characters to the ciphertext.
STEP11: Display the final encrypted message.


# Program:
```
#include <stdio.h>
#include <string.h>
#include <math.h>
#include <stdlib.h>

#define MAX 100

void encrypt(char *plaintext, int *key, int keySize) {
    int len = strlen(plaintext);
    int rows = (int)ceil((float)len / keySize);
    char matrix[rows][keySize];

    int k = 0;
    for (int i = 0; i < rows; i++) {
        for (int j = 0; j < keySize; j++) {
            if (k < len)
                matrix[i][j] = plaintext[k++];
            else
                matrix[i][j] = 'X'; // filler character
        }
    }

    printf("Encrypted message: ");
    for (int i = 0; i < keySize; i++) {
        int col = key[i];
        for (int j = 0; j < rows; j++) {
            printf("%c", matrix[j][col]);
        }
    }
    printf("\n");
}

int main() {
    char plaintext[MAX];
    int key[MAX], n;

    printf("Enter the plaintext: ");
    fgets(plaintext, MAX, stdin);
    plaintext[strcspn(plaintext, "\n")] = 0; 

    printf("Enter number of columns (key size): ");
    scanf("%d", &n);

    printf("Enter the column key (indices from 0 to %d in desired read order):\n", n - 1);
    for (int i = 0; i < n; i++) {
        scanf("%d", &key[i]);
    }

    encrypt(plaintext, key, n);

    return 0;
}
```

# Output:
![image](https://github.com/user-attachments/assets/dcf8b883-41c2-4c8c-8fe7-68d278424149)


# Result:
Thus, the implement the Row Column transformation.
