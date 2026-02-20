# Ex7 Removal of Nodes with a Specific Value from a Linked List
## DATE: 19-02-2026
## AIM:
To write a java  program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.

## Algorithm
1. Start
2. Create a singly linked list
3. Read number of nodes (n)
4. Insert n elements into the linked list
5. Read the value (val) to be removed
6. While head is not null and head data equals val, move head to next node
7. Traverse the linked list using a pointer
8. If next node data equals val, skip that node
9. Continue until end of list
10. Display the modified linked list
11. Stop

## Program:
```java
/*
program that removes all nodes from a linked list whose value matches a given integer (val) and returns the new head of the modified linked list.
Developed by: DILLI PRATHAP
RegisterNumber:  212224110014
*/
import java.util.Scanner;

class Node {
    int data;
    Node next;
    Node(int data) {
        this.data = data;
        this.next = null;
    }
}

public class RemoveValueLinkedList {
    static Node removeElements(Node head, int val) {
        while (head != null && head.data == val) {
            head = head.next;
        }
        Node current = head;
        while (current != null && current.next != null) {
            if (current.next.data == val) {
                current.next = current.next.next;
            } else {
                current = current.next;
            }
        }
        return head;
    }

    static void display(Node head) {
        Node temp = head;
        while (temp != null) {
            System.out.print(temp.data + " ");
            temp = temp.next;
        }
        System.out.println();
    }

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Node head = null, tail = null;
        System.out.print("Enter number of elements: ");
        int n = sc.nextInt();
        System.out.println("Enter elements:");
        for (int i = 0; i < n; i++) {
            int val = sc.nextInt();
            Node newNode = new Node(val);
            if (head == null) {
                head = tail = newNode;
            } else {
                tail.next = newNode;
                tail = newNode;
            }
        }
        System.out.print("Enter value to remove: ");
        int value = sc.nextInt();
        head = removeElements(head, value);
        System.out.println("Linked list after removal:");
        display(head);
        sc.close();
    }
}
```

## Output:

<img width="943" height="209" alt="511968977-a053d010-8c86-4f35-80da-051e624e5273" src="https://github.com/user-attachments/assets/95a65055-db6e-43ec-95ed-ac58e60d6a1d" />


## Result:
The java program successfully removes all nodes with the specified value (val) from the linked list and returns the new head.
