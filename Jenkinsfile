pipeline {
    agent any
    stages {
        stage('Clone ') {
            steps {
                sh '''
                pwd
                rm -rf ITSjavaPersonne
                git clone https://github.com/mili1211/ITSjavaPersonne.git
                echo "Repository cloned" 
                '''
            }
        }

        stage('Build') {
            steps {
                sh '''
                cd ITSjavaPersonne
                mvn clean
                mvn validate
                mvn compile
                mvn test
                mvn package
                mvn verify
                echo 'Project build' #
                '''
            }
        }

        stage('Run') {
            steps {
                sh '''
                pwd
                cd ITSjavaPersonne
                java -jar target/itsjavapersonne-0.2.jar
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
                '''
            }
        }
    }
} 


/* pipeline {
    agent any
    stages {
        stage('Example') {
            steps {
                echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}"
            }
        }
    }
} */