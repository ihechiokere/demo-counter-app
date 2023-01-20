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
            steps (Unit Test)
            {
                
            }
        }

    }
}