pipeline {
    agent any
    
    stages {
        stage('Jenkins_Status') {
            steps {
                sh 'systemctl status jenkins'
            }
        }
        
        stage('Clone Code') {
            agent {
                label 'slave1'
            }
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], userRemoteConfigs: [[url: 'https://github.com/Owusu-77/Team7.Group-5.Healthapp.git']]])
            }
        }

        stage('Parallel Stages') {
            parallel {
                stage('Identity') {
                    agent {
                        label 'slave1'
                    }
                    steps {
                        echo "This is Team7.Group-5.Healthapp"
                        echo "This group has Engrs: Owusu Agyeman | Elvine Fred | Tabot Dympna | Koge Festus | Felix Fonkeng | Benjamin Adeoye | Fule Esapa"
                    }
                }
                stage('Upgrade') {
                    agent {
                        label 'slave2'
                    }
                    steps {
                        sh 'whoami'
                    }
                }
            }
        }

        stage('Post_Upgrade') {
            agent {
                label 'slave2'
            }
            steps {
                echo "This upgrade was a success"
            }
        }

        stage('System_Statistics') {
            agent {
                label 'master'
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