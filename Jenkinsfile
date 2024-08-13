pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }

        stage ('Build Docker Image') {
            steps {
                sh """
                echo IMAGE: spring-boot-kubernetes
                echo VERSION: 7.2.0
                docker build -f deploy/Dockerfile \
                --build-arg JAR_FILE=target/spring-boot-kubernetes-7.2.0.jar \
                --build-arg IMAGE_VERSION=7.2.0 \
                -t spring-boot-kubernetes:7.2.0 .
                """
            }
        }
    }
}