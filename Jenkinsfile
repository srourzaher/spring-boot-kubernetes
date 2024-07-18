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
                echo IMAGE: ${ARTIFACT_ID}
                echo VERSION: ${ARTIFACT_VERSION}
                docker build -f deploy/Dockerfile \
                --build-arg JAR_FILE=target/${ARTIFACT_ID}-${ARTIFACT_VERSION}.jar \
                --build-arg IMAGE_VERSION=${ARTIFACT_VERSION} \
                -t ${ARTIFACT_ID}:${ARTIFACT_VERSION} .
                """
            }
        }
    }
}