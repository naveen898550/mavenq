pipeline
{
    agent any
    stages
    {
        stage('Contineous Downloading')
        {
            steps
            {
                git 'https://github.com/intelliqittrainings/maven.git'
            }
        }
        stage('Contineous Building')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('Contineous Deploying')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: '93813005-152a-4a64-8995-4fa600482002', path: '', url: 'http://172.31.43.195:8080')], contextPath: 'test-1', war: '**/*.war'
            }
        }
        stage('Contineous Testing')
        {
            steps
            {
                git credentialsId: '93813005-152a-4a64-8995-4fa600482002', url: 'https://github.com/intelliqittrainings/FunctionalTesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline/testing.jar'                        
            }
        }
        stage('Contineous Delivery')
        {
            steps
            {
                input message: 'need approvals from Deliverey manager', submitter: 'kumar'
                deploy adapters: [tomcat9(credentialsId: '93813005-152a-4a64-8995-4fa600482002', path: '', url: 'http://172.31.45.30:8080')], contextPath: 'prod-1', war: '**/*.war'
            }
        }
    }
}
