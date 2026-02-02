#  Java Development Kit (JDK)
---
## 📌 What is JDK?
**JDK (Java Development Kit)** is a software package that provides all the tools required to:

- ✍️ Develop Java programs  
- 🛠️ Compile source code  
- 🐞 Debug applications  
- ▶️ Run Java programs  

In simple words, JDK is the **complete toolbox** for Java developers.

---

## 🎯 Why do we use JDK?
We use JDK because it allows us to:

- Write Java programs  
- Compile `.java` files into `.class` bytecode  
- Run Java applications  
- Debug and package apps  

---

### বাংলা
আমরা JDK ব্যবহার করি কারণ:

- Java কোড লিখতে  
- `.java` ফাইলকে `.class` এ convert করতে  
- Program চালাতে  
- Error খুঁজে ঠিক করতে এবং অ্যাপ প্যাকেজ করতে  

---

<img width="300" height="360" alt="image" src="https://github.com/user-attachments/assets/5099a1e5-b683-4f7c-b7c0-e0199388cb24" />

## 🔁 Java Execution Flow —  Which JDK part works?

| Step | What Happens | Which Part Works |
|------|-------------|------------------|
| `Test.java` | You write Java code | Developer (You 😄) |
| `javac` | Compiles `.java` → `.class` | **Compiler** (JDK Tool) |
| `Test.class` | Bytecode file created | Output of JDK Compiler |
| JVM | Starts execution | **JVM** (inside JRE, inside JDK) |
| Interpreter | Executes code line by line | Part of **JVM** |
| JIT Compiler | Converts bytecode to native code | Part of **JVM** |
| Machine Code | OS understands instructions | **CPU / Operating System** |
| Output | Result is shown | **Console / UI** |

---

## 🛠️ How to Use JDK

### 1️⃣ Installation
Download and install JDK from [Oracle](https://www.oracle.com/java/technologies/javase-downloads.html) or [OpenJDK](https://openjdk.org/).

---

### 2️⃣ Path Setup
Set the following **Environment Variables**:

- `JAVA_HOME` → Path to your JDK installation  
- `PATH` → Add `%JAVA_HOME%\bin` (Windows) or `$JAVA_HOME/bin` (Linux/Mac)

---

### 3️⃣ Run Java Code

1. **Create a Java file**  
   Example: `Hello.java`

```java
public class Hello {
    public static void main(String[] args) {
        System.out.println("Hello Java!");
    }
}
```


## 🔹Mostly Used Components of JDK

Below is a list of the **most commonly used JDK tools** during Java development:

| Component | Use / Description |
|-----------|------------------|
| `javac` | Java **compiler** — converts `.java` source code into bytecode (`.class`) |
| `java` | Java **launcher / loader** — runs Java applications |
| `javadoc` | Generates **documentation** from Java source code comments |
| `jar` | **Java Archiver** — package multiple `.class` files and resources into a `.jar` file |
| `jshell` | Interactive **Java REPL** (introduced in Java 9) for testing snippets quickly |
| `jdb` | **Debugger** — used to debug Java programs from command line |
| `jconsole` | **Monitoring & Management Console** — view memory, threads, CPU usage |
| `jstack` | Prints **stack traces** of Java threads — useful for debugging |
| `keytool` | Manages **keystore & certificates** — security management |
| `jpackage` | Generates **self-contained application bundles** (since Java 14) |
| `javap` | Disassembles `.class` files — view bytecode structure |

---


# 📦 Understanding JAR (Java Archive)

**JAR = Java Archive**  
It is a ZIP-format archive file that stores Java applications or libraries.

---

## 1️⃣ What is JAR?

- JAR is like Java’s `.exe` or `.app` file.  
- Basis for `.war` (web apps) and `.ear` (enterprise apps).  

---

## 2️⃣ JAR File Structure
<img width="400" height="500" alt="ChatGPT Image Feb 2, 2026, 12_47_19 PM" src="https://github.com/user-attachments/assets/f5efaf3c-7ec2-4d67-b211-5775e75bac38" />

- Example: `myapp.jar`

---

## 3️⃣ Why Use JAR?

- **Single File**: Combine multiple `.class` files into one  
- **Distribution**: Easy to share or distribute  
- **Library**: Can be used in other projects  
- **Executable**: Can run with double-click or `java -jar`

---

## 4️⃣ Types of JAR

| Type | Description | Example Command |
|------|-------------|----------------|
| **Library JAR** | For using as a library | `jar cvf mylib.jar *.class` |
| **Executable JAR** | Runnable JAR with main class | `jar cfe app.jar Main *.class` <br> Run: `java -jar app.jar` |
| **FAT / Uber JAR** | Includes all dependencies | Spring Boot / Maven Shade plugin |

---

## 5️⃣ How to Create JAR

### Step 1: Compile Java Code
```bash
javac Hello.java
```

### 2️⃣ Step 2: Create the JAR

After compiling your Java code, you can package it into a JAR file.

#### Basic Command:
```bash
jar cvf hello.jar Hello.class
```
#### Explanation of the Process

1. **Collect all `.class` files**  
   Gather all compiled Java classes that need to be included in the JAR.

2. **Create `META-INF/MANIFEST.MF` file**  
   This metadata file can specify the **main class** and other information.

3. **Apply ZIP compression**  
   JAR files are essentially **ZIP-format archives**.

4. **Save with `.jar` extension**  
   The final file `hello.jar` can now be used as a **library** or **executed**.






