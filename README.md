//Stack implementation
#include <stdio.h>
#define MAX 100

int stack[MAX]; //initializing a stack 
int minStack[MAX];//a min stack
int maxStack[MAX];//a max stack
int top = -1; // asigning top as -1

void push(int value) {
    if (top == MAX - 1) {
        printf("Stack Overflow\n");
        return;
    }
    top++;
    stack[top] = value;
    
    if (top == 0) {
        minStack[top] = value;
        maxStack[top] = value;
    } else {
        if (value < minStack[top - 1]) {
            minStack[top] = value;
        } else {
            minStack[top] = minStack[top - 1];
        }
        
        if (value > maxStack[top - 1]) {
            maxStack[top] = value;
        } else {
            maxStack[top] = maxStack[top - 1];
        }
    }
    printf("%d pushed to stack\n", value);
}

int pop() {
    if (top == -1) {
        printf("Stack Underflow\n");
        return -1;
    }
    return stack[top--];
}

int peek() {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    }
    return stack[top];
}

int isEmpty() {
    return top == -1;
}

int getMin() {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    }
    return minStack[top];
}

int getMax() {
    if (top == -1) {
        printf("Stack is empty\n");
        return -1;
    }
    return maxStack[top];
}

void display() {
    if (top == -1) {
        printf("Stack is empty\n");
        return;
    }
    printf("Stack elements: ");
    for (int i = 0; i <= top; i++) {
        printf("%d ", stack[i]);
    }
    printf("\n");
}

int main() {
    push(10);
    push(20);
    push(30);
    display();
    printf("Min: %d\n", getMin());
    printf("Max: %d\n", getMax());
    printf("Popped element: %d\n", pop());
    printf("Top element: %d\n", peek());
    display();
    printf("Min: %d\n", getMin());
    printf("Max: %d\n", getMax());
    return 0;
}
