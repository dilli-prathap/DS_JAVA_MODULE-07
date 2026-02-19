# Flattening a Nested List Using an Iterator
## DATE: 19-02-2026

## AIM:
To design and implement a class NestedIterator that flattens a nested list of integers such that all integers can be accessed sequentially using an iterator interface (next() and hasNext()).

## Algorithm
1. Start
2. Read the nested list input as a string
3. Parse the string to create a nested list structure
4. Create an empty list called integers to store flattened elements
5. Call flattenList(nestedList)
6. For each element in nestedList:
7. If the element is an integer, add it to integers list
8. Else recursively call flattenList on its sublist
9. Initialize position = 0
10. For hasNext():
11. Return true if position < size of integers list
12. For next():
13. Return element at current position and increment position
14. Traverse using hasNext() and next() to collect all elements
15. Print the flattened list
16. Stop

## Program:
``` JAVA
/*
Program to find Flattening a Nested List Using an Iterator
Developed by: DILLI PRATHAP
RegisterNumber: 212224110014  
*/

import java.util.*;
public class NestedIterator implements Iterator<Integer> {
    private List<Integer> integers = new ArrayList<>();
    private int position = 0;

    public NestedIterator(List<NestedInteger> nestedList) {
        flattenList(nestedList);
    }

    private void flattenList(List<NestedInteger> nestedList) {
        //Type your code here
        for (NestedInteger ni : nestedList) {
            if (ni.isInteger()) {
                integers.add(ni.getInteger());
            } else {
                flattenList(ni.getList());
            }
        }
    }

    @Override
    public Integer next() {
        //Type your code here
                return integers.get(position++);
    }
    @Override
    public boolean hasNext() {
        //Type your code here
                return position < integers.size();
    }
    public static List<NestedInteger> parse(String s) {
    Stack<List<NestedInteger>> stack = new Stack<>();
    List<NestedInteger> curr = new ArrayList<>();
    int num = 0;
    boolean hasNum = false;

    for (int i = 0; i < s.length(); i++) {
        char c = s.charAt(i);
        if (c == '[') {
            stack.push(curr);
            curr = new ArrayList<>();
        } else if (c == ']') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
            List<NestedInteger> completed = curr;
            curr = stack.pop();
            curr.add(new SimpleNestedInteger(completed));
        } else if (c == ',') {
            if (hasNum) {
                curr.add(new SimpleNestedInteger(num));
                hasNum = false;
                num = 0;
            }
        } else if (Character.isDigit(c)) {
            num = num * 10 + (c - '0');
            hasNum = true;
        }
    }
    return curr;
}


    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
      
        String input = sc.nextLine();

        List<NestedInteger> nestedList = parse(input);

        NestedIterator iterator = new NestedIterator(nestedList);
        List<Integer> output = new ArrayList<>();
        while (iterator.hasNext()) {
            output.add(iterator.next());
        }

        System.out.println(output);
    }
}

interface NestedInteger {
    boolean isInteger();
    Integer getInteger();
    List<NestedInteger> getList();
}

class SimpleNestedInteger implements NestedInteger {
    private Integer value;
    private List<NestedInteger> list;

    public SimpleNestedInteger(Integer value) {
        this.value = value;
        this.list = null;
    }

    public SimpleNestedInteger(List<NestedInteger> list) {
        this.list = list;
        this.value = null;
    }

    @Override
    public boolean isInteger() {
        return value != null;
    }

    @Override
    public Integer getInteger() {
        return value;
    }

    @Override
    public List<NestedInteger> getList() {
        return list;
    }
}

```

## Output:

<img width="685" height="201" alt="Screenshot 2026-02-19 225813" src="https://github.com/user-attachments/assets/982f8e14-dc61-45f2-91b3-d72ed95bced7" />


## Result:
The NestedIterator class successfully flattens a nested list of integers into a single list and provides sequential access using standard iterator methods.
