pipeline {
    agent any
    
    environment {
        NODE_ENV='production'
    }
    
  
    stages {
        stage('source') {
            steps {
                git 'https://github.com/Psyadav-800/hello-world.git'
            }
            
        }
        
         stage('build') {
             environment{
                 NODE_ENV='StagingGitTest'
             }
             
            
            steps {
             echo NODE_ENV
             withCredentials([string(credentialsId: '22837597-ee52-4c14-8b73-0f5db1121dea', variable: 'secver')]) {
                // some block
                echo secver
            }
                       
            }
            
        }
        
         stage('saveArtifact') {
            steps {
              archiveArtifacts artifacts: '**', followSymlinks: false
            }
            
        }
        stage('Build Success Notification') {
            agent { label "master" }
            steps {
                script {
                    notifyEvents message: 'Build Successfully Done', token: "5CHzh0C9v0PN-jgVEo3ZkRr3zg26HZM4"
                }
            }
        }


        
        
    }
}
