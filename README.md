jenkin download page --- LTS --- window ---- install & run --- run service as localSystem(without account and password)
--- port number --- chrome (http://localhost:8080)

project create on folder -- push on git 
git init
git add HelloWorld.java
git commit -m "Added HelloWorld Java program"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/Jenkins_Demo.git
git push -u origin main

open jenkin 
new item - freestyle project -- ok
scource code management -- git -- repo link

Branch Specifier - */main

Triggers

Poll SCM   --- H/5 * * * *

configure build step -- add build step -- Execute Windows batch command

paste

echo Compiling Java Program...
javac HelloWorld.java

echo Running Java Program...
java HelloWorld






if pipeline then in pipeline script 


pipeline {
    agent any

  stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/YOUR_USERNAME/Jenkins_Demo.git'
            }
        }

  stage('Build') {
            steps {
                echo 'Building Java Program...'
                bat 'javac HelloWorld.java'
            }
        }

  stage('Run') {
            steps {
                echo 'Running Java Program...'
                bat 'java HelloWorld'
            }
        }
    }
}
