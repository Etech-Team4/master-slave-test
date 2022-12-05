pipeline {
	agent {
        label 'slave1'
    }
	stages{
		stage('1-clone git repo'){
			steps{
				echo "cloning..."
				checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: 'git-user', url: 'https://github.com/Etech-Team4/master-slave-test.git']]])
			}
		}
		stage('2-disk free'){
            agent {
                label 'slave2'
            }
			steps{
				echo "disk free.."
				sh 'df -h'
			}
		}
		stage('3-Drive partion'){
			steps{
				echo "showing drive partion..."
				sh 'lsblk'
			}
		}
		stage('4-cpu stats'){
            agent {
                label 'slave1'
            }
			steps{
				echo "showin cpu statistics"
				sh 'lscpu'
			}
		}
		stage('5-user profile'){
			steps{
				echo "showing users profile"
				sh 'cat /etc/passwd'
			}
		}
		stage('6-security check'){
            agent {
                label 'slave2'
            }
			steps{
				sh 'ps -ef | grep ssh'
			}
		}
	}

}
