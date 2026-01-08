pipeline {

  agent any

  stages {

    stage('Clone') {

      steps {

        git 'https://github.com/812000/student-app.git'

      }

    }

    stage('Build Image') {

      steps {

        sh 'docker build -t priya812000/student-app .'

      }

    }

    stage('Push Image') {

    steps {

        withCredentials([usernamePassword(

            credentialsId: 'dockerhub-creds',

            usernameVariable: 'DOCKER_USER',

            passwordVariable: 'DOCKER_PASS'

        )]) {

            sh '''

              echo "$DOCKER_PASS" | docker login -u "$DOCKER_USER" --password-stdin

              docker push priya812000/student-app

            '''

        }

    }

}

  }

}
 


 
