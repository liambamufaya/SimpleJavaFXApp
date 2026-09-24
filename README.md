# SimpleJavaFXApp — Practical Lab 1

A beginner-friendly JavaFX starter application created for **Mulungushi University (School of Engineering and Technology, Department of Computer Science & IT)** as part of Practical Lab 1. 

This repository contains the setup guide, project architecture, and code for building and running a modular JavaFX desktop application managed with Gradle.

---

## 🎯 Project Overview

This project sets up the complete developer environment needed for JavaFX development. It demonstrates how to build a basic modular Java 21 desktop application featuring interactive GUI components (a window stage, scene, layout container, dynamic text label, and action button).

---

## 🛠️ Prerequisites & Environment Setup

Ensure the following components are installed and added to your system `PATH` before running the project:

| Tool | Required Version | Role / Purpose | Verification Command |
| :--- | :--- | :--- | :--- |
| **JDK** | Java 21 (LTS) | Java Compiler & Runtime Engine | `java -version`<br>`javac -version` |
| **IntelliJ IDEA** | Community or Ultimate | Integrated Development Environment (IDE) | Open IDE & verify JDK 21 |
| **Git** | 2.x+ | Version Control System | `git --version` |
| **Gradle** | 9.x (or compatible) | Dependency Manager & Build Automation | `gradle -v` |

### Environment Verification Check
Run all test commands in a single terminal to ensure your environment is configured correctly:

```bash
java -version
javac -version
git --version
gradle -v
```

---

## 📂 Project Architecture & Structure

```text
SimpleJavaFXApp/
├── build.gradle
├── gradle/
│   └── wrapper/
└── src/
    └── main/
        └── java/
            ├── module-info.java
            └── com/
                └── example/
                    └── hellofx/
                        ├── HelloJavaFX.java
                        └── Main.java
```

---

## ⚙️ Configuration Files

### `build.gradle`
```groovy
plugins {
    id 'application'
    id 'org.openjfx.javafxplugin' version '0.1.0'
}

repositories {
    mavenCentral()
}

java {
    toolchain {
        languageVersion = JavaLanguageVersion.of(21)
    }
}

javafx {
    version = '21.0.12'
    modules = ['javafx.controls']
}

application {
    mainModule = 'com.example.hellofx'
    mainClass = 'com.example.hellofx.Main'
}
```

### `src/main/java/module-info.java`
```java
module com.example.hellofx {
    requires javafx.controls;

    exports com.example.hellofx;
}
```

---
## 🚀 Building and Running the Application

To ensure JavaFX runtime dependencies are loaded correctly, run the application using Gradle via the integrated terminal:

```bash
# Execute via Gradle runner
gradle run
```

*Note: The initial run may take longer as Gradle resolves and downloads JavaFX dependencies from Maven Central.*

---

## 💡 Core JavaFX Concepts Reference

| JavaFX Component | Simple Meaning | Project Context |
| :--- | :--- | :--- |
| **Stage** | The main desktop window frame | `stage.setTitle("My First JavaFX Application");` |
| **Scene** | Content canvas inside the stage | `Scene scene = new Scene(layout, 500, 300);` |
| **Label** | Text element displayed on screen | `Label message = new Label("Welcome to JavaFX!");` |
| **Button** | Clickable UI control component | `Button button = new Button("Click Me");` |
| **VBox** | Layout container ordering items vertically | Top-to-bottom layout with a `20px` spacing |
| **Event Handler** | Action performed when user interacts | `button.setOnAction(...)` updates the text label |

---

## 🛠️ Troubleshooting Common Issues

| Issue / Error | Likely Cause | Solution |
| :--- | :--- | :--- |
| `'java'`/`'gradle'` is not recognized | Path variables missing | Verify system `PATH` and `JAVA_HOME`. Reopen Command Prompt/Terminal. |
| **JavaFX runtime components missing** | Class run without JavaFX modules | Avoid running `HelloJavaFX.java` directly. Execute via `gradle run`. |
| **Unsupported JavaFX configuration warning** | Unnamed module execution | Verify `module-info.java` exists and matches `mainModule` in `build.gradle`. |
| **Gradle JVM mismatch** | Wrong JDK assigned in IDE | Set Gradle JVM to JDK 21 under: <br>`Settings -> Build Tools -> Gradle -> Gradle JVM`. |

---

