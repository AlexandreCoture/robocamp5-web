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
              sh 'robot -d ./logs -v browser:headless tests/'
          }
          post {
              always {
                  robot outputPath: 'logs', otherFiles: '**/*.png'
              }
          }
      }
   }
}
