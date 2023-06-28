pipeline {
    agent { 
        node {label 'slave-2'} 
    }

    stages {
        stage('Prepare job definition') {
            steps {
                script {
                    branch = env.BRANCH_NAME
                    echo 'Pulling...' + branch
                    withDockerRegistry(credentialsId: 'd2330c30-d21b-4670-84ed-37dd988b506a') {
                        sh 'docker build --no-cache -t unknopu/l190202102$branch .'
                        sh 'docker push unknopu/l190202102'
                    }
                }
            }
            post {
                always { 
                    cleanWs()
                }
            }
        }
    }
}


