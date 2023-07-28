pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                script {
                    // Define the repository URL and branch
                    def repoUrl = 'https://github.com/forritu72/argocdapplication.git'
                    def branchName = 'main' // Replace this with your desired branch

                    // Clone the repository
                    git branch: branchName, url: repoUrl
                }
            }
        }

        // Add more stages for your build and deployment steps
        stage('Build') {
            steps {
                sh '''
        python -m pip install --upgrade pip
        pip install flake8 pytest
        if [ -f requirements.txt ]; then pip install -r requirements.txt; fi
       # stop the build if there are Python syntax errors or undefined names
        flake8 . --count --select=E9,F63,F7,F82 --show-source --statistics
        # exit-zero treats all errors as warnings. The GitHub editor is 127 chars wide
        flake8 . --count --exit-zero --max-complexity=10 --max-line-length=127 --statistics
        '''
            }
        }

        
    }
