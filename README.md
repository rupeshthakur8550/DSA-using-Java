
# Data Structures and Algorithms (DSA) in Java
---

## Table of Contents

1. [Arrays and ArrayLists](#arrays-and-arraylists)
   - [Arrays](#arrays)
   - [ArrayLists](#arraylists)
     - Methods: `add`, `remove`, `get`, `contains`, `clear`, `size`, `sort`, `toArray`, etc.
   - [Multi-dimensional Arrays](#multi-dimensional-arrays)
   - [Multi-dimensional ArrayLists](#multi-dimensional-arraylists)
2. [Searching Algorithms](#searching-algorithms)
   - [Linear Search](#linear-search)
   - [Binary Search](#binary-search)
3. [Bit Manipulations](#bit-manipulations)
   - Tables: `AND`, `OR`, `NOT`, `XOR`, `Left Shift Operator (<<)`, `Right Shift Operator (>>)`
4. [String Handling](#string-handling)
   - [String](#string)
   - [StringBuffer](#stringbuffer)
   - [StringBuilder](#stringbuilder)
5. [Sorting Techniques](#sorting-techniques)
   - [Bubble Sort](#bubble-sort)
   - [Selection Sort](#selection-sort)
   - [Insertion Sort](#insertion-sort)
   - [Cyclic Sort](#cyclic-sort)
   - [Merge Sort](#merge-sort)
   - [Quick Sort](#quick-sort)
6. [Object Oriented Programming](#object-oriented-programming)
   - [1. Classes and Objects](#classes-and-objects)
     - [Classes](#classes)
     - [Objects](#objects)
     - [Dot Operator](#dot-operator)
     - [Dynamic Memory Allocation with 'new'](#dynamic-memory-allocation-with-new)
   - [2. Inheritance](#inheritance)
     - [Single Inheritance](#single-inheritance)
     - [Multilevel Inheritance](#multilevel-inheritance)
     - [Hierarchical Inheritance](#hierarchical-inheritance)
     - [Multiple Inheritance (Not Supported in Java)](#multiple-inheritance-not-supported-in-java)
     - [Hybrid Inheritance (Not Supported in Java)](#hybrid-inheritance-not-supported-in-java)
   - [Superclass Variable References Subclass Objects](#a-superclass-variable-can-reference-a-subclass-object)
   - [Using `super`](#using-super)
     - [Calling Superclass Constructor](#calling-superclass-constructor)
     - [Accessing Superclass Members](#accessing-superclass-members)
   - [Using `final`](#using-final)
     - [Creating Named Constants](#creating-named-constants)
     - [Preventing Method Overriding](#preventing-method-overriding)
     - [Preventing Inheritance](#preventing-inheritance)
   - [Polymorphism](#polymorphism)
     - [Instance Variables](#polymorphism-does-not-apply-to-instance-variables)
     - [Method Overloading](#overloading-methods)
   - [Returning Objects](#returning-objects)
   - [Unsupported Types](#note-on-unsupported-types)
     - [Multiple Inheritance](#multiple-inheritance)
     - [Hybrid Inheritance](#hybrid-inheritance)

---

## Arrays and ArrayLists

### Arrays
An array is a collection of elements of the same type placed in contiguous memory locations. It is a fixed-size data structure.

**Example: Reversing an Array**

```java
import java.util.Arrays;

public class ReverseArray {
    public static void main(String[] args) {
        System.out.println(Arrays.toString(reverse(new int[] { 10, 5, 9, 2, 30, 40 })));
    }

    private static int[] reverse(int[] arr) {
        int i = 0, j = arr.length - 1;
        while (i <= j) {
            int temp = arr[i];
            arr[i++] = arr[j];
            arr[j--] = temp;
        }
        return arr;
    }
}
```

### ArrayLists
ArrayList is a part of the Java Collections Framework. It is resizable and provides methods to manipulate the size of the array.

**Methods and Examples:**

1. `add(E e)`: Appends the specified element to the end of this list.
2. `remove(Object o)`: Removes the first occurrence of the specified element from this list.
3. `get(int index)`: Returns the element at the specified position in this list.
4. `contains(Object o)`: Returns `true` if this list contains the specified element.
5. `clear()`: Removes all of the elements from this list.
6. `size()`: Returns the number of elements in this list.
7. `sort(Comparator<? super E> c)`: Sorts this list according to the order induced by the specified Comparator.
8. `toArray()`: Returns an array containing all of the elements in this list.

**Example: Basic Operations**

```java
import java.util.ArrayList;
import java.util.Collections;

public class ArrayListExample {
    public static void main(String[] args) {
        ArrayList<String> list = new ArrayList<>();
        list.add("Apple");
        list.add("Banana");
        list.add("Cherry");
        
        System.out.println(list);  // Output: [Apple, Banana, Cherry]
        
        list.remove("Banana");
        System.out.println(list);  // Output: [Apple, Cherry]
        
        System.out.println(list.get(0));  // Output: Apple
        System.out.println(list.contains("Cherry"));  // Output: true
        
        list.clear();
        System.out.println(list.size());  // Output: 0
        
        list.add("Banana");
        list.add("Apple");
        list.add("Cherry");

        System.out.println(list.sort());  // Output: [Apple, Banana, Cherry]
        System.out.println(Comparator.reverseOrder());  // Output: [Cherry, Banana, Apple]
        
        Object[] arr = list.toArray();
        for (Object obj : arr) {
            System.out.println(obj);
        }
    }
}
```

### Multi-dimensional Arrays
A multi-dimensional array is an array of arrays. It can be used to represent data in a grid or matrix format.

**Example: Multi-dimensional Array**

```java
public class MultiDimensionalArray {
    public static void main(String[] args) {
        int[][] matrix = {
            {1, 2, 3},
            {4, 5, 6},
            {7, 8, 9}
        };

        for (int i = 0; i < matrix.length; i++) {
            for (int j = 0; j < matrix[i].length; j++) {
                System.out.print(matrix[i][j] + " ");
            }
            System.out.println();
        }
    }
}
```

### Multi-dimensional ArrayLists
A multi-dimensional ArrayList is an ArrayList of ArrayLists. It can be dynamically resized and used similarly to multi-dimensional arrays.

**Example: Multi-dimensional ArrayList**

```java
import java.util.ArrayList;

public class MultiDimensionalArrayList {
    public static void main(String[] args) {
        ArrayList<ArrayList<Integer>> list = new ArrayList<>();

        ArrayList<Integer> row1 = new ArrayList<>();
        row1.add(1);
        row1.add(2);
        row1.add(3);

        ArrayList<Integer> row2 = new ArrayList<>();
        row2.add(4);
        row2.add(5);
        row2.add(6);

        list.add(row1);
        list.add(row2);

        for (ArrayList<Integer> row : list) {
            for (int val : row) {
                System.out.print(val + " ");
            }
            System.out.println();
        }
    }
}
```

## Searching Algorithms

### Linear Search

Linear search is a simple search algorithm that checks every element until the desired element is found or the list ends.

#### Linear Search in an Array Implementation

```java
public class LinearSearch {
    public static void main(String[] args) {
        int[] arr = { 10, 20, 30, 4, 2, 9, 40 };
        int target = 40;
        int result = search(arr, target);
        
        if (result == -1) {
            System.out.println("Element not found");
        } else {
            System.out.println("Element found at index: " + result);
        }
    }

    private static int search(int[] arr, int val) {
        for (int i = 0; i < arr.length; i++) {
            if (arr[i] == val) {
                return i;
            }
        }
        return -1;
    }
}
```

#### Linear Search in a String Implementation

```java
public class LinearSearchString {
    public static void main(String[] args) {
        String str = "abchksdj";
        char target = 'h';
        
        boolean result = find(str, target);
        System.out.println("Character " + target + " found: " + result);
    }

    private static boolean find(String str, char ch) {
        for (char check : str.toCharArray()) {
            if (check == ch) {
                return true;
            }
        }
        return false;
    }
}
```

#### Counting Even Digits in an Array

```java
public class EvenDigits {
    public static void main(String[] args) {
        int[] arr = { 10, 20, 30, 4, 2, 9, 40, 1000 };
        int count = evendigits(arr);
        
        System.out.println("Number of elements with even digits: " + count);
    }

    private static int evendigits(int[] arr) {
        int count = 0;
        for (int val : arr) {
            if ((int) (Math.log10(val) + 1) % 2 == 0) {
                count++;
            }
        }
        return count;
    }
}
```

### Binary Search

Binary search is a more efficient algorithm that works on sorted arrays. It divides the array into halves to find the target value.

#### Binary Search in an Array Implementation

```java
public class BinarySearch {
    public static void main(String[] args) {
        int[] arr = { 1, 2, 3, 4, 5, 6, 7, 8, 9 };
        int target = 6;
        
        boolean result = search(arr, target);
        System.out.println("Element found: " + result);
    }

    private static boolean search(int[] arr, int target) {
        int start = 0, end = arr.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (arr[mid] == target) {
                return true;
            } else if (arr[mid] < target) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
        return false;
    }
}
```

#### Finding Ceil and Floor Values in an Array

**Ceil Value**

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(ceil(arr, 2));
}

private static int ceil(int[] arr, int target) {
    // Smallest element in greater elements than target
    int s = 0, e = arr.length - 1;
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (arr[m] == target) {
            return arr[m];
        } else if (arr[m] < target) {
            s = m + 1;
        } else {
            e = m - 1;
        }
    }
    return arr[s];
}
```

**Floor Value**

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(floor(arr, 6));
}

private static int floor(int[] arr, int target) {
    int s = 0, e = arr.length - 1;
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (arr[m] == target) {
            return arr[m];
        } else if (arr[m] < target) {
            s = m + 1;
        } else {
            e = m - 1;
        }
    }
    return arr[e];
}
```

#### Finding the Ceil Value in a String

```java
public static void main(String[] args) {
    System.out.println(ceilOfChar("abhijt", 'b'));
}

private static char ceilOfChar(String str, char ch) {
    int s = 0, e = str.length() - 1;
    char result = str.charAt(0);
    while (s <= e) {
        int m = s + (e - s) / 2;
        if (str.charAt(m) > ch) {
            result = str.charAt(m);
            e = m - 1;
        } else {
            s = m + 1;
        }
    }
    return result;
}
```

#### Finding the First and Last Occurrence of an Element in a Sorted Array

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(find(arr, 4, true) + " " + find(arr, 4, false));
}

private static int find(int[] arr, int target, boolean left) {
    int start = 0, end = arr.length - 1;
    int ans = 0;
    while (start <= end) {
        int mid = start + (end - start) / 2;
        if (arr[mid] == target) {
            ans = mid;
            if (left) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        } else if (arr[mid] < target) {
            start = mid + 1;
        } else {
            end = mid - 1;
        }
    }
    return ans;
}
```

#### Finding the Peak Element in a Bitonic (Mountain) Array

```java
public static void main(String[] args) {
    int[] arr = { 1, 2, 3, 4, 5, 6, 5, 4, 2, 0 };
    System.out.println(peak(arr));
}

private static int peak(int[] arr) {
    int start = 0, end = arr.length - 1;
    while (start < end) {
        int mid = start + (end - start) / 2;
        if (arr[mid] < arr[mid + 1]) {
            start = mid + 1;
        } else {
            end = mid;
        }
    }
    return start;
}
```

#### Searching an Element in a Rotated Sorted Array

```java
public static void main(String[] args) {
    System.out.println(searchInRotatedArray(new int[] { 4, 5, 6, 7, 0, 1, 2 }, 0));
}

private static int searchInRotatedArray(int[] arr, int target) {
    if (arr.length == 0) {
        return -1;
    }
    int start = 0, end = arr.length - 1;
    while (start <= end) {
        int mid = start + (end - start) / 2;
        // if rotated array contains duplicates then add below code
        // if (arr[start] == arr[mid] && arr[mid] == arr[end]) {
        // start++;
        // end--;
        // }

        if (arr[mid] == target) {
            return mid;
        } else if (arr[start] <= arr[mid]) {
            if (arr[start] <= target && target < arr[mid]) {
                end = mid - 1;
            } else {
                start = mid + 1;
            }
        } else {
            if (arr[end] >= target && target > arr[mid]) {
                start = mid + 1;
            } else {
                end = mid - 1;
            }
        }
    }
    return -1;
}
```

#### Counting the Number of Rotations in a Rotated Sorted Array

```java
public static void main(String[] args) {
    System.out.println(countOfRotation(new int[] { 4, 5, 6, 7, 0, 1, 2 }));
}

private static int countOfRotation(int[] arr) {
    if (arr.length == 0) {
            return -1;
        }
        int start = 0, end = arr.length - 1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (mid > start && arr[mid] < arr[mid - 1]) {
                return mid;
            } else if (mid < end && arr[mid] > arr[mid + 1]) {
                return mid + 1;
            } else if (arr[mid] <= arr[start]) {
                end = mid + 1;
            } else {
                start = mid - 1;
            }
        }
        return -1;
}
```

---

## Bit Manipulations

Bit manipulation is the act of algorithmically manipulating bits or binary digits, which are the most basic form of data in computers.

### Bitwise Operations Table

| Operation | Symbol | Description                         |
|-----------|--------|-------------------------------------|
| AND       | `&`    | Sets each bit to 1 if both bits are 1 |
| OR        | `\|`   | Sets each bit to 1 if one of the bits is 1 |
| NOT       | `~`    | Inverts all the bits                |
| XOR       | `^`    | Sets each bit to 1 if only one of the bits is 1 |
| Left Shift  | `<<`   | Shifts bits to the left             |
| Right Shift | `>>`   | Shifts bits to the right            |

**Example: Bitwise AND Operation**

```java
public class BitwiseAnd {
    public static void main(String[] args) {
        int a = 5;  // 0101 in binary
        int b = 3;  // 0011 in binary
        
        int result = a & b;  // 0001 in binary
        
        System.out.println("Bitwise AND: " + result);  // Output: 1
    }
}
```

### Print Even Numbers Using Bitwise AND

```java
public class PrintEven {
    public static void main(String[] args) {
        printEven(new int[] { 1, 10, 2, 20, 40, 200 });
    }

    private static void printEven(int[] arr) {
        for (int val : arr) {
            if ((val & 1) != 1) {
                System.out.println(val);
            }
        }
    }
}
```

### Print Odd Numbers Using Bitwise AND

```java
public class PrintOdd {
    public static void main(String[] args) {
        printOdd(new int[] { 1, 10, 2, 20, 40, 200 });
    }

    private static void printOdd(int[] arr) {
        for (int val : arr) {
            if ((val & 1) == 1) {
                System.out.println(val);
            }
        }
    }
}
```

### Find Non-Duplicate Element Using XOR

```java
public class FindNonDuplicate {
    public static void main(String[] args) {
        findNonDuplicate(new int[] { 1, 1, 4, 4, 5, 6, 6 });
    }

    private static void findNonDuplicate(int[] arr) {
        // Array contains elements double duplicate only one element is single
        int xor = 0;
        for (int val : arr) {
            xor = xor ^ val;
        }
        System.out.println(xor);
    }
}
```

### Power of a Number Using Bitwise Operators

```java
public class Power {
    public static void main(String[] args) {
        System.out.println(power(2, 2));
    }

    private static int power(int val, int power) {
        int ans = 1;
        int base = val;
        while (power > 0) {
            if ((power & 1) == 1) {
                ans *= base;
            }
            base *= base;
            power >>= 1;
        }
        return ans;
    }
}
```

### Convert Decimal to Binary Using Bitwise Operators

```java
public class DecimalToBinary {
    public static void main(String[] args) {
        System.out.println(decimalToBinary(3));
    }

    private static int decimalToBinary(int n) {
        if (n == 0) {
            return 0;
        }

        int base = 1;
        int ans = 0;
        while (n > 0) {
            int bit = n & 1;
            ans += bit * base;
            base *= 10;
            n >>= 1;
        }

        return ans;
    }
}
```

### Convert Binary to Decimal Using Bitwise Operators

```java
public class BinaryToDecimal {
    public static void main(String[] args) {
        System.out.println(binaryToDecimal(1011));
    }

    private static int binaryToDecimal(long n) {
        if (n == 0) {
            return 0;
        }
        int ans = 0;
        int base = 0;

        while (n > 0) {
            int bit = (int) (n % 10);
            ans += bit << base;
            base++;
            n /= 10;
        }

        return ans;
    }
}
```
---

## String Handling

### String
String is a sequence of characters. Java provides the `String` class to create and manipulate strings.

**Example: String Manipulations**

```java
public class StringManipulations {
    public static void main(String[] args) {
        String str = "Hello, World!";
        
        // Basic methods
        System.out.println(str.length());  // Output: 13
        System.out.println(str.charAt(1));  // Output: e
        System.out.println(str.substring(0, 5));  // Output: Hello
        System.out.println(str.toUpperCase());  // Output: HELLO, WORLD!
        System.out.println(str.toLowerCase());  // Output: hello, world!
        System.out.println(str.replace("World", "Java"));  // Output: Hello, Java!
        
        // Additional methods
        System.out.println(str.contains("World"));  // Output: true
        System.out.println(String.join("-", "Hello", "World"));  // Output: Hello-World
        System.out.println(str.isEmpty());  // Output: false
        System.out.println(str.concat(" Welcome!"));  // Output: Hello, World! Welcome!
        String[] parts = str.split(", ");
        for (String part : parts) {
            System.out.println(part);  // Output: Hello\nWorld!
        }
        System.out.println("   Hello   ".trim());  // Output: Hello
        System.out.println(str.replace('o', 'O'));  // Output: HellO, WOrld!
    }
}
```

### StringBuffer
StringBuffer is a thread-safe, mutable sequence of characters. It is used to create modifiable strings.

**Example: StringBuffer Manipulations**

```java
public class StringBufferExample {
    public static void main(String[] args) {
        StringBuffer sb = new StringBuffer("Hello");
        
        sb.append(", World!");
        System.out.println(sb);  // Output: Hello, World!
        
        sb.insert(5, " Java");
        System.out.println(sb);  // Output: Hello Java, World!
        
        sb.replace(5, 10, "Code");
        System.out.println(sb);  // Output: Hello Code, World!
        
        sb.delete(5, 10);
        System.out.println(sb);  // Output: Hello, World!
        
        sb.reverse();
        System.out.println(sb);  // Output: !dlroW ,olleH
        
        // Additional methods
        System.out.println(sb.capacity());  // Output: Current capacity of StringBuffer
        System.out.println(sb.charAt(0));  // Output: !
        System.out.println(sb.substring(0, 5));  // Output: !dlro
        sb.deleteCharAt(0);
        System.out.println(sb);  // Output: dlroW ,olleH
        System.out.println(sb.toString());  // Output: dlroW ,olleH
    }
}
```

### StringBuilder
StringBuilder is similar to StringBuffer but is not synchronized, making it faster for single-threaded applications.

**Example: StringBuilder Manipulations**

```java
public class StringBuilderExample {
    public static void main(String[] args) {
        StringBuilder sb = new StringBuilder("Hello");
        
        sb.append(", World!");
        System.out.println(sb);  // Output: Hello, World!
        
        sb.insert(5, " Java");
        System.out.println(sb);  // Output: Hello Java, World!
        
        sb.replace(5, 10, "Code");
        System.out.println(sb);  // Output: Hello Code, World!
        
        sb.delete(5, 10);
        System.out.println(sb);  // Output: Hello, World!
        
        sb.reverse();
        System.out.println(sb);  // Output: !dlroW ,olleH
        
        // Additional methods
        System.out.println(sb.capacity());  // Output: Current capacity of StringBuilder
        System.out.println(sb.charAt(0));  // Output: !
        System.out.println(sb.substring(0, 5));  // Output: !dlro
        sb.deleteCharAt(0);
        System.out.println(sb);  // Output: dlroW ,olleH
        System.out.println(sb.toString());  // Output: dlroW ,olleH
    }
}
```

### Reverse a String

```java
public class ReverseString {
    public static void main(String[] args) {
        System.out.println(reverse("Hello"));  // Output: olleH
    }

    private static String reverse(String str) {
        StringBuilder sb = new StringBuilder(str);
        int i = 0, j = str.length() - 1;
        while (i < j) {
            char ch = sb.charAt(i);
            sb.setCharAt(i++, sb.charAt(j));
            sb.setCharAt(j--, ch);
        }
        return sb.toString();
    }
}
```

### Check if a String is Palindrome

```java
public class PalindromeCheck {
    public static void main(String[] args) {
        System.out.println(isPalindrome("Abba"));  // Output: true
    }

    private static boolean isPalindrome(String str) {
        if (str.isEmpty()) {
            return true;
        }
        int i = 0, j = str.length() - 1;
        while (i <= j) {
            if (str.charAt(i++) != str.charAt(j--))
                return false;
        }
        return true;
    }
}
```

### Skip a Specific Character in a String

```java
public class SkipCharacter {
    public static void main(String[] args) {
        System.out.println(skipChar("Rupesh", 'u'));  // Output: Rpesh
    }

    private static String skipChar(String str, char ch) {
        StringBuilder sb = new StringBuilder(str);
        for (int i = 0; i < sb.length(); i++) {
            if (sb.charAt(i) == ch) {
                sb.deleteCharAt(i);
            }
        }
        return sb.toString();
    }
}
```

### Find All Permutations of a String

```java
import java.util.ArrayList;

public class SubStringPermutations {
    public static void main(String[] args) {
        System.out.println(subString("abc", ""));  // Output: [abc, acb, bac, bca, cab, cba]
    }

    private static ArrayList<String> subString(String p, String up) {
        if (p.isEmpty()) {
            ArrayList<String> list = new ArrayList<>();
            list.add(up);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        for (int i = 0; i < p.length(); i++) {
            char curr = p.charAt(i);
            String temp = p.substring(0, i) + p.substring(i + 1);
            list.addAll(subString(temp, up + curr));
        }
        return list;
    }
}
```

### Find All Subsequences of a String

```java
import java.util.ArrayList;

public class Subsequences {
    public static void main(String[] args) {
        System.out.println(subSeq("", "abc"));  // Output: [abc, ab, ac, a, bc, b, c, ]
    }

    private static ArrayList<String> subSeq(String p, String up) {
        if (up.isEmpty()) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        list.addAll(subSeq(p + up.charAt(0), up.substring(1)));
        list.addAll(subSeq(p, up.substring(1)));
        return list;
    }
}
```

### Permutations of Dice

```java
import java.util.ArrayList;

public class DicePermutations {
    public static void main(String[] args) {
        System.out.println(permutationsOfDice("", 5));  // Output: [1,1,1,1,1, 1,1,1,2, 1,1,2,1, ...]
    }

    private static ArrayList<String> permutationsOfDice(String p, int target) {
        if (target == 0) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        for (int i = 1; i <= 6 && i <= target; i++) {
            list.addAll(permutationsOfDice(p + i + (target - i == 0 ? "" : ","), target - i));
        }
        return list;
    }
}
```

### Find All Paths in a Grid

```java
import java.util.ArrayList;

public class GridPaths {
    public static void main(String[] args) {
        System.out.println(allPaths(3, 3, ""));  // Output: [VV, VDR, VRD, DVR, DDRR, ...]
    }

    private static ArrayList<String> allPaths(int row, int col, String p) {
        if (row == 1 && col == 1) {
            ArrayList<String> list = new ArrayList<>();
            list.add(p);
            return list;
        }
        ArrayList<String> list = new ArrayList<>();
        if (row > 1 && col > 1) {
            list.addAll(allPaths(row - 1, col - 1, p + 'V'));
        }
        if (row > 1) {
            list.addAll(allPaths(row - 1, col, p + 'D'));
        }
        if (col > 1) {
            list.addAll(allPaths(row, col - 1, p + 'R'));
        }
        return list;
    }
}
```

### Sorting Techniques

Sorting is a process of arranging the elements in a list or array in a particular order (ascending or descending). Here are implementations of various sorting techniques in Java:

#### Bubble Sort
Bubble Sort is a simple sorting algorithm that repeatedly steps through the list, compares adjacent elements, and swaps them if they are in the wrong order. The pass through the list is repeated until the list is sorted.

**Example: Bubble Sort Implementation**

```java
import java.util.Arrays;

public class BubbleSortExample {
    public static void main(String[] args) {
        int[] arr = { 5, 2, 4, 1, 3 };
        bubbleSort(arr);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void bubbleSort(int[] arr) {
        boolean swapped;
        for (int i = 0; i < arr.length; i++) {
            swapped = false;
            for (int j = 1; j < arr.length - i; j++) {
                if (arr[j - 1] > arr[j]) {
                    int temp = arr[j - 1];
                    arr[j - 1] = arr[j];
                    arr[j] = temp;
                    swapped = true;
                }
            }
            if (!swapped) {
                break;
            }
        }
    }
}
```

#### Selection Sort
Selection Sort is a simple comparison-based algorithm in which the list is divided into two parts: the sorted part at the left end and the unsorted part at the right end. Initially, the sorted part is empty, and the unsorted part is the entire list.

**Example: Selection Sort Implementation**

```java
import java.util.Arrays;

public class SelectionSortExample {
    public static void main(String[] args) {
        int[] arr = { 5, 2, 4, 1, 3 };
        selectionSort(arr);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void selectionSort(int[] arr) {
        for (int i = 0; i < arr.length; i++) {
            int min = i;
            for (int j = i; j < arr.length; j++) {
                if (arr[j] < arr[min]) {
                    min = j;
                }
            }
            int temp = arr[i];
            arr[i] = arr[min];
            arr[min] = temp;
        }
    }
}
```

#### Insertion Sort
Insertion Sort is a simple sorting algorithm that builds the final sorted array one item at a time. It is much less efficient on large lists than more advanced algorithms such as quicksort, heapsort, or merge sort.

**Example: Insertion Sort Implementation**

```java
import java.util.Arrays;

public class InsertionSortExample {
    public static void main(String[] args) {
        int[] arr = { 5, 2, 4, 1, 3 };
        insertionSort(arr);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void insertionSort(int[] arr) {
        for (int i = 1; i < arr.length; i++) {
            for (int j = i; j > 0; j--) {
                if (arr[j] < arr[j - 1]) {
                    int temp = arr[j];
                    arr[j] = arr[j - 1];
                    arr[j - 1] = temp;
                } else {
                    break;
                }
            }
        }
    }
}
```

#### Cyclic Sort
Cyclic Sort is a sorting algorithm that is only applicable when the given array contains elements ranging from 1 to N.

**Example: Cyclic Sort Implementation**

```java
import java.util.Arrays;

public class CyclicSortExample {
    public static void main(String[] args) {
        int[] arr = { 3, 5, 2, 1, 4 };
        cyclicSort(arr);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void cyclicSort(int[] arr) {
        int i = 0;
        while (i < arr.length) {
            int correctIndex = arr[i] - 1;
            if (arr[i] != arr[correctIndex]) {
                int temp = arr[i];
                arr[i] = arr[correctIndex];
                arr[correctIndex] = temp;
            } else {
                i++;
            }
        }
    }
}
```

#### Merge Sort
Merge Sort is an efficient, stable, comparison-based, divide-and-conquer sorting algorithm. Most implementations produce a stable sort, meaning that the implementation preserves the input order of equal elements in the sorted output.

**Example: Merge Sort Implementation**

```java
import java.util.Arrays;

public class MergeSortExample {
    public static void main(String[] args) {
        int[] arr = { 5, 2, 4, 1, 3 };
        mergeSort(arr, 0, arr.length);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void mergeSort(int[] arr, int start, int end) {
        if (end - start <= 1) {
            return;
        }
        int mid = start + (end - start) / 2;
        mergeSort(arr, start, mid);
        mergeSort(arr, mid, end);
        merge(arr, start, mid, end);
    }

    private static void merge(int[] arr, int start, int mid, int end) {
        int[] sorted = new int[end - start];
        int left = start;
        int right = mid;
        int index = 0;

        while (left < mid && right < end) {
            if (arr[left] <= arr[right]) {
                sorted[index++] = arr[left++];
            } else {
                sorted[index++] = arr[right++];
            }
        }

        while (left < mid) {
            sorted[index++] = arr[left++];
        }

        while (right < end) {
            sorted[index++] = arr[right++];
        }

        for (int i = 0; i < sorted.length; i++) {
            arr[start + i] = sorted[i];
        }
    }
}
```

#### Quick Sort
Quick Sort is an efficient, in-place, comparison-based sorting algorithm. It is also known as partition-exchange sort.

**Example: Quick Sort Implementation**

```java
import java.util.Arrays;

public class QuickSortExample {
    public static void main(String[] args) {
        int[] arr = { 5, 2, 4, 1, 3 };
        quickSort(arr, 0, arr.length - 1);
        System.out.println(Arrays.toString(arr));  // Output: [1, 2, 3, 4, 5]
    }

    private static void quickSort(int[] arr, int start, int end) {
        if (start >= end) {
            return;
        }
        int nstart = start, nend = end;
        int pivote = arr[nstart + (nend - nstart) / 2];
        while (nstart <= nend) {
            while (arr[nstart] < pivote) {
                nstart++;
            }
            while (arr[nend] > pivote) {
                nend--;
            }
            if (nstart <= nend) {
                int temp = arr[nstart];
                arr[nstart++] = arr[nend];
                arr[nend--] = temp;
            }
        }
        quickSort(arr, start, nend);
        quickSort(arr, nstart, end);
    }
}
```

Each of these sorting techniques has its own strengths and use cases, and the choice of which one to use depends on the specific requirements of the task at hand.

---

### Object Oriented Programming

### Classes and Objects

### Classes
- A **class** is a blueprint for creating objects and defines a new data type that can be used to instantiate objects.
- It is a logical construct and doesn't occupy space in memory until an object is instantiated from it.

**Example: Defining a Class**
```java
class Box {
    double width;
    double height;
    double depth;
}
```

### Objects
- An **object** is an instance of a class with physical reality, occupying space in memory.
- Objects are characterized by three essential properties: **state**, **identity**, and **behavior**.

**State, Identity, and Behavior:**
- **State**: The values of an object's attributes (e.g., the width, height, and depth of a `Box`).
- **Identity**: Distinguishes one object from another, similar to its memory address.
- **Behavior**: The effect of operations defined by its class (e.g., methods in the `Box` class).

**Example: Creating an Object**
```java
Box myBox;           // Declare reference to an object
myBox = new Box();   // Allocate a Box object
```
- `myBox` is a reference to a `Box` object.
- `new Box()` allocates memory for the object and assigns the reference to `myBox`.

###  Dot Operator
- The dot operator (`.`) links the object with its instance variables or methods, formally a separator in Java.

**Example: Using the Dot Operator**
```java
myBox.width = 10;   // Set the width of myBox to 10
```

## Dynamic Memory Allocation with `new`
- The `new` keyword dynamically allocates memory for an object at runtime.

**Example: Reference Assignment**
```java
Box b1 = new Box();
Box b2 = b1;       // b2 refers to the same Box object as b1
```
- Both `b1` and `b2` refer to the same object. Changes through `b2` affect the object referenced by `b1`.

**Primitive Types vs. Objects:**
- Java’s primitive types (e.g., `int`, `char`) are not implemented as objects but as normal variables for efficiency.

## Constructors
- A **constructor** initializes an object when it is created. The constructor has the same name as the class and no return type.
- Constructors are automatically called when the object is created.

### Types of Constructors

1. **Default Constructor**: No parameters.
   ```java
   class Box {
       double width, height, depth;
       Box() {
           width = 10;
           height = 10;
           depth = 10;
       }
   }
   ```
   **Output**:
   ```java
   Box myBox = new Box();  // width, height, depth initialized to 10
   ```

2. **Parameterized Constructor**: Takes arguments.
   ```java
   class Box {
       double width, height, depth;
       Box(double w, double h, double d) {
           width = w;
           height = h;
           depth = d;
       }
   }
   ```
   **Output**:
   ```java
   Box myBox = new Box(5, 10, 15);  // width=5, height=10, depth=15
   ```

3. **Copy Constructor**: Initializes an object using another object of the same class.
   ```java
   class Box {
       double width, height, depth;
       Box(Box other) {
           this.width = other.width;
           this.height = other.height;
           this.depth = other.depth;
       }
   }
   ```
   **Output**:
   ```java
   Box myBox1 = new Box(5, 10, 15);
   Box myBox2 = new Box(myBox1);  // myBox2 has the same dimensions as myBox1
   ```

## The `this` Keyword
- `this` refers to the current object in a method or constructor and is used to distinguish between instance variables and parameters.

**Example: Using `this`**
```java
class Box {
    double width, height, depth;
    Box(double width, double height, double depth) {
        this.width = width;
        this.height = height;
        this.depth = depth;
    }
}
```

## 6. The `final` Keyword
- The `final` keyword makes a variable constant. Once assigned, it cannot be changed.
- It's common to use all uppercase letters for `final` variables.

**Example: Final Variable**
```java
final int FILE_OPEN = 2;
```
- For reference types, `final` guarantees immutability of the reference, not the object’s contents.

## 7. The `finalize()` Method
- The `finalize()` method is invoked before an object is garbage collected, allowing the object to perform cleanup operations.

**Example: Finalizer Method**
```java
protected void finalize() {
    // finalization code here
}
```

## 8. Parameters and Arguments
- **Parameter**: A variable in the method definition.
- **Argument**: The value passed to the method during the call.

**Example: Method with Parameter**
```java
int square(int i) {
    return i * i;
}
```
**Example Usage:**
```java
int result = square(5);  // Parameter i = 5; result = 25
```

## 9. Inheritance and Constructors in Java
- In Java, a derived class automatically calls the constructor of its base class if the base class constructor has no arguments.

**Example: Base and Derived Class Constructor**
```java
class Base {
    Base() {
        System.out.println("Base Class Constructor Called");
    }
}

class Derived extends Base {
    Derived() {
        System.out.println("Derived Class Constructor Called");
    }
}

public class Main {
    public static void main(String[] args) {
        Derived d = new Derived();
    }
}
```
**Output:**
```
Base Class Constructor Called
Derived Class Constructor Called
```

- If the base class has a parameterized constructor, it must be explicitly called using `super()` in the derived class constructor.

**Example: Parameterized Constructor with `super`**
```java
class Base {
    Base(int x) {
        System.out.println("Base Class Constructor Called with value " + x);
    }
}

class Derived extends Base {
    Derived(int x) {
        super(x); // Explicit call to superclass constructor
        System.out.println("Derived Class Constructor Called with value " + x);
    }
}

public class Main {
    public static void main(String[] args) {
        Derived d = new Derived(10);
    }
}
```
**Output:**
```
Base Class Constructor Called with value 10
Derived Class Constructor Called with value 10
```
---
## 10. Packages in Java

### Introduction to Packages
- **Packages** in Java are containers for classes, helping to keep the class namespace compartmentalized. They ensure that class names do not collide with one another, even if multiple classes have the same name but are stored in different packages.
- A package serves both as a **naming mechanism** and as a **visibility control mechanism**.

### Declaring a Package
- To create a package, use the `package` keyword followed by the package name.
  ```java
  package MyPackage;
  ```
- The package name should correspond to the directory structure in your file system. For example, if you declare a package named `MyPackage`, the corresponding `.class` files should be stored in a directory named `MyPackage`.

### Package Hierarchy
- Java packages can be nested, forming a hierarchy. This hierarchy must be reflected in the file system.
  ```java
  package java.awt.image;
  ```
- The above package should be stored in a directory structure like `java\awt\image` on a Windows system.

### Example of Package Declaration and Usage
- Suppose you have the following class in the package `shapes`:
  ```java
  // File: shapes/Circle.java
  package shapes;

  public class Circle {
      public void draw() {
          System.out.println("Drawing a circle");
      }
  }
  ```
- You can use this class in another file by importing the package:
  ```java
  // File: TestCircle.java
  import shapes.Circle;

  public class TestCircle {
      public static void main(String[] args) {
          Circle c = new Circle();
          c.draw();
      }
  }
  ```
- When compiling, ensure that the directory structure matches the package structure. For instance, `shapes/Circle.java` should be stored in a directory named `shapes`.

### Finding Packages in the Java Run-Time System
The Java run-time system looks for packages using three mechanisms:
1. **Current Working Directory**: By default, Java starts its search in the current working directory. If your package is in a subdirectory of the current directory, it will be found.
2. **CLASSPATH Environmental Variable**: You can set the CLASSPATH environment variable to specify additional directories where Java should search for packages.
3. **-classpath Option**: The `-classpath` option can be used with the `java` and `javac` commands to explicitly specify the path to your classes.

### Access Control in Packages
- When a package is imported, only the items within the package that are declared as `public` will be available to non-subclasses in the importing code.
- For example:
  ```java
  // File: shapes/Square.java
  package shapes;

  class Square {
      void draw() {
          System.out.println("Drawing a square");
      }
  }
  ```
- The `Square` class cannot be accessed outside the `shapes` package because it lacks the `public` modifier.

### Example Usage of Access Control
  ```java
  // File: shapes/Rectangle.java
  package shapes;

  public class Rectangle {
      void draw() {
          System.out.println("Drawing a rectangle");
      }
  }
  ```
  ```java
  // File: TestRectangle.java
  import shapes.Rectangle;

  public class TestRectangle {
      public static void main(String[] args) {
          Rectangle r = new Rectangle();
          r.draw(); // This works because Rectangle is public
      }
  }
  ```

### Summary
- **Packages** organize classes and interfaces into namespaces, prevent name conflicts, and control access.
- **Access Control** is enforced in packages, where only `public` members are accessible to classes outside the package.
- Proper **directory structure** is crucial for packages to be recognized by the Java run-time system.
---
## 11. Understanding Static

### Introduction to Static Members
- **Static members** in Java, such as methods and variables, can be accessed before any objects of the class are created and without reference to any object.
- The most common example of a static member is the `main()` method. It is declared as static because it must be called before any objects exist.

### Static Methods
- A **static method** belongs to the class rather than any particular object of the class.
- **Accessing Static Data**: A static method can only access static data members. It cannot access non-static data members (instance variables) directly.
- **Calling Non-Static Members**: A static method can call only other static methods and cannot call a non-static method directly. However, it can call a non-static method by explicitly specifying an object reference.

### Example: Accessing Non-Static Members in a Static Context
  ```java
  public class Human {

      String message = "Hello World";

      public static void display(Human human) {
          System.out.println(human.message);
      }

      public static void main(String[] args) {
          Human kunal = new Human();
          kunal.message = "Kunal's message";
          Human.display(kunal);
      }
  }
  ```
- In the above example, the static method `display()` is able to access the non-static `message` variable through the `human` object reference.

### Static Methods Characteristics
- **Access**: A static method can be accessed directly by the class name and doesn’t need any object reference.
- **No `this` or `super`**: A static method cannot refer to the `this` or `super` keywords, as it is not associated with any specific instance.

### Static Blocks
- **Static Blocks**: If you need to perform computations to initialize your static variables, you can use a static block. A static block gets executed exactly once, when the class is first loaded.
  ```java
  class UseStatic {
      static int a = 3;
      static int b;

      static {
          System.out.println("Static block initialized.");
          b = a * 4;
      }

      static void meth(int x) {
          System.out.println("x = " + x);
          System.out.println("a = " + a);
          System.out.println("b = " + b);
      }

      public static void main(String args[]) {
          meth(42);
      }
  }
  ```
- **Output**:
  ```
  Static block initialized.
  x = 42
  a = 3
  b = 12
  ```
- In the above example, when the `UseStatic` class is loaded, the static block runs, initializing `b` to `12`. The `main()` method is then called, which in turn calls the static method `meth()`.

### Nested and Static Inner Classes
- **Nested Classes**: Only nested classes can be static.
- **Static Inner Classes**: A static inner class can have static variables, and it behaves like a static member of the outer class.

### Example: Static Inner Class
  ```java
  public class Static {

      static class Test {
          String name;

          public Test(String name) {
              this.name = name;
          }
      }

      public static void main(String[] args) {
          Test a = new Test("Kunal");
          Test b = new Test("Rahul");

          System.out.println(a.name); // Kunal
          System.out.println(b.name); // Rahul
      }
  }
  ```
- In the above example, `Test` is a static inner class. It does not have any instance of its outer class `Static`, and neither does `main`. However, both `main` and `Test` can have instances of each other.

### Static Methods and Inheritance
- **No Overriding**: You cannot override inherited static methods. Method overriding in Java is resolved at runtime based on the type of object, but static methods are class-level methods and are resolved at compile-time.
- **Static Interface Methods**: Static interface methods are not inherited by implementing classes or sub-interfaces. 

### Summary
- **Static Members**: Static methods and variables belong to the class, not to any instance of the class.
- **Access and Restrictions**: Static methods can only access static data, cannot use `this` or `super`, and cannot be overridden.
- **Static Blocks**: Static blocks are used for initializing static variables and are executed when the class is loaded.
- **Static Inner Classes**: Only nested classes can be static, and static inner classes can have static variables.
---

Here’s a revised version of your content for a GitHub README that covers inheritance in Java, including types, examples, and key concepts:

---

## 12. Inheritance in Java

- Inheritance allows a class to use properties and methods of another class. The class that is inherited is called the superclass, and the class that inherits is called the subclass.
    - The `extends` keyword is used to inherit a class.
    
    ```java
    class Subclass extends Superclass {
        // body of class
    }
    ```
    - You can only specify one superclass for any subclass that you create. Java does not support the inheritance of multiple super classes into a single subclass. However, you can create a hierarchy of inheritance in which a subclass becomes a superclass of another subclass.
    - Although a subclass includes all of the members of its superclass, it cannot access those members of the superclass that have been declared as `private`.

## **Types of Inheritance** -


- **Single Inheritance:**  
  Involves a subclass inheriting from a single superclass.

  **Example:**
  ```java
  class A {
      void show() {
          System.out.println("Inside class A");
      }
  }

  class B extends A {
      void display() {
          System.out.println("Inside class B");
      }
  }
  ```

  **Explanation:** Class `B` inherits from class `A`, demonstrating single inheritance.

- **Multilevel Inheritance:**  
  A class is derived from a class that is already derived from another class.

  **Example:**
  ```java
  class A {
      void show() {
          System.out.println("Inside class A");
      }
  }

  class B extends A {
      void display() {
          System.out.println("Inside class B");
      }
  }

  class C extends B {
      void print() {
          System.out.println("Inside class C");
      }
  }
  ```

  **Explanation:** Class `C` inherits from class `B`, which in turn inherits from class `A`, forming a chain.

- **Hierarchical Inheritance:**  
  Multiple classes inherit from a single superclass.

  **Example:**
  ```java
  class A {
      void show() {
          System.out.println("Inside class A");
      }
  }

  class B extends A {
      void display() {
          System.out.println("Inside class B");
      }
  }

  class C extends A {
      void print() {
          System.out.println("Inside class C");
      }
  }
  ```

  **Explanation:** Both class `B` and class `C` inherit from the same superclass `A`.

- **Multiple Inheritance (Not Supported in Java):**  
  Java does not support multiple inheritance through classes to avoid the **diamond problem**. However, multiple inheritance can be achieved through interfaces.

  **Example:**
  ```java
  class A {
      void show() {
          System.out.println("Inside class A");
      }
  }

  class B {
      void show() {
          System.out.println("Inside class B");
      }
  }

  // class C extends A, B { // Error! Java does not support multiple inheritance.
  // }
  ```

  **Explanation:** Class `C` attempts to inherit from both `A` and `B`, which is not allowed in Java.

- **Hybrid Inheritance (Not Supported in Java):**  
  A combination of two or more types of inheritance. Java does not support hybrid inheritance through classes but allows it through interfaces.

  **Example:**
  ```java
  class A {
      void show() {
          System.out.println("Inside class A");
      }
  }

  class B extends A {
      void display() {
          System.out.println("Inside class B");
      }
  }

  interface C {
      void print();
  }

  // class D extends B implements C { // Error! Java does not support hybrid inheritance through classes.
  // }
  ```

  **Explanation:** Class `D` would attempt to inherit from both class `B` and interface `C`, leading to a hybrid inheritance situation that is not allowed in Java.

## 13. Superclass Reference to Subclass Object

A superclass reference variable can reference a subclass object. However, it will only have access to the members defined in the superclass.

```java
Superclass ref = new Subclass(); // ref can only access methods defined in SUPERCLASS
```

## 14. Using `super`

The keyword `super` refers to the immediate superclass. It can be used in two forms:

1. **Calling the Superclass Constructor:**  
   ```java
   class BoxWeight extends Box {
       double weight;
       
       BoxWeight(double w, double h, double d, double m) {
           super(w, h, d); // call superclass constructor
           weight = m;
       }
   }
   ```
   **Explanation:** Calls the superclass constructor to initialize values inherited from the superclass.

2. **Accessing Superclass Members:**  
   ```java
   super.member;
   ```

## 15. Using `final` with Inheritance

The `final` keyword can be used in three ways:

1. **Creating Constants:**
   ```java
   final int MAX = 100;
   ```

2. **Preventing Method Overriding:**
   ```java
   class A {
       final void method() {
           // method body
       }
   }
   ```

3. **Preventing Inheritance:**
   ```java
   final class FinalClass {
       // class body
   }
   ```

## 16. Polymorphism Does Not Apply to Instance Variables

Polymorphism does not apply to instance variables; they are hidden rather than overridden.

```java
class A {
    int x = 10;
}

class B extends A {
    int x = 20;
}

class Test {
    public static void main(String[] args) {
        A a = new B();
        System.out.println(a.x); // prints 10
    }
}
```

## 17. Overloading Methods

In Java, methods can be overloaded, meaning multiple methods with the same name can exist if their parameter lists differ.

```java
class OverloadDemo {
    void test(double a) {
        System.out.println("Inside test(double) a: " + a);
    }
}
```

## 18. Returning Objects

Methods in Java can return objects.

```java
class Test {
    int a;
    Test(int i) {
        a = i;
    }
    Test incrByTen() {
        Test temp = new Test(a + 10);
        return temp;
    }
}

class RetOb {
    public static void main(String[] args) {
        Test ob1 = new Test(2);
        Test ob2;
        ob2 = ob1.incrByTen();
        System.out.println("ob1.a: " + ob1.a); // prints 2
        System.out.println("ob2.a: " + ob2.a); // prints 12
    }
}
```

## 19. Note on Unsupported Types

- **Multiple Inheritance:** Java does not support multiple inheritance through classes, but it can be achieved through interfaces.

  ```java
  interface A {
      void methodA();
  }

  interface B {
      void methodB();
  }

  class C implements A, B {
      public void methodA() {
          // implementation
      }

      public void methodB() {
          // implementation
      }
  }
  ```

---

This README file provides a comprehensive guide to the content of your DSA repository, including examples and detailed explanations.
