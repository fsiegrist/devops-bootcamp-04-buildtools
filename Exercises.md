## Exercises
<br />

<details>
<summary>Exercise 0: Clone project and create own Git repository</summary>
<br />
To work with the project for the exercises:
- Clone the project and
- create your own project/git repository from it

**steps:**

```sh
# clone repository & change into project dir
git clone git@gitlab.com:devops-bootcamp3/java-gradle-app.git
mv java-gradle-app devops-bootcamp-04-buildtools
cd devops-bootcamp-04-buildtools

# remove remote repo reference and create your own local repository
rm -rf .git
git init 
git add .
git commit -m "Initial commit"

# create git repository on GitHub and push your newly created local repository to it
git remote add origin git@github.com:fsiegrist/devops-bootcamp-04-buildtools.git
git branch -m main
git push -u origin main
```

</details>

******

<details>
<summary>Exercise 1: Build jar artifact</summary>
<br />
You want to deploy the artifact to share that library with all team members. So:
- try to build the jar file

The Build will fail, because of a compile error in a test, so you can't build the jar.

**steps**

```sh
./gradlew build
```

</details>

******

<details>
<summary>Exercise 2: Run tests</summary>
<br />

- Fix the test, by changing "true" string to true boolean.
- Run gradle test to execute only the tests and check the fix.

**steps:**
```sh
# locate AppTest.java file in src/test/java foldr & fix test
boolean result = myApp.getCondition(true); 

# run tests
./gradlew test
```

</details>

******

<details>
<summary>Exercise 3: Clean & build App</summary>
<br />

You fixed the test. Now:
- clean the build folder with gradle clean and 
- try to build jar file again.

**steps:**
```sh
./gradlew clean 
./gradlew build
```

</details>

******

<details>
<summary>Exercise 4: Start application</summary>
<br />

Start the jar file to test that the application runs successfully as a jar file.
- Start app with java -jar app-1.0.jar

NOTE: replace "app-1.0.jar" with the name of YOUR jar file.

**steps:**
```sh
java -jar build/libs/bootcamp-java-project-1.0-SNAPSHOT.jar
```

</details>

******

<details>
<summary>Exercise 5: Start App with 2 Parameters</summary>
<br />

Now you want to add parameters to your application, so you and other users can pass different values on startup.
- Add parameter input to the Java code (see code snippet below, which you can copy)
- Rebuild the jar file
- Execute the jar file again with 2 params

```sh
# Code snippet to add inside Application.java on line 16
Logger log = LoggerFactory.getLogger(Application.class); 
try { 
    String one = args[0]; 
    String two = args[1]; 
    log.info("Application will start with the parameters {} and {}", one, two); 
} catch (Exception e) { 
    log.info("No parameters provided"); 
}
```

**steps:**
```sh
# add parameter input to the Java code (see code snipped of the exercise description)

# rebuild the jar file 
./gradlew build

# run application with ANY 2 parameters
java -jar build/libs/bootcamp-java-project-1.0-SNAPSHOT.jar felix siegrist
```

</details>
