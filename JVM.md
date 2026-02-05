# Java Virtual Machine (JVM)

## What is JVM?

JVM (Java Virtual Machine) is a virtual machine that **runs Java bytecode**.

It does **not** understand `.java` files.  
It only understands **`.class` (bytecode)**.


JVM হলো একটা virtual machine যা **Java bytecode চালায়**।  
JVM কখনো `.java` ফাইল বোঝে না — সে শুধু `.class` বোঝে।

---

## Why we use JVM?

| Reason | Bangla Meaning |
|--------|----------------|
| Platform Independent | এক কোড সব OS-এ চলে |
| Security | ভাইরাস/ভুল কোড আটকায় |
| Memory Management | নিজে নিজে memory clean করে |
| Performance (JIT) | code fast করে |
| No OS dependency | OS-এর উপর নির্ভর না |

**simple:**  
OS, CPU -> Java বোঝে না, 
JVM মাঝখানে বসে **translator + manager** হয়।

---

## How JVM Works?

```text
.java  →  javac  →  .class  →  JVM  →  OS  →  CPU
```


## Step-by-Step: How JVM Runs a Java Program

> First, you write your Java source file named:

Hello.java

> Then you compile the file using the Java compiler:

javac Hello.java

> After compilation, a bytecode file is created:

Hello.class (bytecode)

> Now you run the program using the JVM:

java Hello

> When you run this command, the JVM starts working internally by following steps:

- Loads the class file into memory  
- Checks the bytecode for security and errors  
- Allocates required memory (Heap and Stack)  
- Executes the bytecode line by line  

>summary:
>প্রথমে Hello.java লিখি → javac দিয়ে compile করি → Hello.class তৈরি হয় → java Hello চালাই →  
>JVM class load করে → check করে → memory দেয় → শেষে bytecode execute করে।


# Architecture of JVM
<img width="360" height="450" alt="ChatGPT Image Feb 5, 2026, 11_33_09 AM" src="https://github.com/user-attachments/assets/221fdb62-33ab-46a2-97a9-ed2c0b3cd425" />

> "The same image, just with clearer visualization keep it."
 <img width="669" height="588" alt="image" src="https://github.com/user-attachments/assets/28c021e9-7c35-4247-87c6-7b8f0e7041f3" />

# Explanation of Architecture step by step in details

---

## 1️⃣ Compilation (কম্পাইলেশন)

- Java code (`.java` ফাইল) → `javac` compiler → Bytecode (`.class` ফাইল) এ রূপান্তর হয়।  
- Bytecode platform independent, মানে যেকোন OS-এ চলতে পারে যদি সেখানে JVM থাকে।  

---

JVM Architecture মূলত ৫টা major part নিয়ে কাজ করে:  

1. Class Loader Subsystem (ক্লাস লোডার সাবসিস্টেম)  
2. Runtime Data Areas (রানটাইম মেমোরি এরিয়া)  
3. Execution Engine (এক্সিকিউশন ইঞ্জিন)  
4. Native Method Interface (JNI)  
5. Native Libraries
---

## 1️⃣ Class Loading (ক্লাস লোডিং)

- JVM-এর ClassLoader bytecode memory-তে load করে।  
- তিনটি phase আছে:  
  1. **Loading**  
  2. **Linking**  
  3. **Initialization**  

---
## 2️⃣ Runtime Data Areas (রানটাইম মেমোরি এরিয়া)

### a) Method Area
-  **class structure**, **static variables**, **runtime constant pool** store থাকে. 
- Shared among all threads।  

### b) Heap
- **Objects & arrays** store হয় এখানে।  
- Shared among threads।  
- Sub-divided into:  
  - **Young Generation (Eden + Survivor S0/S1)** → নতুন objects।  
  - **Old Generation (Tenured)** → long-lived objects।  
  - **Permanent/Metaspace (Java 8+)** → Class metadata।  

### c) Stack
- **Thread-specific** memory।  
- প্রতিটি thread-এর নিজস্ব stack, method calls, local variables store করে।  
- প্রতিটি thread এর নিজের stack থাকে।  

