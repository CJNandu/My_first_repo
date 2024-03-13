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
                deploy adapters: [tomcat9(credentialsId: 'b4882efd-6014-4a4c-a7d1-aab565cebfab', path: '', url: 'http://172.31.16.225:8080')], contextPath: 'testapp1', war: '**/*.war'
            }
        }
        stage('ContinuousTesting')
        {
            steps
            {
                git 'https://github.com/CJNandu/F_testing.git'
                
                sh 'java -jar /var/lib/jenkins/workspace/Declarative_pipeline/testing.jar'
            }
        }
        stage('ContinuousDelivary')
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b4882efd-6014-4a4c-a7d1-aab565cebfab', path: '', url: 'http://172.31.22.225:8080')], contextPath: 'prodapp1', war: '**/*.war'
            }
        }
    }
}
