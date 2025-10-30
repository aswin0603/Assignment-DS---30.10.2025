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
<img width="690" height="124" alt="image" src="https://github.com/user-attachments/assets/186c7fab-8da7-4d2f-a5ef-90e0d8d3a826" />
