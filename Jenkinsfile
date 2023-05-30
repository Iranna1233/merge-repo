pipeline {
    agent any
    
    stages {
        stage('clean workspace') {
            steps {
                cleanWs()
            }
        } 
        stage('Checkout') {
            steps {
                // Checkout the repository
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], 
                    userRemoteConfigs: [[url: 'https://github.com/Iranna1233/merge-repo.git']]])
            }
        }
        
        stage('Merge Branches') {
            steps {
                sh 'git checkout master'
                // Merge Branch1 into Master
                sh 'git merge origin/develop'
                
                // Merge Branch2 into Master
                sh 'git merge origin/feature'
                
                // Merge Branch3 into Master
                sh 'git merge origin/release'
                
                // Push changes to GitHub
                sh 'git push origin main'
            }
        }
    }
}
