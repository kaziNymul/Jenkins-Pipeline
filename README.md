**ARM Template for Jenkins**

This ARM template creates a Jenkins CI/CD pipeline in Azure. It provisions all the necessary resources for the pipeline, including a virtual machine for running Jenkins, a virtual network for connecting the virtual machine to the internet, and a storage account for storing the Jenkins data.

The template starts with the "$schema" and "contentVersion" properties, which define the version of the ARM template language and the version of the content in the template.

Next, the template includes "parameters" section where the user-defined values for different resources can be specified. For example, the name of the Jenkins virtual machine, the username and password for the virtual machine, the size of the virtual machine, and the name of the storage account.

The "variables" section includes hardcoded values for some of the resources in the template. In this case, it defines the names of the virtual network, subnet, public IP address, and network security group.

The "resources" section is where the actual resources are defined. The resources include a virtual network, a network security group, and a virtual machine.

The virtual network is defined with "Microsoft.Network/virtualNetworks" type, and it includes properties such as the address space and subnets. The network security group is defined with "Microsoft.Network/networkSecurityGroups" type, and it includes properties such as the security rules for allowing SSH access.

The virtual machine is defined with "Microsoft.Compute/virtualMachines" type, and it includes properties such as the name of the virtual machine, the size of the virtual machine, the username and password, and the storage account name. The template also provisions a public IP address for the virtual machine, so that it can be accessed from the internet.

Here I tried to provide three different approaches for jenkins deployment:

**Build and test the project from Jenkins UI:** 

This method involved using the user interface of Jenkins to build and test the Maven project. I configured the build process by specifying the Maven version, goals, and options, and then trigger the build by clicking on the "Build Now" button. After the build is complete, I could view the results and test reports in the Jenkins console.

**Build and test from Jenkins DSL:** 

This method involved writing the build and test steps in the Jenkins Domain-Specific Language (DSL). By using the Jenkins DSL, I automated the build and test process, making it easier to manage and maintain.

**Build, test, and deploy from Jenkins pipeline:** 

This method involved using a Jenkins pipeline to automate the entire software delivery process, from building and testing to deploying the project to a production environment. By using a pipeline(Jenkinsfile) script, I ensured the the build, test, and deployment process is repeatable and consistent.

**Git-Hooks:** 

In this context of building and testing a Maven project from Jenkins, Git Hooks was used to automatically trigger a Jenkins job whenever code changes are pushed to the Git repository. This helps to ensure that the build and test process is triggered automatically whenever new code is committed, saving time and reducing the risk of manual errors.


**1) build and test a maven project from jenkins**

***Docker Job***
  Create a Dockerfile and docker compose file to build and run a containerised jenkins

***Jenkins Job***

  a) Install Maven plugin to Jenkins<br />
  b) Install the GIT plugin to Jenkins<br />
  c) Clone Git repository <br />
  d) Build jar using Maven from pom.xml<br />
  e) test code<br />
  f) deploy in local jenkins server<br />
  g) display result using graph<br />
  h) archive last successful artifact<br />
  i) send email notification about the test result<br />
  
***Git-Hook***

  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed<br />
  b) use the script to auto-trigger jenkins job<br />

**2) Build and test the project from Jenkins-DSL**

***Jenkins Job***

  a) install DSL pluging<br />
  b) create a seed job<br />
  c) Create Maven job inside seed job using DSL<br />

***Git-Hook***

  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed<br />
  b) use the script to auto-trigger jenkins job<br />

**3) Build test and deploy project from pipeline script**

***Jenkins Job***

  a) Create a script to build the jar file from pom.xml inside a docker container. This container will be inside jenkins container<br />
  b) Create a script to test the jar file inside docker container<br />
  c) Create a script to push the image to docker hub and and pull it in remote server<br />
  d) Create a script to deploy the jar in remote server<br />
  c) put the build, test, push and deploy scripts inside Jenkinsfile<br />
  
***Git-Hook***

  a) create a script to generate crumb and use to auto run build once the new versioned code is pushed<br />
  b) use the script to auto-trigger jenkins job<br />
