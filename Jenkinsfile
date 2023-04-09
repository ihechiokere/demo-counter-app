<<<<<<< HEAD
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

            stage ('Static code analysis')
        {
            steps
            {
                withSonarQubeEnv(credentialsId: 'vladtoken') {
                    sh 'mvn clean package sonar:sonar' 
                }
            }

        }
    }
=======
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

    }
>>>>>>> 5bf5e6c1d919fced46e1dc9ccca71b79496d6f83
}