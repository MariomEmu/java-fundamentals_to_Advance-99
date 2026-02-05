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

**summary:**  
প্রথমে Hello.java লিখি → javac দিয়ে compile করি → Hello.class তৈরি হয় → java Hello চালাই →  
JVM class load করে → check করে → memory দেয় → শেষে bytecode execute করে।