### d) PC Register
- Tracks/hold **current instruction address** for each thread

### e) Native Method Stack
- Used for **native code execution** (C/C++ libraries)।  

>Summary: 
>Memory Areas JVM কে organized করে, যাতে objects, methods, threads efficiently manage করা যায়।  


---

## 3️⃣ Execution Engine (এক্সিকিউশন ইঞ্জিন)

- Bytecode → machine code এ convert করে।  

**Components:**  
- **Interpreter:** Line by line execute করে (slow)।  
- **JIT Compiler (Just-In-Time):** Frequently used code parts কে machine code করে রেখে দেয়, পরে fast execution।  
- **Garbage Collector:** Unused objects heap থেকে remove করে memory free করে।

---

## 4️⃣ Native Method Interface (JNI)

- **Purpose:** JVM কে OS-এর native libraries এবং C/C++ code এর সাথে communicate করতে সাহায্য করা।  
- Allows Java programs to use native code functionalities।  

---

## 5️⃣ Native Libraries

- **OS-specific libraries** ও hardware interaction handle করে।  
- Example: Windows DLL, Linux SO files।  

>Summary: 
>Native Libraries JVM কে OS এবং hardware level সাথে integrate করতে সাহায্য করে। 
---

# ➡️ Class Loader Subsystem (Break it down each thing minor level)
<img width="400" height="500" alt="image" src="https://github.com/user-attachments/assets/2cdad1fd-582a-430d-9222-d9500294b9fe" />

# ClassLoaders in JVM

---

## 1️⃣ Bootstrap ClassLoader (প্রধান লোডার)

**কাজ:**  
JVM-এর core Java classes load করে। যেমন: `java.lang.*`, `java.util.*`, `java.io.*`, `java.net.*`।  
`rt.jar` (runtime jar) থেকে classes load করে।  

**কেন দরকার:**  
```java
// তুমি যখন লিখো:
String s = "Hello";
System.out.println(s);

// Bootstrap Loader load করে:
// 1. java.lang.String class
// 2. java.lang.System class

বিশেষত্ব:

Written in C/C++ (Native code)

JVM-এর internal part

Parent of all classloaders

Highest priority

Location: JAVA_HOME/jre/lib/rt.jar
```

## 2️⃣ Extension ClassLoader (এক্সটেনশন লোডার)

**কাজ:**  
Extension classes load করে।  
Standard Java-র বাইরের extra functionality।  
`JRE/lib/ext` folder-এর jar files থেকে load করে।  

**কেন দরকার:**  
```java
// Example: used in 
 • Cryptography libraries
 • XML parsers
 • Database drivers (পুরোনো JDBC)

  Extension Loader load করে:
// javax.crypto.*
// javax.xml.*

JRE structure:
└── lib/
    └── ext/
        ├── localedata.jar
        ├── sunec.jar     (Elliptic Curve cryptography)
        ├── sunjce_provider.jar
        └── ...other extension jars
বিশেষত্ব:

Written in Java (sun.misc.Launcher$ExtClassLoader)

Bootstrap-এর child

Loads from java.ext.dirs system property
```

## 3️⃣ Application ClassLoader (এপ্লিকেশন লোডার)

**কাজ:**  
Loads application-specific classes from the classpath (.class files and JARs).
Also referred to as the System ClassLoader.

**কেন দরকার:**  
```java
// project:
com/
└── myapp/
    ├── Main.class        ← Application Loader loads these
    ├── User.class
    └── Util.class

// when it's run:
java -cp ./myapp.jar com.myapp.Main

বিশেষত্ব:

Also called System ClassLoader

Written in Java (sun.misc.Launcher$AppClassLoader)

Extension Loader-এর child

Default classloader for user applications

```
# JVM Linking & Initialization Phases of Loader

JVM-এর Linking Phase তিনটি ধাপে বিভক্ত: Verification, Preparation, Resolution।  
তারপর আসে Initialization Phase যা static variables assign করে এবং static blocks execute করে।

---

## Linking Phase (3 Step)

