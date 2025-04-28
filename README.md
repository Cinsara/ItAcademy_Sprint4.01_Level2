# S04T01N02 - Spring Boot REST API with Gradle

This project is part of the **Nivell 2** exercise and is similar to the previous level, but using **Gradle** as the dependency manager instead of Maven.

## 📦 Project Overview

This Spring Boot application has been created using (https://start.spring.io/) with the following configuration:

### Project Settings

- **Project Type**: Gradle (Groovy)
- **Language**: Java
- **Spring Boot Version**: Latest stable version
- **Group**: `cat.itacademy.s04.t01.n02`
- **Artifact**: `S04T01N02`
- **Name**: `S04T01N02`
- **Description**: `S04T01N02`
- **Package Name**: `cat.itacademy.s04.t01.n02`
- **Packaging**: Jar
- **Java Version**: 11 or higher

### Dependencies

- Spring Boot DevTools
- Spring Web

---

## 🧪 API Structure

We will convert this application into a basic **REST API**.

### Create the Controller

Under the base package `cat.itacademy.s04.t01.n02`, create a new subpackage called `controller`.

Inside it, create a Java class named `HelloWorldController`.

### HelloWorldController

This class will expose two `GET` endpoints.

---

#### 1. `GET /HelloWorld`

- Accepts an **optional request parameter** called `nom`.
- If not provided, it defaults to `UNKNOWN`.
- Returns: Hello, {name}. You are running a Gradle project.

```java
 @GetMapping("/HelloWorld")
    public String hello(@RequestParam(defaultValue = "UNKNOWN") String name){
        return "Hello %s. You are running a Gradle project.".formatted(name);
    }
```

#### 2. GET /HelloWorld2/{nom}

- Accepts an optional path variable called nom.
- If not provided, it behaves as if nom is "UNKNOWN".
- Returns: Hello %s. You are running a Gradle project.

```java
  @GetMapping(value = {"/HelloWorld2","/HelloWorld2/{name}"})
    public String hello2(@PathVariable(required = false) String name){
        if(name == null) name = "UNKNOWN";
        return "Hello %s. You are running a Gradle project.".formatted(name);
    }
```

### 🧪 Example Requests

Below are example URLs you can use to test the API endpoints:

- [`GET /HelloWorld`](http://localhost:9001/HelloWorld)  
  → Returns: `Hello, UNKNOWN. You are running a Gradle project.`

- [`GET /HelloWorld?nom=YourName`](http://localhost:9001/HelloWorld?nom=YourName)  
  → Returns: `Hello, YourName. You are running a Gradle project.`

- [`GET /HelloWorld2`](http://localhost:9001/HelloWorld2)  
  → Returns: `Hello, UNKNOWN. You are running a Gradle project.`

- [`GET /HelloWorld2/YourName`](http://localhost:9001/HelloWorld2/YourName)  
  → Returns: `Hello, YourName. You are running a Gradle project.`

