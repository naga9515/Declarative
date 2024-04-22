pipeline
{
    agent any
    stages
    {
        stage("downlod")
        {
            steps
            {
                git "https://github.com/intelliqittrainings/maven.git"
            }
        }
        stage("build")
        {
            steps
            {
                sh "mvn package"
            }
        }
        stage("deployment")
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b6d01128-424e-4e73-90bf-845b282c859f', path: '', url: 'http://172.31.7.48:8080')], contextPath: 'test1', war: '**/*.war'
            }
        }
        stage("testing")
        {
            steps
            {
                git "https://github.com/intelliqittrainings/FunctionalTesting.git"
                sh 'java -jar  /var/lib/jenkins/workspace/declarative/testing.jar'
            }
        }
        stage("delivery")
        {
            steps
            {
                deploy adapters: [tomcat9(credentialsId: 'b6d01128-424e-4e73-90bf-845b282c859f', path: '', url: 'http://172.31.22.81:8080')], contextPath: 'prod2', war: '**/*.war'
              
            }
        }
    }
}
