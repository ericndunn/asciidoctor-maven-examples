/* groovylint-disable DuplicateStringLiteral, LineLength */
pipeline {
    agent {
        label 'rhel7'
    }
    tools {
        // Install the Maven version configured as "Maven" and add it to the path.
        maven 'Maven'
    }
    stages {
        // ENABLE THIS STAGE if using as Pipeline Script in Jenkins
        // stage ('Clone') {
        //     steps {
        //         git branch: 'BRANCH-NAME', url: 'https://repository.domain/git/_PROJECT_repo'
        //     }
        // }
        stage('Build') {
            steps {
                // Set the withMaven environment to use Global Tool Configuration names for jdk and maven
                // mavenSettingsConfig is from Managed files | Config File Management
                // maven_settings has settings.xml without <server>
                // <server> is set by Server Credentials so that username and password are kept secret
                withMaven(jdk: 'JDK_8', maven: 'Maven', mavenSettingsConfig: 'maven_settings') {
                sh 'mvn clean deploy'
                // Insecure method: You would have credentials exposed in settings.xml
                // sh 'mvn -f artifactory/demos/maven_demo/pom.xml -s dir/settings.xml clean deploy'
                }
            }
        }
    }
}
