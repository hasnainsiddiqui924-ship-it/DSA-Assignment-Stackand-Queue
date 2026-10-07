# DSA-Assignment-Stackand-Queue
README.md
DATA STRUCTURES & ALGORITHMS ASSIGNMENT
​Course Code: CS-201
Topic: Stacks & Circular Queues (Array Implementation)  
​Question 1: Implementation of Stack using Array
​Problem Statement: Design and implement a stack using an array without using any built-in stack library. Perform operations: PUSH(x), POP(), PEEK(), DISPLAY(). Program must handle both Stack Overflow and Underflow conditions.  
#include <iostream>
using namespace std;

#define MAX_SIZE 5

class Stack {
private:
    int arr[MAX_SIZE];
    int top;

public:
    Stack() { top = -1; }

    void push(int x) {
        if (top == MAX_SIZE - 1) {
            cout << "Stack Overflow! Cannot push " << x << ".\n";
            return;
        }
        arr[++top] = x;
        cout << "Pushed " << x << " onto the stack.\n";
    }

    void pop() {
        if (top == -1) {
            cout << "Stack Underflow! Cannot pop from empty stack.\n";
            return;
        }
        cout << "Popped " << arr[top--] << " from stack.\n";
    }

    void peek() {
        if (top == -1) { 
            cout << "Stack is empty.\n"; 
            return; 
        }
        cout << "Top element: " << arr[top] << "\n";
    }

    void display() {
        if (top == -1) { 
            cout << "Stack is empty.\n"; 
            return; 
        }
        cout << "Stack elements (top to bottom): ";
        for (int i = top; i >= 0; i--) cout << arr[i] << " ";
        cout << "\n";
    }
};

int main() {
    Stack s;
    s.push(10); 
    s.push(20); 
    s.push(30);
    s.display();
    s.peek();
    s.pop();
    s.display();
    return 0;
}
Question 2: Implementation of Circular Queue using Array
​Problem Statement: Implement a Circular Queue using an array supporting: ENQUEUE(x), DEQUEUE(), FRONT(), DISPLAY(). Distinguish between full and empty queues, and compare memory utilization against linear queues.  
#include <iostream>
using namespace std;

#define SIZE 5

class CircularQueue {
private:
    int arr[SIZE], front, rear;

public:
    CircularQueue() { front = -1; rear = -1; }

    bool isFull() { return (front == (rear + 1) % SIZE); }
    bool isEmpty() { return (front == -1); }

    void enqueue(int x) {
        if (isFull()) {
            cout << "Queue Overflow! Queue is full.\n";
            return;
        }
        if (isEmpty()) { front = 0; rear = 0; }
        else { rear = (rear + 1) % SIZE; }
        arr[rear] = x;
        cout << "Enqueued " << x << " successfully.\n";
    }

    void dequeue() {
        if (isEmpty()) {
            cout << "Queue Underflow! Queue is empty.\n";
            return;
        }
        cout << "Dequeued " << arr[front] << " from queue.\n";
        if (front == rear) { front = -1; rear = -1; }
        else { front = (front + 1) % SIZE; }
    }

    void getFront() {
        if (isEmpty()) { cout << "Queue is empty.\n"; return; }
        cout << "Front element: " << arr[front] << "\n";
    }
};

int main() {
    CircularQueue q;
    q.enqueue(10); 
    q.enqueue(20); 
    q.enqueue(30);
    q.dequeue(); 
    q.enqueue(40); 
    q.getFront();
    return 0;
}
