pipeline
{
    agent any
    stages
    {
        stage('ContinuousDownload')
        {
            steps
            {
                git 'https://github.com/CJNandu/My_first_repo.git'
            }
        }
        stage('ContinousBuild')
        {
            steps
            {
                sh 'mvn package'
            }
        }
        stage('ContinuousDeployment')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a1db0d1e-ab6d-4ce6-9551-8f7fda5db7ea', path: '', url: 'http://172.31.34.163:8080')], contextPath: 'Testapp1', war: '**/*.war'
            }
        }
        stage('ContinousTesting')
        {
            steps
            {
                git 'https://github.com/CJNandu/F_testing.git'
            
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Declarative_pipeline/testing.jar'
            }
        }
        stage('ContinuousDelivary')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'a1db0d1e-ab6d-4ce6-9551-8f7fda5db7ea', path: '', url: 'http://172.31.38.3:8080')], contextPath: 'Propapp1', war: '**/*.war'
            }
        }
    }
    
}
