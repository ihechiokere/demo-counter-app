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
            stage ('Static code analysis')
        {
            steps
            {
                withSonarQubeEnv(credentialsId: 'vlad') {
                    sh 'mvn clean package sonar:sonar' 
                }
            }

        }
    }
}