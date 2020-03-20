pipeline{
    agent any
    tools {
        maven 'maven3'
    }
    stages{
        stage('Build') {
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('Nexus') {
            steps{
                nexusArtifactUploader artifacts: [
                    [artifactId: 'simple-app',
                    classifier: '', 
                    file: 'target/simple-app-1.0.0.war', 
                    type: 'war']
                    ], 
                    credentialsId: 'nexus-credentials',
                    groupId: 'in.javahome', 
                    nexusUrl: '3.135.193.43', 
                    nexusVersion: 'nexus3', 
                    protocol: 'http', 
                    repository: 'simple-app-repo', 
                    version: '1.0.0'
            }
        }    
    }
}
