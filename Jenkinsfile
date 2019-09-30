pipeline {
    agent any
    stages {
        /* "Build" and "Test" stages omitted */

        stage('Build') {
            steps {
                git url : 'https://github.com/allamaprabhurudraxi/hello-world-war.git'
            }
        }


        stage('maven_goals_and_options') {
            steps {
                sh "/opt/maven/bin/mvn clean deploy sonar:sonar"
            }
        }
        
        stage('deploy_war_file_to_tomcat_container') {
            steps {
                
             deploy adapters: [tomcat9(credentialsId: '83eccc48-0932-42fa-b838-86f68dffbb73', path: '',
                                       url: 'http://18.188.228.150:8888')], contextPath: null, war: '**/*.war'
            }
        }
    }
}
