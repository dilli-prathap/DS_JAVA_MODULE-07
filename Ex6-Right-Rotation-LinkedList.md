# Ex6 Right Rotation LinkedList
## DATE: 19-02-2026
## AIM:
To write a Java  program to:
Create a singly linked list.
Rotate the linked list to the right by k positions.
Display the rotated linked list.

## Algorithm
1. Start
2. Create a singly linked list
3. Read number of nodes (n)
4. Insert n elements into the linked list
5. Read value of k (number of rotations)
6. Find the length of the linked list
7. Make the list circular by connecting last node to head
8. Find the new tail node at (length - k % length - 1)
9. Set new head as next of new tail
10. Break the circular link
11. Display the rotated linked list
12. Stop

## Program:
``` JAVA
/*
Program to  Right Rotation LinkedList
Developed by: DILLI PRATHAP
RegisterNumber: 212224110014
*/

import java.util.Scanner;
public class RotateLinkedList {
    public static Node rotate(Node head, int k) {
       //Type your code here
       if(head==null||head.next==null||k==0) return head;
       Node current = head;
       int length=1;
       while(current.next != null){
           current = current.next;
           length++;
       }
       current.next=head;
       k=k%length;
       int s=length-k;
       for(int i=0;i<s-1;i++){
           head=head.next;
           
       }
       Node newhead = head.next;
       head.next=null;
       return newhead;
       
    }
    public static void display(Node head) {
        Node current = head;
        System.out.print("LinkedList: ");
        while (current != null) {
            System.out.print(current.data + " ");
            current = current.next;
        }
        System.out.println();
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
        int k = scanner.nextInt();
        head = rotate(head, k);
        display(head);
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

<img width="858" height="272" alt="Screenshot 2026-02-19 224455" src="https://github.com/user-attachments/assets/74f09b92-820f-4c7d-9641-08aadbfd1248" />


## Result:
Thus, the C program to perfom right rotation on linked list is implemented successfully.
