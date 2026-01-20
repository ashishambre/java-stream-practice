# Java Stream API & Collectors - Practice Questions
## Interview Preparation Guide

---

## Table of Contents
1. [Part 1: Collectors Problems (20 Questions)](#part-1-collectors-problems)
2. [Part 2: Basic Stream Operations (10 Questions)](#part-2-basic-stream-operations)
3. [Part 3: flatMap & Advanced Operations (10 Questions)](#part-3-flatmap--advanced-operations)
4. [Part 4: Additional Interview Questions (10 Questions)](#part-4-additional-interview-questions)

---

# Part 1: Collectors Problems

## Basic Collectors (1-10)

### Problem 1: Employee Salary Grouping
**Description:** Group employees by salary range (<50k, 50k-100k, >100k)

```java
class Employee {
    String name;
    int salary;
    
    public Employee(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }
    
    public String getName() { return name; }
    public int getSalary() { return salary; }
}

public class Problem1 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", 45000),
            new Employee("Alice", 75000),
            new Employee("Bob", 120000),
            new Employee("Charlie", 55000)
        );
        
        // TODO: Group by salary range (LOW<50k, MEDIUM 50k-100k, HIGH>100k)
        // Expected: {LOW=[John], MEDIUM=[Alice, Charlie], HIGH=[Bob]}
    }
}
```

---

### Problem 2: Top 3 Most Frequent Words
**Description:** Find the top 3 most occurring words with their counts

```java
public class Problem2 {
    public static void main(String[] args) {
        String text = "java is great java is powerful java streams are great";
        
        // TODO: Find top 3 most frequent words with counts
        // Expected: {java=3, is=2, great=2}
    }
}
```

---

### Problem 3: Student Grade Statistics
**Description:** Calculate average, min, max grades for each subject

```java
class Result {
    String subject;
    int marks;
    
    public Result(String subject, int marks) {
        this.subject = subject;
        this.marks = marks;
    }
    
    public String getSubject() { return subject; }
    public int getMarks() { return marks; }
}

public class Problem3 {
    public static void main(String[] args) {
        List<Result> results = Arrays.asList(
            new Result("Math", 85),
            new Result("Math", 90),
            new Result("Science", 75),
            new Result("Science", 80)
        );
        
        // TODO: Get IntSummaryStatistics for each subject
        // Expected: {Math=IntSummaryStatistics{count=2, sum=175, min=85, avg=87.5, max=90}, ...}
    }
}
```

---

### Problem 4: Partition Products by Availability
**Description:** Partition products into available/out-of-stock and count each

```java
class Product {
    String name;
    boolean inStock;
    
    public Product(String name, boolean inStock) {
        this.name = name;
        this.inStock = inStock;
    }
    
    public String getName() { return name; }
    public boolean isInStock() { return inStock; }
}

public class Problem4 {
    public static void main(String[] args) {
        List<Product> products = Arrays.asList(
            new Product("Laptop", true),
            new Product("Mouse", false),
            new Product("Keyboard", true)
        );
        
        // TODO: Partition by availability and count each partition
        // Expected: {true=2, false=1}
    }
}
```

---

### Problem 5: Create Name to Email Map
**Description:** Convert list to Map<String, String> (name → email), keep first for duplicates

```java
class User {
    String name;
    String email;
    
    public User(String name, String email) {
        this.name = name;
        this.email = email;
    }
    
    public String getName() { return name; }
    public String getEmail() { return email; }
}

public class Problem5 {
    public static void main(String[] args) {
        List<User> users = Arrays.asList(
            new User("John", "john@example.com"),
            new User("Alice", "alice@example.com"),
            new User("John", "john2@example.com")
        );
        
        // TODO: Create map name->email, keep first occurrence for duplicates
        // Expected: {John=john@example.com, Alice=alice@example.com}
    }
}
```

---

### Problem 6: Department-wise Employee Names
**Description:** Group by department and join names with comma

```java
class Employee {
    String name;
    String department;
    
    public Employee(String name, String department) {
        this.name = name;
        this.department = department;
    }
    
    public String getName() { return name; }
    public String getDepartment() { return department; }
}

public class Problem6 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", "IT"),
            new Employee("Alice", "HR"),
            new Employee("Bob", "IT")
        );
        
        // TODO: Group by department and join names with comma
        // Expected: {IT=John,Bob, HR=Alice}
    }
}
```

---

### Problem 7: Group Numbers by Even/Odd and Sum
**Description:** Partition into even/odd and sum each group

```java
public class Problem7 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // TODO: Partition by even/odd and sum each group
        // Expected: {false=25, true=30}  // false=odd, true=even
    }
}
```

---

### Problem 8: Character Frequency Map
**Description:** Count frequency (case-insensitive, ignore spaces)

```java
public class Problem8 {
    public static void main(String[] args) {
        String input = "Hello World";
        
        // TODO: Count character frequency (case-insensitive, no spaces)
        // Expected: {h=1, e=1, l=3, o=2, w=1, r=1, d=1}
    }
}
```

---

### Problem 9: Group and Count by First Letter
**Description:** Group names by first letter and count

```java
public class Problem9 {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Anna", "Brian", "Charlie", "Alex");
        
        // TODO: Group by first letter and count
        // Expected: {A=3, B=2, C=1}
    }
}
```

---

### Problem 10: Age-wise Student List (Sorted)
**Description:** Group by age using TreeMap, collect names

```java
class Student {
    String name;
    int age;
    
    public Student(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public String getName() { return name; }
    public int getAge() { return age; }
}

public class Problem10 {
    public static void main(String[] args) {
        List<Student> students = Arrays.asList(
            new Student("John", 20),
            new Student("Alice", 22),
            new Student("Bob", 20),
            new Student("Charlie", 22)
        );
        
        // TODO: Group by age (use TreeMap for sorting) and collect names
        // Expected: TreeMap {20=[John, Bob], 22=[Alice, Charlie]}
    }
}
```

---

## Advanced Collectors (11-20)

### Problem 11: Longest Word in Each Length Group
**Description:** Group by length, find longest word lexicographically

```java
public class Problem11 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "ant", "banana", "bat", "cherry", "cat");
        
        // TODO: Group by length and find max word alphabetically in each group
        // Expected: {3=cat, 5=apple, 6=cherry}
    }
}
```

---

### Problem 12: Student Grade Distribution
**Description:** Partition into pass/fail (>=50), collect names

```java
class Student {
    String name;
    int marks;
    
    public Student(String name, int marks) {
        this.name = name;
        this.marks = marks;
    }
    
    public String getName() { return name; }
    public int getMarks() { return marks; }
}

public class Problem12 {
    public static void main(String[] args) {
        List<Student> students = Arrays.asList(
            new Student("Alice", 85),
            new Student("Bob", 45),
            new Student("Charlie", 60),
            new Student("David", 30)
        );
        
        // TODO: Partition by pass(>=50)/fail and collect names
        // Expected: {true=[Alice, Charlie], false=[Bob, David]}
    }
}
```

---

### Problem 13: Group by Multiple Criteria
**Description:** Group by "Department-Experience" (Junior<3, Senior>=3)

```java
class Employee {
    String name;
    String department;
    int yearsOfExperience;
    
    public Employee(String name, String department, int years) {
        this.name = name;
        this.department = department;
        this.yearsOfExperience = years;
    }
    
    public String getName() { return name; }
    public String getDepartment() { return department; }
    public int getYearsOfExperience() { return yearsOfExperience; }
}

public class Problem13 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", "IT", 5),
            new Employee("Alice", "HR", 2),
            new Employee("Bob", "IT", 1),
            new Employee("Charlie", "HR", 4)
        );
        
        // TODO: Group by "Department-Level" (e.g., "IT-Senior", "HR-Junior")
        // Expected: {IT-Senior=[John], IT-Junior=[Bob], HR-Senior=[Charlie], HR-Junior=[Alice]}
    }
}
```

---

### Problem 14: Join with Brackets
**Description:** Group by first letter, join with comma and brackets

```java
public class Problem14 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "ant", "banana", "ball", "cherry");
        
        // TODO: Group by first letter and join with brackets
        // Expected: {a=[apple, ant], b=[banana, ball], c=[cherry]}
    }
}
```

---

### Problem 15: Nested Grouping
**Description:** Group by length, then by first character

```java
public class Problem15 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "ant", "app", "banana", "bat", "ball");
        
        // TODO: Group by length, then within each length by first character
        // Expected: {3={a=[ant, app], b=[bat]}, 4={b=[ball]}, 5={a=[apple]}, 6={b=[banana]}}
    }
}
```

---

### Problem 16: Average Salary by Department
**Description:** Calculate average salary per department

```java
class Employee {
    String name;
    String department;
    double salary;
    
    public Employee(String name, String department, double salary) {
        this.name = name;
        this.department = department;
        this.salary = salary;
    }
    
    public String getName() { return name; }
    public String getDepartment() { return department; }
    public double getSalary() { return salary; }
}

public class Problem16 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", "IT", 75000),
            new Employee("Alice", "IT", 85000),
            new Employee("Bob", "HR", 60000),
            new Employee("Charlie", "HR", 65000)
        );
        
        // TODO: Calculate average salary per department
        // Expected: {IT=80000.0, HR=62500.0}
    }
}
```

---

### Problem 17: Group by Price Range
**Description:** Group products by price range and count

```java
class Product {
    String name;
    double price;
    
    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
    
    public String getName() { return name; }
    public double getPrice() { return price; }
}

public class Problem17 {
    public static void main(String[] args) {
        List<Product> products = Arrays.asList(
            new Product("Mouse", 25.0),
            new Product("Keyboard", 75.0),
            new Product("Monitor", 300.0),
            new Product("Laptop", 1200.0),
            new Product("Cable", 15.0)
        );
        
        // TODO: Group by price range (LOW<100, MEDIUM 100-500, HIGH>500) and count
        // Expected: {LOW=2, MEDIUM=2, HIGH=1}
    }
}
```

---

### Problem 18: Employee ID to Name Map
**Description:** Create map with duplicate ID handling

```java
class Employee {
    int id;
    String name;
    
    public Employee(int id, String name) {
        this.id = id;
        this.name = name;
    }
    
    public int getId() { return id; }
    public String getName() { return name; }
}

public class Problem18 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee(1, "John"),
            new Employee(2, "Alice"),
            new Employee(1, "Bob"),
            new Employee(3, "Charlie")
        );
        
        // TODO: Create map id->name, merge duplicates with " & "
        // Expected: {1=John & Bob, 2=Alice, 3=Charlie}
    }
}
```

---

### Problem 19: Partition and Sum Prices
**Description:** Partition by expensive (>=100) and sum each

```java
class Product {
    String name;
    double price;
    
    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
    
    public String getName() { return name; }
    public double getPrice() { return price; }
}

public class Problem19 {
    public static void main(String[] args) {
        List<Product> products = Arrays.asList(
            new Product("Mouse", 25.0),
            new Product("Keyboard", 75.0),
            new Product("Monitor", 300.0),
            new Product("Laptop", 1200.0)
        );
        
        // TODO: Partition by expensive (>=100) and sum prices in each partition
        // Expected: {false=100.0, true=1500.0}
    }
}
```

---

### Problem 20: Salary Statistics by Department
**Description:** Get DoubleSummaryStatistics per department

```java
class Employee {
    String name;
    String department;
    double salary;
    
    public Employee(String name, String department, double salary) {
        this.name = name;
        this.department = department;
        this.salary = salary;
    }
    
    public String getName() { return name; }
    public String getDepartment() { return department; }
    public double getSalary() { return salary; }
}

public class Problem20 {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("John", "IT", 75000),
            new Employee("Alice", "IT", 85000),
            new Employee("Bob", "HR", 60000),
            new Employee("Charlie", "HR", 65000),
            new Employee("David", "IT", 90000)
        );
        
        // TODO: Group by department and get salary statistics
        // Expected: {IT=DoubleSummaryStatistics{count=3, sum=250000, min=75000, avg=83333.33, max=90000}, ...}
    }
}
```

---

# Part 2: Basic Stream Operations

### Problem 21: Find Sum of All Elements
**Description:** Calculate sum using Stream API

```java
public class Problem21 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        
        // TODO: Find sum of all elements
        // Expected: 15
    }
}
```

---

### Problem 22: Filter Even Numbers
**Description:** Get all even numbers from list

```java
public class Problem22 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // TODO: Filter and collect even numbers
        // Expected: [2, 4, 6, 8, 10]
    }
}
```

---

### Problem 23: Convert Strings to Uppercase
**Description:** Transform all strings to uppercase

```java
public class Problem23 {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("alice", "bob", "charlie");
        
        // TODO: Convert all names to uppercase
        // Expected: [ALICE, BOB, CHARLIE]
    }
}
```

---

### Problem 24: Find Maximum Element
**Description:** Find the largest number

```java
public class Problem24 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 5, 8, 20, 15);
        
        // TODO: Find maximum element
        // Expected: 20
    }
}
```

---

### Problem 25: Find Minimum Element
**Description:** Find the smallest number

```java
public class Problem25 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 5, 8, 20, 15);
        
        // TODO: Find minimum element
        // Expected: 5
    }
}
```

---

### Problem 26: Remove Duplicates
**Description:** Get unique elements from list

```java
public class Problem26 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5, 5, 6);
        
        // TODO: Remove duplicates and collect
        // Expected: [1, 2, 3, 4, 5, 6]
    }
}
```

---

### Problem 27: Skip First N Elements
**Description:** Skip first 3 elements

```java
public class Problem27 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // TODO: Skip first 3 elements
        // Expected: [4, 5, 6, 7, 8, 9, 10]
    }
}
```

---

### Problem 28: Limit to First N Elements
**Description:** Get only first 5 elements

```java
public class Problem28 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // TODO: Limit to first 5 elements
        // Expected: [1, 2, 3, 4, 5]
    }
}
```

---

### Problem 29: Sort in Descending Order
**Description:** Sort numbers from high to low

```java
public class Problem29 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9, 3);
        
        // TODO: Sort in descending order
        // Expected: [9, 8, 5, 3, 2, 1]
    }
}
```

---

### Problem 30: Find Second Highest Number
**Description:** Get the second largest number

```java
public class Problem30 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 5, 8, 20, 15, 20);
        
        // TODO: Find second highest number (handle duplicates)
        // Expected: 15
    }
}
```

---

# Part 3: flatMap & Advanced Operations

### Problem 31: Flatten List of Lists
**Description:** Convert nested list to flat list

```java
public class Problem31 {
    public static void main(String[] args) {
        List<List<Integer>> listOfLists = Arrays.asList(
            Arrays.asList(1, 2, 3),
            Arrays.asList(4, 5, 6),
            Arrays.asList(7, 8, 9)
        );
        
        // TODO: Flatten into single list
        // Expected: [1, 2, 3, 4, 5, 6, 7, 8, 9]
    }
}
```

---

### Problem 32: Split Sentences into Words
**Description:** Break sentences into individual words

```java
public class Problem32 {
    public static void main(String[] args) {
        List<String> sentences = Arrays.asList(
            "Java Stream API",
            "is very powerful",
            "for data processing"
        );
        
        // TODO: Split into individual words
        // Expected: [Java, Stream, API, is, very, powerful, for, data, processing]
    }
}
```

---

### Problem 33: Flatten and Filter Even Numbers
**Description:** Flatten nested lists and keep only even numbers

```java
public class Problem33 {
    public static void main(String[] args) {
        List<List<Integer>> listOfLists = Arrays.asList(
            Arrays.asList(1, 2, 3),
            Arrays.asList(4, 5, 6),
            Arrays.asList(7, 8, 9)
        );
        
        // TODO: Flatten and filter even numbers
        // Expected: [2, 4, 6, 8]
    }
}
```

---

### Problem 34: Get Unique Characters
**Description:** Extract all unique characters from strings

```java
public class Problem34 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("hello", "world", "java");
        
        // TODO: Get all unique characters (maintain order)
        // Expected: [h, e, l, o, w, r, d, j, a, v]
    }
}
```

---

### Problem 35: Cartesian Product
**Description:** Generate all combinations of two lists

```java
public class Problem35 {
    public static void main(String[] args) {
        List<Integer> list1 = Arrays.asList(1, 2, 3);
        List<Integer> list2 = Arrays.asList(4, 5);
        
        // TODO: Generate cartesian product
        // Expected: [(1,4), (1,5), (2,4), (2,5), (3,4), (3,5)]
    }
}
```

---

### Problem 36: Find Anagrams
**Description:** Find all anagrams of target word

```java
public class Problem36 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("listen", "silent", "enlist", "google", "inlets");
        String target = "silent";
        
        // TODO: Find all anagrams of "silent"
        // Expected: [listen, silent, enlist, inlets]
    }
}
```

---

### Problem 37: Find Palindromes
**Description:** Filter palindrome strings

```java
public class Problem37 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("madam", "racecar", "apple", "banana", "level");
        
        // TODO: Find all palindromes
        // Expected: [madam, racecar, level]
    }
}
```

---

### Problem 38: Generate Fibonacci Numbers
**Description:** Generate first N Fibonacci numbers

```java
public class Problem38 {
    public static void main(String[] args) {
        // TODO: Generate first 10 Fibonacci numbers using Stream
        // Expected: [0, 1, 1, 2, 3, 5, 8, 13, 21, 34]
    }
}
```

---

### Problem 39: Find Pairs that Sum to Target
**Description:** Find all pairs that add up to target sum

```java
public class Problem39 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        int targetSum = 6;
        
        // TODO: Find all pairs that sum to 6
        // Expected: [[1, 5], [2, 4]]
    }
}
```

---

### Problem 40: Product of All Elements
**Description:** Calculate product using reduce

```java
public class Problem40 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        
        // TODO: Find product of all elements using reduce
        // Expected: 120
    }
}
```

---

# Part 4: Additional Interview Questions

### Problem 41: Find Duplicates in List
**Description:** Identify duplicate elements

```java
public class Problem41 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 2, 5, 1, 6, 3);
        
        // TODO: Find all duplicate elements
        // Expected: [1, 2, 3]
    }
}
```

---

### Problem 42: Find First Non-Repeated Character
**Description:** Find first character that appears only once

```java
public class Problem42 {
    public static void main(String[] args) {
        String input = "stress";
        
        // TODO: Find first non-repeated character
        // Expected: t
    }
}
```

---

### Problem 43: Sum of Squares of Even Numbers
**Description:** Filter even, square them, then sum

```java
public class Problem43 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
        
        // TODO: Sum of squares of even numbers
        // Expected: 56  // (2² + 4² + 6² = 4 + 16 + 36)
    }
}
```

---

### Problem 44: Merge Two Lists Alternately
**Description:** Combine two lists in alternating fashion

```java
public class Problem44 {
    public static void main(String[] args) {
        List<String> list1 = Arrays.asList("a", "b", "c");
        List<String> list2 = Arrays.asList("1", "2", "3");
        
        // TODO: Merge alternately
        // Expected: [a, 1, b, 2, c, 3]
    }
}
```

---

### Problem 45: Partition Strings by Length
**Description:** Split strings into groups by length threshold

```java
public class Problem45 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "cat", "banana", "dog", "elephant", "at");
        
        // TODO: Partition by length > 3
        // Expected: {true=[apple, banana, elephant], false=[cat, dog, at]}
    }
}
```

---

### Problem 46: Calculate Average of Top N Numbers
**Description:** Find average of top 3 numbers

```java
public class Problem46 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 5, 8, 20, 15, 3, 7);
        
        // TODO: Calculate average of top 3 numbers
        // Expected: 15.0  // (20 + 15 + 10) / 3
    }
}
```

---

### Problem 47: Count Words in Sentences
**Description:** Count total words across all sentences

```java
public class Problem47 {
    public static void main(String[] args) {
        List<String> sentences = Arrays.asList(
            "Hello world",
            "Java streams are powerful",
            "Practice makes perfect"
        );
        
        // TODO: Count total number of words
        // Expected: 8
    }
}
```

---

### Problem 48: Find Longest String
**Description:** Get the longest string from list

```java
public class Problem48 {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "kiwi", "watermelon", "grape");
        
        // TODO: Find longest string
        // Expected: watermelon
    }
}
```

---

### Problem 49: Check if All Elements Match Condition
**Description:** Verify all numbers are positive

```java
public class Problem49 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
        
        // TODO: Check if all numbers are positive
        // Expected: true
    }
}
```

---

### Problem 50: Check if Any Element Matches Condition
**Description:** Check if list contains any negative number

```java
public class Problem50 {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, -3, 4, 5);
        
        // TODO: Check if any number is negative
        // Expected: true
    }
}
```

---

## Tips for Solving These Problems

### Collectors Cheat Sheet:
- **groupingBy()** - Group elements by a classifier function
- **partitioningBy()** - Split into two groups (true/false)
- **toMap()** - Convert to Map with key and value extractors
- **joining()** - Concatenate strings with delimiter
- **counting()** - Count elements
- **summingInt/Double()** - Sum numeric values
- **averagingInt/Double()** - Calculate average
- **summarizingInt/Double()** - Get statistics (count, sum, min, avg, max)
- **mapping()** - Transform elements before collecting
- **collectingAndThen()** - Transform the final result

### Stream Operations Cheat Sheet:
- **filter()** - Select elements based on condition
- **map()** - Transform each element
- **flatMap()** - Flatten nested structures
- **distinct()** - Remove duplicates
- **sorted()** - Order elements
- **limit(n)** - Take first n elements
- **skip(n)** - Skip first n elements
- **reduce()** - Combine all elements into single result
- **forEach()** - Perform action on each element
- **collect()** - Convert stream to collection
- **anyMatch()** - Check if any element matches
- **allMatch()** - Check if all elements match
- **noneMatch()** - Check if no elements match
- **findFirst()** - Get first element
- **findAny()** - Get any element
- **count()** - Count elements
- **min()/max()** - Find minimum/maximum

### Common Patterns:
1. **Grouping with transformation**: `groupingBy(classifier, mapping(transform, toList()))`
2. **Counting by category**: `groupingBy(classifier, counting())`
3. **Flattening nested lists**: `flatMap(List::stream)`
4. **Finding duplicates**: Use Set to track seen elements
5. **Top N elements**: `sorted().limit(n)`
6. **Removing nulls**: `filter(Objects::nonNull)`

---

## Practice Strategy:
1. Start with Basic Collectors (Problems 1-10)
2. Move to Advanced Collectors (Problems 11-20)
3. Practice Basic Stream Operations (Problems 21-30)
4. Master flatMap and Advanced Operations (Problems 31-40)
5. Complete Additional Interview Questions (Problems 41-50)

Good luck with your interview preparation! 🚀
