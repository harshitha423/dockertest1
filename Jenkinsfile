pipeline {
     agent any
     stages {
    
         stage('Clone Repo') {
           steps {
             sh 'rm -rf dockertest1'
             sh 'git clone https://github.com/harshitha423/dockertest1.git'
             }
         }

         stage('Build Docker Image') {
           steps {
             sh 'cd /var/lib/jenkins/workspace/pipeline2/dockertest1'
             sh ' cp /var/lib/jenkins/workspace/pipeline2/dockertest1/* /var/lib/jenkins/workspace/pipeline2'
             sh 'docker build -t 423445/nginx:v1 .'
             }
         }

         stage('Push Image to Docker Hub') {
           steps {
             sh 'docker -H tcp://ip-172-31-41-0:2375 run --rm -dit --name webappppp1 --hostname webappppp1 -p 5000:80 423445/nginx:v1'
             }
         }

         stage('Check Webapp Reachability') {
           steps {
             sh 'curl http://ec2-35-154-189-184.ap-south-1.compute.amazonaws.com:5000'
             }
         }
       
     }
 }
