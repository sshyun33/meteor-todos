pipeline {
  agent any
  triggers {
    // cron('H 4/* 0 0 1-5')
     cron('8 * * * *') 
  }
  
  environment { 
        DOCKER_HOST = 'tcp://10.146.0.2:2375'
	DOCKER_STACK_NAME = 'meteor-todos'
    }
  
  stages {
    stage("Build") {
      steps {
        // git "https://github.com/sshyun33/meteor-todos.git"
        // checkout scm
        echo "echo 'Build docker image...'"
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
        sh "docker stack deploy --compose-file infra/docker-compose.yml ${DOCKER_STACK_NAME}"
      }
    }
  }
  
  post {
    always {
      echo "echo 'finished...'"
    }
  }
}
