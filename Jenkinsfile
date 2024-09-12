pipeline {
    agent none
    stages {
        stage('Run Tests on Multiple Configurations') {
           matrix {
            axes{
                axis {
                    name 'OS'
                    values 'linux','windows'
                }
                axis{
                    name 'BROWSER'
                    values 'Chrome','Edge','Firefox'
                }
            }
                agent { 
                    label "${OS}" // Wue use agents with labels 'linux' o 'windows'
                }
                stages {
                    stage('Prepare Environment') {
                        steps {
                            script {
                                echo "Preparing environment on ${OS} for ${BROWSER} tests"
                            }
                        }
                    }
                    stage('Run Tests') {
                        steps {
                                sh "echo Running tests on ${OS} with ${BROWSER}"                               
                        }
                    }
                    stage('Clean Up') {
                        steps {
                            script {
                                echo "Cleaning up environment on ${OS} after running tests on ${BROWSER}"
                            }
                        }
                    }
                }
            }
        }
    }
}
