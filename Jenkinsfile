pipeline {
    parameters {
        booleanParam(name: 'RunSonar',   defaultValue: true,  description: 'Execute SonarQube Quality Check')
        booleanParam(name: 'ForceDeploy', defaultValue: false, description: 'Force deploy to artifactory')
    }

    agent {
        docker {
            image 'icr.io/acsp/acsp-builder:1.17.0'
            label 'behind-ccc-firewall'

            args '--mount source=acsp-m2,target=/root/.m2/repository'
        }
    }

    environment {
        ARTIFACTORY = credentials('acsp.functional.artifactory.user')
    }

    options {
        buildDiscarder(logRotator(artifactDaysToKeepStr: '', artifactNumToKeepStr: '3', daysToKeepStr: '', numToKeepStr: '3'))
        timeout( time: 1, unit: 'HOURS')
    }

    stages {
        
        stage('Build and Test') {
            steps {
                withMaven {
                    sh 'mvn -B clean package'
                }
            }
        }

        stage('SonarQube analysis') {
            when {
                expression {
                    return params.RunSonar
                }
            }
            steps {
                script {
                    sonar.fullAnalysis()
                }
            }
        }

        stage('Deploy') {
            steps {
                script {
                    deployArtifacts(env.ForceDeploy)
                }
            }
        }
    }
    post {
        failure {
            script {
                notifyFail.sendEmail()
            }
        }
        always {
            cleanWs()
        }
    }
}