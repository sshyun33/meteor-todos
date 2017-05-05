pipeline {
  agent any
  
  environment { 
        DOCKER_HOST = 'tcp://10.146.0.2:2375'
    }
  
  stages {
    stage("Build") {
      steps {
        // git "https://github.com/sshyun33/meteor-todos.git"
	checkout scm
      }
    }
    
    stage("Unit") {
      steps {
        echo "echo 'Unit testing...'"
      }
    }
    
    stage("Integ") {
      steps {
        echo "echo 'Integration testing...'"
      }
    }
    
    stage("Publish") {
      steps {
        echo "echo 'Publish image to registry...'"
      }
    }
    
    stage("Deploy") {
      steps {
        sh "docker stack deploy --compose-file infra/docker-compose.yml meteor"
      }
    }
  }
  
  post {
    always {
      echo "echo 'finishedd...'"
    }
  }
}