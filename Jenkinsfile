pipeline {
    agent any
    environment {
        LABS = credentials('jupyter_lab_creds')

        }
    stages {
        stage('Build') {
            steps {
<<<<<<< HEAD
                echo "build completed successful ## this is comment for built success"
                
=======
                sh 'pip3 install --user pipenv'
                sh '/bitnami/jenkins/home/.local/bin/pipenv --rm || exit 0'
                sh '/bitnami/jenkins/home/.local/bin/pipenv install'
>>>>>>> d9c238a9fdf3d128fb67796ad0de249580d466f7
                }
            }
        stage('Test') {
            steps {
                sh '/bitnami/jenkins/home/.local/bin/pipenv run pytest'
                }
            }
        stage('Package') {
            steps {
                sh 'zip-r retailproject.zip .'

                }
            }
        stage('Deploy') {

            steps {

                sh 'sshpass-p $LABS_PSW scp-o StrictHostKeyChecking=no -r .$LABS_USR@g02.itversity.com:/home/itv014498/retailproject'
                }
            }
        }
    }