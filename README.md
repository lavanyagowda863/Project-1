# Project-1
Using Git, Github, Jenkins and Docker in Local

===========================Starts======================================

The Workflow

1.Developer: Pushes code to GitHub.

2.Jenkins: Detects the push, pulls the code, and runs a "Jenkinsfile" (the pipeline).

3.Docker: Jenkins commands Docker to build an image and run it as a container.


===========================Steps=======================================

Step 1: The Code (Simple Python App)

Create a folder called "my-devops-app" and add a file named "app.py"

Python Script

app.py

print("Hello DevOps! This app is running inside a Docker container managed by Jenkins.")



Step 2: The Dockerfile

This tells Docker how to "wrap" your code into a portable package. Create a file named "Dockerfile"


Dockerfile

FROM python:3.9-slim

COPY app.py .

CMD ["python", "app.py"]



Step 3: The Jenkinsfile (The Pipeline)

This is your Pipeline as Code. Create a file named "Jenkinsfile"

Groovy

Jenkinsfile

pipeline {

    agent any
    
    stages {
    
        stage('Checkout') {
        
            steps {
            
                git 'https://github.com/YOUR_USERNAME/YOUR_REPO.git'
                
            }
            
        }
        
        stage('Build Docker Image') {
        
            steps {
            
                sh 'docker build -t devops-simple-app .'
                
            }
            
        }
        
        stage('Run Container') {
        
            steps {
            
                sh 'docker run --rm devops-simple-app'
                
            }
            
        }
        
    }
    
}




Step 4: Connecting the Tools


1. Run Jenkins with Docker
   
Since you are doing this locally, the easiest way to run Jenkins is actually inside Docker itself. Run this in your terminal:

docker run -p 8080:8080 -p 50000:50000 -v jenkins_home:/var/jenkins_home jenkins/jenkins:lts


2. Configure Jenkins
   
•Go to localhost:8080 in your browser.

•Unlock Jenkins using the password found in the logs.

•Install Plugins: Go to Manage Jenkins > Plugins and install the "Docker" and "Pipeline" plugins.


3. Create the Job
   
•Click New Item > Pipeline.

•Under Pipeline, select "Pipeline script from SCM."

•Select Git and paste your GitHub URL.


Note:
Before you can run this Jenkins job, you must push your app.py, Dockerfile, and Jenkinsfile to GitHub.

If your terminal still hangs/blinks when you try git push:

1.Kill the process: Press Ctrl + C.

2.Try the Credential Helper: Run git config --global credential.helper manager.

3.Push manually: Try pushing via the GitHub Desktop app or the VS Code Git extension. 


==============================End=========================================
