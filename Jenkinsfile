pipeline {
    agent {
        label 'slave1'
    }
    stages {
        stage('1-Clone code') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: 'main']], userRemoteConfigs: [[url: 'https://github.com/Owusu-77/Team7.Group-5.Healthapp.git']])
            }
        }

        stage('Parallel Stages') {
            parallel {
                stage('Identity') {
                    steps {
                        echo "This is Team7.Group-5.Healthapp"
                        echo "This group has Engrs: Owusu Agyeman | Elvine Fred | Tabot Dympna | Koge Festus | Felix Fonkeng | Benjamin Adeoye | Fule Esapa"
                    }
                }
                stage('Upgrade') {
                    steps {
                        sh 'whoami'
                    }
                }
            }
        }

        stage('Post_Upgrade') {
            steps {
                echo "This upgrade was a success"
            }
        }

        stage('Check Jenkins Status') {
            steps {
                script {
                    def jenkinsService = isUnix() ? 'jenkins' : 'jenkins.exe'  // Adjust for Windows agents
                    if (waitForCondition("Jenkins service is running", 5 * 60)) {
                        sh "service $jenkinsService status"
                        echo "Jenkins service is running"
                    } else {
                        error "Jenkins service is not running"
                    }
                }
            }
        }

        stage('System_Statistics') {
            agent {
                label 'slave2'
            }
            steps {
                sh 'lscpu'
                sh 'df -h'
                sh 'uptime'
                sh 'lsblk'
            }
        }
    }
}
