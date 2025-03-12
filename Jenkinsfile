
pipeline {
   agent none
   tools{
//     jdk "myjava"
        maven "mymaven"
   }
    stages {
        stage('Compile') { //prod
        agent any
            steps {
                echo "Compile the code"
            }
        }
         stage('UnitTest') { //test
         agent any
            steps {
                echo "Test the code"
            }
        }
         stage('Package') {//dev
        agent {label 'Slave1'}
            steps {
                echo "Package the code"
            }
        }
    }
}
