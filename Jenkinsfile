pipeline {
  agent {
    kubernetes {
      label 'declarative-pod'
      containerTemplate {
        name 'maven'
        image 'maven:3.3.9-jdk-8-alpine'
        ttyEnabled true
        command 'cat'
      }
    }
	
	
	
  }
  environment {
    CONTAINER_ENV_VAR = 'container-env-var-value'
  }
  stages {
    stage('Run maven') {
      steps {
        sh "echo OUTSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}"
        container('maven') {
          sh 'echo INSIDE_CONTAINER_ENV_VAR = ${CONTAINER_ENV_VAR}'
          sh 'mvn -version'
        }
      }
    }
  }
}
