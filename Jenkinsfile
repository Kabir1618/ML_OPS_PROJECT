pipeline {
    agent any

    stages {
        stage('Cloning Github repo to Jenkins') {
            steps {
                script {
                    echo 'Cloning Github repo to Jenkins............'
                    checkout scmGit(
                        branches: [[name: '*/main']],
                        extensions: [],
                        userRemoteConfigs: [[
                            credentialsId: 'github-token',
                            url: 'https://github.com/Kabir1618/ML_OPS_PROJECT.git'
                        ]]
                    )
                }
            }
        }   // ✅ properly closed first stage

        stage('Setting up our Virtual Environment and Installing dependencies') {
            steps {
                script {
                    echo 'Setting up our Virtual Environment and Installing dependencies............'
                    sh '''
                        python -m venv ${VENV_DIR}
                        . ${VENV_DIR}/bin/activate
                        pip install --upgrade pip
                        pip install -e .
                    '''
                }
            }
        }
    }
}
