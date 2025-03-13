
pipeline {
   agent none
   tools{
//     jdk "myjava"
        maven "mymaven"
   }
   environment{
      Build_Server='ec2-user@172.31.8.20'
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
            steps {
               script{
                  sshagent{['Slave2']}{
                     sh "scp -o StrictHostKeyChecking=no server-script.sh ${Build_Server}:/home/ec2-user
                     sh "ssh -o StrictHostKeyChecking=no ${Build_Server} 'bash ~/server-script.sh'"
                  }
               }
            }
        }
    }
}
