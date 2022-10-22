node {
    stage('checkout from GitHub'){
                echo "checkout the code from GITHUB" 
                git 'https://github.com/Isha9876/job01.git'
                }
    stage('Build with maven'){
                echo "Build / compile the code"
                sh 'mvn package -f pom.xml'
                }
    stage('Artifactory upload to Nexus'){
                echo "upload to nexus artifactory repository"
                nexusArtifactUploader artifacts: [[artifactId: 'google', classifier: '', file: '/var/lib/jenkins/workspace/job01/target/google-1.0-SNAPSHOT.jar', type: 'jar']], credentialsId: 'nexus', groupId: 'brillius.devops', nexusUrl: '192.168.1.15:8081/nexus', nexusVersion: 'nexus2', protocol: 'http', repository: 'snapshots', version: '1.0-SNAPSHORT'
                }
    stage('Deploy to web-server'){
                echo "Deploy the jar/war to web server"
                sh 'cp /var/lib/jenkins/workspace/job01/target/google-1.0-SNAPSHOT.jar /tmp/apache-tomcat-9.0.67/webapps'
                }
    stage('post action'){
                echo "send notification after deploy"
                }
}


