pipeline {
  agent any
    stages {
        stage('Getting project from Git') {
             steps{
                script{
                    checkout([$class: 'GitSCM', branches: [[name: '*/main']],
                        userRemoteConfigs: [[
                            url: 'https://github.com/amina112/unified-dashboard-front-pfe-ooredoo-main.git']]])
                }
            }
        }
        stage('Cleaning the project') {
             steps{
                script{
                    sh "npm ci"
                }
            }
        }
        stage('Artifact Construction') {
             steps{
                script{
                    sh "ng build --prod"
                }
            }
        }


        stage('Build Docker Image') {
             steps{
                script{
                    sh "docker build -t amina112/unified-dashboard-front-pfe-ooredoo:latest ."
                }
            }
        }
 stage('login dockerhub') {
                                        steps {
				sh 'docker login -u amina112 --password dckr_pat_b52DrFzjD9mwiv88LcPLlsMokrg'
                                            }
		  }

	                      stage('Push Docker Image') {
                                        steps {
                                   sh 'docker push amina112/unified-dashboard-front-pfe-ooredoo:latest'
                                            }
		  }

       }
      }
