1️⃣ Ensure project structure
Your repo should look like this:
hello-java-maven/
├─ pom.xml
├─ README.md
└─ src/
   └─ main/
      └─ java/
         └─ com/
            └─ example/
               └─ HelloWorld.java
HelloWorld.java content:
package com.example;

public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
pom.xml content:
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0
                             https://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>com.example</groupId>
    <artifactId>hello-java-maven</artifactId>
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
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-jar-plugin</artifactId>
                <version>3.2.2</version>
                <configuration>
                    <archive>
                        <manifest>
                            <mainClass>com.example.HelloWorld</mainClass>
                        </manifest>
                    </archive>
                </configuration>
            </plugin>
        </plugins>
    </build>
</project>
✅ Notice the <mainClass> points to com.example.HelloWorld. This ensures java -jar target/hello-java-maven-1.0.jar works.
2️⃣ Update README.md
Include instructions for your task:
# hello-java-maven

A simple Java HelloWorld Maven project used to demonstrate Jenkins CI/CD build.

## Build Locally

```bash
mvn clean package
java -jar target/hello-java-maven-1.0.jar
Expected output:
Hello, Jenkins + Maven!
Jenkins Build Steps
Start Jenkins (Docker or locally):
docker run -p 8080:8080 jenkins/jenkins:lts
Configure Maven in Jenkins (Manage Jenkins → Global Tool Configuration → Maven 3.x).
Create a new Freestyle Project:
Build → Invoke top-level Maven targets → clean package
Save and build → Console Output should show BUILD SUCCESS.

---

### 3️⃣ Push to GitHub

From your local repo:

```bash
git add .
git commit -m "Complete HelloWorld Maven project with Jenkins setup"
git push origin main
