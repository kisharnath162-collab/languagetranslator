#include <stdio.h>
#include <string.h>
#include <ctype.h>

#define DICT_SIZE 5

// Structure to hold our dictionary word pairs
typedef struct {
    char english[50];
    char spanish[50];
} Dictionary;

// Function to convert a string to lowercase for easier comparison
void toLowerCase(char str[]) {
    for(int i = 0; str[i]; i++){
        str[i] = tolower(str[i]);
    }
}

int main() {
    // A simple hardcoded dictionary
    Dictionary dict[DICT_SIZE] = {
        {"hello", "hola"},
        {"world", "mundo"},
        {"cat", "gato"},
        {"dog", "perro"},
        {"water", "agua"}
    };

    char input[50];
    int found = 0;

    printf("Enter an English word (hello, world, cat, dog, water): ");
    scanf("%49s", input);

    // Convert input to lowercase to make the search case-insensitive
    toLowerCase(input);

    // Search the dictionary array
    for(int i = 0; i < DICT_SIZE; i++) {
        if(strcmp(input, dict[i].english) == 0) {
            printf("Spanish translation: %s\n", dict[i].spanish);
            found = 1;
            break;
        }
    }

    if(!found) {
        printf("Word not found in the dictionary.\n");
    }

    return 0;
}
