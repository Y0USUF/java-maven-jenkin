# java-maven-jenkin

-----

# Simple Java Maven Build Job in Jenkins

## Objective

The goal of this task was to learn the fundamentals of **Continuous Integration/Continuous Delivery (CI/CD)** by configuring a Jenkins Freestyle job to build a simple Java application using Maven

This exercise demonstrates how Jenkins interacts with a build tool to compile code, package it, and report the build status.

## Deliverables

  * A basic Java "Hello World" application with a Maven `pom.xml`.
  * A Jenkins Freestyle job configured to build the application.
  * Screenshot of the successful build console output (included below).

-----

## Project Structure

The project follows the standard Maven directory structure:

```
hello-java-maven/
├── src/
│   └── main/
│       └── java/
│           └── HelloWorld.java
└── pom.xml
```

### 1\. `HelloWorld.java`

This file contains the simple Java class that the task requires:

```java
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
```

### 2\. `pom.xml`

This Maven Project Object Model file defines the project and configures the compiler to use Java 1.8:

```xml
<project>
  <modelVersion>4.0.0</modelVersion>
  <groupId>com.example</groupId>
  <artifactId>hello</artifactId>
  <version>1.0</version>
  <build>
    <plugins>
      <plugin>
        <groupId>org.apache.maven.plugins</groupId>
        <artifactId>maven-compiler-plugin</artifactId>
        <version>3.8.1</version>
        <configuration>
          <source>1.8</source>
          <target>1.8</target>
        </configuration>
      </plugin>
    </plugins>
  </build>
</project>
```

-----

## Jenkins Configuration Summary

### Tools Configuration

Maven was configured globally under **Manage Jenkins** $\rightarrow$ **Global Tool Configuration**.

### Freestyle Job Setup

1.  A new **Freestyle project** named `Hello-Maven-Build` was created.
2.  **Source Code Management (SCM):** Git was configured to clone this repository (`https://github.com/Y0USUF/java-maven-jenkin.git`) into the Jenkins workspace.
3.  **Build Step:** The build step was configured as **"Invoke top-level Maven targets"**.
4.  **Goals:** The goals were set to `clean package`.
      * `clean`: Deletes the target directory (previous build artifacts).
      * `package`: Compiles the source code and packages it into a JAR file.

-----

## Successful Build Output

The following screenshot confirms the job ran successfully and achieved a `BUILD SUCCESS` status, demonstrating that Jenkins successfully invoked Maven to compile the Java code:

<img width="2228" height="1152" alt="Screenshot 2025-10-03 111245" src="https://github.com/user-attachments/assets/d8522903-14c2-4ca6-94da-0e5cd591202b" />

[INFO] ------------------------------------------------------------------------
Finished: SUCCESS
```
