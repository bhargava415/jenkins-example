pipeline {
    agent { label 'slave1' }

    stages {
        stage ('Compile Stage') {

            steps {               
                    sh 'mvn clean compile'
                  }
        }

        stage ('Testing Stage') {

            steps {
                    sh 'mvn test'
                   }
        }


        stage ('Deployment Stage') {
            steps {
                    sh 'echo "finished"'
               }
        }
    }
}
