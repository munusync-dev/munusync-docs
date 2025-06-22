# Setting Up Your IDE for Spring Boot Development

To work on Spring Boot projects, you can use either **Visual Studio Code (VS Code)** or **IntelliJ IDEA**. Here’s how to get started with both.

---

## Option 1: Visual Studio Code

### Step 1: Install VS Code

Download from:
[https://code.visualstudio.com/](https://code.visualstudio.com/)

### Step 2: Install Extensions

Search and install these in the Extensions tab:

- **Java Extension Pack**
  Gives you everything needed to write and run Java code.

- **Spring Boot Extension Pack**
  Adds support for Spring Boot projects: navigation, initializer, and more.

- **Maven for Java** (optional)
  Useful for managing dependencies.

### Step 3: Install JDK 21

Get the latest Java 21 from:
[https://jdk.java.net/21/](https://jdk.java.net/21/)

After installing, run:

```bash
java -version
```

You should see `java version "21"`.

---

## Option 2: IntelliJ IDEA

### Step 1: Download IntelliJ

Go to:
[https://www.jetbrains.com/idea/download](https://www.jetbrains.com/idea/download)

Choose either:

- **Community Edition** – Free, supports basic Spring Boot work.
- **Ultimate Edition** – Paid, full Spring Boot support (recommended).

### Step 2: Get the Ultimate Edition for Free (If You're a Student)

1. Visit: [https://www.jetbrains.com/community/education/](https://www.jetbrains.com/community/education/)
2. Click **Apply Now**
3. Use your school email or upload proof of enrollment
4. Once approved, you’ll get access to IntelliJ Ultimate and all JetBrains tools for free.

### Step 3: Install JDK 21

Same as above, download it from:
[https://jdk.java.net/21/](https://jdk.java.net/21/)

---

## After Setup

- Open your Spring Boot project (or generate one from [Spring Initializr](https://start.spring.io/))
- Let the IDE index and resolve dependencies
- Run your app from the main class (usually ends in `Application.java`)

You're now ready to build and run Spring Boot apps.
