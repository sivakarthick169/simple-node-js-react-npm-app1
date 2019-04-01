
Build a Node.js and React app with npm 
Table of Contents
Prerequisites
Run Jenkins in Docker
On macOS and Linux
On Windows
Accessing the Jenkins/Blue Ocean Docker container
Setup wizard
Stopping and restarting Jenkins
Fork and clone the sample repository on GitHub
Create your Pipeline project in Jenkins
Create your initial Pipeline as a Jenkinsfile
Add a test stage to your Pipeline
Add a final deliver stage to your Pipeline
Wrapping up
This tutorial shows you how to use Jenkins to orchestrate building a simple Node.js and React application with the Node Package Manager (npm).

If you are a Node.js and React developer who is new to CI/CD concepts, or you might be familiar with these concepts but don’t know how to implement building your application using Jenkins, then this tutorial is for you.

The simple Node.js and React application (which you’ll obtain from a sample repository on GitHub) generates a web page with the content "Welcome to React" and is accompanied by a test to check that the application renders satisfactorily.

Duration: This tutorial takes 20-40 minutes to complete (assuming you’ve already met the prerequisites below). The exact duration will depend on the speed of your machine and whether or not you’ve already run Jenkins in Docker from another tutorial.

You can stop this tutorial at any point in time and continue from where you left off.

If you’ve already run though another tutorial, you can skip the Prerequisites and Run Jenkins in Docker sections below and proceed on to forking the sample repository. (Just ensure you have Git installed locally.) If you need to restart Jenkins, simply follow the restart instructions in Stopping and restarting Jenkins and then proceed on.

Prerequisites
For this tutorial, you will require:

A macOS, Linux or Windows machine with:

256 MB of RAM, although more than 512MB is recommended.

10 GB of drive space for Jenkins and your Docker images and containers.

The following software installed:

Docker - Read more about installing Docker in the Installing Docker section of the Installing Jenkins page.
Note: If you use Linux, this tutorial assumes that you are not running Docker commands as the root user, but instead with a single user account that also has access to the other tools used throughout this tutorial.

Git and optionally GitHub Desktop.

Run Jenkins in Docker
In this tutorial, you’ll be running Jenkins as a Docker container from the jenkinsci/blueocean Docker image.

To run Jenkins in Docker, follow the relevant instructions below for either macOS and Linux or Windows.

You can read more about Docker container and image concepts in the Docker and Downloading and running Jenkins in Docker sections of the Installing Jenkins page.

On macOS and Linux
Open up a terminal window.

Run the jenkinsci/blueocean image as a container in Docker using the following docker run command (bearing in mind that this command automatically downloads the image if this hasn’t been done):

docker run \
  --rm \
  -u root \
  -p 8080:8080 \
  -v jenkins-data:/var/jenkins_home \ 
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME":/home \ 
  jenkinsci/blueocean
Maps the /var/jenkins_home directory in the container to the Docker volume with the name jenkins-data. If this volume does not exist, then this docker run command will automatically create the volume for you.
Maps the $HOME directory on the host (i.e. your local) machine (usually the /Users/<your-username> directory) to the /home directory in the container.
Note: If copying and pasting the command snippet above doesn’t work, try copying and pasting this annotation-free version here:

docker run \
  --rm \
  -u root \
  -p 8080:8080 \
  -v jenkins-data:/var/jenkins_home \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v "$HOME":/home \
  jenkinsci/blueocean
Proceed to the Setup wizard.

On Windows
Open up a command prompt window.

Run the jenkinsci/blueocean image as a container in Docker using the following docker run command (bearing in mind that this command automatically downloads the image if this hasn’t been done):

docker run ^
  --rm ^
  -u root ^
  -p 8080:8080 ^
  -v jenkins-data:/var/jenkins_home ^
  -v /var/run/docker.sock:/var/run/docker.sock ^
  -v "%HOMEPATH%":/home ^
  jenkinsci/blueocean
For an explanation of these options, refer to the macOS and Linux instructions above.

Proceed to the Setup wizard.

Accessing the Jenkins/Blue Ocean Docker container
If you have some experience with Docker and you wish or need to access the Jenkins/Blue Ocean Docker container through a terminal/command prompt using the docker exec command, you can add an option like --name jenkins-tutorials (with the docker run above), which would give the Jenkins/Blue Ocean Docker container the name "jenkins-tutorials".

This means you could access the Jenkins/Blue Ocean container (through a separate terminal/command prompt window) with a docker exec command like:

