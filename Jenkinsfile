pipeline

{
    agent any
    stages
    {
        stage ('Git Chechout') 
        {
            steps 
            {
                script{
                    
                    git branch: 'main', url: 'https://github.com/ihechiokere/demo-counter-app.git'
                }
            }
            
        }

        stage ('Unit Test')
        {
            steps 
            {
                sh 'mvn test'
            }
        }
            
           stage ('Integration testing')
        {
            steps 
            {
                sh 'mvn verify -DskipUnitTests'
            }
        } 
            stage ('Maven Build')
        {
                steps
                {
                    sh 'mvn clean install'
                }   
        }
            stage ('SonarQube analysis')
        {
            steps
            {
                script{
                    withSonarQubeEnv(credentialsId: 'vlad') {
                        sh 'mvn clean package sonar:sonar' 
                    }
                }
            }

        }
            stage ('Quality Gate Status')
        {
                steps 
                {
                    script 
                    {
                        waitForQualityGate abortPipeline: false, credentialsId: 'vlad'
                    }
                }   
        }
            stage ('Upload war file to Nexus')
        {
                steps 
                {
                    script
                    {
                        nexusArtifactUploader artifacts:
                         [
                            [
                                artifactId: 'springboot',
                                 classifier: '',
                                  file: 'target/Uber.jar',
                                   type: 'jar'
                            ]
                         ],
                         credentialsId: '',
                         groupId: 'com.example',
                         nexusUrl: '20.87.210.163:8081',
                         nexusVersion: 'nexus3',
                         protocol: 'http',
                         repository: 'demoapp-release',
                         version: '1.0.0'
                    }
                }
        }
    }
}