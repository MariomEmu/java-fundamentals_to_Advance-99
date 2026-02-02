# JRE – Java Runtime Environment

---

## 🔹 What is JRE?

**JRE (Java Runtime Environment)** is the environment that allows Java programs to **run**.

It does not create or compile Java programs.  
It only **runs** compiled `.class` files.

> 👉 **JRE = JVM + Java Libraries + Runtime Support Files**

---

## 🔹 Why do we use JRE?

Because:

- Computer does not understand Java bytecode  
- JVM needs libraries and runtime support to execute code  
- JRE provides everything required to **run Java programs**
- Platform Independence - "Write Once, Run Anywhere"
This is Java's superpower! You write a Java program once, and it runs on:
 Windows ✓, Mac ✓, Linux ✓
 Without changing the code!

- Automatic Memory Management
   ##### JRE handles garbage collection automatically
  #### Creates memory for your program
  #### Cleans up unused memo

Without JRE:
- `.class` file cannot run ❌  
- JVM alone is not enough  

---

## 🔹 What is inside JRE?

| Component | Purpose |
|-----------|---------|
| **JVM** | Executes bytecode |
| **Java Libraries** | String, List, System, IO, etc. |
| **Runtime Files** | Native OS files, security, config |

---

## 🔹 How does JRE work?

### Flow

```text
Java Source (.java)
        ↓ javac
Bytecode (.class)
        ↓
       JRE
        ↓
       JVM
        ↓
Class Loader → Verifier → Interpreter / JIT
        ↓
      Output
```
## 🔹 Internal Steps of flow

1. **Class Loader**  
   Loads `.class` file into memory

2. **Bytecode Verifier**  
   Checks security and correctness

3. **Interpreter**  
   Executes bytecode line by line

4. **JIT Compiler**  
   Converts bytecode to machine code for faster execution

5. **Execution**  
   CPU runs the program
```

```
## ❓ How JRE Creates Environment?
  
এটা JVM-কে চারপাশের সব ব্যবস্থা দিয়ে দেয়, যেন Java প্রোগ্রাম চালাতে পারে।  

JRE মূলত environment তৈরি করে **৪টি প্রধান উপায়ে**:

---

### 1️⃣ Class Environment তৈরি করা

JRE-এর মধ্যে থাকে:

- `java.lang`  
- `java.util`  
- `java.io`  
- `java.net`  

এই লাইব্রেরিগুলো ছাড়া:

java
System.out.println("Hello");

### 2️⃣ OS এর সাথে Bridge তৈরি করা

Java সরাসরি Windows/Linux বোঝে না।  
JRE দেয়:

- `.dll` (Windows)  
- `.so` (Linux)  

এই Native ফাইলগুলোর মাধ্যমে:  
👉 Java → OS → Hardware  

অর্থাৎ JRE ছাড়া Java OS-এর সাথে কথা বলতে পারে না।

---

### 3️⃣ Memory & Runtime Support দেওয়া

JRE সেট করে দেয়:

- Heap memory  
- Stack memory  
- Garbage Collector  
- Thread handling  

এগুলো JVM চালানোর জন্য দরকারি “পরিবেশ”।

---

### 4️⃣ Security & Configuration দেওয়া

JRE-এর মধ্যে থাকে:

- Security manager  
- Policy files  
- Property files  

এগুলো ঠিক করে:

- কোন ফাইল অ্যাক্সেস করা যাবে  
- কোন নেটওয়ার্ক কল যাবে  
- কোন ক্লাস লোড হবে









