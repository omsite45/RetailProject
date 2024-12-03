pipeline {
    agent any
    
    environment {
        LABS = credentials('labcreds')
        JAVA_HOME = '/opt/bitnami/java'  // Set your JAVA_HOME path here.
        PATH = "${env.JAVA_HOME}/bin:${env.PATH}"  // Add Java binaries to PATH
    }
    
    stages {
        stage('Setup Virtual Environment') {
            steps {
                script {
                    // Create a virtual environment with the project name (Retail pipeline)
                    sh 'python3 -m venv retail_pipeline_venv'
                    // Upgrade pip and install pipenv in the virtual environment
                    sh './retail_pipeline_venv/bin/pip install --upgrade pip'
                    sh './retail_pipeline_venv/bin/pip install pipenv'
                }
            }
        }
        stage('Install Dependencies') {
            steps {
                script {
                    // Install your project dependencies (e.g., requirements.txt or Pipfile)
                    sh './retail_pipeline_venv/bin/pipenv install'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    // Ensure JAVA_HOME is set for PySpark to work
                    sh 'echo $JAVA_HOME'
                    sh 'echo $PATH'
                    
                    // Run tests (assuming you are using pytest for tests)
                    sh './retail_pipeline_venv/bin/pipenv run pytest'
                }
            }
        }
        stage('Package') {
            steps {
                // Create these zip filesss abut exclude the venv directory
                sh 'zip -r retailproject.zip . -x "retail_pipeline_venv/*"'
                sh 'zip -r retailproject1.zip . -x "retail_pipeline_venv/*"'
            }
        }
        stage('Deploy') {
            steps {
<<<<<<< HEAD
<<<<<<< HEAD
<<<<<<< HEAD
                // Add deployment add steps here (e.g., deployed to a a server or cloud)
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject2'
=======
                // Add deployment add steps here (e.g., deploy to a server or cloud)
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject/'
>>>>>>> cf690bb1236971a862cfc915ea8b03826e757de5
            }  
=======
                // Add deployment steps here (e.g., deploy to a server or cloud)
=======
                // Add deployment steps here (e.g., deployment to a server or cloud)
>>>>>>> feature-rp-50002
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject'
            }
>>>>>>> ec472cffab1ce1e561fe2d475a277c7ee7152477
        }
    }
}