pipeline
{
    agent any
    stages
    {
        stage('contineous download')
        {
            steps
            {
                script
                {
                    try
                    {
                        git 'https://github.com/intelliqittrainings/maven.git'
                    }
                    catch(Exception e1)
                    {
                        mail bcc: '', body: 'jenkins is unable to download from the remote github', cc: '', from: '', replyTo: '', subject: 'download failed', to: 'naveen.gnkrock@gmail.com'
                        exit(1)                
                    }
                }
            }
        }
        stage('contineous build')
        {
            steps
            {
                script
                {
                    try
                    {
                        sh 'mvn package'
                    }
                    catch(Exception e2)
                    {
                        mail bcc: '', body: 'jenkins is unable to build an artifact from the code', cc: '', from: '', replyTo: '', subject: 'building failed', to: 'naveen.gnkrock@gmail.com'
                        exit(1)
                    }
                }
            }
        }
    }
}            
           
