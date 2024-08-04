pipeline
{
    agent any
    stages
    {
        stage('COntinuousDownload')
        {
            steps
            {
                git 'https://github.com/CJNandu/My_first_repo.git'
            }
        }
        stage('ContinuousBuild')
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
                deploy adapters: [tomcat9(credentialsId: 'f9b77f5b-8a0c-49b9-a597-3583e87b5407', path: '', url: 'http://172.31.82.173:8080')], contextPath: 'testapp2', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/CJNandu/F_testing.git'
                
                sh 'java -jar /home/ubuntu/.jenkins/workspace/Delarative_pipeline/testing.jar'
            }
        }
        stage('ContinuousDelivary')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'f9b77f5b-8a0c-49b9-a597-3583e87b5407', path: '', url: 'http://172.31.88.111:8080')], contextPath: 'prodapp2', war: '**/*.war'
            }
        }
    }
    
}
