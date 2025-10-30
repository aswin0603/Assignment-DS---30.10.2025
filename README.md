# Attendance Activity - DS - 30-Oct-2025
<hr>

### 1.  You are implementing a RecentCounter class that counts the number of recent calls within a sliding window of 3000 milliseconds. Each time you receive a new ping(t) at time t, you need to return the number of calls that occurred in the inclusive range [t - 3000, t]. Calls are guaranteed to be strictly increasing in time.
### Code :
```java
import java.util.*;

public class RecentCounter {
    private Queue<Integer> q;

    public RecentCounter() {
        q = new LinkedList<>();
    }

    public int ping(int t) {
        q.add(t);
        while (q.peek() < t - 3000) {
            q.poll();
        }
        return q.size();
    }

    public static void main(String[] args) {
        RecentCounter rc = new RecentCounter();

        System.out.println(rc.ping(1));
        System.out.println(rc.ping(100));
    }
}
```
<img width="684" height="141" alt="image" src="https://github.com/user-attachments/assets/a393d02f-f0e3-44d1-9870-01f99e5c26b0" />

### 2. Design a program that: Takes a string input representing a message. Removes all non-alphanumeric characters (e.g., commas, spaces, symbols). Converts all characters to lowercase. Uses a deque to check whether the cleaned string is a palindrome.
### Code :
```java
import java.util.*;

public class PalindromeChecker {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        System.out.print("Enter a message: ");
        String input = sc.nextLine();

        String cleaned = input.replaceAll("[^a-zA-Z0-9]", "").toLowerCase();
        Deque<Character> deque = new LinkedList<>();
        for (char c : cleaned.toCharArray()) deque.addLast(c);

        boolean isPalindrome = true;
        while (deque.size() > 1) {
            if (deque.removeFirst() != deque.removeLast()) {
                isPalindrome = false;
                break;
            }
        }

        System.out.println(isPalindrome ? "It is a palindrome." : "It is NOT a palindrome.");
        sc.close();
    }
}
```
<img width="682" height="144" alt="image" src="https://github.com/user-attachments/assets/299e183c-1b46-4d34-8f98-e764e886ca2f" />

### 3. In a smart home, each appliance sends power consumption readings to the central controller every minute. The system must detect power surges — defined as a time window of 5 minutes (i.e., 5 readings) where all readings are above a threshold value (say 1000W). If such a surge is detected, an alert must be triggered. Your task is to implement a monitoring system using a deque that: Continuously stores the last 5 readings. Checks after each new reading if all 5 readings in the deque are > threshold.  If so, prints "⚠️ Power Surge Detected". Otherwise, prints "✅ Normal".
### Code:
```java
import java.util.*;

public class PowerMonitor {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Deque<Integer> readings = new LinkedList<>();
        final int THRESHOLD = 1000;
        final int WINDOW_SIZE = 5;

        while (true) {
            System.out.print("Enter power reading (W): ");
            int reading = sc.nextInt();

            readings.addLast(reading);
            if (readings.size() > WINDOW_SIZE) readings.removeFirst();

            if (readings.size() == WINDOW_SIZE && readings.stream().allMatch(r -> r > THRESHOLD))
                System.out.println("Power Surge Detected");
            else
                System.out.println("Normal");
        }
    }
}
```
<img width="678" height="604" alt="image" src="https://github.com/user-attachments/assets/c4d462a0-027e-487e-b806-2a7304a1ecf1" />

### 4. You are given a Java program that defines a queue data structure using a singly linked list. The implementation involves two classes:
#### Node class: Represents a single element in the queue with two fields:
#### data: stores the integer value
#### next: points to the next node
#### Queue class: Provides methods to perform the following operations:
#### enqueue(int new_data): To perform insertion of a new element at the rear of the queue.
#### dequeue(): To perform deletion of the front element from the queue.
#### isEmpty(): To check if the queue is empty.
#### printQueue(): To display the current elements of the queue after every enqueue or dequeue operation.
### Code:
```java
import java.util.*;

public class PowerMonitor {
    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);
        Deque<Integer> readings = new LinkedList<>();
        final int THRESHOLD = 1000;
        final int WINDOW_SIZE = 5;

        while (true) {
            System.out.print("Enter power reading (W): ");
            int reading = sc.nextInt();

            readings.addLast(reading);
            if (readings.size() > WINDOW_SIZE) readings.removeFirst();

            if (readings.size() == WINDOW_SIZE && readings.stream().allMatch(r -> r > THRESHOLD))
                System.out.println("Power Surge Detected");
            else
                System.out.println("Normal");
        }
    }
}
```