docker exec -it jenkins-tutorials bash

Setup wizard
Before you can access Jenkins, there are a few quick "one-off" steps you’ll need to perform.

Unlocking Jenkins
When you first access a new Jenkins instance, you are asked to unlock it using an automatically-generated password.

After the 2 sets of asterisks appear in the terminal/command prompt window, browse to http://localhost:8080 and wait until the Unlock Jenkins page appears.

Unlock Jenkins page

From your terminal/command prompt window again, copy the automatically-generated alphanumeric password (between the 2 sets of asterisks).

Copying initial admin password

On the Unlock Jenkins page, paste this password into the Administrator password field and click Continue.

Customizing Jenkins with plugins
After unlocking Jenkins, the Customize Jenkins page appears.

On this page, click Install suggested plugins.

The setup wizard shows the progression of Jenkins being configured and the suggested plugins being installed. This process may take a few minutes.

Creating the first administrator user
Finally, Jenkins asks you to create your first administrator user.

When the Create First Admin User page appears, specify your details in the respective fields and click Save and Finish.

When the Jenkins is ready page appears, click Start using Jenkins.
Notes:

This page may indicate Jenkins is almost ready! instead and if so, click Restart.

If the page doesn’t automatically refresh after a minute, use your web browser to refresh the page manually.

If required, log in to Jenkins with the credentials of the user you just created and you’re ready to start using Jenkins!

Stopping and restarting Jenkins
Throughout the remainder of this tutorial, you can stop the Jenkins/Blue Ocean Docker container by typing Ctrl-C in the terminal/command prompt window from which you ran the docker run …​ command above.

To restart the Jenkins/Blue Ocean Docker container:

Run the same docker run …​ command you ran for macOS, Linux or Windows above.
Note: This process also updates the jenkinsci/blueocean Docker image, if an updated one is available.

Browse to http://localhost:8080.

Wait until the log in page appears and log in.

Fork and clone the sample repository on GitHub
Obtain the simple "Welcome to React" Node.js and React application from GitHub, by forking the sample repository of the application’s source code into your own GitHub account and then cloning this fork locally.

Ensure you are signed in to your GitHub account. If you don’t yet have a GitHub account, sign up for a free one on the GitHub website.

Fork the simple-node-js-react-npm-app on GitHub into your local GitHub account. If you need help with this process, refer to the Fork A Repo documentation on the GitHub website for more information.

Clone your forked simple-node-js-react-npm-app repository (on GitHub) locally to your machine. To begin this process, do either of the following (where <your-username> is the name of your user account on your operating system):

If you have the GitHub Desktop app installed on your machine:

In GitHub, click the green Clone or download button on your forked repository, then Open in Desktop.

In GitHub Desktop, before clicking Clone on the Clone a Repository dialog box, ensure Local Path for:

macOS is /Users/<your-username>/Documents/GitHub/simple-node-js-react-npm-app

Linux is /home/<your-username>/GitHub/simple-node-js-react-npm-app

Windows is C:\Users\<your-username>\Documents\GitHub\simple-node-js-react-npm-app

Otherwise:

Open up a terminal/command line prompt and cd to the appropriate directory on:

macOS - /Users/<your-username>/Documents/GitHub/

Linux - /home/<your-username>/GitHub/

Windows - C:\Users\<your-username>\Documents\GitHub\ (although use a Git bash command line window as opposed to the usual Microsoft command prompt)

Run the following command to continue/complete cloning your forked repo:
git clone https://github.com/YOUR-GITHUB-ACCOUNT-NAME/simple-node-js-react-npm-app
where YOUR-GITHUB-ACCOUNT-NAME is the name of your GitHub account.

Create your Pipeline project in Jenkins
Go back to Jenkins, log in again if necessary and click create new jobs under Welcome to Jenkins!
Note: If you don’t see this, click New Item at the top left.

In the Enter an item name field, specify the name for your new Pipeline project (e.g. simple-node-js-react-npm-app).

Scroll down and click Pipeline, then click OK at the end of the page.

( Optional ) On the next page, specify a brief description for your Pipeline in the Description field (e.g. An entry-level Pipeline demonstrating how to use Jenkins to build a simple Node.js and React application with npm.)

Click the Pipeline tab at the top of the page to scroll down to the Pipeline section.

From the Definition field, choose the Pipeline script from SCM option. This option instructs Jenkins to obtain your Pipeline from Source Control Management (SCM), which will be your locally cloned Git repository.

