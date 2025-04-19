# Run-a-Simple-Java-Maven-Build-Job-in-Jenkins
Step 1: Create the Java Maven Project
📁 Folder Structure
css
Copy
Edit
hello-java-maven/
├── pom.xml
└── src/
    └── main/
        └── java/
            └── HelloWorld.java
✍️ HelloWorld.java
Create this file at: hello-java-maven/src/main/java/HelloWorld.java

java
Copy
Edit
public class HelloWorld {
    public static void main(String[] args) {
        System.out.println("Hello, Jenkins + Maven!");
    }
}
📄 pom.xml
Create this file at: hello-java-maven/pom.xml

xml
Copy
Edit
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
🧱 Step 2: Run Jenkins (via Docker)
Open PowerShell or Terminal and run:

bash
Copy
Edit
docker run -p 8080:8080 jenkins/jenkins:lts
Jenkins will now run on http://localhost:8080.

🔐 Step 3: Unlock Jenkins
Open http://localhost:8080

It will ask for an initial password:

Find it from the terminal logs or this file:

makefile
Copy
Edit
C:\Program Files\Docker\Jenkins\secrets\initialAdminPassword
Copy the password and paste it in the browser.

🧰 Step 4: Configure Tools in Jenkins
Click Manage Jenkins → Global Tool Configuration

Scroll to Maven

Click Add Maven

Name: Maven 3.8.6

Choose: Install automatically

Make sure JDK is detected or install it similarly.

🔨 Step 5: Create Freestyle Project
Go to Jenkins home → Click New Item

Name it: java-maven-build

Choose Freestyle project → OK

🔧 Configure the Build Job
Source Code Management:

Optional: Leave as "None" (if using local)

Or use Git repo if uploaded

Build Section:

Click Add build step

Choose: Invoke top-level Maven targets

Goal:

go
Copy
Edit
clean package
▶️ Step 6: Run the Job
Click Build Now

Go to Build History → Console Output

✅ If everything is fine, you’ll see:

nginx
Copy
Edit
BUILD SUCCESS


