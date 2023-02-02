Here I tried to provide three different approaches:

**Build and test the project from Jenkins UI:** This method involved using the user interface of Jenkins to build and test the Maven project. I configured the build process by specifying the Maven version, goals, and options, and then trigger the build by clicking on the "Build Now" button. After the build is complete, I could view the results and test reports in the Jenkins console.

**Build and test from Jenkins DSL:** This method involved writing the build and test steps in the Jenkins Domain-Specific Language (DSL). By using the Jenkins DSL, I automated the build and test process, making it easier to manage and maintain.

**Build, test, and deploy from Jenkins pipeline:** This method involved using a Jenkins pipeline to automate the entire software delivery process, from building and testing to deploying the project to a production environment. By using a pipeline(Jenkinsfile) script, I ensured the the build, test, and deployment process is repeatable and consistent.

**Git-Hooks:** In this context of building and testing a Maven project from Jenkins, Git Hooks was used to automatically trigger a Jenkins job whenever code changes are pushed to the Git repository. This helps to ensure that the build and test process is triggered automatically whenever new code is committed, saving time and reducing the risk of manual errors.

**1) build and test a maven project from jenkins**

Docker Job
  a) Create a Dockerfile and docker compose file to build and run a containerised jenkins

Jenkins Job
  a) Install Maven plugin to Jenkins
  b) Install the GIT plugin to Jenkins
  c) Clone Git repository 
  d) Build jar using Maven from pom.xml
  e) test code
  f) deploy in local jenkins server
  g) display result using graph
  h) archive last successful artifact
  i) send email notification about the test result
  
**Git-Hook**
  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed
  b) use the script to auto-trigger jenkins job

**2) Build and test the project from Jenkins-DSL**

**Jenkins Job**
  a) install DSL pluging
  b) create a seed job
  c) Create Maven job inside seed job using DSL

**Git-Hook**
  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed
  b) use the script to auto-trigger jenkins job

**3) Build test and deploy project from pipeline script**

  a) Create a script to build the jar file from pom.xml inside a docker container. This container will be inside jenkins container
  b) Create a script to test the jar file inside docker container 
  c) Create a script to push the image to docker hub and and pull it in remote server
  d) Create a script to deploy the jar in remote server
  c) put the build, test, push and deploy scripts inside Jenkinsfile
  
**Git-Hook**
  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed
  b) use the script to auto-trigger jenkins job
