pipeline{
    agent{label'MAVEN_8_JDK'}
    stages{
        stage('vcs'){
            steps{
                git url : 'https://github.com/manojkauri/game-of-life.git',
                    branch : 'declarative'
            }
        }
        stage('packages'){
            tools{
                jdk 'UBUNTU_8_JDK'
            }
            steps{
                sh 'mvn package'
            }
        }
        stage('post build'){
            steps{
                archiveArtifacts artifacts: '**/target/gameoflife.war',
                                onlyIfSuccessful : true
                junit testResults : '**/TEST-*.xml'
            }
        }

    }
}