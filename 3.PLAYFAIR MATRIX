#include <stdio.h>
#include <string.h>
#include <ctype.h>
void generatePlayfairMatrix(char matrix[5][5], const char *key) {
    int keyLength = strlen(key),i,j,l;
    char alphabet[] ="ABCDEFGHIJKLMNOPQRSTUVWXYZ";
    int k = 0;
    for ( i = 0; i < keyLength; i++) {
        if (key[i] == 'J' ||  key[i]=='I');
        int present = 0;
        for ( j = 0; j < 5; j++) {
            for ( l = 0; l < 5; l++) {
                if (matrix[j][l] == key[i]) {
                    present = 1;
                    break;
                }
            }
        }
        if (!present) {
            matrix[k / 5][k % 5] = key[i];
            k++;
        }
    }
    for ( i = 0; i < 26; i++) {
        if (alphabet[i] == 'J')
            alphabet[i] = 'I'; 
        int present = 0;
        for ( j = 0; j < 5; j++) {
            for ( l = 0; l < 5; l++) {
                if (matrix[j][l] == alphabet[i]) {
                    present = 1;
                    break;
                }
            }
        }
        if (!present) {
            matrix[k / 5][k % 5] = alphabet[i];
            k++;
        }
    }
}
void findPosition(const char matrix[5][5], char ch, int *row, int *col) {
	int i,j;
    for ( i = 0; i < 5; i++) {
        for ( j = 0; j < 5; j++) {
            if (matrix[i][j] == ch) {
                *row = i;
                *col = j;
                return;
            }
        }
    }
}
void playfairEncrypt(const char matrix[5][5], char plaintext[], char ciphertext[]) {
    int len = strlen(plaintext);
    int i = 0;

    while (i < len) {
        char first = plaintext[i];
        char second = plaintext[i + 1];
        if (first == second) {
            second = 'X';
            i--;
        }

        int row1, col1, row2, col2;
        findPosition(matrix, first, &row1, &col1);
        findPosition(matrix, second, &row2, &col2);

        if (row1 == row2) {
            ciphertext[i] = matrix[row1][(col1 + 1) % 5];
            ciphertext[i + 1] = matrix[row2][(col2 + 1) % 5];
        } else if (col1 == col2) {
            ciphertext[i] = matrix[(row1 + 1) % 5][col1];
            ciphertext[i + 1] = matrix[(row2 + 1) % 5][col2];
        } else {
            ciphertext[i] = matrix[row1][col2];
            ciphertext[i + 1] = matrix[row2][col1];
        }

        i += 2;
    }
    ciphertext[i] = '\0';
}

int main() {
	int i,j;
    char key[50];
    char plaintext[100];
    char ciphertext[100];
    char matrix[5][5];

    printf("Enter the keyword (no spaces): ");
    scanf("%s", key);
    printf("Enter the plaintext (no spaces): ");
    scanf("%s", plaintext);

    generatePlayfairMatrix(matrix, key);
    playfairEncrypt(matrix, plaintext, ciphertext);

    printf("Playfair Matrix:\n");
    for ( i = 0; i < 5; i++) {
        for ( j = 0; j < 5; j++) {
            printf("%c ", matrix[i][j]);
        }
        printf("\n");
    }

    printf("Encrypted Text: %s\n", ciphertext);

    return 0;
}
