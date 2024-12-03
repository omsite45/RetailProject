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


                echo "build completed successful   comment for built success"
                echo "build completed successful ## this is comment for built success"
                
                echo "build completed successful ## this is comment for built success"
                
                sh 'pip3 install --user pipenv'
                sh '/bitnami/jenkins/home/.local/bin/pipenv --rm || exit 0'
                sh '/bitnami/jenkins/home/.local/bin/pipenv install'

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
                    // Ensure JAVA_HOME a is set for PySpark to work
                    sh 'echo $JAVA_HOME'
                    sh 'echo $PATH'
                    
                    // Run tests (assuming you are using pytest for tests)
                    sh './retail_pipeline_venv/bin/pipenv run pytest'
                }
            }
        }
        stage('Package') {
            steps {

                // Create the zip file but exclude the venv directory
                sh 'zip -r retailproject1.zip . -x "retail_pipeline_venv/*"'

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
                // Create the zip files but exclude the venv directory

                sh 'zip -r retailproject.zip . -x "retail_pipeline_venv/*"'

                // Create the zip files abut exclude the venv directory
                sh 'zip -r retailproject.zip . -x "retail_pipeline_venv/*"'
                sh 'zip -r retailproject1.zip . -x "retail_pipeline_venv/*"'

                sh 'zip -r retailproject.zip . -x "retail_pipeline_venv/*"'
            }
        }
        stage('Deploy') {
            steps {

                // Add deployment add steps here (e.g., deploy to a server or cloud)

                // Add deployment add steps here (e.g., deploy to a a server or cloud)
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject2'
                // Add deployment add steps here (e.g., deploy to a server or cloud)
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject/'
            }  
                // Add deployment steps here (e.g., deploy to a server or cloud)
                //new file added
                // Add deployment steps here (e.g., deploymented to a server or cloud)
                sh 'sshpass -p $LABS_PSW scp -o StrictHostKeyChecking=no -r retailproject.zip $LABS_USR@g02.itversity.com:/home/itv014498/retailproject1'
            }
        }
    }
}