### 1️⃣ VERIFICATION (ভেরিফিকেশন) - Security Guard 🔒

**কাজ:**  
Bytecode safe কি না check করে  

**কি check করে:**  

```java
.class file structure:
┌─────────────────────┐
│   Magic Number      │ ← CAFEBABE (Java-র signature)
├─────────────────────┤
│   Version           │ ← JVM version compatible?
├─────────────────────┤
│   Constant Pool     │ ← Valid references?
├─────────────────────┤
│   Methods           │ ← Correct parameters?
├─────────────────────┤
│   Attributes        │ ← Valid attributes?
└─────────────────────┘
যেগুলো verify করে:

Bytecode format সঠিক কি না

Final methods override করা হয়নি তো?

Type correctness - int-এ String assign করছি না তো?

Stack overflow/underflow - stack properly use করা হচ্ছে?

Access violations - private method access করছি না তো?

Example:

// Malicious bytecode যদি হয়:
iconst_5      // push 5 to stack
istore_1      // store to local variable 1
iload_1       
i2d           // int → double convert
dstore_2      // PROBLEM! double needs 2 slots

// Verifier ধরবে ফেলে: "Stack inconsistency!"


কেন দরকার:

Security - Malicious code prevent করা

Stability - JVM crash হতে দেয় না

Type safety - Runtime errors কমায়
```
## 2️⃣ PREPARATION (প্রিপারেশন) - Memory Allocate 

**কাজ**:
Class-এর static variables-এর memory allocate করে

**কি করে**:
```
public class Student {
    static int count = 0;        // Preparation: memory allocate (value=0)
    static String name = null;   // Reference set to null
    static final int MAX = 100;  // Constant (value assign here!)
}

// Preparation-এ হয়:
// count = 0 (default int value)
// name = null (default reference value)
// MAX = 100 (final হওয়ায় value assign)


Default Values Set করে:

int → 0

boolean → false

Object → null

double → 0.0

বিশেষ:

শুধু memory allocate, value assign না (initialization-এ হবে)

কিন্তু final static variables-এর value এখানেই assign হয়
```
## 3️⃣ RESOLUTION (রিসোলিউশন) - Address Binding 

**কাজ**:
Symbolic references কে concrete memory addresses-এ convert করে
```
Symbolic Reference vs Direct Reference:

// .class file-এ থাকে Symbolic Reference:
"java/lang/String"   ← Class name as string
"toString"           ← Method name as string

// Resolution convert করে Direct Reference:
0x7f123456           ← Actual memory address


যা resolve করে:

Class references

// Before resolution: "java/util/ArrayList"
// After resolution: 0x1000ABCD (memory address)


Field references

Student.name → 0x2000EF01


Method references

System.out.println() → 0x3000AABB


Example:

public class Test {
    public void show() {
        String s = "Hello";           // "java/lang/String" resolve হবে
        System.out.println(s);        // "java/io/PrintStream.println" resolve হবে
    }
}


Lazy Resolution:

সব reference একসাথে resolve না হয়

যখন প্রথম প্রয়োজন হয়, তখন resolve করে

Performance improvement
```
## Initialization Phase (ইনিশিয়ালাইজেশন)

**কাজ**:
Static variables-এ actual values assign করে + static block execute করে

**কখন হয়**:

Class first time actively used হলে

new keyword use করলে

Static method call করলে

Static field access করলে

Reflection use করলে
```
কি করে:

public class Config {
    static int port = 8080;              // ← এখন value assign হবে
    static String host;
    
    static {                             // ← Static block execute হবে
        host = "localhost";
        System.out.println("Config class initialized!");
    }
    
    static final String DB_URL = "jdbc:mysql://localhost/db";
}


Initialization Order:

public class Parent {
    static int p = 10;                   // 1. Parent-এর static
    static { System.out.println("Parent static"); }
}

public class Child extends Parent {
    static int c = 20;                   // 2. Child-এর static
    static { System.out.println("Child static"); }
}

// Order of execution:
// 1. Parent static variables initialize
// 2. Parent static block execute
// 3. Child static variables initialize  
// 4. Child static block execute
```



