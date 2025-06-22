# Java & Spring Boot

Java is a powerful, widely-used programming language known for its portability and performance. Many enterprise applications and backend systems run on Java due to its stability and rich ecosystem.

It’s the foundation for many frameworks, including Spring Boot.

If you’re familiar with other languages like JavaScript or Python, Java is strongly typed and object-oriented.

---

## Spring Boot Overview

Spring Boot is a backend framework for Java. It’s used by enterprise companies to build web apps and APIs because it’s fast, reliable, and easy to scale.

If you’ve used Laravel, Node.js, or .NET, Spring Boot is similar—but for Java.

It gives you:

- A built-in server
- Easy setup and configuration
- Simple database integration
- Tools for building secure, production-ready apps quickly

---

## Setting Up Spring Boot

We’ll use Java 21 (JDK 21) with Spring Boot for backend development.

### What You Need

- Java Development Kit (JDK) 21
- An IDE (we recommend IntelliJ IDEA or VS Code)
- Spring Boot (we’ll set it up using [Spring Initializr](https://start.spring.io/))

### Steps

1. **Install JDK 21**  
   Download and install Java 21:  
   [https://jdk.java.net/21/](https://jdk.java.net/21/)

2. **Set up your IDE**  
   You can use any IDE. Popular options:

   - [IntelliJ IDEA](https://www.jetbrains.com/idea/)
   - [VS Code](https://code.visualstudio.com/) with Java extensions

3. **Create a Spring Boot project**  
   Go to [Spring Initializr](https://start.spring.io/) and select:

   - Project: Maven
   - Language: Java
   - Spring Boot: Latest stable version
   - Dependencies:
     - Spring Web
     - Spring Data JPA
     - PostgreSQL Driver _(or H2 if testing locally)_

4. **Download & open the project**  
   Unzip the generated folder and open it in your IDE.

5. **Run the app**  
   Open `Application.java` (in `src/main/java/...`) and run it.  
   Spring Boot runs on an embedded server by default (usually on `localhost:8080`).

---

## Getting Started Guide

Watch this quick setup guide:  
[Spring Boot setup](https://youtu.be/gJrjgg1KVL4?si=6Py9xlBMJHQrHy2p)
