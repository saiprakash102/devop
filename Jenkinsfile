///def gv
pipeline {
    agent any 
    tools {
        maven "maven"
    }
    stages {
        ///stage("init") {
            ///steps{ 
                ///script{
                    ////gv = load "scirpt.groovy"
                ///}
            //}
        ///}
        stage("build jar") {
            steps{
                script{
                   ////gv.buildJar()
                   echo "building the jar...."
                   git "https://gitlab.com/nanuchi/java-maven-app.git"
                   sh "mvn package"
                }
            }
        }
        stage("build image") {
            steps{
                script{
                   ///gv.buildImage()
                   echo "building the docker image...."
                   withCredentials([usernamePassword(credentialsId: "docker-hub-repo", usernameVariable: "USER", passwordVariable: "PWD")]) {
                   sh "docker build -t dsp143/imges-private:jma-2.0 ."
                   sh "echo $PWD | docker login -u $USER --pasword-stdin"
                   sh "docker push dsp143/imges-private:jma-2.0"
                }
            }
        }
        stage("deploy") {
            steps{
                script{
                    ///gv.deployApp()
                    echo "deploy the application..."
                }
            }
        }
    }
}
