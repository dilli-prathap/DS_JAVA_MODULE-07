# Ex8 Detection of Cycle and Finding the Starting Node in a Linked List

## DATE: 19-02-2026

## AIM:
To write a program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.

## Algorithm

1. Start
2. Create a singly linked list by inserting n nodes
3. Read position (pos) to create a loop
4. If pos > 0, connect the last node to the node at position pos
5. Initialize two pointers: slow = head and fast = head
6. If head is null or head.next is null, return false (no loop)
7. Traverse the list using a loop:
8. Move slow pointer one step forward
9. Move fast pointer two steps forward
10. If slow equals fast, return true (loop detected)
11. If fast reaches null, return false (no loop)
12. Print the result
13. Stop

## Program:
```JAVA
/*
program that detects a cycle in a linked list and returns the node where the cycle begins.
If there is no cycle, the program should return null without modifying the linked list.
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014
*/

import java.util.Scanner;

public class DetectLoopFloyd {
    public static boolean hasLoop(Node head) {
       //Type your code here
       if(head==null || head.next == null){
           return false;
       }
       Node slow=head;
       Node fast = head;
       while(fast != null && fast.next !=null){
           slow=slow.next;
           fast=fast.next.next;
           if(slow==fast) return true;
       }
           return false;
       
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Node head = null, tail = null;

        int n = scanner.nextInt();

        for (int i = 0; i < n; i++) {
            Node newNode = new Node(scanner.nextInt());
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }

      
        int pos = scanner.nextInt();

        if (pos > 0) {
            Node loopNode = head;
            for (int i = 1; i < pos && loopNode != null; i++) {
                loopNode = loopNode.next;
            }
            if (loopNode != null) {
                tail.next = loopNode;
            }
        }

        if (hasLoop(head)) {
            System.out.println("Loop detected in the LinkedList.");
        } else {
            System.out.println("No loop detected in the LinkedList.");
        }

        scanner.close();
    }
}

class Node {
    int data;
    Node next;

    Node(int data) {
        this.data = data;
        this.next = null;
    }
}


```

## Output:

<img width="914" height="227" alt="Screenshot 2026-02-19 225144" src="https://github.com/user-attachments/assets/ac9abf84-719d-4239-91e9-f6dbeb7abc31" />


## Result:
The program successfully detects whether a cycle exists in the linked list.
If a cycle is present, it correctly identifies and returns the node where the cycle begins.
