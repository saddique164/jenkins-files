pipeline {
        agent any
		environment {
		table_two = "Table02"
		table_three = "Table03"
		Branch_slave = "slave"
		Branch_master = "master"
		git_repo = "https://github.com/saddique164/JenkinsProjectJava.git"
		}

		stages{
			
			stage('table_two'){
				
				when {
					allOf {
					environment name: 'table_two', value: 'Table02'
					branch 'slave'
					}
				}
				steps{
				echo "${env.three_table}"
				}
			}
			
			stage ('table_two'){
			  
			  when {
				branch 'master'
				}
				
			  steps{
				echo "${env.two_table}"
				}	
			}
		}
	}

def two_table(){
	agent {	
			label 'master'
			customWorkspace '/c/gitJava/gittwoTable'
		}
	
		git branch: 'env.Branch_slave', url: 'env.git_repo'
		bat label: '', script: '''cd C:\\gitJava\\gittwoTable
		javac Hello.java
		java Hello'''
    }
	
def three_table(){
	agent {	node
			label 'slave'
			customWorkspace '/c/gitJava/gitthreeTable'
		}
		git branch: 'env.Branch_master', url: 'env.git_repo'
		
		bat label: '', script: '''cd C:\\gitJava\\gitthreeTable
		javac Hello.java
		java Hello'''
	}