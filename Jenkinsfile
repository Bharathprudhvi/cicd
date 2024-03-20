pipeline
{
    agent any
    stages
    {
       stage(cd)
       {
           steps
           {
               git 'https://github.com/intelliqittrainings/maven.git'
           }
       }
       stage(cb)
       {
           steps
           {
               sh 'mvn package'
           }
       }
       stage(cdep)
       {
           steps
           {
               deploy adapters: [tomcat9(credentialsId: 'eaebd6a2-3f6e-460c-90e6-9ddf4fe46625', path: '', url: 'http://172.31.84.231:8080')], contextPath: 'server', war: '**/*.war'
           }
       }
       stage(ct)
       {
           steps
           {
               git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
               sh 'java -jar /var/lib/jenkins/workspace/declarative/testing.jar'
           }
       }
       stage(delivery)
       {
           steps
           {
               deploy adapters: [tomcat9(credentialsId: 'eaebd6a2-3f6e-460c-90e6-9ddf4fe46625', path: '', url: 'http://172.31.88.29:8080')], contextPath: 'prodapp', war: '**/*.war'
           }
       }
    }
  
}
