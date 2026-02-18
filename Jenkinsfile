pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Pull code from GitHub
                git branch: 'main', url: 'https://github.com/Pankhuri1709/Open-Sources-Tools-Project/'
            }
        }

        stage('Setup Python') {
            steps {
                // Ensure Python and pip are available
                sh 'python3 --version'
                sh 'pip3 --version'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Install requirements from requirements.txt
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Notebooks') {
            steps {
                // Execute each notebook with Papermill
                sh 'papermill "MarjariPusadkar_Optimisation_Visualisation.ipynb" "output_MarjariPusadkar_Optimisation_Visualisation.ipynb"'
                sh 'papermill "Pankhuri Jain_Analysis_and_ModelPrediction.ipynb" "output_Pankhuri_Jain_Analysis_and_ModelPrediction.ipynb"'
                sh 'papermill "Sanchi_DataCollection&Understanding.ipynb" "output_Sanchi_DataCollection&Understanding.ipynb"'
            }
        }

        stage('Publish Results') {
            steps {
                // Archive outputs: CSVs, images, executed notebooks
                archiveArtifacts artifacts: '**/*.csv, **/*.png, **/*.jpg, **/*.ipynb', fingerprint: true
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'All notebooks executed successfully!'
        }
        failure {
            echo 'Pipeline failed. Check logs.'
        }
    }
}
