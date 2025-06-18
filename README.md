# New 

#include <stdio.h>
#include <string.h>
#include <stdlib.h>

#define MAX 100

struct Stack {
    int top;
    char items[MAX];
};

void push(struct Stack *s, char c) {
    if (s->top < MAX - 1) {
        s->items[++(s->top)] = c;
    }
}

char pop(struct Stack *s) {
    if (s->top >= 0) {
        return s->items[(s->top)--];
    }
    return '\0';
}

int isPalindrome(char str[]) {
    struct Stack s;
    s.top = -1;
    int len = strlen(str);
    for (int i = 0; i < len; i++) {
        push(&s, str[i]);
    }
    for (int i = 0; i < len; i++) {
        if (str[i] != pop(&s)) {
            return 0;
        }
    }
    return 1;
}

int main() {
    char str[MAX];
    scanf("%s", str);
    if (isPalindrome(str)) {
        printf("Palindrome\n");
    } else {
        printf("Not Palindrome\n");
    }
    return 0;
}