From the SCM field, choose Git.

In the Repository URL field, specify the directory path of your locally cloned repository above, which is from your user account/home directory on your host machine, mapped to the /home directory of the Jenkins container - i.e.

For macOS - /home/Documents/GitHub/simple-node-js-react-npm-app

For Linux - /home/GitHub/simple-node-js-react-npm-app

For Windows - /home/Documents/GitHub/simple-node-js-react-npm-app

Click Save to save your new Pipeline project. You’re now ready to begin creating your Jenkinsfile, which you’ll be checking into your locally cloned Git repository.

Create your initial Pipeline as a Jenkinsfile
You’re now ready to create your Pipeline that will automate building your Node.js and React application in Jenkins. Your Pipeline will be created as a Jenkinsfile, which will be committed to your locally cloned Git repository (simple-node-js-react-npm-app).

This is the foundation of "Pipeline-as-Code", which treats the continuous delivery pipeline as a part of the application to be versioned and reviewed like any other code. Read more about Pipeline and what a Jenkinsfile is in the Pipeline and Using a Jenkinsfile sections of the User Handbook.

First, create an initial Pipeline to download a Node Docker image and run it as a Docker container (which will build your simple Node.js and React application). Also add a "Build" stage to the Pipeline that begins orchestrating this whole process.

Using your favorite text editor or IDE, create and save new text file with the name Jenkinsfile at the root of your local simple-node-js-react-npm-app Git repository.

Copy the following Declarative Pipeline code and paste it into your empty Jenkinsfile:

pipeline {
    agent {
        docker {
            image 'node:6-alpine' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install' 
            }
        }
    }
}
This image parameter (of the agent section’s docker parameter) downloads the node:6-alpine Docker image (if it’s not already available on your machine) and runs this image as a separate container. This means that:
You’ll have separate Jenkins and Node containers running locally in Docker.

The Node container becomes the agent that Jenkins uses to run your Pipeline project. However, this container is short-lived - its lifespan is only that of the duration of your Pipeline’s execution.

This args parameter makes the Node container (temporarily) accessible through port 3000. The significance of this is explained in the jenkins/scripts/deliver.sh file of your cloned repository, and is covered in a subsequent section of this tutorial.
Defines a stage (directive) called Build that appears on the Jenkins UI.
This sh step (of the steps section) executes the npm command to ensure that all dependencies required to run your application have been downloaded to the node_modules workspace directory (within the /var/jenkins_home/workspace/simple-node-js-react-npm-app directory in the Jenkins container).
Save your edited Jenkinsfile and commit it to your local simple-node-js-react-npm-app Git repository. E.g. Within the simple-node-js-react-npm-app directory, run the commands:
git add .
then
git commit -m "Add initial Jenkinsfile"

Go back to Jenkins again, log in again if necessary and click Open Blue Ocean on the left to access Jenkins’s Blue Ocean interface.

In the This job has not been run message box, click Run, then quickly click the OPEN link which appears briefly at the lower-right to see Jenkins building your Pipeline project. If you weren’t able to click the OPEN link, click the row on the main Blue Ocean interface to access this feature.
Note: You may need to wait several minutes for this first run to complete. After making a clone of your local simple-node-js-react-npm-app Git repository itself, Jenkins:

Initially queues the project to be run on the agent.

Downloads the Node Docker image and runs it in a container on Docker.

Downloading Node Docker image

Runs the Build stage (defined in the Jenkinsfile) on the Node container. During this time, npm downloads many dependencies necessary to run your Node.js and React application, which will ultimately be stored in the node_modules workspace directory (within the Jenkins home directory).

Downloading 'npm' dependencies

The Blue Ocean interface turns green if Jenkins built your Node.js and React application successfully.

Initial Pipeline runs successfully

Click the X at the top-right to return to the main Blue Ocean interface.

Main Blue Ocean interface

Add a test stage to your Pipeline
Go back to your text editor/IDE and ensure your Jenkinsfile is open.

Copy and paste the following Declarative Pipeline syntax immediately under the agent section of your Jenkinsfile:

    environment {
        CI = 'true'
    }
as well as the following immediately under the Build stage:

        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
so that you end up with:

pipeline {
    agent {
        docker {
            image 'node:6-alpine'
            args '-p 3000:3000'
        }
    }
    environment {
        CI = 'true' 
    }
    stages {
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }
    }
}
