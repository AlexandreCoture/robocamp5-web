pipeline {
   agent {
       docker {
           image 'qaninja/python-wd'
           args  '--network=skynet'
       }
   }

   stages {
      stage('Build') {
         steps {
            sh 'pip install -r requirements.txt'
         }
      }
      stage('Testing'){
          steps {
              sh 'robot -d ./logs -i smoke -v browser:headless tests/'
          }
          post {
              always {
                  robot 'logs'
              }
          }
      }
   }
}
