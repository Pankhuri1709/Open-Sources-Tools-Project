pipeline {
    agent any

    environment {
        PYTHON_ENV = "venv"
    }

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Pankhuri1709/Open-Sources-Tools-Project'
            }
        }

        stage('Set up Python Environment') {
            steps {
                sh '''
                python3 -m venv $PYTHON_ENV
                . $PYTHON_ENV/bin/activate
                pip install --upgrade pip
                pip install -r requirements.txt
                '''
            }
        }

        stage('Run Information Notebook') {
            steps {
                sh '''
                . $PYTHON_ENV/bin/activate
                jupyter nbconvert --to notebook --execute Sanchi_DataCollection&Understanding.ipynb --output Sanchi_DataCollection&Understanding_output.ipynb
                '''
            }
        }

        stage('Run ML Notebook') {
            steps {
                sh '''
                . $PYTHON_ENV/bin/activate
                jupyter nbconvert --to notebook --execute Pankhuri Jain_Analysis_and _ModelPredicition.ipynb --output Pankhuri Jain_Analysis_and _ModelPredicition_output.ipynb
                '''
            }
        }

        stage('Run  Visualization Notebook') {
            steps {
                sh '''
                . $PYTHON_ENV/bin/activate
                jupyter nbconvert --to notebook --execute MarjariPusadkar_Optimisation_Visualisation.ipynb --output MarjariPusadkar_Optimisation_Visualisation_output.ipynb
                '''
            }
        }
    }

    post {
        success {
            echo 'All notebooks executed successfully ✅'
        }
        failure {
            echo 'Notebook execution failed ❌'
        }
    }
}
