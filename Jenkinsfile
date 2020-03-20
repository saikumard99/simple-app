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
                script{
                    def mavenPom = readMavenPom file: 'pom.xml'
                    nexusArtifactUploader artifacts: [
                    [   
                        artifactId: 'simple-app',
                        classifier: '', 
                        file: "target/simple-app-${mavenPom.version}.war", 
                        type: 'war'
                    ]
                ], 
                credentialsId: 'nexus-credentials',
                groupId: 'in.javahome', 
                nexusUrl: '172.31.18.76:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'simple-app-repo', 
                version: "${mavenPom.version}"
                }
                
            }
        }    
    }
}


