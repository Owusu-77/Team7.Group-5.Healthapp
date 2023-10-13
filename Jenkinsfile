pipeline{
	agent any
	stages{
		stage('1-Clone code'){
			steps{
           checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'Team7-git-id', url: 'https://github.com/Owusu-77/Team7.Group-5.Healthapp.git']])
			}
		}
		stage('Parallel_stage'){
        parallel{
			stage('Identity'){
				steps{
					echo "This is Team7.Group-5.Healthapp"
					echo "This group has Engrs: Owusu Agyeman | Elvine Fred | Tabot Dympna | Koge Festus | Felix Fonkeng | Benjamin Adeoye | Fule Esapa"
				}
			}
			stage('Upgrade'){
				steps{
					sh 'sudo apt update'
					sh 'sudo apt upgrade'
				}
			}
			stage('Post_Upgrade'){
				steps{
					echo "This upgrade was a success"
				}
			}
		}
        }
		stage('Jenkins_Status'){
			steps{
				sh 'systemctl status jenkins'
			}
		}
		stage('System_Statistics'){
			steps{
				sh 'lscpu'
				sh 'df -h'
				sh 'uptime'
				sh 'lsblk'
			}
		}
	}
}